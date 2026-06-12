---
title: "Toshiba Satellite L505 overheats"
date: 2010-04-06
forum: Hardware
---

### Post by saamirahman on 2010-04-06
Hi guys,

I installed Ubuntu Karmic Koala on my Toshiba Satellite L505-S6946 several days ago, and it seems to overheat. The bottom gets quite heated, and so does the palmrest. I dual boot with Windows 7, and when I'm running Windows 7, the laptop is as cool as it has always been. So, I don't think the issue is hardware related.

Any help will be much appreciated.

Thanks.

---

### Post by Michele Albano on 2010-04-09
Try to add either "acpi_osi=Linux" or "lapic" to the boot command line:

 - open /boot/grub/menu.lst with a text editor (sudo it, because it is owned by root)
 - add one of the option (first try with "acpi_osi=Linux") to the end of the row starting with "kernel"
 - try the other option if this does not work
 - give us feedback about your results :-P

---

### Post by saamirahman on 2010-04-10
Hi,

I tried the command above, and it opens up an empty file. I browsed to boot/grub/ and couldn't find menu.lst. I looked into the hidden files, too. Am I missing something very obvious here? :S

Thanks

---

### Post by Michele Albano on 2010-04-12
You are using grub 2, and I have no experience with it, sorry.


Try looking at:

[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

or simply get to the interactive boot menu at boot time and
try adding the acpi_osi=Linux or lapic to the boot parameters.

---

### Post by bmillham on 2010-08-01
I'm having the same problem with my Toshiba L505. Overheats when running Ubuntu, works fine when running Windows 7.

I tried adding the "acpi_osi=Linux" and "lapic" options, but no luck, still overheating.

It's most noticeable under heavy CPU usage, like when compiling. It also happens  when running XBMC. I don't even have to be watching a movie, just having XBMC running idle will cause it to overheat after about 5 minutes.

---

### Post by saamirahman on 2010-08-01
I stopped using ubuntu natively after a while, but for some reason, the heating reduces, but doesn't go away completely.

---

### Post by bmillham on 2010-08-02
I seem to have solved my overheating problem.  I turned off visual effects.

I can now run xbmc with no problems (CPU temp about 85C).  I let it run for 8 hours without a crash.

I ran a compile that took 15 minutes,  using -j2 (runs on both cores that way) and CPU temp hit 91C.

I'm encoding a video using HandBrake right now, been running for about 20 minutes and CPU temp is stable at 64C.

Strange how turning off visual effects made such a difference.

---

### Post by Madan80 on 2010-08-07
tried the same thing on the M500(turning off visual effects), it seems to be working now and the computer does not appear to be running hot anymore. Dunno if this is a quickfix. 

migrated to Ubuntu. (hurrah! ):popcorn:

---

