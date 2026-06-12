---
title: "WizardPen 5x4 Graphics Tablet issue"
date: 2005-03-13
forum: Hardware &amp; Laptops
---

### Post by Narkath on 2005-03-13
Greeting fellow penguin lurvers,

I have managed to get every piece of hardware working except my Graphics Tablet. This is the only thing preventing me from using linux exclusively. I found [this](http://www.stud.fit.vutbr.cz/~xhorak28/index.php.iso-8859-1?page=WizardPen) tutorial on how to get it working. Unfortunately, I can't understand it. I'm stupid apparently. Anyway, I would appreciate some help from one of you oh so helpful linux gurus.

This is what I have tried so far:
- Downloaded the driver 0.0.2
- Installation
[quote="pensite"]
3.  	change to wizardpen-driver-0.0.2 directory and run xmkmf command to create driver Makefile
cd wizardpen-driver-0.0.2
xmkmf
4. 	run make and make install
make
make install[/quote]
It gives me loads of errors.
eg. Xincludes/xc/exports/include.X11/extension/XIproto.h:1161: error: previous declaration of 'keys'
I did the rest as well but it didn't work. probably because of the make and make install errors.
Also, what is up with the two different X86Config changes 'tablet' and 'input'

This may be the cause of errors me thinks
> Kernel options which must be enabled:
1. 	USB support
USB Human Interface Device (full HID) support - may be as Module
HID input layer support
/dev/hiddev raw HID device support - Y
2. 	Input device support
Event interface - may be as Module
Any ideas?

---

### Post by daller on 2006-09-03
My guide should get around EVERY detail in setting up the tablet:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

