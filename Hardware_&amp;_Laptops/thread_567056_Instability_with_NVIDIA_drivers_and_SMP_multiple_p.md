---
title: "Instability with NVIDIA drivers and SMP multiple processors - NMI errors"
date: 2007-10-04
forum: Hardware &amp; Laptops
---

### Post by paul_uk_nrth on 2007-10-04
Quick solution:

If you have a multicore/multiprocessor system and use the non-open source nvidia drivers and have stability problems (strange NMI error messages and crashes), then check out this page:

[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

In my case, the solution was to add "idle=poll" to the kernel boot options.


The long saga:

I recently updated a dual processor system (see below for details) from Hoary to Xubuntu 7.04 (Ubuntu Feisty) and then immediately installed the non-open-source legacy nvidia driver package for my Riva TNT.   I immediately started  getting error messages a bit like this that I had never encountered under Hoary:

Uhhuh. NMI received for unknown reason 3c on CPU 0.
Do you have a strange power saving mode enabled?
Dazed and confused, but trying to continue
Uhhuh. NMI received for unknown reason 2c on CPU 0.
Do you have a strange power saving mode enabled?
Dazed and confused, but trying to continue

Google came up with a few different sites, most of which were not very helpful.  I fiddled endlessly with the BIOS, disabling anything even remotely related to power saving, and that had no effect.  Looking in /proc/interrupts, there were loads of entries under the NMI line.  I also had problems with stability, and the system would often hang when running X.

NMI is the non-maskable interrupt -- the highest level interrupt possible in the computer system.    It's reserved for the most critical processes, so loads of NMI requests seemed like bad news!  Many sites indicated that this might point to a memory error (not the case here), or some sort of problem with the CPU temperature or the motherboard (also not the case). I also tried disabling the NMI watchdog, but that also had no effect.

I eventually found out that it's a problem with the interaction between the non-open-source nvidia drivers and the particular kernel version, and found the solution here:

[http://www.nvnews.net/vbulletin/showthread.php?t=58498](http://www.nvnews.net/vbulletin/showthread.php?t=58498)

Adding the kernel option "idle=poll" to /boot/grub/menu.lst has solved all of my problems: no NMI errors at all, and no system hangs!  I just hope that this helps if someone else has this problem. 

A newbie's guide of how to fix this problem:

Open a terminal window and type "sudo pico /boot/grub/menu.lst".  Type in your password when requested and then scroll down as far as the section marked:

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=splash quiet

Then add idle=poll to the defoptions line to make it read:

# defoptions=splash quiet idle=poll

Press F3 Enter to save the file, and then F2 to exit.  Then type "sudo update-grub" to update the bootloader and then reboot.  Hopefully your problems will be solved!!

Another fix is just to use the open source nvidia driver (nv), but then you lose GLX of course...

-----
My system is pretty old:

Dual processor PII 450MHz on a Tyan motherboard with onboard sound and ethernet
Nvidia Riva TNT video card
SoundBlaster
512M of memory, a 10 Gig IDE drive, and a 4.5 Gig SCSI drive.

---

### Post by paul_uk_nrth on 2007-10-05
OK, so it's not entirely fixed, but it's much better than before.  Now I only get NMI errors when I'm loading the graphics card heavily (e.g. if I run glxgears and surf the web at the same time).  No system locks so far...

I've tried a number of other things:

1. Disabling other devices on the same IRQ line as the graphics card.
2. Compiling the nvidia driver from source.
3. Compiling the nvidia driver from source, having edited the source to make sure that it recognises the SDRAM in my TNT graphics card.
4. Turning off AGP.

None of these have helped.  If I use the nv drivers, however, I never see an NMI error, regardless of how hard I'm working the graphics card (graphics are _much_ slower, however, and there's no GLX of course).

Paul.

---

