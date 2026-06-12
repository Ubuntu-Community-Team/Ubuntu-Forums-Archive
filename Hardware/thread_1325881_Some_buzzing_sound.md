---
title: "Some buzzing sound"
date: 2009-11-13
forum: Hardware
---

### Post by ramukumar on 2009-11-13
Hi
   Today only i installed ubuntu 9.04 in Hp Dv4 1211TU. when i logged in i m hearing some buzzing sound from speaker. Can any one help in this issue.

---

### Post by gradinaruvasile on 2009-11-27
Is this sound continuous? Also, post the output of the lspci command (in a terminal).
What are your sound levels? (right click on the speaker in the taskbar, click open volume control). Click preferences and tick everything. Post a screenshot.

---

### Post by ramukumar on 2009-11-27
HI thanks for ur response

I am using Hp laptop (DV4 pavilian 1211TU)


Output of lspci


>  ramukumar@ramukumar-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
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
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
05:00.0 System peripheral: JMicron Technologies, Inc. SD/MMC Host Controller
05:00.2 SD Host controller: JMicron Technologies, Inc. Standard SD Host Controller
05:00.3 System peripheral: JMicron Technologies, Inc. MS Host Controller
05:00.4 System peripheral: JMicron Technologies, Inc. xD Host Controller
Output of aplay - l
> ramukumar@ramukumar-laptop:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 0/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 3: INTEL HDMI [INTEL HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
ramukumar@ramukumar-laptop:~$ 


Do u need any other information

---

### Post by ramukumar on 2009-11-27
I am hearing only some drum like sound if any action is done for example if any one pings me in gtalk also i am hearing tht sound. and if play any video in youtube on in vlc I am hearing the same sound. Please help me in this issue

---

### Post by gradinaruvasile on 2009-11-27
Ok... First of all, i advise to disable pulseaudio:
Open a terminal. 
1. 

sudo gedit /etc/alsa/alsa.conf

Comment out the line with pulse.conf in it (just put the # caracter as the first character on that line)

save, quit

2. Go to system->preferences->sound

set everything to ALSA

3. Go to system->preferences->startup applications

uncheck the pulse one that has pulse in it.
add a new entry - 
name: pulsekill, 
command: killall pulseaudio
This will prevent pulseaudio from loadng at startup.

Reboot

PS Are you using Gtalk? I thought thats Windows only...


Edit:sorry the alsa.conf path had a typo in it. Corrected.

---

### Post by ramukumar on 2009-11-28
hi 
   Sound is coming for each and every action. For example Tab ,right click etc... and in alsa.conf nothing is there to comment it is empty and in startup application pulse is not there to uncheck.

---

### Post by gradinaruvasile on 2009-11-30
Im sorry i think i messed up the alsa.conf path. It is /usr/share/alsa/alsa.conf. 

The startup app thing is not that essential. Just put the killall pulseaudio there.

Also, make sure the sound theme (volume control applet->sound theme tab) is set to "no sounds".

And if i think about it, i might have a similar problem (only it surfaced in ubuntu 9.10) - but it has to do with the touchpad movements and only when there is no sound output, and the sound card is in "sleep mode" (Dell D630 laptop). Anyway the sound card sleep is only from the newer kernels of 9.10.

---

