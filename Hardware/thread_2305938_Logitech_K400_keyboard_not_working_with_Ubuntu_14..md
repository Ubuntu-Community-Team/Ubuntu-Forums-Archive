---
title: "Logitech K400 keyboard not working with Ubuntu 14.04 LTS"
date: 2015-12-10
forum: Hardware
---

### Post by Christopher_Naught on 2015-12-10
I am a Ubuntu noob and I have a new Chromebox that I managed to get Ubuntu 14.04 LTS on. I also have a Logitech K400 I am trying to use with it. The trackpad works great, but the keyboard does not work at all. I tried the Logitech on another computer I have and the keyboard and trackpad both worked on my Mac, so I know the receiver and the keyboard are good, and I know that Ubuntu at least recognizes the receiver and the trackpad, but I cannot get it to do anything with the keyboard. I am hoping somebody has some suggestions that will get this working. I am sick of using a wired keyboard as I am using this in my living room as a Plex server. Thanks in advance for any help.

---

### Post by blm-ubunet on 2015-12-10
This is no real help but.. 
The K830 works fine with ubuntu 10.04 & 14.04.
Works faultless in mobo BIOS, GRUB, console login, everywhere..

You could look in /var/log/Xorg.0.log file or stdout from "dmesg" for clues..

Do you use the logitech BT dongle or the chromebox internal BT? (assuming that is possible).
Did you use some custom crafted kernel ?

Curious that the k400 keyboard does not work with original chromebox OS (along with lots of other keyboards)
[http://forum.kodi.tv/showthread.php?tid=211797](http://forum.kodi.tv/showthread.php?tid=211797)
Swap the k400 for a k830? much better keyboard IMO.

---

### Post by Christopher_Naught on 2015-12-14
So I switched to the k830 and am still having the exact same problem.

---

### Post by kurt18947 on 2015-12-15
This may or may not help but did you try plugging the receiver into a different USB port? I had trouble with a Logitech K350 keyboard appearing to 'buffer' keystrokes. Moving the unifying receiver to a different USB port appears to have reduced the problem 98%.

---

### Post by Christopher_Naught on 2015-12-15
I have tried multiple USB ports. sudo lsusb shows my unifying receiver, but the trackpad is the only thing that works. I cannot get the keyboard to do anything.

---

### Post by kurt18947 on 2015-12-16
Have you looked at Keyboard settings? I can't imagine a setting that would totally disable a USB keyboard input but it's the only thought I can come up with. Do you have access to a wired USB keyboard to try on the Chromebook? If a wired keyboard didn't work either I'd wonder if there's some incompatibility between the Ubuntu install and the Chromebook's USB system. I wish I could be of more help.

---

### Post by Christopher_Naught on 2015-12-18
So a wired keyboard works, and a wireless Logitech keyboard with no trackpad works, just any keyboard that has a built in keyboard does not work.

---

### Post by blm-ubunet on 2015-12-18
What error/warning are there in
/var/log/Xorg.0.log ?

From a terminal (& using the wired keyboard) run "xev" then hit some keys on the K830..
Do you get any keystroke events?

Is your *buntu14.04 & kernel a normal build or something special for chromebox?

---

### Post by Christopher_Naught on 2016-01-17
My Ubuntu build is normal and when I run xev I do not get any events.

---

### Post by him610 on 2016-03-01
For what its worth...

The Logitech K400 has been replaced by model K400r.  I recently acquired a K400r, it worked when I first plugged it in. To pair it with my older wireless Logitech  mouse, M325, it was necessary to configure it on a computer running Win7. Logitech's pairing application is only available for Windows, MacOS, and Chrome OS.  After pairing the M325 with the unifying receiver than came with the K400, I moved all of the components over to my Ubuntu machine where they all work great together. 
Oh, one more thing..., the K400r sells for ~$20 in Walmart. ;)

Update: the application for Chrome OS is actually for the Chrome browser, so one doesn't need a Windows machine to pair additional devices

---

### Post by Christopher_Naught on 2016-03-01
The keyboard is actually already paired with receiver and works with other computers, just not Ubuntu on the Chromebox.

---

### Post by him610 on 2016-03-01
I checked the specs of a lower priced Chromebox. It comes with only USB3 ports; the Logitech device has a USB2 connector.  Supposedly, USB3 is backward compatible with USB2 devices, but in my opinion, it is iffy at best. 
Other people seem to have experienced similar problem...
[https://forums.logitech.com/t5/Mice-and-Pointing-Devices/Unifying-Receiver-stops-working-when-a-USB-3-0-device-is-plugged/td-p/779173]("https://forums.logitech.com/t5/Mice-and-Pointing-Devices/Unifying-Receiver-stops-working-when-a-USB-3-0-device-is-plugged/td-p/779173")
[https://communities.intel.com/thread/51416?tstart=0]("https://communities.intel.com/thread/51416?tstart=0")

---

