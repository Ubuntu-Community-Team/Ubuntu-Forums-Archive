---
title: "A few problems Im having"
date: 2007-10-20
forum: Hardware &amp; Laptops
---

### Post by Herbonator on 2007-10-20
I have just installed 7.10 on my Intel Dual Core HP Pavilion dv2000 and I'm having a couple problems.

Mic not working
I have installed skype and my mic is not working. I went to system\preferences\sounds to test it and it gave the following error:

Quote:
Failed to construct test pipeline for 'gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat'
Speaker not working correctly.
It always thinks headphones are plugged in. It is play sound but at an extremely low volume (as in headphone volume)

Webcam
The in built webcam isnt working in skype. I dont believe its detected, I cant find any options to turn it on or test it or whatever.

Small USB drive is undetected
My 160gb I.O Data HDPG drive is not being detected. It was partitioned when i got to it have a small partition that displays as a CD drive with all of the vendor software on it. I couldnt get rid of it on windows either. Ubuntu is finding the faux-cd part of the drive fine. I have the main part of the drive formatted to NTSF and it is empty. Ubuntu cant find it.

Wacom not detected
Is detected but not working.


The funny thing is that the HDD's were fine on the Live CD but stopped working when i installed linux (i am dual booting if that makes a difference).

Thanks a lot for any help you can give me.

---

### Post by Herbonator on 2007-10-21
Just sending this to the top to see if anyone may be able to help me? Ive got no where so far with this.

---

### Post by Zetheroo on 2007-10-21
Not sure about your sound issues .... sorry...

Webcam in Skype... ummm I don't think Video for Skype is happening yet! So don't test out your cam with Skype.
I got my webcam working just fine.... may want to enter lsusb in the terminal to see if your webcam is being seen by Ubuntu.

As for your HDD... dunno why its showing up twice... unless its been partitioned in some way shape or form....!? I would unmount all volumes and plug them back in.... and see....

and your little HDD .... if its has extra software loaded onto it which is natively catered for Windows.. you may need to look into the specifics of that. I have a U3 usb drive which also shows a CDrom and is a bit finiky ... just cause its meant for Windows environment.....

---

### Post by Herbonator on 2007-10-21
> **Zetheroo said:**
> Not sure about your sound issues .... sorry...

Webcam in Skype... ummm I don't think Video for Skype is happening yet! So don't test out your cam with Skype.
I got my webcam working just fine.... may want to enter lsusb in the terminal to see if your webcam is being seen by Ubuntu.


Thanks for your reply,
Here are the results of the lsusb. Im not sure what this means though...

Bus 003 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 056a:0065 Wacom Co., Ltd 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0411:00a8 MelCo., Inc. 
Bus 001 Device 005: ID 0c45:62c0 Microdia 
Bus 001 Device 001: ID 0000:0000

---

### Post by Herbonator on 2007-10-21
Also the Big HDD issue has resolved itself magically. Ive edited my first post to reflect this.

---

### Post by aardwolfsgp on 2007-10-21
Hi if you are using the USB Wacom, try this:

$ sudo gedit /etc/X11/xorg.conf

Look for the section under wacom driver and change all the "/dev/wacom" to "/dev/input/wacom"


save it and restart your system, hope it helps.

Works for my Wacom tablet.

---

### Post by Herbonator on 2007-10-21
> **aardwolfsgp said:**
> Hi if you are using the USB Wacom, try this:

$ sudo gedit /etc/X11/xorg.conf

Look for the section under wacom driver and change all the "/dev/wacom" to "/dev/input/wacom"


save it and restart your system, hope it helps.

Works for my Wacom tablet.

It is already set to /dev/input/wacom.

Thanks anyway!

---

