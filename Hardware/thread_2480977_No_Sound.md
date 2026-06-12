---
title: "No Sound"
date: 2022-11-15
forum: Hardware
---

### Post by guy14 on 2022-11-15
Was gifted an older 12 yr old HP SFF desktop with xubuntu, ver.   22.10 kinetic, it runs well but there's no audio, volume control  shows Dummy Output.  I'm told audio worked before the update. Is there  anything I can do?

---

### Post by guy14 on 2022-11-15
The output of lspci shows two sound cards:
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Caicos HDMI Audio [Radeon HD 6450 / 7450/8450/8490 OEM / R5 230/235/235X OEM]

Neither of witch seem to be enabled/ working on this desktop.  However I used a usb live version of mxlinux and there was audio.  So there's something unique between this version of xubuntu and my desktop.  Any suggestions?

---

### Post by &amp;KyT$0P# on 2022-11-15
Does the audio work with Xubuntu 22.04?

---

### Post by guy14 on 2022-11-15
I will download that version and try it on a USB stick.

---

### Post by guy14 on 2022-11-15
Audio works perfect on Xbuntu 22.04

---

### Post by &amp;KyT$0P# on 2022-11-15
> **guy14 said:**
> Audio works perfect on Xbuntu 22.04

Then I would suggest just using Xubuntu 22.04 for now.  It is the latest LTS release: the XFCE components are supported [until April 2025]("https://wiki.xubuntu.org/releases/22.04/release-notes#xubuntu_2204_release_notes") and the base Ubuntu system is supported [until April 2027]("https://wiki.ubuntu.com/Releases").  Whereas all support for 22.10 ends in July 2023.

---

### Post by Claus7 on 2022-11-16
Hello,

> **guy14 said:**
> ...I'm told audio worked before the update. ...

before the update or before the **upgrade**? 

If the latter, then I do not think that there is an easy solution. I had the same issue with ubuntu. I did a clean install in the end. Have you tried a usb stick with kinetic kudu as well? 

You mention that you checked using a stick with 22.04. It worked. That's fine. You could test kinetic as well. If it is working, then it is due to faulty upgrade.

Regards!

---

### Post by Yellow Pasque on 2022-11-17
> **guy14 said:**
> Any suggestions?

Try creating another user and see if audio works for them. If it does, then you probably need to run this as your main user:
```
rm -rf ~/.config/pulse*
```

---

