---
title: "can't remove drive"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by X5-655 on 2005-09-05
my laptop has it's CD-ROM drive external, using a proprietary port..

it's a Latitude CSx..

when I try and remove the drive, the whole laptop freezes..  in Windows, this would happen too, but in Windows, I could click an icon in the system tray to allow safe removal (no third party software, it's the standard Windows device removal icon)..

is there a way in Ubuntu to do this?  I tried shutting down and removing it that way, but it would freeze at startup, as if it was trying to find it..

---

### Post by odin on 2005-09-05
I'm just guessing but have u tried unmounting it with umount?

I dont know something like umount /dev/sda? where /dev/sda? is your usb device if it usb....

just guessing but hope it helps.

---

### Post by X5-655 on 2005-09-05
[QUOTE=odin]I'm just guessing but have u tried unmounting it with umount?

I dont know something like umount /dev/sda? where /dev/sda? is your usb device if it usb....

just guessing but hope it helps.[/QUOTE]

unmounting just gets rid of the CD/DVD, right?

it's not USB, it's like a IDE port on the side of the laptop that's made externally, and only Dells own module drives support it (it uses other internal Latitude modules, but on this laptop, it's used externally..)

it's hard to explain, but I took a picture of it when installing linux on it, so here's a pic of the drive next to the laptop..

[http://www.deviantart.com/view/22576266/](http://www.deviantart.com/view/22576266/)

the drive is on the right side of the Starwars box (which by the way, couldn't even get to play..)

sorry, im still new to linux.  i mean, i have used it for years, but never understood it good at all..

EDIT:  Unmount isn't even an option..  it just says "Mount Volume"

---

### Post by odin on 2005-09-05
sorry man,called me stupid but I have never seen such device in my life.

---

### Post by X5-655 on 2005-09-05
[QUOTE=odin]sorry man,called me stupid but I have never seen such device in my life.[/QUOTE]
nah, i won't call you stupid ;)

i managed to finally remove it..  i shut the laptop down, and removed it with it off, again, and finally it booted without the drive..  it was still weird though..

though, i still can't get it to play my starwars DVD.  it says something like can't read rescource..  though the icon shows on the desktop saying the DVD name and which disc it is..

---

### Post by odin on 2005-09-05
Try to see if you can find a solution in this thread for plyaing the dvd

[http://www.ubuntuforums.org/showthread.php?t=34096](http://www.ubuntuforums.org/showthread.php?t=34096)

---

