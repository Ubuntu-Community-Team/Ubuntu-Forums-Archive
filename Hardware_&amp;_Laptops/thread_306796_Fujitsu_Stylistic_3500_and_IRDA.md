---
title: "Fujitsu Stylistic 3500 and IRDA"
date: 2006-11-25
forum: Hardware &amp; Laptops
---

### Post by lfjewett on 2006-11-25
I'm installing Ubuntu on a Fujitsu 3500 and have a great start.  The touchscreen drivers are working great ( after 6 hours of work ), sound, usb, etc are all working.  Now I'm up to the part where I'd like to get the system working with an IR Keyboard.  and I'm stuck.    I had to do the install on my laptop and then transfer the HD to this computer since there is no CDROM or Floppy on these systems.  

I've enabled the IR port in the BIOS and have tried both options IRDA and FIR.  I have no clue what the difference is or which I should pick.  Both seem to have a PORT associated and I had to change this from the last of 4 ports ( com4 maybe ) to the second to last (com3) because the touchscreen works off of the last address I believe. (ttyS3).  

I've installed the irda-utils package, and I've tried looking through the FAQ's, HOWTO's, and Forums for help.  The only tutorial I found simple to follow though on was about an IBM Laptop and those configs do not work with this machine.  ( the ncc drivers report no device found during the modprobe ).  

So here I sit with an almost great machine, if I could just get around this and a couple more bugs.  Does anybody have any suggestions?  PLEASE!

Louis

---

### Post by iamthedruid on 2006-12-05
> **lfjewett said:**
> I'm installing Ubuntu on a Fujitsu 3500 and have a great start.  The touchscreen drivers are working great ( after 6 hours of work ), sound, usb, etc are all working.  Now I'm up to the part where I'd like to get the system working with an IR Keyboard.  and I'm stuck.    I had to do the install on my laptop and then transfer the HD to this computer since there is no CDROM or Floppy on these systems.  

I've enabled the IR port in the BIOS and have tried both options IRDA and FIR.  I have no clue what the difference is or which I should pick.  Both seem to have a PORT associated and I had to change this from the last of 4 ports ( com4 maybe ) to the second to last (com3) because the touchscreen works off of the last address I believe. (ttyS3).  

I've installed the irda-utils package, and I've tried looking through the FAQ's, HOWTO's, and Forums for help.  The only tutorial I found simple to follow though on was about an IBM Laptop and those configs do not work with this machine.  ( the ncc drivers report no device found during the modprobe ).  

So here I sit with an almost great machine, if I could just get around this and a couple more bugs.  Does anybody have any suggestions?  PLEASE!

Louis

Thanks. I am trying to load ubuntu on Fujitsu Stylistic 3500. Could you please post major things that I need to watch out for ?

thanks

---

### Post by lfjewett on 2006-12-06
USB and Sound both worked out of the box.  Still no resolution on the IR port.  The touchscreen took awhile to setup. 

The fpit drivers work fine just be sure you read the man page first.  You must insert some scripts into the boot process to set up the serial connection to the touchscreen.  Mine is preset on COM 4 just like the manual says. 

Calibrating the touchscreen was also fairly time consuming.  I wasn't able to compile the calibration tool so I had to do it manually.  In the xorg.conf file you'll have the difinitions for the fpit driver.  There are 4 X1 X2 Y1 Y2 numbers in there for calibration. I think they are labled minsize maxsize.   The easiest way is to play with 1 number at a time, save the file then CTRL - ALT - BACKSPACE to restart X.  test and repeat.   haveing an open ssh connection to edit the file makes it go faster.  Time spent on this was about 30 min.

Other than that everything has gone pretty smoothly.  One thing to note the onscreen keyboards do not work well with the touchpad. It seems to record a mouse click but no mouse off event and the keys get stuck down..  I'm still searching for a solution but if anyone else reads this and wants to chime in I'm all ears!!

---

### Post by bwiewiora on 2007-02-17
Hi,

It seems like we have opposite problems--my IR port worked right out of the installation with my IR mouse, but I can't get the touchscreen to work for anything.  In my BIOS, the IR port is set to AUTO.  

I'm a noob, so I'm not sure what else to try, but if there is any file or anything on mine that you'd like to see the configuration for, let me know.  Hopefully we'll both learn something!

---

### Post by cosmobreton on 2007-02-18
Hi:

Ubuntu-Dapper works fine on my Stylistic 3500 also....: but i have troubles configuring the pen, with the 3400 method : is it possible to have details on your xorg.conf and your start-up scripts please ?

(for the IRDA, if you have "Universe-Multiverse" i have installed (Synaptic) "irda-utils" and "ircp" + "toshset" , then "gksudo gedit /var/lib/setserial/autoserial.conf" to find your IRDAport, "gksudo gedit /etc/default/irda-utils" and replace Device="/dev/ttyS1" with YOUR result )

FrenchDocumentation: [http://doc.ubuntu-fr.org/materiel/port_irda](http://doc.ubuntu-fr.org/materiel/port_irda)

---

### Post by bwiewiora on 2007-02-18
I used the 3400 method described in this forum post:

[http://ubuntuforums.org/showthread.php?p=2169401#post2169401](http://ubuntuforums.org/showthread.php?p=2169401#post2169401)

the how-to is on page 3, but after going through that, the pen still didn't work for me.  My last post on page 4, however, describes what I had to do to get it to work.

---

### Post by cosmobreton on 2007-02-19
Woooow THANKS bwiewiora  !!!!! :popcorn: 

it Works! Right-Click and everything ! i'm adjusting the tablet-pressure under Gimp, but still!!!!!!, it' just Rocks!!!!!!! :KS 

THANKS for the advice (retakes on page4, essential!) 

I will tell to let you a place in Paradise... :) you're my guest 

aaaaaaaaaaaaaaaaaaaaaaaaaaaaa:) now, instead of the usual "Gnome" graphic interface , let's have FluxBox :):):)

---

