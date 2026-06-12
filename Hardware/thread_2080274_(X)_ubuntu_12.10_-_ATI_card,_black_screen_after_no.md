---
title: "(X) ubuntu 12.10 - ATI card, black screen after nomodeset"
date: 2012-11-03
forum: Hardware
---

### Post by checco.lnx on 2012-11-03
Hi all,

**The fact:** I've a notebook with an ATI Radeon 9100 IGP as video card. If KMS is enabled i get freezes. The solution is to disable KMS in GRUB adding "nomodeset". Ok up to Ubuntu 12.04. 

**The problem:** I've installed the new Xubuntu 12.10, kernel 3.5.0.17-generic. Again, if KMS is enabled i get freezes. This time, the "nomodeset" produces a black screen at startup (it's like a pseudo-stanby). In other words, the desktop is not shown.

Any possible solution? 

Thanks in advance,
Checco

---

### Post by Bashing-om on 2012-11-03
hi ! checco.lnx; Welcome to the forum.
Try this as a boot option and see if you can boot:
"radeon.modeset=0" -> also disables KMS 
once booted up, try "additional drivers" to load an appropriate driver.
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by checco.lnx on 2012-11-03
Hi Bashing-om,

The option "radeon.modeset=0" is not working. The effect is the same as "nomodeset": black screen.
Also I think there's no additional driver to install for the Radeon 9100 IGP.

I'm not a particulary advanced ubuntu user. My question is: Can I use the xorg.conf file to bypass the not working "nomodeset" option?

Thanks for your reply,
Checco

---

### Post by Yellow Pasque on 2012-11-04
The open-source ati driver (xserver-xorg-video-ati) has dropped support for user-space modesetting in version 7.0: [http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDI](http://www.phoronix.com/scan.php?page=news_item&px=MTEyMDI)
Quantal uses a pre-release version of 7.0, so userspace mode-setting is not going to work.

---

### Post by checco.lnx on 2012-11-05
Hi Temüjin,
thanks for your reply.

As I said, I'm not an advanced user. So the difference between "*Kernel Mode Setting*" and "*User-space Mode Setting*" is not perfectly clear.  I'll try to plug the gap!
In the meantime I ask you if it's possible "to play" with the **xorg.conf** configuration to try different settings for my Radeon 9100 IGP.

For example (xorg.conf):

```
Section "Device"
    Identifier  "Radeon"
    Driver      "radeon"
    VendorName  "Ati"
    BoardName   "Radeon 9100IGP"
    Option         "AGPFastWrite"     "1"
    Option      "MonitorLayout"      "CRT, NONE"
    Option      "RenderAccel"        "1"
    Option      "AccelMethod"        "xaa"

    Option      "ForceMinDotClock"   "15MHz"
    Option      "NoTV"               "1"
EndSection
```Is it ignored with KMS enabled in ubuntu 12.10? Or it has a sense...

Thanks,
Checco

---

### Post by Yellow Pasque on 2012-11-05
A lot of those options are not for use with KMS. Read the radeon man page.

---

### Post by checco.lnx on 2012-11-06
Hi Temüjin,
thanks for your reply.

I read the Radeon man page. I'll try to disable hardware acceleration to avoid freezes (i don't know where to start to solve the problem).

Is this configuration right? 

```
Section "Device"
    Identifier "Radeon"
    Driver "radeon"
    VendorName  "Ati"
    Option "NoAccel" "1"
EndSection
```Thanks,
Checco

---

