---
title: "WARNING: Ubuntu 10 LTS may have permabroke my laptop"
date: 2010-07-04
forum: Hardware
---

### Post by Asymptotic on 2010-07-04
I have an Acer Aspire 5735Z.

It came stock with Windows Vista. The Hard Drive was partitioned, One called C: the other Data.

Using gParted from the live CD:
I shrank Data to 10gb (after checking it was empty in windows) leaving 50gb or so for an Ubuntu partition.

I installed Ubuntu to the largest continuous free space.
The install completed and I restarted my laptop.

My monitor no longer turns on, I cannot enter BIOS, I cannot boot from the following LiveCDs

Ubuntu 10
Ubuntu 9.04
Fedora 13
Windows 7 installer
Windows Vista Recovery

The machine powers up.. the screen stays off, the harddrive light blinks a few times, if a disk is in the machine it will spin the drive, if not it will turn off and repeat, this will happen to the machine 3 times then it turns off.

I am at a complete loss of what to do, I think its completely buggered my dads work laptop... I'm going to get hell for this.

Before I go out and spend money, would buying a replacement HDD fix this? By which I mean at least allow me to install Vista again.

Asymptotic.

---

### Post by davidmohammed on 2010-07-04
if the BIOS screen doesnt even appear then I strongly doubt that ubuntu caused the issue - ubuntu installer cant flash the BIOS.  It looks like you've got a very unfortunate coincidence.

Something may have become loose e.g. RAM needs taking out and repositioning, hard-drive, CD-Drive needs disconnecting and reconnecting etc.  It must be a hardware issue.

---

### Post by an0dos on 2010-07-04
> **Asymptotic said:**
> I have an Acer Aspire 5735Z.

It came stock with Windows Vista. The Hard Drive was partitioned, One called C: the other Data.

Using gParted from the live CD:
I shrank Data to 10gb (after checking it was empty in windows) leaving 50gb or so for an Ubuntu partition.

I installed Ubuntu to the largest continuous free space.
The install completed and I restarted my laptop.

My monitor no longer turns on, I cannot enter BIOS, I cannot boot from the following LiveCDs

Ubuntu 10
Ubuntu 9.04
Fedora 13
Windows 7 installer
Windows Vista Recovery

The machine powers up.. the screen stays off, the harddrive light blinks a few times, if a disk is in the machine it will spin the drive, if not it will turn off and repeat, this will happen to the machine 3 times then it turns off.

I am at a complete loss of what to do, I think its completely buggered my dads work laptop... I'm going to get hell for this.

Before I go out and spend money, would buying a replacement HDD fix this? By which I mean at least allow me to install Vista again.

Asymptotic.

It sounds like you may have had a hardware failure (possibly the mobo) occur coincidentally around the same time as you installed ubuntu. You should be able to access the bios even if there is no hard drive in the computer. Have you tried connecting an external monitor to it?

On the bright side, it's probably not directly your fault that the computer is having problems. :)

---

### Post by Asymptotic on 2010-07-04
Yes I have tried An external monitor, nothing comes up on that either.

Im currently downloading the Fedora bootable install CD.. see if that'll let me install over the Ubuntu partition and maybe reinstall the bootloader (I am still naively hoping that's the issue)

Im hoping this laptop is still under warranty and that my Dad happens to have his receipt, although I think it was bought on a credit card so that would do for proof of purchase.
 
I'm going to try booting the restore CD's that I made when he first got the machine (although I highly doubt it will work anyway)

---

### Post by magneze on 2010-07-04
Ubuntu won't have broken it. The monitor won't turn on? Is it plugged in? :popcorn:

---

### Post by Asymptotic on 2010-07-04
> **magneze said:**
> Ubuntu won't have broken it. The monitor won't turn on? Is it plugged in? :popcorn:

Heh, I admire your optimism, its a laptop so I Bloody hope so! and the external monitor? yes it was (now its on my main machine again and is how I can see what im typing)

---

### Post by ajgreeny on 2010-07-04
If you can not access the BIOS, then I agree that the problem is nothing at all to do with ubuntu.  The BIOS is read and acted upon long before anything else on any hard drive is even detected, and should be accessible with no hard drive in the machine.

I reckon you have a coincidental hardware failure as others have said.

---

### Post by bcbc on 2010-07-04
This link looks interesting... [http://www.theeldergeek.com/forum/index.php?showtopic=37583](http://www.theeldergeek.com/forum/index.php?showtopic=37583)

> Problem: On Acer's website, the only BIOS file for Aspire 5735z is a .exe and .sys file. How do I make the BIOS flash work properly, using the [Fn]+[Esc] boot method and CD?

---

### Post by Asymptotic on 2010-07-04
OOOh Bcbc you may have given me a happy in my pants, I'll give this a try and let you know how it goes.

---

### Post by _Mark_ on 2010-07-04
Try disconnecting the power and remove the battery for 5 mins then try again, simplistic but has worked for me in the past

---

### Post by Asymptotic on 2010-07-04
> **bcbc said:**
> This link looks interesting... [http://www.theeldergeek.com/forum/index.php?showtopic=37583](http://www.theeldergeek.com/forum/index.php?showtopic=37583)

bcbc, I'm so happy I could cry, Thanks for your awesome research skills, you have saved my *** so badly. Flashing the Bios worked like a charm!
Thank you SO SO SO SO SO SO SO SO SO SO SO much

---

### Post by bcbc on 2010-07-04
> **Asymptotic said:**
> OOOh Bcbc you may have given me a happy in my pants, I'll give this a try and let you know how it goes.

lol, that gave me a good chuckle... 

> **Asymptotic said:**
> bcbc, I'm so happy I could cry, Thanks for your awesome research skills, you have saved my *** so badly. Flashing the Bios worked like a charm!
Thank you SO SO SO SO SO SO SO SO SO SO SO much

You're welcome :)

---

