---
title: "MCE Keyboard with IRTrans"
date: 2008-08-13
forum: Hardware
---

### Post by theCroc on 2008-08-13
I recently turned my Mediaportal box into a mythtv box (using mythbuntu-desktop on top of an ubuntu install) I have a few problems though that I hope you guys can hep me out with.

1) I'm using an OrigenAE x15e case with a touchscreen on it. I can't for the life of me figure out how to install and/or calibrate the drivers. Touch seems to work but it is really uncalibrated and seems to be rotated 90 degrees in relation to the monitor. Thats OOTB as I couldn't be bothered with the driver this time around. Now I can live without touch as Mythtv doesnt support mouse input everywhere anyway.

2) It uses an IRTrans reciever that, from what I understand, completely replaces lirc (or rather, emulates it.) This works great with my remote (MS USB2/OrigenAE branded) However I recently got an MS MCE Keyboard. The remote parts of the keyboard works great but the mouse pointer, qwerty-keyboard and shortcut buttons need another driver. I dont even know where to start other then that mod_mce is the only working driver right now. Any guide I find assumes I have the MS usb2 reciever using lirc. If anyone who knows more about the mod_mce driver then I do could help out I'd be very thankfull.

3)I have a Leadtek WinFast 2000XP EXPERT TV-Tuner card. Its software encoding (I know, lame) But according to the Mythbuntu.org website it is supported. Any tips on getting this working with myth would be awesome (Myth identifies the card but never finds any channels on it) I know it has something to do with the bttv driver but havent been able to find an updated guide on how to install/configure it.

So any help in any of those areas would be fantastic. The TV or touchscreen is not a dealbreaker for me. If I loose patience I'll just sell the TV-tuner on ebay and get a hardware encoding one and as I said I can live without touchscreen. **The keyboard on the other hand I really want working.**

---

### Post by theCroc on 2008-08-23
Update:

1) I unplugged the touchscreen so that is no longer an issue.

2) I bought an MS MCE Remote with ir reciever and managed to get the keyboard and mouse part to work woth Lirc:mod_usb. However I lost all remote functionality (Only keyboard and mouse works) Although it is usable it is lacking in functionality this way (Play pause etc. doesn't work) Does anyone know how I get Mythtv to recognize lirc_mod_mce as a lirc remote?

3) As yet unresolved.

---

