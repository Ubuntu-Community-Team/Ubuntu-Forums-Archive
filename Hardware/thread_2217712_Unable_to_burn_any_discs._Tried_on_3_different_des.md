---
title: "Unable to burn any discs. Tried on 3 different desktops. (suspect because of 1310)"
date: 2014-04-18
forum: Hardware
---

### Post by vap1485 on 2014-04-18
Greetings all I have been trying (unsuccessfully) to burn onto DVDs or CDs. I have tried on my home desktop running ubuntu 13.10 x64, on my wife's laptop, (same OS) and on my mom's desktop (same os) all giving errors leaving me with a ruined disc. Here is the error I'm getting on my mom's computer.

Failure: SCSI error on write(181232,16): [5 21 02] Illegal request. Invalid address for write.

The only thing these computers have in common is ubuntu 13.10. Am I incorrect?

I've also tried different discs on all the computers.

---

### Post by Bashing-om on 2014-04-18
vap1485; Hi !

Did you verify the .iso image(s) ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Did you burn correctly ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Did you verify the disk burn ?
Boot the liveDVD, depress and hold right shift key as soon as the bios screen clears -> language screen, escape key to accept default ->
boot options screen -> "check disk for errors".

Then if it does not boot, need to do some tweek'n in those boot options.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by vap1485 on 2014-04-18
Greetings. I've tried burning many different things. ISOs, Audio CDs, & files. All with no success. rebooting now..

---

### Post by vap1485 on 2014-04-18
I tried to boot the live dvd as your directions, but it had no effect, I was able to boot wit the live dvd by selecting it in the boot menu though.

---

### Post by Bashing-om on 2014-04-18
vap1485; Hey,

Really need to verify the burn to DVD, There is but a small window in time for grub to recognize that a key has been depressed, Try again; As soon as ubuntu's purple splash screen ( stick figure & keyboard icons at bottom of screen ) appears repeatedly hit the right shift key -> ( any key should work ) language screen ?
Yes !, escape key to accept the default and now should have the boot options screen -> "check disk for defects".

[INDENT][INDENT]it is ubuntu
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

