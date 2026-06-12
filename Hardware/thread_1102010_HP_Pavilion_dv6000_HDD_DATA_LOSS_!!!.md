---
title: "HP Pavilion dv6000 HDD DATA LOSS !!!"
date: 2009-03-21
forum: Hardware
---

### Post by sysex on 2009-03-21
Hello all,

I am facing a huge problem with my laptop. It is a HP Pavilion dv6000 / CPU-2ghz / 1024RAM

Triple Boot:
[B]> Ubuntu 8.04.1, kernel 2.6.24-21-generic
> Ubuntu 8.04.1, memtest86+
> Windows XP Professional
> Windows XP Professional[/B]

Yesterday as I was working on a windows software, it kinda had a weird behaviour, so I quit all the rest of the programs running thinking that it was a matter of ram. The program continued to act weird so I went for restart. It brought, a first time my eyes have seen, window message saying something about a "dummy winidow error" (not window, but winidow) but I don't remember the rest of that message. Windows stuck at "saving your settings" screen, left it there for about 10 minutes and then I shut down the laptop. At that point I googled that message (from another computer of course) and found some ppl considering it as a virus or spy, so I thought, alright, I will go into windows and install some antispy software to clean things. Started up again, grub came up with the choices. Both Windows XP systems cannot load, they stop at the very first screen (which usually takes less than 1 second) saying "starting up", gets stuck there with the cursor blinking for 1 minute and then it says:

[B]Starting up ...

A disk read error occurred
Press Ctrl+Alt+Del to restart[/B]

Then I tried to boot into ubuntu, it did for it's 35% of the loading bar, then it turned into text, everything ended with the [ OK ] msg, but when it started with the hard drive, errors started. Then tried a memory test, and ram looks fine. I resterted again to try a live linux boot using "Ubuntu 9.04 (Jaunty Jackalope)". For my "good luck" so far (sometimes) it does see the partitions at "places" menu, but cannot enter them. Example if I choose the "DATA" partition from the places menu, it takes about 1 to 2 minutes to react and then, It brings a window message saying this:

[B]Cannot mount volume.
Unable to mount the volume 'DATA'.

Details
The disk contains an unclean file system (0, 0). The file system wasn't safely closed on Windows. Fixing. ntfs_attr_pread_i: ntfs_pread failed: Input/output error Failed to read NTFS $Bitmap: Input/output error NTFS is either inconsistent, or there is a hardware fault, or it's a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows twice. The usage of the /f parameter is very important! If the device is a SoftRAID/FakeRAID then first activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation for more details. Failed to sync device /dev/sda4: Input/output error Failed to close volume /dev/sda4: Input/output error[/B]

My way of thnking so far is not to "touch" that data before you backup them. But in that case I would have to try the recovery console of Windows cd. Booted with it, and after I spent 1 hour looking at a blank screen (before the blue screen), when the choices came up and I hit R for recovery console, this message came up:

[B]Windows XP Professional Setup
========================

Setup did not find any hard disk drives isntalled in your computer.

Make sure any hard disk drives are powered on and properly connected to your computer, and that any disk-related hardware configuration is correct. This may involve running a manufacturer-supplied diagnostic or setup program.

Setup cannot continue. To quit Setup, press F3[/B]

In the laptop's BIOS and in the System Configutation, I have this:

**SATA Native Support [Enable/Disable]**

and says:

**Item Specific Help: Enabling SATA Native Support will improve the HDD performance. Disabling SATA Native Support may be necessary when a legacy OS, such as Win2000 and Wn9x, is used.**

I've always had this to Disable otherwise I was never able to install Windows XP.

The serious problem I have is that I got very important data on several partitions of the laptop which I haven't backed up. So all I want to do is to get in touch with that data in any possible way and copy them to LAN or another HD or burn on a DVD. Most important of all is that I need that data as soon as possible, cause I have a time deadline limit to finish a work.

If there was a way to use some sort of data recovery program it would be great. But I cannot do this so far. If it was a different type of hard drive it would be easy for me.

I am sure there is some way to fix part of all this and get the data, then I really don't care what will be the luck of this laptop anymore. All I care is that data.

If some of you can help while I am working on this I will very much appreciate. Same as if I get to find a solution I will post a reply describing it.

Many thanks

---

### Post by DizzyTech on 2009-03-21
First thing to do is calm down.  Everything is going to be okay.  Your laptop's hard drive communicates with its internal components using a method of wiring and control called SATA.  SATA tends to be much faster and secure than its predecessor, ATA.  The downside to this is that it requires new, different drivers; this is mostly true for Windows.  XP does not include SATA drivers for your laptop on its CD.  You will either need to slipstream or install Vista or 7.

A tutorial is available [here](http://www.digitgeek.com/how-to-slipstream-sata-drivers-into-xp-cd/).

---

### Post by sysex on 2009-03-21
hello DizzyTech and thanks very much for your reply,

you most possibly refer to the why the recovery console didn't see any hard drive if I am not wrong. In all this confusion, yes, I forgot that it needs 3rd party drivers for sata to work, but that can be installed from a floppy drive in the beginning of windows blue screen, which I don't have on laptop. On the other side as far as I remember, windows xp sp2 cd (which is the one I have bought) doesn't need this, right ? otherwise I wouldn't have been able to install windows xp on laptop huh ? I never used a utility for this or a floppy drive as far as I can remember !

---

### Post by sysex on 2009-03-21
So all those hours I tried some software for data recovery such as "ontrack easy recovery professional" (never loaded the boot cd at all, have no idea why), SpinRite v6 (it was stuck at the beginning of the process and saw something like 186 hours remaining) could not quit this at all. I feel a little weird about all this, so I decieded to load ubuntu again and let it do all it needs in order to completely boot and take me to the log in screen.

some things I saw was:

ata1.00: status: { DRDY }
ata1: softreset failed (device not ready)
ata1: comreset failed (errno=-16)

then some more like this:

init: Unable to execute "/sbin/getty" for tty1: Input/output error
init: Unable to execute "/sbin/getty" for tty6: Input/output error
init: tty2 main process (4874) terminated with status 255
init: tty2 main process ended, respawning
init: tty3 main process (4872) terminated with status 255
init: tty3 main process ended, respawning
init: tty6 main process (4873) terminated with status 255
init: tty6 main process ended, respawning
init: tty1 main process (4875) terminated with status 255
init: tty1 main process ended, respawning
init: tty2 respaqning too fast, stopped
init: tty3 respaqning too fast, stopped
init: tty6 respaqning too fast, stopped
init: Unable to execute "/sbin/getty" for tty1: Input/output error
init: tty1 main process (4876) terminated with status 255
init: tty1 main process ended, respawning
init: tty1 respawning too fast, stopped
[  236.411861] Buffer I/0 error on device sda6, logical block 655400
[  236.411950] Buffer I/0 error on device sda6, logical block 655413
[  236.412033] Buffer I/0 error on device sda6, logical block 655473
[  236.412115] Buffer I/0 error on device sda6, logical block 1
[  236.412181] Buffer I/0 error on device sda6, logical block 1015810
[  236.412248] Buffer I/0 error on device sda6, logical block 1179649

now its stuck there for more than 30 minutes... I even typed it all here.

I will try SpinRite again. :/

---

