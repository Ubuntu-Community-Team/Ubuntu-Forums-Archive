---
title: "upgrading RAM causes system to be unstable"
date: 2010-09-24
forum: Hardware
---

### Post by d0.higgs on 2010-09-24
Hi,

I recently bought 2 modules, 1GB each, of RAM to upgrade my system replacing the 460 MB I had before.
Once replaced, I started my system and check with 'free -m' that the system can see them and uses them.
But my system became unstable, and it gets stuck after 20-40 minutes and I have to do a hard reboot.
Also flash-player crashes all the time no matter which browser I use.
I have made an upgrade after installing my new RAM and have the latest Kernel installed.

I cannot understand this behavior, any help will be appreciated.


d0higgs

---

### Post by d0.higgs on 2010-09-24
Sorry for the mistake in the title. I could not edit it.
Moderator(s), please help.

d0higgs

---

### Post by Fafler on 2010-09-24
Run memtest86+ from the installation CD to test the new memory for defects. And make sure i use the correct speed and voltage settings.

---

### Post by ajgreeny on 2010-09-24
It is also worth running with just a single ram module for a while, using both modules singly, as that may tell you which one is at fault.

It is possible, however, that each will run perfectly when alone, but that together they are not stable.  It has happened to me once when using a previous machine, and upgrading from a single 256 to the same 256 and a 512 added; each alone was fine, but together, a disaster.

---

### Post by CharlesA on 2010-09-24
Fixed the title for you.

I's suggest trying them a stick at a time and running memtest86+ for a few hours (overnight is best imo) on each stick and again with both sticks and see if it has any problems.

memtest86+ is included on the Ubuntu livecd - hit any key when the purple screen first comes up and select memory test.

---

### Post by pricetech on 2010-09-24
Defective RAM is my first guess too.  You said you just installed both, so I would guess they're identical.  If not, they may not play well with one another, yet both be okay.

---

### Post by d0.higgs on 2010-09-24
Hi all,

Well, since this is a ~5 yrs old box (with a 2.4 GHz Processor) I do not know its motherboard brand. I also do not know if these two modules are compatible with the motherboard or not.
But I tried this:
I tried the first module and I hot this:
```
[   2.179016 ] --- [end trace 8ccd1f00c4abbe2b] --- 
init: Error while reading from descriptor: Bad file descriptor
init: hw clock main process (228) killed by KILL signal
```

I have no idea what does this mean, but when I tried the second module, it did not give the same error as the one above. In both cases I have not reached the Ubuntu main boot screen.

Then I put back my old module, and as usual it worked fine, then I had one of the new modules added with the old not (I hope you are not lost now) and the machine seems to work without problem. It's been working for 30 minutes now.

Any ideas what does this mean?

I will be happy to do anything you suggest.

~d0higgs

---

### Post by CharlesA on 2010-09-24
Did you already try the memtest86+ thing?

Does the BIOS detect the new memory when it's inserted?

---

### Post by d0.higgs on 2010-09-24
No, I haven't yet, sorry. I am working on this machine.
I will do the test tonight for sure.

As for the bios detecting the memory, I could check from the command line (not from the setup)
free -m gave me 1475 MB, which is the memory I have now.

d0higgs

---

### Post by d0.higgs on 2010-09-24
Sorry, I had to reboot to bios to get these info:
Here is what I have from the BIOS:
```
 Base Memory: 640k
 Extended Memory: 1539072 K
 Total Memory: 1540096 K 
```

Which means the memory is already read

---

### Post by CharlesA on 2010-09-24
Yeah, it's seeing about a gig and a half. Give memtest86 a shot tonight and see if it spits back any errors.

---

### Post by d0.higgs on 2010-10-04
Hi again,

I knew what was wrong. It was the cooling fan!
Yes, the cooling fan was dying and used to stop from time to time, this is whyy my machine used to hang up!

Thank you so much for help and support, no wonder one loves Linux :)

~higgs

---

