---
title: "Genius Tablet - mouse moves, rest don't work"
date: 2013-03-25
forum: Hardware
---

### Post by Toci on 2013-03-25
Hello, I tried to install a genius i608x tablet, I followed the instructions here:

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

 I kept getting many errors but I don't know what they meant.
 Before trying to install the tablet did move the mouse, but the buttons did nothing.

 I also removed the WALCOM driver as somebody suggested [elsewhere ]("http://www.ubuntu-es.org/node/150417#.UVA-XvEkd2M")that could be interfering. 

 I would very much appreciate your help, if not to get it working, to at least know how to revert all the things I did wrong.

 Thank you.

---

### Post by Favux on 2013-03-25
Hi Toci,

Depending on your Ubuntu release it might have worked out of the box.

So what release of Ubuntu do you have?

And what do you mean when you say?
>  also removed the WALCOM driver as somebody suggested elsewhere that could be interfering. 
Exactly what did you do?

The wiki [https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen) is getting dated and the instructions are not so useful.

In addition to the release let us verify the model.  Post the output of the following terminal command.
```
lsusb
```

---

### Post by Toci on 2013-03-25
Hello Favux,

 I'm using the Ubuntu 12.04 version. 

 As for the WALCOM driver what I did was search for it on synaptic (xserver-xorg-input-wacom) and removed it. 

 The result I got from running that command was:

```
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 152d:2329 JMicron Technology Corp. / JMicron USA Technology Corp. JM20329 SATA Bridge
Bus 002 Device 002: ID 03f0:8104 Hewlett-Packard Printing Support
Bus 003 Device 002: ID 0461:4d81 Primax Electronics, Ltd 
Bus 004 Device 002: ID 413c:2106 Dell Computer Corp. Dell QuietKey Keyboard
Bus 005 Device 002: ID 0458:5011 KYE Systems Corp. (Mouse Systems) 

```

---

### Post by Favux on 2013-03-25
Alright, from the Tablet support page on the DIGImend site:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_support_status)  you can see the KYE MousePen i608X (0458:5011) is supported in the 3.4 kernel and later.  So it would be supported out of the box with Ubuntu Quantal 12.10 or later.

For Precise you would need to either use one of the pre-patched kernel packages or use the v. 6 patch set and patch the HID kernel modules yourself:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=DIGImend)  Your other option is to compile the WizardPen driver for Precise and use it instead:  [http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen](http://sourceforge.net/apps/mediawiki/digimend/index.php?title=Tablet_setup_with_WizardPen)

Uninstalling the Wacom driver should have also removed xserver-xorg-all too and you need that.  Surprised nothing else got disabled on your system.  Go ahead and reinstall xserver-xorg-input-wacom.  And by the way when the kernel driver is working you do not have to use the evdev X driver for your KYE.  The Wacom X driver also works for the KYE pen and avoids the Qt evdev bug.  Of course this doesn't apply if you use the WizardPen driver.

---

### Post by Toci on 2013-03-25
Thank you very much for the clear reply Favux.

 I was actually thinking about downgrading, because this version of Ubuntu seemed to be very unstable. But anyway, I'll be following the instructions you gave me and will inform of the results.



EDIT:
 Ok, so I had indeed removed the xserver-xorg-all file and couldn't get it back, so I decided to upgrade, and now the tablet works. Thanks again!

---

### Post by ppsirg on 2013-11-08
hello, i have the same problem, i'm using Xubuntu saucy salamander (13.10) and the tablet(genius mousepen i608X) is recognized with lsusb

Bus 002 Device 004: ID 0458:501a KYE Systems Corp. (Mouse Systems) 

and when i use the pen works ok moving but preasure, main and second button events doesnt work at all. i've tryed on gimp, inkscape and mypaint and with xdev i realized pad event is recognized as button8, main button as button9 and second button as button10, so events sended by the tablet are working, i've tryed to use this guide ([http://jhs-corner.blogspot.com/2013/10/tableta-grafica-genius-mousepen-i608x.html](http://jhs-corner.blogspot.com/2013/10/tableta-grafica-genius-mousepen-i608x.html)) but it damages event recognition.

---

### Post by sdfgeoff on 2013-11-20
I also bought a Genius Mousepen i608x, and have the same problem.
Looking over at the kbuntu forums ([this thread]("https://www.kubuntuforums.net/showthread.php?62838-Genius-I608X-graphic-tablet-not-drawing")), it appears that it is being recognized as the wrong device. 
As you say, when it's plugged in, it comes up as:
```
[COLOR=#000000]Bus 002 Device 004: ID 0458:501a KYE Systems Corp. (Mouse Systems) 
```
It should be coming up as device ID [/COLOR][COLOR=#000000]0458:5011

The solution presented in that thread is to recompile the kernel editing one file to force the tablet to be recognised correctly. I haven't attempted this yet, and haven't decided if I will yet (because it will probably screw up my graphics drivers), but if I do, I'll let you know what happens....[/COLOR]

---

