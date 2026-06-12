---
title: "LCD HDTV works with XP but not Ubuntu"
date: 2009-05-17
forum: Hardware
---

### Post by hugha on 2009-05-17
I have been using Win Xp and Ubuntu 9.04 with a regular old CRT monitor and a KVM switch. This had worked well.  I recently decided that I would like to clear the old clunker CRT off my desk and get a flat screen monitor.  I found a great deal on an inexpensive Sansui HDLCD1955 19" HDTV with a tuner This allows me to get rid of my tv old monitor and get more space on my desk. Much to my surprise I get no display for my Ubuntu system when I switch it.

I get a Bios screen "F2" and then before it gets to the login in screen it is blank. I am not a "serious tech" type of user. The Xp works great. the Tv works. Just no Ubuntu display.

Any ideas. Do I need to connect my old CRT to the Ubuntu box and tweak some settings? Careful semi newbie at work here!

Any help much appreciated.

---

### Post by irv on 2009-05-17
One thing you might try is when your grub comes up at boot time go to the recovery mode. When it boot to the menu scroll down to Xorg fix and let it find the video for the LCD. Then try booting normal. Maybe it will work.

---

### Post by taurus on 2009-05-17
Can you get to GRUB menu (press Esc key to bring it up if you don't see it when you first turn on your machine)?  Try booting into recovery mode (usually the second option on the screen) and run the xfix to fix the X server.

---

### Post by LinGNUbie on 2012-02-10
I have a working xorg.conf file posted in this thread: [http://ubuntuforums.org/showthread.p...ghlight=sansui]("http://ubuntuforums.org/showthread.p...ghlight=sansui")

If familiar with using vim:

Let the computer boot, when it seems to stop, CTRL+ALT+F2.

Log in, then sudo vim /etc/X11/xorg.conf, enter your password.

Copy information I posted, and reboot.

---

