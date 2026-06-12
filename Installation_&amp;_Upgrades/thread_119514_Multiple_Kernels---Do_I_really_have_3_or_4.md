---
title: "Multiple Kernels---Do I really have 3 or 4?"
date: 2006-01-19
forum: Installation &amp; Upgrades
---

### Post by tamarku on 2006-01-19
Okay, I loaded Hoary, then upgraded to Breezy.  Today I went into Synaptic and loaded all updates and it was a kernel Update.  Now when I boot I see multiple kernels:  Here is my menu.lst:

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda6 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

#title		Ubuntu, kernel 2.6.10-6-386 
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda6 ro quiet splash
#initrd		/boot/initrd.img-2.6.10-6-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.10-6-386 (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.10-6-386 root=/dev/hda6 ro single
#initrd		/boot/initrd.img-2.6.10-6-386
#boot

#title		Ubuntu, kernel 2.6.10-5-386 
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro quiet splash
#initrd		/boot/initrd.img-2.6.10-5-386
#savedefault
#boot

#title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
#root		(hd0,5)
#kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda6 ro single
#initrd		/boot/initrd.img-2.6.10-5-386
#boot

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


I commented out the lower versions just because I want to load the most recent.  Does this mean I have multiple OS's?  Or Ubuntu versions of Breezy?  Is this taking up precious disk space on a 17 gig partition?  Is commenting them out?  Should I, if there is a way, uninstall these lower versions?  I guess I don't understand this kernel stuff so if someone could answer my questions and then point me to a thread that explains the kernel updates I'd appreciate it.

---

### Post by citronmg on 2006-01-19
Those are the old versions of the kernel you still have installed.  You can go to synaptic and uninstall them if you want.

---

### Post by Klaidas on 2006-01-20
(I have a similar problem and a question)
So, is there any need to leave old kernels? Or should I simply remove them after I have upgraded?

---

### Post by Buffalo Soldier on 2006-01-20
what i usually do is after an upgrade to reboot into the new kernel and remove the old kernel.

---

### Post by alingatong on 2006-01-20
sometimes keeping some old kernels are good because if ever you have a problem with a new one you can always go back to the old kernel and try to repair the system. 

as for me, i moved from breezy to dapper and i also installed the both the i386 and i486 kernels--i ended up filling my grub menu. :-) I uninstalled all the i386 (because they say i686 is appropriate for my processor) and the old kernels. I only keep the the old kernel immediately below the latest one.

---

### Post by Sokraates on 2006-01-20
Sorry. Doublepost. See below.

---

### Post by Sokraates on 2006-01-20
How do I remove an old kernel? I know how to delete the entry in GRUB, but thats not actually "removing" it.

Synaptic does not let me select which version to remove, or did I miss an option?

---

### Post by Klaidas on 2006-01-23
This topic is on the fourth page now, so I'd like to ask again: how could I remove those old kernels? 
Thanks in advance, 
Klaidas

---

### Post by Brigrat on 2006-01-23
I don't know if this is the right section or not but maybe I can get a faster answer here.  I have an old box with a Tyan dual slot one Main Board.  Original install was I386 2.6.12***.  I installed several packages and then discovered the 686 grub.  I upgraded to that.  My machine refuses to shut down under soft power now (it did under i386).  My sister did the same thing on a different board still DP, and has no issues with power down.  any help or direction here????
Puzzled!

---

### Post by Sokraates on 2006-01-24
[quote=Brigrat]I don't know if this is the right section or not but maybe I can get a faster answer here.  I have an old box with a Tyan dual slot one Main Board.  Original install was I386 2.6.12***.  I installed several packages and then discovered the 686 grub.  I upgraded to that.  My machine refuses to shut down under soft power now (it did under i386).  My sister did the same thing on a different board still DP, and has no issues with power down.  any help or direction here????
Puzzled![/quote] 


The section may be okay, but you should rather start a new thread, since your problem seems to be different from having multiple kernels. So there are fewer chances for a good answer.

Now for some things I don't understand: Did you install the 686 GRUB or the 686 kernel? FYI: I've never heard of a 686 GRUB.

Also different kernel images (386, 686, k7 etc) depend on certain CPUs, not on the mainboard. 386 is generic and works best for older CPUs. 686 is optimized for Pentium Pro/Celeron/Pentium II/Pentium III/Pentium IV etc and k7 is optimized for AMD Duron/Athlon. Of the latter two there are -smp versions, which are optimized for dual-CPU systems.

If I understand correctly, you've got a dual-CPU system, so -smp will be your kernel of choice.

---

### Post by jackwhite on 2006-01-24
I'd actually like to remove the newest kernel (I recompiled it and think i messed it up a bit). I can boot into my older one but don't have a clue how to remove any of them...

any help?

---

### Post by Sokraates on 2006-01-25
[quote=jackwhite]I'd actually like to remove the newest kernel (I recompiled it and think i messed it up a bit). I can boot into my older one but don't have a clue how to remove any of them...

any help?[/quote]

I found out how it works (asked the question here myself, but ...).

Just start synaptic and search for "kernel" or "image". Then you need to search for the kernel-image you compiled yourself (look for the version) and remove or purge it.

Alternatively, I think you could also find the kernel image by using the "uninstallable"-filter, i.e. installed apps that are not found in the repos. There you should find only a image: the one you compiled yourself.

Good luck!

---

### Post by Klaidas on 2006-01-25
Thanks for your answer!

---

### Post by jackwhite on 2006-01-26
Hey Sokraates,

Thanks for the tip, that worked out perfectly!

---

