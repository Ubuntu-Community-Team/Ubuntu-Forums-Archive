---
title: "Error while installing Ubuntu 8.10"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by rwpage on 2009-02-19
Hi, just so you all know I would consider myself "new" to ubuntu, although i used it around v3 or 4 a LONG time ago. I've been trying to install it on my laptop and I keep getting errors. I tried to install it with the live installer and i got an I/O Errno 5. After searching around a bit, it seemed that using the alternate (text) installer was a "fix." However, after trying to install the base system with the text installer, I get a warning that essentially
```
file:///cdrom/pool/main/g/gcc-4.3/gcc-4.3-base_4.3.2-1ubuntu11_i386.deb
```
was corrupt. I then pressed continue and it told me that it couldn't download package gcc-4.3-base (presumably because the package was corrupt). Then I continued through that (just for grins) and I got around 71% and it said:
> An error was returned while trying to install the busybox-initramfs onto target system.

Could anyone help me? I'd really like to get back to using ubuntu again, but I must be honest, this type of fiddling around with installations that is associated with linux is what drove me away back to windows in the first place. o_O

EDIT: Just a thought, maybe it is the CD I'm using. I'll try using the DVD installation tomorrow (I don't have any other CD's, only this HP brand).

---

### Post by Partyboi2 on 2009-02-19
Did you check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") that it matched before you burned it to disk? Also did you check the cd for defects (One of the option at the main menu of the ubuntu cd) Also make sure you burn the iso to disk at x4 or less to avoid corruption.

---

### Post by rwpage on 2009-02-19
Yes the md5sum matched.. but I can only burn at 16x for the lowest speed (using nero in windows). Is there some problem burning faster than 4x?

EDIT 1: OK, well I checked the CD for errors and, such a surprise, there was one on it. I really don't know why I didn't check this last night -_-. Well I'm gonna get another program and burn it slower and see how that goes.

And just for the record, the md5sum matches for the ISO file, so I'm assuming it's burning the ISO that's generating the problem.

EDIT 2: I did a little bit of reading about CD burners and I came across a lot of people who say that data corruption occurs when you push the writer to its limits (whether it's too slow, or too fast). Since my burner is a 42x writer, I decided to burn the CD at 32x. And something I hadn't done before was verify the data after writing. It checked through. Next I booted from the CD and checked for errors. None. Now I'm attempting to install the OS, it is copying as I type this. I will post an update when it finishes (or craps out -_-).

---

### Post by rwpage on 2009-02-19
SUCCESS! Everything works great now. I guess that was my problem; burning the CD too slow. **For anyone who is getting an errno 5, I sugguest VERIFYING your data after you burn it, and then CHECKING your disc for errors BEFORE installing anything** (yes I know, a bit of a n00by mistake, but give me a break I've been using windows for the past 2 years :D).

---

### Post by Therion on 2009-02-19
Two things that help in my experience: 

1.  **Proper** burn speed (slower is not *always* better).  8x seems to be just about right generally speaking, with 4x and 16x being close seconds.  
Decent media and read-verifies are a MUST.

2.  Use of an **80-wire**, 40-pin connector cable for IDE optical drives (SATA optical-drive users can obviously ignore this).  Pushing music across a standard 40/40 cable is one thing (you're not going to notice a missed or dropped bit here or there) but the sheer volume of data required for a bootable CD or DVD, such as you need for a distro, is another matter - not too mention you need absolute accuracy to ensure a good install.  

The 80/40 ribbon cable has an additional 40 wires (but the standard number of 40 connecting pins) that insulate against and help to dissipate the electromagnetic noise that can cause "coasters" when trying to burn a bootable .iso CD/DVD.  This simple change will really help ensure you get "clean" burns at higher speeds.  

If you have an IDE optical drive, an 80-wire 40-pin connector cable will be the best $10 you can spend on your PC.

---

### Post by RJARRRPCGP on 2009-02-19
Actually 80-wire cabling only is required when the optical drive is UDMA/66 (UDMA 4) or higher. Only the new DVD and CD combo drives support this. 

I never have seen a UDMA/66 (UDMA 4) CD drive.

They are usually UDMA/33 (UDMA 2)

UDMA/33 DOES NOT require an 80-wire cable.

---

### Post by Therion on 2009-02-20
> **RJARRRPCGP said:**
> UDMA/33 DOES NOT require an 80-wire cable.
I never said anything about them being "required".

---

### Post by rwpage on 2009-02-21
Hope this thread helps a lot of people like me. Definitely a lot of people here know what they're talking about :) Thanks for all the help guys.

---

