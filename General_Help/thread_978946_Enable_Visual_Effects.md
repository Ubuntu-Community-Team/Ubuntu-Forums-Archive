---
title: "Enable Visual Effects"
date: 2008-11-11
forum: General Help
---

### Post by tvks on 2008-11-11
Hi,

I am a newbie to Linux. I had recently installed Ubuntu and my problem is that I am not able to set the visual effects. As per one of my friends instructions I have executed the "lspci" command and the following is the output.

[PHP]
$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. P4M266 Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:09.0 Multimedia controller: Philips Semiconductors SAA7134/SAA7135HL Video Broadcast Decoder (rev 01)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 80)
00:10.3 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 82)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8235 ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 50)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 74)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]
[/PHP]

What should I do to enable the visual effects come better ?

Thanx for any help.

Regards,

tvks

---

### Post by ant1060 on 2008-11-11
Hi :
Have you done the obvious right click on the desktop background (Change Desktop Background)?  If not, visual effects is the last tab and you can enable the settings there! :)

---

### Post by CLomax on 2008-11-11
I saw "ProSavage" in there somewhere... I doubt it can handle visual effects but worth a shot.

Make sure you know what to do in the even of a crash before trying to put these effects on.

[B]> Right click on desktop
> Click on 'Visual Effects'
> Try 'Normal' first. If it works but you're not satisfied...
> Tick the 'Extra' box[/B]

```
sudo apt-get install compizconfig-settings-manager
```

---

### Post by eternalnewbee on 2008-11-11
Make sure your graphic card is enabled (**Main Menu > System > Administration > Hardware Drivers**)
After that press ALT-F2 and enter ```
compiz --replace
```
Hope this helps.

---

### Post by tvks on 2008-11-16
Hi,

:( No use at all.. Nothing seems to work my way.

I am indeed upset with Hardy Heron for being so Hard.

I am not able to install any beautiful theme and beautify my systems look and feel. I am not able to use the beryl (compiz) functionality. Neither am I able to properly execute gdesklets.

All Roads Lead to Rome.

All these are being kicked back because of me unable to Enable the Visual effects.

When M$ Windows works fine with the inbuilt display card why does Ubuntu (Hardy) seek all these ??

Regards,

tvks

---

### Post by Nithish on 2009-02-01
Same problem here... please someone help us!!

---

