---
title: "Live-CD boot error"
date: 2009-04-12
forum: Hardware
---

### Post by Levviathor on 2009-04-12
A couple of days ago I downloaded the iso for Desktop Ubuntu x386.  Tonight I burned it onto a CD as directed to by help.ubuntu.com/community/LiveCD, including the whole md5 business.

It didn't automatically boot from the CD, so I had to hold f12 and tell it to from the boot menu.  I got a neat fade effect of the words "ubuntu", and then the Ubuntu boot screen (with the orange bar bouncing back and forth).  After about five minutes, it gave me an error screen that scrolled by fairly slowly (1 line per second or so), repeating the same ~six messages.  I wrote down the errors as best I could.

Here they are:
end_request: I/O error, dev sr0, 17636
Buffer I/O error on device, logical block 4411
SQUASHES error: sb_bread failed reading block 4409
SQUASHES error: Unable to read fragment cache block [659e02]
SQUASHES error: Unable to read page, block 659e02, size ed1

My system:
Dell Inspiron 1525
Windows HP 32bit
4GBs of RAM (I know, I know)
Pentium dual CPU T2370 1.73GHz

---

### Post by lisati on 2009-04-12
My first impression is that you might have to burn the disk again. Have you had a chance to use the "Check CD for errors" option that usually displays on the menu?

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto) is also a good read if you're not used to burning disks.

---

### Post by Levviathor on 2009-04-12
EDIT:

I found the menu you were referring to.  It got stuck at ~3 percent, so I just rebooted.  The default speed for burning an image in InfraRecorder is Maximum. Unfortunately, it would seem that it wrecked the file.  Having re-burned the image it minimum speed, I will now attempt to do a CD boot.  Wish me luck.

---

### Post by egalvan on 2009-04-12
> **Levviathor said:**
> 

My system:
Dell Inspiron 1525
Windows HP 32bit
4GBs of RAM (I know, I know) [COLOR="Red"]<--What's wrong with this? Sounds good to me :)[/COLOR]
Pentium dual CPU T2370 1.73GHz

Have you been told that 4GB is "bad"?

I run 8GB under Ubuntu 8.04.2 32bit...

---

### Post by Levviathor on 2009-04-12
@Egalvan, Windows 32bit can only utilize 3.5Gbs.  I assume that Ubuntu 32bit is similarly limited...?

Anyway, I successfully managed to boot Ubuntu off the new CD I burned.  Everything worked beautifully.  I even managed to connect to my wireless modem.  I'll be too busy today to set up a partition and install Ubuntu, but I will as soon as I get the chance.  If all goes well, you probably won't hear from me again xD

---

### Post by egalvan on 2009-04-15
> **Levviathor said:**
> @Egalvan, Windows 32bit can only utilize 3.5Gbs.  I assume that Ubuntu 32bit is similarly limited...?


You assume wrongly...

There are many things that MS XP cannot do that *nix's do very well...

Better memory management is one... better hard drive space use is another...

Don't measure *nix with the same yardstick that MS-XP uses.
*nix is DIFFERENT than MS-Windows.
In many ways BETTER.

As I stated, I run **8GB** on a **32bit** version of Ubuntu.
It sees all 8GB.
try THAT with MS-XP **32bit**.

Yes, I will soon be transitioning to a 64bit version...
It's just that I value stability above "newness", so I am running 8.04.2 LTS.

I truly hope all goes well with you here in *nix Land...
Welcome, and I hope to "see" you again soon...

ErnestG

---

