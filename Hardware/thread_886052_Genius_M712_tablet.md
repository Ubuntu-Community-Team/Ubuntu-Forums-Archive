---
title: "Genius M712 tablet"
date: 2008-08-10
forum: Hardware
---

### Post by billstei on 2008-08-10
Anyone successfully using the Genius G-Pen M712 tablet ?

Bill

---

### Post by Arthur Millar on 2008-10-20
any ideas anyone?

---

### Post by Arthur Millar on 2008-10-21
well billstei
i f#&^%kn did it!!!!!
i followed the wizard pen wiki
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)
I onl got as far as _Setting up udev_
and it showed up as **media tablet**
[code]sudo cat /sys/bus/usb/devices/*/product[code/]
Media Tablet
USB2.0 Hub
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
OHCI Host Controller
EHCI Host Controller
i cant beleive how well this driver actually works 
the tablet is working, the nobs work even the buttons on the pen 
to be honest i feel like i got lucky!! 
It does need a bit of calibrated as the right side doesnt go all the way t the end of the screen 
and i wonder if the pressure works?

---

### Post by Arthur Millar on 2008-10-21
[COLOR="Red"]{ignore}[/COLOR]um problem
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

:~/wizardpen-0.6.0.2# ls -la /dev/tablet-event
ls: cannot access /dev/tablet-event: No such file or directory
:~/wizardpen-0.6.0.2# 

followed to the T 
anyone?
[COLOR="Red"]{ignore}[/COLOR]

---

### Post by Arthur Millar on 2008-10-21
everything works except the actual surface and the quiklink buttons

im strugling with the collaboration bit  
any help would be appreciated

---

### Post by hazelp on 2010-04-04
i have a CDR-KING 14.1 Media tablet which is the same as the Genius M712. my first attempt at making this work on ubuntu 9.10 failed. i used instructions from here.

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

i couldn't get to the calibrate folder, etc.  after much work and getting xorg.conf to work, rebooting gave me an error on the graphics card.  whatever i did, the pentab only functioned as a mouse and nothing more.  it culdn't even trigger commands upon pressure or clicking the buttons.

then i stumbled upon this:

[http://ubuntuforums.org/showpost.php?p=8311575&postcount=35](http://ubuntuforums.org/showpost.php?p=8311575&postcount=35)

the only different thing i did was this command (step #4):

```
cd /where wizardpen-calibrate command is located/ 
OR
cd ~/wizardpen/xserver-xorg-input-wizardpen-0.7.1/calibrate
wizardpen-calibrate /dev/input/by-id/usb-WALTOP_International_Corp._Media_Tablet-event-if00
```it worked.  i can now use the pentab on GIMP, inkscape, Krita as long as the interface is properly set on each app.  choose "Screen" mode.

i'm not entrely sure if it's pressure sensitive. look like it's not. i have to spend more time there i guess.

---

