---
title: "Not online"
date: 2019-08-08
forum: Hardware
---

### Post by torbentf on 2019-08-08
HI,

I can receive a video call and hear the voice and the caller can hear my  voice, but the caller (and I) cannot see my picture or me. The caller says  that I am not online and I get the same message if I try to video call  myself. Here follows my data.

I get:
"We could not connect to your selected camera: Please select a different camera or try restarting Skype. Audio and Video Settings."
and I get a small screen with no picture if I click "Audio and Video Settings". Restarting Skype makes no difference.

lsusb gives:
Bus 001 Device 009: ID 04f2:b520 Chicony Electronics Co., Ltd 
Bus 001 Device 008: ID 8087:0a2a Intel Corp. 
Bus 001 Device 011: ID 1532:0015 Razer USA, Ltd Naga Mouse
Bus 001 Device 006: ID 04a9:172b Canon, Inc. MP140 ser
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I believe the relevant one is Chicony Electronics Co., Ltd 

Video: mpv Media Player

Ubuntu 18.04.3 LTS

Computer: torben-Aspire-E5-773G

I have cleaned my computer of all Skype and reinstalled skype with "snap install skype --classic" which made no difference.

Can anyone help?
torben

---

### Post by ajgreeny on 2019-08-08
My first thought is to remove the snap version you're running at present and then get the version that is available as a .deb from [https://go.skype.com/skypeforlinux-64-preview.deb](https://go.skype.com/skypeforlinux-64-preview.deb)

Download it to your Downloads folder then run command ```
sudo apt install Downloads/skypeforlinux-64-preview.deb
```

This should install it and add the repository for continued updating of the package.

I am sure many will suggest you use something else than skype, but you may be like me, having too many members of your family who use skype and are not going to install anything else however much you may tell them that there are better VOIP applications available.  It took me years to get some of them to try skype, so suggestions of alternatives are met with groans and complete inactivity, so for now, skype it is; and generally I admit it works well.

---

