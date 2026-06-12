---
title: "Hibernate problems, both with uswsusp and standard"
date: 2007-05-31
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2007-05-31
I'm having trouble hibernating my laptop (a Dell Latitude D800). It used to work on 6.10, but now that I have 7.04 it doesn't work properly anymore.

If I run the standard hibernation mechanism, the screen blacks out for a little while and than comes back. The terminal says:

```

$ sudo /etc/acpi/hibernate.sh
...(snip)...
FATAL: Module cpufreq_performance not found.
Function not supported
...(snip)...
FATAL: Module acpi_sbs not found.

```

I installed uswsusp, and using s2disk from that package has worked better, but sometimes (I would say more than 50% of the time) the computer hangs on a screen saying "Snapshotting system...", and then I have to reboot.

Is this happening to somebody else? I filed a bug report about the first problem.

---

### Post by scotthanson on 2007-06-01
I'm having a similar problem with s2disk, except that when it fails on the "Snapshotting system" screen, it drops me back to the desktop. I've had better luck with uswsusp than the standard swsusp, but like you, it seems to fail about half the time. The annoying thing is, I can't seem to isolate the cause. For a while I thought it was due to running XGL and/or Beryl. It does seem more likely to fail under XGL; however, it will sometimes hibernate successfully, even with Beryl running at full blast. Here is my uswsusp.conf--maybe we can compare notes.

```
# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both
resume device = /dev/hda2
compress = y
early writeout = y
image size = 1500000000 # maximum image of 1.5 GB, my swap is 2 GB
shutdown method = shutdown # platform wouldn't turn off my laptop

```

I'm running Feisty on an ASUS M6Ne laptop, latest BIOS version. It has a 1.8 GHz Centrino with 1024 MB RAM and an ATI Mobility Radeon 9700. I am using fglrx, and have all the latest Ubuntu updates installed.

---

### Post by scotthanson on 2007-06-01
Also, for completeness, this is the output when I run /etc/acpi/hibernate.sh

```
<snip>
Shutting down ALSA...done.
Usage: suspend [-f config][resume_device]
Laptop mode disabled, not active.
/etc/acpi/resume.d/17-video-restore.sh: line 5: /var/lib/acpi-support/vbestate: No such file or directory
Function not supported
ifup: interface eth0 already configured
Ignoring unknown interface eth1=eth1.
Setting up ALSA...done.
grep: /proc/acpi/fan/*/state: No such file or directory
FATAL: Module acpi_sbs not found.
FATAL: Module acpi_sbs not found.

```

I also get the "HAL failed to hibernate" message from the Gnome power manager.

---

### Post by scotthanson on 2007-06-02
jazzgossen, 

I don't know if you're still monitoring this thread, but I seem to be having more success with s2disk after adjusting the image size in /etc/uswsusp.conf

Right now I have it set to 500000000 (500 MB) and I have 1 GB of RAM and a 2 GB swap partition. I haven't had it fail in about 10 hibernation attempts. You may want to mess with that setting to see if it helps at all.

---

### Post by scotthanson on 2007-06-02
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Grrr. I just had to eat my words because s2disk failed again. I still think it has something to do with memory consumption or something to do with the image size. I was looking through my dmesg and saw that swsusp had reported not having enough free memory to write all the necessary pages.

See this thread for a bug report with a possible resolution. I haven't tried it yet:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377")

---

### Post by jazzgossen on 2007-06-05
Thanks a lot for the input. My uswsusp,conf currently looks like this:

```

# /etc/uswsusp.conf(8) -- Configuration file for s2disk/s2both 
resume device = /dev/hda5
compress = y
image size = 242932285 #/dev/hda5 is 1 GB and I have 512 MB RAM
RSA key file = /etc/uswsusp.key
shutdown method = platform
#splash = y
compute checksum = y
suspend loglevel = 10
max loglevel = 10

```

I tried to use splashy (thats where the "splash=y" comes from), but when that package is installed, the computer fails to boot. Neither the laptop nor my stationary computer work with splashy. I recently did a "dpkg-reconfigure uswsusp" and changed a few options there. I guess that's why I don't have the early writout option, and that's also why I have a bit higher loglevels than the default.  

"cat /sys/power/image_size" says 524288000. I tried lowering it to my swap partition size in kB, as suggested in that other thread, but I got a permission denied error when doing "sudo echo 1000000 > /sys/power/image_size".

Last time I tried to hibernate (with increased loglevels), the machine hung on a message saying "suspending all terminals", or something similar, after the "snapshotting system" message.

---

### Post by scotthanson on 2007-06-05
Currently, I have image size set to 1073741824 (1 GB) which is equal to my RAM. Whenever I change the value in /etc/uswsusp.conf and use s2disk, it automatically updates /sys/power/image_size to the same value, so I haven't had to use the echo command you mentioned.

