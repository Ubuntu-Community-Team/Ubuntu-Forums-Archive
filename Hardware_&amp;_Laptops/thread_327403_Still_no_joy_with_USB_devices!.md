---
title: "Still no joy with USB devices!"
date: 2006-12-29
forum: Hardware &amp; Laptops
---

### Post by conal on 2006-12-29
Ok, here's what I wrote a day or two ago:

 "...I've just installed Xubuntu on an old laptop (Toshiba Portege 7020ct). It works great but I have one problem- I can't get any usb devices working.
There are two usb ports in the laptops docking station. These work with my mp3 player and my speedtouch modem. however I need to use the usb port on the laptop itself. {as the docking station is too heavy to carry}
If I plug in my memory stick/mp3 player the light comes on- so I know it's getting power- however no icon appears on the screen..."

What I really want to know is: 
a) What commands would I enter to test if my laptop recognises I'ts usb port? (xubuntu has no device manager app. like ubuntu has)
b) Could there be power going to my usb port but still a bad connection inside my computer? (I tried to have a look inside but realised I'ts not so simple with a laptop!) 

Tried experementing with the 'lsusb' command to no avail, Is it something to do with xserver-xorg (I had to reconfigure this to get my display working - thanks to old post by Jason DeRose)

I'm trying to make a living as a graphic designer using old computers, and I don't know what im doing when it comes to linux - please help!

Many many thanks!

---

### Post by Titus A Duxass on 2006-12-29
Have you tried booting with your USB devices plugged in?  Sometimes that does the trick.

---

### Post by conal on 2006-12-29
Thanks.  

I've tried booting up with them in: 

-With the memory stick the light doesn't even come on (as it does when I insert it once booted up) 
-With the usb modem the lights come on (but flash red to show it is not communicating with the computer). 

Is there something I have to change in the BIOS settings or something? (I don't really understand how that stuff works).

---

### Post by Titus A Duxass on 2006-12-29
Sorry, but that is the only thing that I have to help.
I think the  USB support in Ubuntu still needs a bit of work.

---

### Post by xmastree on 2006-12-29
> **conal said:**
> Tried experementing with the 'lsusb' command to no avail,
What happens when you run it?

```
chris@pollard:~$ lsusb
Bus 002 Device 005: ID 03f0:7104 Hewlett-Packard DeskJet 3420c
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
chris@pollard:~$

```
That shows my mouse and printer plugged in and recognised.

Plug in my external drive to another port, and run it again and I get:
```
Bus 002 Device 005: ID 03f0:7104 Hewlett-Packard DeskJet 3420c
Bus 002 Device 003: ID 045e:0039 Microsoft Corp. IntelliMouse Optical
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 058f:6390 Alcor Micro Corp.
Bus 001 Device 001: ID 0000:0000

```

Then the disk automounts perfectly. This is on a desktop, but my ubuntu laptop works the same way apart from the external disk, which kills the port until the next reboot. My guess is that it demands too much power. Thumbdrive and card reader work just fine.

---

### Post by kinematic on 2006-12-29
connect your mp3 player and enter "dmesg"(without the quotes)in the terminal and see what that turns up(could also be "sudo dmesg" but i don't know for sure since our ubuntu box is in the shop for repair).

---

### Post by TheWizzard on 2006-12-29
> **Titus A Duxass said:**
> I think the  USB support in Ubuntu still needs a bit of work.
:confused: 


```
dmesg 
``` will give you the information about the usb drive. you can also use: 
```
tail -f /var/log/syslog
```
before you plug in and watch for (error) messages. 


> **xmastree said:**
>  This is on a desktop, but my ubuntu laptop works the same way apart from the external disk, which kills the port until the next reboot. My guess is that it demands too much power. Thumbdrive and card reader work just fine.

did you try your external disk with a powered usb hub? usb ports on laptops have limited power. i'm not 100% sure, but i think you should be able to control the power output of your usb ports.

---

### Post by xmastree on 2006-12-29
> **TheWizzard said:**
> did you try your external disk with a powered usb hub?
Nope, I don't have one. No big deal, I don't use it much anyway. I'm sure that would work though.

---

### Post by conal on 2007-01-08
Hello,

Thanks all, I've tried everything suggested, and have been puzzling over it for the past week.

When I enter "lsusb" i get this:

```
Bus 001 Device 010: ID 2032:0001
Bus 001 Device 003: ID 06b9:4061 Alcatel Telecom SpeedTouch ISDN or ADSL Modem
Bus 001 Device 001: ID 0000:0000
```

The computer has 3 usb ports, 2 on the base and one on the laptop, so I think I'ts got this right (?)

If i enter "sudo dmesg" I get this (just the bit about usb):


```
[   46.641523] uhci_hcd 0000:00:05.2: irq 11, io base 0x0000ffe0
[   46.642765] hub 1-0:1.0: USB hub found
[   46.642818] hub 1-0:1.0: 2 ports detected
[   46.985347] usb 1-1: new low speed USB device using uhci_hcd and address 2
[   47.029099] Attempting manual resume
[   47.117011] EXT3-fs: INFO: recovery required on readonly filesystem.
[   47.117032] EXT3-fs: write access will be enabled during recovery.
[   47.377162] usb 1-2: new full speed USB device using uhci_hcd and address 3
```


(at this point I only have a modem plugged in)

I tried the command suggested by TheWizzard: "tail -f /var/log/syslog" 
I then plugged in the memory stick and watched for errors. Nothing happened at all, so, I'm thinking that there's a loose connection inside the computer.

I think I'll just be grateful to have got a good OS working on this old computer!

Thanks for all the help!

---

### Post by conal on 2007-01-12
PROBLEM SOLVED

Our local IT man had a look inside the laptop and found that a cable had been hardwired to the internal side of the USB port. It was for a touchscreen, which I didn't know I had, and don't need. 

I don't know if the laptop was sold like this. I'ts 8 years old so I guess an external usb port was less essential then.

From what I saw, it looked very difficult to remove it- I wouldn't reccomend trying this unless you really know what you are up to!

My laptop is now fully operational!

Thanks to everyone who gave help on the forum, and thanks Joe, for fixing it!

---

