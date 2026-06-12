---
title: "Help with Ubuntu Hardy on Asus m50vm-a1"
date: 2008-07-28
forum: Hardware
---

### Post by Yoctosecond on 2008-07-28
So far I've been able to get almost everything running fine for this laptop. However, I've stumbled upon two big issues that I can't solve. The biggest being sound. I've tried as much as I could and came out with no results. I'm still fairly new to linux, but I have tried to reinstall alsa and reconfigure the alsa driver compilation. My other problem is that sometimes my network connection doesn't work when I boot up the laptop and refuses to work until I reboot again. Sometimes while in this, Firefox (3.0) is somehow switched to a offline mode. Well, here's the specs for my laptop after lspci. Any help would be much appreciated.
```
00:00.0 Host bridge: Intel Corporation Cantiga Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Cantiga PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0648 (rev a1)
03:00.0 Network controller: Atheros Communications Inc. Unknown device 002a (rev 01)
08:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

```

---

### Post by b4b5 on 2008-08-11
how did u manage to recognase the HD.
?

---

### Post by TwistedLincoln on 2008-08-15
Did you ever find a solution to these network and audio problems?  I have the exact same notebook, and am experiencing the same issues.

---

### Post by pigeon768 on 2008-08-24
I have a similar laptop (m50vm-b2) and also couldn't get alsa working. (on gentoo - not ubuntu. so at least you know it's not an ubunut-specific problem) It was detected as a generic HDA intel codec, and had two volume bars, could adjust volume and mutedness, but no sound came out of speakers or headphone jack. No 'model=xxxx' option passed to the kernel modules would help.

I couldn't ever get alsa working, but OSS4 (mercurial checkout) works fine.

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-13
have you solved thet problem?

I have buied the same notebook and I have network problem with avahi and audio not working

can you say to me how can I solved these problem?

thanks a lot

---

### Post by trippnk on 2008-09-15
I'm about to buy this laptop and don't want to switch back to Windoze.  Any fixes yet?

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-15
> **trippnk said:**
> I'm about to buy this laptop and don't want to switch back to Windoze.  Any fixes yet?

hi trippnk

I solved problem following this how-to [https://help.ubuntu.com/community/OpenSound](https://help.ubuntu.com/community/OpenSound)

but I have a low volume until here,and I didn't solved that problem 

anyway the suont card is working

for the eth card I solved problem,so you can drop out your winzoz quietly if you want

now,I have to see if I get to work the cam and the fingerprint....then I think there isn't anything that don't work

---

### Post by trippnk on 2008-09-15
Ya, placed my order today!! YEAH ME!!!  I've read in other places that the sound and wireless seem to be the biggest issues.  I think there is a wiki that says how to fix most little problems.  Can't wait for a good OOTB Ubuntu to load up and everything magically works.  I've heard good things about the upcoming 8.10 64bit :)  "fingers crossed"

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-16
> **trippnk said:**
> Ya, placed my order today!! YEAH ME!!!  I've read in other places that the sound and wireless seem to be the biggest issues.  I think there is a wiki that says how to fix most little problems.  Can't wait for a good OOTB Ubuntu to load up and everything magically works.  I've heard good things about the upcoming 8.10 64bit :)  "fingers crossed"

ho,good notice!!! Wath did you heard about?Can you give information? Do you think that wen ubuntu 8.10 will be available,we can install it on our asus m50 without many problem?

---

### Post by trippnk on 2008-09-16
Right now its still in alpha of course so lots of updates till it releases but I think the big one is that the intel 5100 wireless drivers will be included which will be nice.

---

### Post by ^[H3ad-Tr1p]^ on 2008-09-16
> **trippnk said:**
> Right now its still in alpha of course so lots of updates till it releases but I think the big one is that the intel 5100 wireless drivers will be included which will be nice.

one of the problem is eth 
another problem is audio oss with ICH9 chipset

---

### Post by pqrs541 on 2008-09-16
The Weather:[buy wow gold](http://www.mmoinn.com)  It's so dry, the trees are bribing the dogs. It's been hitter?s a goat's butt in a pepper patch.  Wintry roads are said to be "slicker than otter snot. [wow gold](http://wowus.mmoinn.com/index.do?PageModule=OrderForm_new)[wow gold](http://woweu.mmoinn.com/index.do?PageModule=OrderForm_new) [World of warcraft Gold](http://www.mmoinn.com)[wow gold](http://www.mmoinn.com)

---

### Post by sliverdragon37 on 2008-12-18
I have an asus m50vm-x1 and i'm running 8.10. i got the sound to work by updating to alsa v1.0.18a, solved all the problems except that when i plug in headphones sound still comes out of the speakers.

---

### Post by vOdikon on 2009-01-20
> **sliverdragon37 said:**
> I have an asus m50vm-x1 and i'm running 8.10. i got the sound to work by updating to alsa v1.0.18a, solved all the problems except that when i plug in headphones sound still comes out of the speakers.

you are on the right track. once you have upgraded to alsa v1.0.18a (this page shows you how to do it: [http://ubuntuforums.org/showthread.php?t=962695](http://ubuntuforums.org/showthread.php?t=962695) ), you need to edit your /etc/modprobe.d/alsa-base file.

```
sudo gedit /etc/modprobe.d/alsa-base
```

then add

```
options snd-hda-intel model=haier-w66
```

to the end of the file. save it and reboot, and your audio should mute when you plug in headphones!

---

### Post by ARam1024 on 2009-02-11
I was having sound/wireless problems.  I managed to mostly solve the wireless problems by using the intrepid backports package.  I fixed the audio problems by following [this]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301185").  I still can't mute the speakers when I'm using headphones though.

I'm updating my progress [here]("http://ubuntuforums.org/showthread.php?p=6718965#post6718965").

---

