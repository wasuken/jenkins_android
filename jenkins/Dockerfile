FROM jenkins/jenkins:lts
# FROM openjdk:11
USER root

# 環境変数の設定
ENV ANDROID_SDK_ROOT=/opt/android-sdk
ENV PATH=$ANDROID_SDK_ROOT/cmdline-tools/tools/bin:$ANDROID_SDK_ROOT/platform-tools:$PATH

# Android SDKのインストール
RUN apt-get update && apt-get install -y wget unzip && \
    mkdir -p $ANDROID_SDK_ROOT/cmdline-tools && \
    wget https://dl.google.com/android/repository/commandlinetools-linux-8092744_latest.zip -O /opt/cmdline-tools.zip && \
    unzip /opt/cmdline-tools.zip -d $ANDROID_SDK_ROOT/cmdline-tools && \
    yes | $ANDROID_SDK_ROOT/cmdline-tools/cmdline-tools/bin/sdkmanager --sdk_root=$ANDROID_SDK_ROOT "platform-tools" "build-tools;33.0.0" "platforms;android-33"

WORKDIR /workspace

user jenkins
