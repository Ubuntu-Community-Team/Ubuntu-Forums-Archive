---
title: "Audio problem Sony VGN-UX17GP micro PC"
date: 2008-09-24
forum: Hardware
---

### Post by owenspa on 2008-09-24
Hi,

I'm installing Kubuntu 8.04 on a Sony VAIO VGN-UX17P.

An alc262 audio card is detected and the snd-hda-intel module is loaded.
Originally I was getting very low level scratchy sound out of either
the in built speaker or the headphone jack.

After searching the forums for anything mildly relevant I hit upon
putting "options snd_hda_intel model=vaio" in /etc/modprobe.d/alsa-base.
Now I get fair audio out of the headphone jack, its less than half normal
volume.  However, I get absolutely nothing out of the speaker (with the
plug removed from the headphone jack).

I have played with the mixer settings, I can adjust the volume out of
the headphone jack but only to a very low max.

Can anyone help me?  Are there other module options that are relevant?
Are there other controls I should be using?

---

### Post by Crafty Kisses on 2008-09-24
I'd like to see the results of the following command:
```
lspci
```

---

### Post by owenspa on 2008-09-24
> **Codename said:**
> I'd like to see the results of the following command:
```
lspci
```
Here it is

> # lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
06:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8036 PCI-E Fast Ethernet Controller (rev 15)
07:04.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
07:04.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
07:04.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
#

---

### Post by owenspa on 2008-09-25
I found this howto
    [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

It indicates that my problem is not unexpected with this driver, there are
many "models" that provide solutions for different configurations.

I also found this file
    [http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt](http://www.mjmwired.net/kernel/Documentation/sound/alsa/ALSA-Configuration.txt)

It indicates that the "vaio" model is not available for the ALC262.  However,
it does refer to a "hippo" model for Sony UX90's.  So I tried it.
I now have full sound level out of the headphones, but still nothing out
of the in-built speaker.

---

### Post by fourthofjuly on 2008-09-25
dear owenspa,

i too have intel integrated sound and my sound started working after adding the line

options snd-hda-intel model=ref

to the end of my /etc/modprobe.d/alsa-base file

---

### Post by owenspa on 2008-09-25
> **fourthofjuly said:**
> dear owenspa,

i too have intel integrated sound and my sound started working after adding the line

options snd-hda-intel model=ref

to the end of my /etc/modprobe.d/alsa-base file

Thanks fourthofjuly.  I tried that it made no difference
that I could hear.

It seems that the "model"s available depends on the codec
you have.  Mine is an ACL262.  You can find out yours by
running
> cat /proc/asound/card0/codev#* | grep Codec

Regards.

---

### Post by fourthofjuly on 2008-09-26
sad, but that's the best i could suggest...!

---

### Post by markbuntu on 2008-09-26
If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

---

### Post by owenspa on 2008-09-27
> **markbuntu said:**
> If you are having problems with headphone/speaker control with your HDA sound device you can try this thread:

[http://ubuntuforums.org/showthread.php?t=806620](http://ubuntuforums.org/showthread.php?t=806620)

Thank you markbuntu.  You put me onto the the next part of the solution.
That part of the problem was my misunderstanding of the mixer controls.
This machine has a mono speaker, the slider label just says "mono".  Once I switched that on and raised the level - BINGO!  I now have sound out
of the mono built-in speaker :).

Thanks everyone for your help.

---