I've only tried s2disk a few times with this setting, but it hasn't failed yet (famous last words). At lower values it was either taking a long time to resume, or would give the dmesg errors about not having enough free memory. I had to disable splash = y as well. It seemed to hibernate successfully, but would lock up on resume. 

From what I've read, setting the image size equal to RAM seems to be the best idea. Have you tried that? (512 MB would be 536870912). You might also try enabling early writeout to see if that helps. Also, do you need your image file to be encrypted? I would try commenting out the RSA key and compute checksum lines to see if that might be causing the problem.

---

### Post by jazzgossen on 2007-06-06
I found that the reason that "sudo echo xxx > /sys/power/image_size" doesn't work is that the scope of sudo doesn't cover the ">" redirection. But after becoming root with "sudo su", I could echo to the file.

From the discussion of [bug 88377]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/88377"), it seems that a possible explanation is that the unit of the image_size has changed from bytes to kilobytes in Feisty. If that is true, 1000000 should be 1GB. I just tried to set /sys/power/image_size to 1000000 (which I'm guessing is 1GB, which is the size of my swap partition), and then I could hibernate. I also set the image size in uswsusp.conf  to the same value. Let's hope it works like this.

---

### Post by scotthanson on 2007-06-06
jazzgossen,

Just to clarify, did you get it working with s2disk/uswsusp or the standard swsusp?

For me, s2disk still isn't working every time, and it's really bugging me. I feel like I'm *this close* to getting it working, but something is still causing an intermittent problem. When I look at dmesg, failure is always due to the "Not enough free memory" error when copying X number of "pages." I still don't quite understand what that means.

Does it mean there's not enough available RAM? Or not enough space on the swap partition? When I decrease the image size to a value in kilobytes rather than bytes, it seems to take longer to hibernate, and quite a bit longer to resume. And while it resumes, the display is filled with garbled color that usually only appears for a second or two when the image size is set higher.

Maybe I need to find a uswsusp forum or mailing list and see if I can get a definite answer on the KB vs. B image size, and what values are recommended.

---

### Post by jazzgossen on 2007-06-07
Well, it only worked once. Last time I tried to hibernate with s2disk, it failed as before. 

The standard swsusp still fails like it has since I installed Feisty. The screen turns back for a few seconds, and then I get back to the desktop.

The output from s2disk when it fails, with increased loglevels, is:

[timestamp] Disabling non-boot CPUs
[timestamp] Stopping tasks... done
suspend: Snapshotting system
[timestamp] Shrinking memory... done (113204 pages freed)
[timestamp] Freed 452816 kbytes in 52.79 s (8.57 MB/s)
[timestamp] Suspending consoles

and then it just hangs, and I can't switch to another terminal, and all I can do is to reboot. I wrote that down on paper last time it crashed.

I'm not getting any memory-related error messages. So maybe we don't have the same problem, after all.

---

### Post by scotthanson on 2007-06-11
I think I've got my problem fixed. I uninstalled fglrx and XGL, and started using the open source radeon driver instead. s2disk is working great now. The only trouble I have is the occasional failure to actually power off the laptop after writing the image, but I have not experienced the "out of memory" error at all.

---

### Post by jazzgossen on 2007-07-23
Just an update. 

I have an nVidia card, so I need to use either the "nv" or the closed-source "nvidia" driver. Using "nv" works a lot better when hibernating, but I need to use accelerated 3D for my work, so using "nv" isn't really an option.

I haven't done a scientific study on this, but it seems that I can always hibernate once with uswsusp, after a clean boot. When I resume from hibernation, the next time I try to hibernate, uswsusp hangs on "Suspending consoles". 

Darn. Hope this gets fixed somehow in Gutsy.

---

### Post by private_lock on 2007-07-26
Concerning the value in /sys/power/image_size I found this text:

[http://www.mjmwired.net/kernel/Documentation/power/swsusp.txt](http://www.mjmwired.net/kernel/Documentation/power/swsusp.txt)

To sum up, what I guessed / understood (no guarantees :-):
- Current kernels should take the value in bytes (at least 2.6.20 does)
- Default is 524288000 byte (500 MB)
- The feature is new since kernel 2.6.16
- A value of 0 will restore the behaviour of kernel 2.6.15
- The difference should be:
high values take longer to write the disk image
low values let the system later on suffer from heavy paging
- extra user memory for applications beyond this limit is paged out first and this is kind of a contiguous block for the kernel and everything, that will fit inside. So it's not a hard limit, of how much memory can be in use the moment you try to suspend, but a soft limit, to decide, what is paged out individually and what can take part in the final large burst.
- maybe it cannot be larger than half the RAM, because it must fit in there twice ??? (loaded via burst and then piece by piece dismantled in RAM)

HTH
private_lock

---

