---
title: "Computer just died..."
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by PriceChild on 2006-08-18
Playing around happily and suddenly ubuntu crashes... unresponsive, won't move mouse and even the keyboard lights won't change.
 
I gave it a few minutes then reset it.
 
It will now not reboot, telling me that i need to insert a system disk.
 
Same for both my hard drives.
 
It will get stuck on "mounting root filesystem" if i boot an ubuntu cd.
 
I've tried my backup bios, no luck.
 
Got a:
```
[SIZE=2][COLOR=#008000]**BIOS**-**ERROR**-**WIDE**-RANGE-**ERROR**-PROTECTION
``` on one of my reboots on the starting bios screen.[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][/COLOR][/SIZE] 
[SIZE=2][COLOR=#008000]Motherboard is a Gigabyte GA-7vAXP[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][/COLOR][/SIZE] 
[SIZE=2][COLOR=#008000]Gonna try and restore the bios from floppy tomorrow when i'm not tired and can think straight.[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][/COLOR][/SIZE] 
[SIZE=2][COLOR=#008000]Any other ideas?[/COLOR][/SIZE]
[SIZE=2][COLOR=#008000][/COLOR][/SIZE] 
[SIZE=2][COLOR=#008000]Pricey[/COLOR][/SIZE]

---

### Post by coolclassic on 2006-08-19
It is possible your grub configuration is incorrect causing the boot sequence to look at an incorrect partion or drive for booting. This can cause the errors you are describing. You will need a rescue disk to have a look at your grub configuration.

---

### Post by PriceChild on 2006-08-19
This is DEFINATELY NOT a grub error... This is hardware failure.

I think it must be the cmos... I've flashed each bios and restored it with a new version from the motherboard's site. I've also restored it to earlier versions which i know work but still no luck.

Getting random "CMOS checksum error. loading defaults"

ALso, when booting linux in recovery mode, i get:
```
17179642.744000 hda: lost interrupt
```
repeated with different numbers.

Any ideas?

Think i'll have to get a new motherboard?

Pricey

---

### Post by NetworkGuy on 2006-08-19
Hi Pricey,

I think you should start looking for a new motherboard.  

I feel your pain..

---

### Post by coolclassic on 2006-08-19
I thought the same as you when I had exactly the same errors. The problem was the partition numbers in grub was incorrect. I would seriously look at this first before going any further.

The advice just given from NetworkGuy was the same advice I was given with my problem.

---

### Post by PriceChild on 2006-08-19
I'm just trying to boot the Desktop cd again...

and its worked... despite getting stuck on launching EVMS for a while.

I think i'll check your idea out coolclassic ;)

Still seems dodgy though seen as i was getting BIOS error before anything else had even loaded?

---

### Post by PriceChild on 2006-08-19
My menu.lst looks absolutely fine.

However its still not booting from the hard drives.

From the linux drive, it gets stuck at "Mounting root filesystem"

Tells me its "Waiting for root filesystem" below it.
EDIT 
I then get dropped to Ash...

And for windows, there's the hint of a BSOD before it resets completely.

Pricey

ANOTHER UPDATE

Ok... so it definately can't be my grub... i just ripped out the linux drive and booted straight from the windows drive.

Again, it simply reset the box after a bit.

---

### Post by coolclassic on 2006-08-19
title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

This is the grub entry I have for booting.

hd0,0 tells what device to use for its root directory this is where your problem may be.

This tells me its the 1st primary partion on the first hard drive

If you have been playing around it may be that your first entry has been rewritten so It might be worthwhile trying to comment these lines out with #

Post your menu.lst

---

### Post by coolclassic on 2006-08-19
You've updated your bios windows might not like that.

---

### Post by NetworkGuy on 2006-08-19
I'm still sticking with my original thought.    I just googled on your error message you received and got no answers only the same question mirrored on 6 different forums.

But..  have you tried to reset your BIOS to factory defaults and then configure it again? 

If that does it then I'll eat crow ;)

---

### Post by PriceChild on 2006-08-19
I'm gonna go with you Network Guy.

Attaching ONLY my windows hard drive to the machine, it will now boot perfectly off of IDE2. However, it hangs on IDE1.

This explains why the Desktop cd would boot earlier when the hard drives didn't, as both drives were on IDE1 and the cdrom on IDE2.

Its gotta be a busted motherboard hasn't it now? 

Gonna keep using it like this till i get a new one me thinks.

---

### Post by John.Michael.Kane on 2006-08-19
PriceChild have you tried replacing the cmos batt? 


just a thought...

---

### Post by PriceChild on 2006-08-19
Yup, no luck.

I've just gone out and bought a new motherboard for £40... not bad me thinks.

Plugged everything in and all seems fine :D

almost... ubuntu crashes eventually which i'm guessing is because it wasn't installed on this motherboard.
Will reinstall tomorrow on a separate harddrive tomorrow to see if that fixes it.

Pricey

---

### Post by NetworkGuy on 2006-08-19
You gotta wonder about these things.  Computer pieces and parts work perfectly "forever" and then one day they decide to stop working.  

And usually this happens only after you make some sort of software/hardware change that masks the actual problem until you pull your hair out trying to figure out how an update caused this sort of issue because "It can't be my __________ (insert failed hardware here)."

Let us know if that was it Pricey.

---

### Post by PriceChild on 2006-08-19
> **NetworkGuy said:**
> And usually this happens only after you make some sort of software/hardware change that masks the actual problem

Nope... it just froze one evening, and never worked since. No updates, no hardware changes.

---

### Post by NetworkGuy on 2006-08-23
Hey Pricey,

I'm assuming no news is good news??

---

