---
title: "usb3, ubuntu 14.10, and pci-1"
date: 2015-01-19
forum: Hardware
---

### Post by jgw on 2015-01-19
I am running with ubuntu 14.10  I bought a pic-1 usb3 card so that my machine could have usb3.  What I do not know is if its really working and the machine understands its usb3.  I also have a usb3 hub plugged into the usb3 plugs from the card.  When I do an lsusb it does show the usb3 stick plugged into the usb3 hub which is plugged into the usb3 plug on the usb3 card.  Everything seems to be right but I do not know a command to make sure I am dealing with usb3.

thank you..........

---

### Post by shantiq on 2015-01-22
hi jgw     look for "[COLOR=#000000]*Device can operate at SuperSpeed*[/COLOR]"   in the output of those [commands]("http://ubuntuforums.org/showthread.php?t=2260364&p=13209036#post13209036")

when you get to lsusb command maybe do it this way so dumped on your desktop
 > sudo lsusb -v   > ~/Desktop/lsusb.txt   then open and enter ctrl+f   enter "*Device can operate at SuperSpeed*"

---

### Post by jgw on 2015-01-22
thanks for the reply AND solution!!!!

I did as suggested and got:
SuperSpeed USB Device Capability:
    bLength                10
    bDescriptorType        16
    bDevCapabilityType      3
    bmAttributes         0x00
    wSpeedsSupported   0x000c
      Device can operate at High Speed (480Mbps)
      Device can operate at SuperSpeed (5Gbps)
    bFunctionalitySupport   2
      Lowest fully-functional device speed is High Speed (480Mbps)
    bU1DevExitLat           4 micro seconds

This means everything is dandy, I think - thanks again!!!

---

### Post by mörgæs on 2015-01-22
Good, please mark the thread 'solved'.

---

### Post by shantiq on 2015-01-23
yes **[COLOR=#000000][COLOR=#dd4814][B]jgw**[/COLOR] [/COLOR][/B][COLOR=#000000][/COLOR] "[FONT=arial]Device can operate at SuperSpeed (5Gbps)[/FONT]" is the one you want to see.  Again thanx to Temüjin for the commands on linked thread.

---

### Post by Mike_Walsh on 2015-01-23
Hi, jgw.

Shantiq and I have BOTH recently fitted these PCIe USB 3.0 cards, and have been helping each other out.....with a bit of help from Temujin' s terminal commands to show what's going on.

Looks like yours, too, is 'up & running' correctly, so.....enjoy the speed increase!

DO remember that you'll never get the full 5 GB/s when using a flash drive; the design (even of the 3.0 standard 'sticks') means that you won't get the quoted speed. That's enjoyed more by SSDs and high-end hard drives; the firmware within the 'stick' and the fundamental nature of the type of flash memory used (NAND) means that's not possible. You SHOULD, however, see a good 350-400% speed increase.....which is VERY much worth having!

Enjoy.


Regards,

Mike.

---

