---
title: "Hard drive failure. Data recovery?"
date: 2009-07-31
forum: Hardware
---

### Post by Eamon1 on 2009-07-31
Hi,

my hard drive failed recently and I am seeking advice.

My laptop will not boot with the hard drive installed, even to a live cd, and my usb hdd dock won't read it.

I had most of the data backed up, but lost a few recently edited files.

I was wondering if anyone had any advice for retrieving lost data as this is my first hard drive failure and don't really know where to start.

(if it helps my hard drive is Hitachi 80gb SATA [http://www.hitachigst.com/hdd/support/5k100/5k100.htm](http://www.hitachigst.com/hdd/support/5k100/5k100.htm))

---

### Post by CrinkElite on 2009-07-31
first check to see if you can see the drive in the bois, if it can you should try getting your hands on a copy of spinrite. you can install it to a usb stick and boot into it, it uses a number of very thorough techniques which enable it to get a good read from ailing sectors and restores damaged drives to working order. it is pricey at $90 but it's workrd for me. i recovered a maxtor 1tb external drive that i had dropped while in use. Even though it was clicking and could not be mounted spinrite restored all my data and the drive is now functioning is a local drive in the system.
I know I sound like a fanboy or a spammer but i'm just so impressed by this software.

[http://www.grc.com/intro.htm](http://www.grc.com/intro.htm)

---

### Post by Eamon1 on 2009-08-01
Hi,

thanks for the help.

Unfortunately, when the drive is installed in the laptop, I can not even access the bios, or boot to a cd/usb/anything else even though they are set to a higher priority in the boot sequence.

The computer stalls after the RAM test and will not do anything after (it says to press F2 to enter setup, but does not respond).

So when the drive is in my computer, the computer is fairly useless, unless I'm being an idiot (which is quite possible...). Anyway, any other ideas?

---

### Post by IcarusR on 2009-08-01
Remove the drive, put it in an external case, then connect it to another computer (running linux) & you will then be able to run spinrite on it.

---

### Post by Eamon1 on 2009-08-01
I have removed the drive and put it in an external case, but but the computer doesn't seem to be able to find it. "fdisk -l" does not list it.

Will Spinrite be able to do its thing, its just I don't really want to go spending ~£50 if it's not going to work.

---

