---
title: "newby issue installing Brother scanner"
date: 2009-09-06
forum: Installation &amp; Upgrades
---

### Post by lets on 2009-09-06
Hello everyone.

I'm having trouble getting a Brother MFC210c scanner to work with a newly upgraded version of ubuntu - now version 9.04

The print function of the mfc is working fine, but whenever I try to scan from gimp, I'm getting an error that there is an invalid argument. Xsane reports that it attempted to open Brother2:bus5;dev1. However when I run  sane-find-scanner from the Terminal window it report that...
found USB scanner (vendor=0x04f9, product=0x0161) at libusb:005:002

If I understand that correctly, it means that the scanner is on bus 5 device 2 - but gimp, via sane, is trying to open the scanner on bus 5, device 1.

Is this the reason it isn't working? Or is there something else I don't understand? If this is the issue, how do I tell sane to look in the right place?

Many thanks in anticipation,

Regards,

lets

---

### Post by pcal on 2009-09-09
I'd like to see an answer to this issue also. Any clues...

---

### Post by statakos on 2009-09-15
> **pcal said:**
> I'd like to see an answer to this issue also.

Me too.

---

### Post by TopEnder on 2009-09-17
lets
pcal
statakos

Scanner Installation:   Download and install the following from the Brother Scanner Driver Web download [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)  most of what's  covered below originated from this site/page:

	[COLOR="Blue"]brscan2-0.2.4-0.i386.deb[/COLOR]     ( or the latest version - if any)
	[COLOR="Blue"]brscan-skey-0.2.1-3.i386.deb[/COLOR]   ( or the latest version  - if any)

1.In Terminal:   Open to edit:"/lib/udev/rules.d/50-udev-default.rules file by      

[COLOR="Blue"]gksudo gedit /lib/udev/rules.d/50-udev-default.rules[/COLOR] 

Edit this entry:
Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="[COLOR="Blue"]0664[/COLOR]"
into:
Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="**0666**"
Then perform:
Code:
[COLOR="Blue"]sudo /etc/init.d/udev restart[/COLOR]


&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install:    sane-utils (if not already installed , it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New

Enter "brscan-skey" in:
Name:                             and 
Command:
Comment: 	Enter what you want to call your Scanner

Press OK and enable the entry. 

Hope this helps you.

---

### Post by statakos on 2009-09-20
Worked like a charm.

Thanks.

---

### Post by pcal on 2009-09-23
Thanks! So many things to get right!!

---

### Post by lets on 2009-09-24
> **TopEnder said:**
> lets
pcal
statakos

Scanner Installation:   Download and install the following from the Brother Scanner Driver Web download [http://solutions.brother.com/linux/en_us/](http://solutions.brother.com/linux/en_us/)  most of what's  covered below originated from this site/page:

    [COLOR=Blue]brscan2-0.2.4-0.i386.deb[/COLOR]     ( or the latest version - if any)
    [COLOR=Blue]brscan-skey-0.2.1-3.i386.deb[/COLOR]   ( or the latest version  - if any)

1.In Terminal:   Open to edit:"/lib/udev/rules.d/50-udev-default.rules file by      

[COLOR=Blue]gksudo gedit /lib/udev/rules.d/50-udev-default.rules[/COLOR] 

Edit this entry:
Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="[COLOR=Blue]0664[/COLOR]"
into:
Code:
# libusb device nodes
SUBSYSTEM=="usb", ENV{DEVTYPE}=="usb_device", NAME="bus/usb/$env{BUSNUM}/$env{DEVNUM}", MODE="**0666**"
Then perform:
Code:
[COLOR=Blue]sudo /etc/init.d/udev restart[/COLOR]


&#65279;To get the scan-key-tool to start automatically at Ubuntu boot by default.

Install:    sane-utils (if not already installed , it's in Synaptic Package Manager)

Add the brscan-skey command to your startup program.

System -> Preference -> Sessions -> Startup Programs -> New

Enter "brscan-skey" in:
Name:                             and 
Command:
Comment:     Enter what you want to call your Scanner

Press OK and enable the entry. 

Hope this helps you.


Works a treat Thanks for your help
lets:P

---

