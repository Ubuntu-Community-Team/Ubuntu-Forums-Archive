---
title: "Installed vokoscreen. Now external microphone makes humming input."
date: 2018-07-18
forum: Hardware
---

### Post by robertcull1 on 2018-07-18
Using 16.04.

I installed vokoscreen and used it to record video and audio of screen. All recordings had a humming sound in the background. So I uninstalled vokoscreen.

My laptops internal microphone works fine. But when I plug in the external microphone to my headphones it makes a loud humming. You can watch the sound level of the microphone in the sound system settings.

$ lspci
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

To compound the problem I installed sound drivers as instructed here:

[https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS](https://wiki.ubuntu.com/Audio/UpgradingAlsa/DKMS)

Now I hear an echo when I play sound. I still have the hum when I record from an external microphone.

I have a conference meeting soon on zoom. Can someone please tell me how to get everything back to normal?

---

