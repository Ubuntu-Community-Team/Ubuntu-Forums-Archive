---
title: "Creative Sound Blaser Z doesn't work"
date: 2018-08-20
forum: Hardware
---

### Post by soames on 2018-08-20
I have a "Creative Sound Blaser Z" sound card but it doesn't work on Ubuntu 18.04

Ubuntu 18.4 sees that sound card as 
Creative Labs SB1570 SB Audigy Fx

```
lspci -k | grep -iA2 audio
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] SBx00 Azalia (Intel HDA)
	Subsystem: ASRock Incorporation SBx00 Azalia (Intel HDA)
	Kernel driver in use: snd_hda_intel
--
01:00.1 Audio device: NVIDIA Corporation GF108 High Definition Audio Controller (rev a1)
	Subsystem: Gigabyte Technology Co., Ltd GF108 High Definition Audio Controller
	Kernel driver in use: snd_hda_intel
	Kernel modules: snd_hda_intel
02:00.0 Audio device: Creative Labs Sound Core3D [Sound Blaster Recon3D / Z-Series] (rev 01)
	Subsystem: Creative Labs SB1570 SB Audigy Fx
	Kernel driver in use: snd_hda_intel
```

I had found advice in this thread - [https://ubuntuforums.org/showthread.php?t=2326126](https://ubuntuforums.org/showthread.php?t=2326126) but it doesn't work because mu kernel is older

Ubuntu sees only 2 chanels (stereo 2.0) but sound card has 6 chanels (5.1)
There is no sound in any chanel

---

### Post by soames on 2018-08-20
[ATTACH=CONFIG]280791[/ATTACH]


Please do not post large images. Use the attachment functionality provided in the paperclip button in the toolbar above the text entry box. That adds a thumbnail that users can click to enlarge if they choose to. Some users have low bandwidth or data limits.

---

### Post by Yellow Pasque on 2018-08-20
[https://www.phoronix.com/scan.php?page=news_item&px=Recon3D-Linux-Sound-2018](https://www.phoronix.com/scan.php?page=news_item&px=Recon3D-Linux-Sound-2018)

The patches should be easy to try once the ALSA dkms PPA is updated: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

---

### Post by soames on 2018-08-21
> **Temüjin said:**
> [https://www.phoronix.com/scan.php?page=news_item&px=Recon3D-Linux-Sound-2018](https://www.phoronix.com/scan.php?page=news_item&px=Recon3D-Linux-Sound-2018)

The patches should be easy to try once the ALSA dkms PPA is updated: [https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages](https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+packages)

I have installed [oem-audio-hda-daily-dkms_0.201808050301~ubuntu18.04.1_all.deb]("https://code.launchpad.net/~ubuntu-audio-dev/+archive/ubuntu/alsa-daily/+files/oem-audio-hda-daily-dkms_0.201808050301~ubuntu18.04.1_all.deb") but nothing changed

---

### Post by Yellow Pasque on 2018-08-21
The patches are not included in that version. Notice how it says 0805 (August 5th). The patches were pulled into the kernel on August 8th. That's why I said it needed to be updated.

---

### Post by soames on 2018-08-22
> **Temüjin said:**
> The patches are not included in that version. Notice how it says 0805 (August 5th). The patches were pulled into the kernel on August 8th. That's why I said it needed to be updated.

Can I download that patches anywhere and install them manually? Shall I wait pathes included in next PPA version ?

---

### Post by Yellow Pasque on 2018-08-22
You can check out the kernel from git and build it if you really want to.
If you don't know how to build a kernel, you're better off waiting for the PPA to update or for kernel 4.19-rc1 to be released: [http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)

---

### Post by soames on 2018-08-27
The 4.19 kernel was uploaded yesterday.
Can I install it now?

---

### Post by Yellow Pasque on 2018-08-27
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc1/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.19-rc1/)

---

### Post by Yellow Pasque on 2018-08-27
EDIT: Nvm

---

### Post by Yellow Pasque on 2018-08-27
Well, if it Recon3D based, then it appears surround sound is problematic, even with the patches. The author of those patches mentions it here:
[https://www.phoronix.com/forums/forum/software/linux-gaming/1039876-sound-blaster-recon3d-finally-seeing-better-linux-support?p=1040977#post1040977](https://www.phoronix.com/forums/forum/software/linux-gaming/1039876-sound-blaster-recon3d-finally-seeing-better-linux-support?p=1040977#post1040977)

(Sorry to inundate you with posts.)

---

### Post by soames on 2018-08-28
> **soames said:**
> The 4.19 kernel was uploaded yesterday.
Can I install it now?

I have tried it and it better than 4.15 one but not good yet.
alsa mixer with kernel 4.15 sees soundcard as &#1057;reative CA032
alsa mixer 4.19 one sees it as  creative Sound Blaster Z as I need 
alsa mixer have front, center & LFE wit kernel 4.19

I can make 2 or 4 or 6 chanells in alsamixer now

I had only 2 chanells earlier and no sound in anyone of them

I have now sound in 2 chanels - ubuntu sees them as center and subboofer chanels but i hear sound in  rear speakers

---

### Post by soames on 2018-08-28
My alsamixer now [[IMG]http://img11.lostpic.net/2018/08/28/9ceaa1c4b30057f95901c49e565eb6e2.th.png[/IMG]]("http://lostpic.net/image/nUQi")

---

