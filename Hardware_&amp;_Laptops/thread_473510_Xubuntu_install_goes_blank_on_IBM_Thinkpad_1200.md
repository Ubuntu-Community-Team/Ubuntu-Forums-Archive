---
title: "Xubuntu install goes blank on IBM Thinkpad 1200"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by som4 on 2007-06-14
Laptop: IBM Thinkpad iSeries 1200, 700MHz Processor, 192MB RAM, 20GB HD

Have been trying to install Xubuntu on my laptop.  Problem is when i select install or install in text mode.... or even check the cd i am presented with a blank screen with an underscore flashing in the top left corner.  I am using the Xubuntu Alt 7.04 image.  I've burnt the regular Xubuntu but that wont even get to the cd autostart menu.  Just goes blank straight away.

I can run Damn Small Linux fine on the laptop, but would love to have Xubuntu as i run Ubuntu on my Desktop.  Please please help!

---

### Post by hrtsgs on 2007-07-03
I have same problem.

I got some messages in "Install a command-line system" mode:

> [ 42.210212] PCI: Guessed IRQ 10 for device 0000:00:14.0
[ 42.210378] ohci_hcd 0000:00:14.0: OHCI Host Controller
[ 42.211674] ohci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 1
[ 42.211868] ohci_hcd 0000:00:14.0: irq 10, io mem 0x81c00000
[ 42.238965] hda: max request size: 128KiB

and stopped. (Sorry, it was difficult to copy & paste all text...)

By the way, I tried to boot with Knoppix, and it freezed at USB device detection without any message.
Debian works with the version up to 3.0. 3.1 is already tricky.


I think, ThinkPad i Series 1200 was designed only for Windows. Like Software-Modem, I/O-Chip, etc...
I don't like Windows, but I'm using stil Win2k, because Linux on i Series 1200 never works!:(

---

### Post by hrtsgs on 2007-07-15
So, I found a solution to boot Ubuntu on my ThinkPad i1200. :-)
Google searching for a week...

You should add following boot-options:
```
vga=792 acpi=force irqpoll
```

Xubuntu 7.04 works o my ThinkPad perfectly! Yeah :-D

---

### Post by Tekcronic on 2007-07-27
Thank you I search for a few days a while back for my laptop it's an i series 1300 and that seems to have gotten it up and running but I am trying to install edubuntu. Well I have tried and to no avail. I also attempted with xubuntu alternate install but I will seem to need to use the livecd so that I can boot it all the way to the desktop at least 1 time.

Well I had forgotten to add the option in during booting and nw it is installed fine, thanks again.

---

### Post by rjc83x on 2007-12-03
As you can see I'm a total Xubuntu newbie - this is my first post!

I retreived my old Thinkpad 1200 iSeries from my friend and decided it needed a new lease of life. Spent a few hours tinkering around with different straps on the bootloader to no avail. 

I tried your tip hrtsgs and OH HAPPY DAY - STRAIGHT IN!!!! Your hours of googling are much appreciated!!! And thank you for taking time to share it on the board!!

rjc x

---

### Post by rjc83x on 2007-12-03
I should add that I'm installing Xubuntu 7.10 (Gutsy Gibbon) and haven't *technically* finished installing it but so far so good!!

---

