---
title: "Random Lock ups where mouse could be moved."
date: 2009-10-31
forum: Hardware
---

### Post by kagashe on 2009-10-31
I downloaded Ubuntu 9.10 RC and installed on hard disk. There were random lock ups in which I could move the mouse but clicking on anything did not work. Keyboard did not work except Alt+SysRq+r+e+i+s+u+b to shut-down. The lock ups continued even after release of Final and applying all updates.

I have downloaded Final Desktop ISO and the random lock up takes place even on Final Live CD.

$ lspci -nn | grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device [8086:2562] (rev 03)

The PCI ID [8086:2562] is blacklisted on Compiz.

Any help to solve random lock ups would be appreciated.

kagashe

---

### Post by kagashe on 2009-10-31
I filed a [bug report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/466310") and it was confirmed within 2 hours since another bug report for same chipset was filed on Oct 21st.

In view of the bug Karmic becomes unusable on this hardware unless I can downgrade the driver to Ubuntu Jaunty version.

Is it possible to downgrade the driver? If yes, how?

kagashe

---

### Post by kagashe on 2009-11-03
I switched to vesa driver using following xorg.conf:
> Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vesa"
EndSection

kagashe

---

### Post by AdamRG on 2009-11-03
I have the exact same issue with the same graphics card.  I am a complete newbie with Ubuntu and Linux.  Are the instructions you provided to downgrade the graphics card in the xorg.conf file all that you have to do?  Sorry for such a rudimentary question.

Regards

---

### Post by kagashe on 2009-11-04
> **AdamRG said:**
> I have the exact same issue with the same graphics card.  I am a complete newbie with Ubuntu and Linux.  Are the instructions you provided to downgrade the graphics card in the xorg.conf file all that you have to do?  Sorry for such a rudimentary question.

RegardsDon't worry. I am using Ubuntu for more than 4 years.

Initially I have asked a question to this forum whether I can downgrade the intel driver (to avoid random lock ups) and there is no reply.

The alternative to intel driver is vesa driver which works on any graphic card. To use vesa driver you can copy the code in my third post in this thread and save it as xorg.conf. You can move the file to the appropriate folder by typing following command:
> $ sudo mv xorg.conf /etc/X11

The vesa driver will be loaded on reboot or restart of GDM:
> $ sudo /etc/init.d/gdm restart

kagashe

---

### Post by JoePits on 2009-11-04
are you by any chance using a laptop with a touchpad?

this bug happened to me and all i had to do was move the mouse with the touchpad and then the usb mouse would work again.

---

### Post by kagashe on 2009-11-04
> **JoePits said:**
> are you by any chance using a laptop with a touchpad?

this bug happened to me and all i had to do was move the mouse with the touchpad and then the usb mouse would work again.No, it is a Desktop with PS2 mouse.

kagashe

---

