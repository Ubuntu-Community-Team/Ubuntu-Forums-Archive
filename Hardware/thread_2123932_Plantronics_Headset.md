---
title: "Plantronics Headset"
date: 2013-03-09
forum: Hardware
---

### Post by Elvis99 on 2013-03-09
Hi all,

I've bought a Plantronics Headset (Gamecom 780) and it somehow is not appearing in the sound settings.

lsusb gives me this

> Bus 004 Device 002: ID 047f:c010 Plantronics, Inc.

dmesg

> 
[  428.911373] input: Plantronics Plantronics GameCom 780 as /devices/pci0000:00/0000:00:12.1/usb4/4-2/4-2:1.3/input/input6
[  428.911680] generic-usb 0003:047F:C010.0005: input,hidraw1: USB HID v1.00 Device [Plantronics Plantronics GameCom 780] on usb-0000:00:12.1-2/input3


So it seems, it is recognized by the system but I can't hear anything in the headphones. 

Help please?

---

### Post by jb0nez on 2013-04-04
I'm sorry that I can't offer help, but I also just got these headphones and am trying to get Kubuntu 12.10 working with them. For me they are recognized no problem, but I can't figure out how to do 5.1/7.1 surround - the only options in audio setup are stereo. 
My main point though is that it is possible to at least get them recognized. Maybe make sure you're on 12.10 and all system updates are installed.

---

### Post by Elvis99 on 2013-04-05
Hey jb0nez, try in the console typing "alsaconf" you may get more options.

---

### Post by jb0nez on 2013-04-06
> **Elvis99 said:**
> Hey jb0nez, try in the console typing "alsaconf" you may get more options.

I don't have an alsaconf command, and can't seem to find it - tried apt-get install *alsa* and nothing.

Edit: I should mention I'm using kubuntu - I think the underlying sound system is different?

Edit2: Yeah I think it uses pulseaudio and gstreamer instead of ALSA. Also what I'm reading online is headphones that do surround through software would need a special linux driver made for them. Don't think plantronics has one.

Edit3: But then I found that I do have alsa kernel modules running:

justin@justin-FX6831:/etc/modprobe.d$ modprobe -l |grep alsa
kernel/arch/x86/crypto/salsa20-x86_64.ko
kernel/crypto/salsa20_generic.ko
kernel/drivers/media/video/saa7134/saa7134-alsa.ko
kernel/drivers/media/video/cx88/cx88-alsa.ko
kernel/drivers/media/video/em28xx/em28xx-alsa.ko
kernel/drivers/media/video/cx231xx/cx231xx-alsa.ko
kernel/drivers/media/video/cx25821/cx25821-alsa.ko
kernel/drivers/media/video/tm6000/tm6000-alsa.ko
kernel/drivers/media/video/cx18/cx18-alsa.ko


All very cryptic to me. I don't seem to understand what alsa does, do I have it installed, would installing conflict with pulseaudio, and finally the most important - would it allow me to do surround sound on my Gamecom 780.

Edit #?: I have alsamixer installed - I ran it, it's a text-based mixer. For my "HDA Intel" (which is odd because I have a realtek HD audio chip) I get a lot of controls, and changing the master volume does change the volume. There is a section called "surround" which is turned all the way down; that's fine because I only had a stereo speaker setup on this, not the full surround speakers its capable of. But when I hit F6 and pick the Gamecom 780 device, I just get volume and mic. No surround.

---

### Post by lord-melchett on 2013-11-16
Hi all,

got a Plantronics C710 Blackwire Bluetooth / USB headset and had difficulty getting it to work. It caused mouse hangs, desktop hangs, etc.

Lots of searching failed to come up with a good answer, so I thought I'd try it in a Windows partition. It worked in Windows.

As the Plantronics site says:
[INDENT][SIZE=1]Blackwire 700 Series: How to Update the Firmware

MyHeadset Updater enables you to update the firmware on your Plantronics Blackwire 700 Series headset. In addition, MyHeadset Updater enables you to set certain options for your headset, such as the preferred language for voice prompts and commands, as well as toggling the Smart Sensors on and off.

Note: You must have access to a Windows PC in order to perform the update. If you do not have access to a PC, we will be happy to replace your headset with one that has the latest firmware. Please contact our Technical Assistance Center for more information.
Procedure

To download and install the software:

    Go to [http://www.plantronics.com/myheadset-updater](http://www.plantronics.com/myheadset-updater)
    Choose Blackwire 700 Series, and then click Get Started.
    Click Start.
    Click Download.
    Follow the on-screen prompts for downloading and installing the application.

To update your headset:

    Connect your headset to the computer via its USB cable.
    Go to [http://www.plantronics.com/myheadset-updater](http://www.plantronics.com/myheadset-updater)
    Choose Blackwire 700 Series, and then click Get Started.
    Click Continue.
    Click Continue again.
    Personalize any of your settings, if desired.
    Click Update Your Headset.
    Click Update.
    When prompted, disconnect your headset from the PC.[/SIZE]
[/INDENT]
[SIZE=2]
So updated the headseat firmware - the version as-shipped was many versions out of date - and it now works well in 12.04 - selectable from "Sound settings" - not sure it if automatically becomes the default device on hot-plug or not yet - task for another day....

[/SIZE]Hope this [SIZE=2] is helpful for others[/SIZE]

Cheers

---

### Post by justin_acklin on 2013-11-16
Thanks, but the Blackwire and Gamecom are different. There's no Gamecom in the headset updater. I'm pretty sure the Game com 780 relies on windows software to do the 7.1.
They work fine in stereo on ubuntu.

---

