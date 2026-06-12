---
title: "Stopping Automatic Crash Report Generation [FAIL]"
date: 2012-04-16
forum: Hardware
---

### Post by goaliedude3919 on 2012-04-16
I am in desperate need of help. Earlier today I was trying to get Unity to stop running in 2D mode on my Dell Latitude E6420 laptop running Ubuntu 11.10. After some research I found out it was because of the GPU drivers and I spent a while trying to install other drivers to get it working. I came across one suggestion that said to add the line "UNITY_FORCE_START=1" to the file /etc/environment through gedit. I did so and rebooted my computer. Since then I have not been able to properly boot my computer. It either gets stuck at a blank screen or it gets stuck on a screen where it says "**Stopping Automatic Crash Report Generation [FAIL]" **and everything else says [OK].  I have tried multiple "fixes" for this but none have worked. I tried the nomodeset fix, but that results in the same Crash Report Generation [FAIL]. I should also mention that I went back and deleted the "UNITY_FORCE_START=1" line.

I'm beginning to think this is a lost cause and that it might be best to just backup my files and do a fresh install. I really don't want to do that as I've spent countless hours getting everything how I wanted them. I'm really hoping someone will be able to help me out.

---

### Post by goaliedude3919 on 2012-04-16
I ended up just reinstalling Ubuntu with a Live USB, so this is no longer a problem.

---

