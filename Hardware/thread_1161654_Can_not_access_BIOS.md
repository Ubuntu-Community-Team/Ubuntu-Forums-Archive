---
title: "Can not access BIOS"
date: 2009-05-16
forum: Hardware
---

### Post by DougieFresh4U on 2009-05-16
Some one gave me an old, old laptop today and I can not/don't know how to access BIOS to point it to boot from cd-rom.
It's an IBM Thinkpad 770x with Win2000 on it. I can not get it to boot as it goes to a prompt that looks like a 'padlock' with flashing cursor and if I hit 'enter' it goes to a screen with an error box. If I put a disc in (I have the Win2000 and Ubuntu disc) it does not even recognize them.
Any help would be great, or maybe I should find a rubbish pile to toss it!

---

### Post by abn91c on 2009-05-16
google the system manual, sounds like a BIOS password. this may help also [http://www-307.ibm.com/pc/support/site.wss/DSHY-3PGT93.html](http://www-307.ibm.com/pc/support/site.wss/DSHY-3PGT93.html)

---

### Post by DougieFresh4U on 2009-05-16
> **abn91c said:**
> google the system manual, sounds like a BIOS password. this may help also [http://www-307.ibm.com/pc/support/site.wss/DSHY-3PGT93.html](http://www-307.ibm.com/pc/support/site.wss/DSHY-3PGT93.html)

Thanks, been to that site and read through the whole manual and nothing about accessing BIOS.

---

### Post by DougieFresh4U on 2009-05-17
Is there a key that can be held while booting to make it boot from cd?

---

### Post by hansdown on 2009-05-17
Hi DougieFresh4U.

Hold the F1 key when you first turn on the power.

This sould get you into the bios.

You should be able to set the boot priority to the cd drive.

---

### Post by DougieFresh4U on 2009-05-17
> **hansdown said:**
> Hi DougieFresh4U.

Hold the F1 key when you first turn on the power.

This sould get you into the bios.

You should be able to set the boot priority to the cd drive.

Tried that and it still gets to screen with little padlock and flashing cursor

---

### Post by hansdown on 2009-05-17
Try doing a manual system reset. To do this:
1. Remove battery and unplug AC adapter.
2. Press and HOLD power ON button for 30secs. at least
3. Put back the battery and plug back the AC adapter
4. Power ON the laptop as normal. 

There may be a problem if the battery is not fairly charged.

---

### Post by hansdown on 2009-05-17
There is one other way without having to open it up.

Download offline nt password and registry editor, and burn a disk.

[http://home.eunet.no/pnordahl/ntpasswd/](http://home.eunet.no/pnordahl/ntpasswd/)

What if Windows is password-protected and you don't know the password? This might be the case if the laptop runs Windows NT or 2000. If this is the case, you have a couple of options. One is to reset the password using free tools such as ntpasswd. These free utilities are often available on Linux "rescue CDs," such as Knoppix. You can boot almost any "live Linux CD" (also known as a "live CD") and read Windows NT/2000/2003/XP files. But, you need a utility like ntpasswd to reset the password so that you actually log in to Windows and use its installed applications. The book, Knoppix Hacks, gives examples of how to use ntpasswd to reset Windows NT, 2000, and XP passwords.

---

