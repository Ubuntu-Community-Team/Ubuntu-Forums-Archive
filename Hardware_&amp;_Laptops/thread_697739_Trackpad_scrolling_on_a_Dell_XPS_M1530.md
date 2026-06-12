---
title: "Trackpad scrolling on a Dell XPS M1530"
date: 2008-02-15
forum: Hardware &amp; Laptops
---

### Post by JaggedOne on 2008-02-15
I just got my new XPS M1530 in the mail. I wiped the bloatware that is Vista and installed Ubuntu 7.10. I was thrilled to find everything working out of the box except for one thing, the trackpad scrolling. No matter what I set the options to it doesn't work. Moving my finger up and down the right side of the trackpad will produce momentary jerks on the webpage, but I can not get it to scroll smoothly like it did in windows before I removed it.

---

### Post by JaggedOne on 2008-02-17
Anyone?

---

### Post by JaggedOne on 2008-02-18
I really need help with this. Anybody out there?

---

### Post by JaggedOne on 2008-02-18
Help.... Please?

---

### Post by jespdj on 2008-02-19
I have an XPS M1330, but I guess it's exactly the same on the M1530.

Do you have desktop effects (Compiz Fusion) enabled? I do, and on my laptop, the vertical scrolling on the side of the trackpad is used to switch desktops instead of for scrolling inside programs.

I don't know exactly how to change the behaviour, but you can probably change it with the Compiz Fusion settings manager. See [this](http://ubuntu-tutorials.com/2007/10/04/compiz-fusion-on-ubuntu-710-gutsy-gibbin/).

---

### Post by sygram on 2008-02-24
Hi guys,

hopefully i will receive my xps 1530 on Tuesday the 26th of this month.

The first thing will be to install ubuntu, so i will post by the end of this week :)

Leon

---

### Post by sygram on 2008-03-01
ok i have just received it :)

The trackpad scrolling is fine. The mic is not working though ...

Thanks

Leon

---

### Post by havanahjoe on 2008-03-11
> **sygram said:**
> ok i have just received it :)

The trackpad scrolling is fine. The mic is not working though ...

Thanks

Leon

Can you post your xorg.conf?  I have Ubuntu 7.10 running on my M1530 but my touchpad does not work.  I get the same behavior as Jaggedone.

---

### Post by sygram on 2008-03-13
sorry guys , i thought it was working but not...

Sometimes if i click it will move especially if the scroll bar has the focus.

My apologies...

Leon

---

### Post by sygram on 2008-05-03
Hi guys , i found this on another forum . Vertical scrolling seems to work fine. : 

Section "InputDevice"
 Identifier "Synaptics Touchpad"
 Driver "synaptics"
 Option "SendCoreEvents" "true"
 Option "Device" "/dev/psaux"
 Option "Protocol" "auto-dev"
 Option "ZAxisMapping" "4 5"
 Option "Emulate3Buttons" "on"
 Option "SHMConfig" "on"
 Option "VertEdgeScroll" "on"
 Option "VertTwoFingerScroll" "on"
 Option "LeftEdge" "85"
 Option "RightEdge" "910"
 Option "TopEdge" "85"
 Option "BottomEdge" "715"
 Option "FingerLow" "25"
 Option "FingerHigh" "30"
 Option "MaxTapTime" "180"
 Option "MaxTapMove" "220"
EndSection

Regards

---

### Post by semiconductor on 2008-05-08
I have just got an XPS 1530 today and am installing Ubuntu now. I am a virgin to linux BUT am not having any trouble with it so far. Im exited to use it.

My problem is that the trackpad does not work at all in ubuntu. It makes the mouse behave like Im right clicking and goes totally ape. Im not just talking about the scrolling but the whole trackpad.

HELP!

What on earth is this SYGRAM and can and how I use it?

Hi guys , i found this on another forum . Vertical scrolling seems to work fine. : 

Section "InputDevice"
Identifier "Synaptics Touchpad"
Driver "synaptics"
Option "SendCoreEvents" "true"
Option "Device" "/dev/psaux"
Option "Protocol" "auto-dev"
Option "ZAxisMapping" "4 5".....

---

### Post by Vaun on 2008-05-08
It sounds like behavior consistent with Bios version A08.  If that's the case :

```
sudo gedit /boot/grub/menu.lst
```

Add ```
18042.nomux=1
``` at the end of the kernel line.

If you add:

```
Option          "RightEdge" "910"
```

in /etc/X11/xorg.conf it will widen your trackpad vertical scrolling.

---

### Post by thetrav on 2008-05-14
> **Vaun said:**
> It sounds like behavior consistent with Bios version A08.  If that's the case :

```
sudo gedit /boot/grub/menu.lst
```

Add ```
18042.nomux=1
``` at the end of the kernel line.

If you add:

```
Option          "RightEdge" "910"
```

in /etc/X11/xorg.conf it will widen your trackpad vertical scrolling.

I have the same problem with my track pad going bezerk in hardy 64, how do I check the bios version?

---

### Post by thetrav on 2008-05-14
Additionally I added that to the end of my kernal line which is:
```
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=fa99f5fc-166b-4411-986b-a2c76b4501b9 ro quiet splash
```
and re-booted, but it told me 18042.nomux=1 is an invalid boot option and that it's ignoring it.

---

