---
title: "Did my hard drive crash?"
date: 2010-03-10
forum: Hardware
---

### Post by gstilma on 2010-03-10
Hello all -- first post for me, after reading and benefiting from this forum for some time.

I recently got an IBM Thinkpad T42 (2373), 2 GB RAM, 60 GB HDD, for pretty cheap and did a fresh install of Ubuntu 9.10. I think the HDD is the original, so it could be 6 years old.  Everything was working flawlessly until today, when the thing suddenly hiccuped and shut down. Since then, I haven't been able to boot into the OS successfully in order to retrieve anything, as it always hangs right after entering login information, if not before. I finally resorted to re-installing Ubuntu, but not even that works -- no live CD or USB drive.

I'd really like to be able to retrieve some files, but mainly just want to get it back in working order. I should mention that most of the time now, I get a boot menu showing the two kernel options and a recovery mode for each, which I can get into.

Is replacing the hard drive the only option here? Why won't a live CD work?

---

### Post by Sumo74 on 2010-03-10
Sounds like the problem I have had a bunch of times. Try to get into the Recovery shell, and run fsck. It should fix the problem and allow Ubuntu to boot, and run, with all your files in tack.

---

### Post by IcarusR on 2010-03-10
If it will not boot from hdd, cd-rom or usb then your problem is not hdd. More likely mobo or bios.
Can you get into bios, if so does it recognise hdd correctly ?
How far do you get booting from hdd ?
Will any cd-rom boot ?

---

### Post by gradinaruvasile on 2010-03-10
> **IcarusR said:**
> If it will not boot from hdd, cd-rom or usb then your problem is not hdd. More likely mobo or bios.
Can you get into bios, if so does it recognise hdd correctly ?
How far do you get booting from hdd ?
Will any cd-rom boot ?

The guy said "it hangs after entering login information". Assume it boots but something is messed up. A fsck would be in order.

---

### Post by gstilma on 2010-03-10
> **Sumo74 said:**
> Sounds like the problem I have had a bunch of times. Try to get into the Recovery shell, and run fsck. It should fix the problem and allow Ubuntu to boot, and run, with all your files in tack.

Did this - no result.  fsck didn't detect any filesystem errors, but now booting from hdd, as soon as 'GRUB loading...' appears it kicks into a GRUB bash. I have minimal commands now available. Interesting, though: when I type 'exit' I get this:

Intel(R) Boot Agent GE v1.2.17
Copyright[...]

Intel(R) Boot Agent PXE Base Code (BA1217BC)
Copyright[...]

PXE-E61: Media test failure, check cable
PXE-M0F: Exiting Intel Boot Agent.
Operating System not found

...and this now happens every time, i.e. I don't get nearly as far as I used to booting from hdd.

---

### Post by gstilma on 2010-03-10
> **IcarusR said:**
> If it will not boot from hdd, cd-rom or usb then  your problem is not hdd. More likely mobo or bios.
Can you get into bios, if so does it recognise hdd correctly ?
How far do you get booting from hdd ?
Will any cd-rom boot ?

I can get into bios no problem, and it seems to see the hdd just fine. I used to get pretty far from hdd, sometimes through the login screen, but never all the way. I just tried a GParted live CD which gave some errors and then kicked out into a terminal. Not looking good. The most success I've had with a live CD is Ubuntu's alternate 9.10 iso. It lets me execute a shell in /dev/sda1, which is the one with the bad filesystem...

> **gradinaruvasile said:**
> The guy said "it hangs after entering login information". Assume it boots but something is messed up. A fsck would be in order.

...however -- in this rescue mode shell, fsck spits back:

WARNING: couldn't open /etc/fstab: Not a directory.

This is bad, I think.

---

### Post by gstilma on 2010-03-10
Thanks to those who replied -- I ran memtest and figured out that one of my RAM modules was bad. I removed the bad module and the boot problem disappeared. I had been getting a SQUASHFS error when trying to run a live CD. Too bad I didn't figure that out before reinstalling Ubuntu. Live and learn.

---

