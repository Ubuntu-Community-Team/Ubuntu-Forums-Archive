---
title: "Sony VAIO Z505SX - Live CD graphics failure"
date: 2007-03-17
forum: Hardware &amp; Laptops
---

### Post by dentonlt on 2007-03-17
Video settings challenge.  

I have been using this laptop with Damn Small Linux for awhile.  I also have Xubuntu on a Dell Inspiron laptop.  They were both relatively painless to set up.

I am trying to run Xubuntu Dapper Drake off the Live CD (no install) to see if it's going to be light enough for a Sony VAIO Z505SX.  Unfortunately, the VAIO (in question) doesn't like any graphics mode I try.  Its specs:

Pentium II-366
128MB RAM
20GB HD
USB 1.1
CD w/ PCMCIA interface
LCD & Video card unknown (but they work automatically w/ other distros)

On DSL, this VAIO likes 1024x768x16 just fine, and it will display in other modes (800x600, 640x480, whatever).  The GParted CD shows up w/ 1024x768x16, and mucks up the display in other modes ... but they work enough to see that they're close.

From the Xubuntu live CD I get through most of the boot with the standard VAIO options:

```
acpi=off pci=off ide1=0x180,0x386
```

But once the monitor displays "GNOME starting", the screen blanks out to either nothing or just a cursor in the top left.  The color of the screen is sometimes different - I think that just depends upon what is sitting around in memory.  The CD drive quiets down like the boot is complete, but I can't tell what I'm doing onscreen.  Ctrl-Alt-Delete brings back the shutdown splash/monitor, and reboot is fine (when I use the splash boot option).

So it seems like it's booting up, but the display mode is wrong?  In short I have tried:

xforcevesa
many display modes
turning off the framebuffer
visual impairment mode (a stretch)
other Ubuntu distros (Fluxbuntu, Dapper Alt Install)

I don't believe it's a GNOME or lack-of-memory problem - I tried the recent Fluxbuntu CD, and it dies with the same black-out problem.  The Xubuntu Alternate Install CD boots to the shell with 'rescue' ... but I'm not interested in installing without knowing the GUI will work.

I have tried the combinations below, and I'm running out of ideas.  I'll keep plugging/reading, but I'm open to suggestions.

Attempted/failed boot options:

```
no options - blue-ish screen
acpi=off pci=off ide1=0x180,0x386 xforcevesa - bluish screen
f4 option 1024x768x16 + boot w/ safe graphics - black screen
f4 option 1024x768x16 - black screen

f4 option 640x480x16 - splash & boot monitor okay ... eventually black screen

f4 option 1024x78x24 - splash & boot monitor okay ... eventually black screen

rescue - text boot (not quiet/splash) ... grey screen

live f4 option 1024x768x16 - splash/boot monitor okay ... eventually black screen; reset monitor okay

vga=773 (1024x768x256) - black screen

vga=771 (800x600x256) - black screen

debian-installer/framebuffer=false - greenish screen ...

xforcevesa debian-installer/framebuffer=false vga=771 - greenish screen ...

xforcevesa debian-installer/framebuffer=false vga=791 noapic nolapic - black screen

acpi=off pci=off noapic nolapic ide1=0x180,0x386 - gets to funny blue-ish screen ...

acpi=off pci=off noapic nolapic debian-installer/framebuffer=false vga=771 xforcevesa ide1=0x180,0x386 - black screen

acpi=off pci=off noapic nolapic framebuffer=false ide1=0x180,0x386 vga=791 - black screen
acpi=off pci=off ide1=0x180,0x386 ide=nodma - blue screen, no reboot monitor splash
lowmem acpi=off pci=off ide1=0x180,0x386 live - bright green screen (?), inverted reboot monitor splash ...
live lowmem xforcexvesa vga=769 acpi=off pci=off ide1=0x180,0x386 - black screen, reboot splash ok
live xforcexvesa vga=790 acpi=off pci=off ide1=0x180,0x386 - boot splash ok, then black screen ...  
live lowmem vga=791 acpi=off pci=off ide1=0x180,0x386 [moderate visual impairment] - splash monitor fine, black screen, reboot splash fine
vga=792 acpi=off pci=off ide1=0x180,0x386 - splash monitor fine, black screen, reboot monitor fine
vga=normal acpi=off pci=off ide1=0x180,0x386 - white/grey screen
retype the whole boot line as "live ..." - kernel panic
```

addition:
I've already read through as many Linux/Z505sx resources as I could find.  (Hardware compatibility list, Z505SX/Suse, Z505SX/Redhat, etc.).  Not much help there, but I'll review if I don't hear anything ...

addition 26 March 2007:
No news.  Still no luck.  I'm happy to recompile the kernel if I have to ... maybe you can give me an idea of what to attack???

---

### Post by dentonlt on 2007-04-13
I'm still working on this problem, to no avail.  Of the 200 viewers out there, surely somebody has some thoughts?

If I don't hear any ideas within the next few weeks, I guess I'll install rather than trying to run from the CD.  That seems like a royally bad idea, but ... I don't know what else to try.

"Help!" & "thanks!"

---

### Post by dentonlt on 2007-04-15
A couple days ago the power flickered at my apartment while my VAIO was reading/writing the hard drive.  Little data lost, but I had to reformat the drive.  Fixed the drive with Hitachi Drive Tools, etc.

Today I successfully installed Xubuntu from the "Alternate Install" CD.  Process:

Repartition with GParted LiveCD (unnecessary ... skip this if you're doing it)
Boot up with Xubuntu Alternate Install CD.  Select Text Install, add the boot option: "ide2=0x180,0x386".  Do not add pci or acpi boot options - they will get in the way of hardware detection later.

Install takes ~90 minutes.  Step out, come back every 10-15 to answer a question.  On this system Xubuntu is definitely much slower than Damn Small Linux (already knew that would happen), but the interface and repositories are nice.  I may try Fluxbuntu later.

Finally, I believe the above 'graphics' problem was due to the pci=off line.  Necessary to keep the pcmcia cd drive from disappearing, but then it bashed the screen detection (?).  My only other guess is that 128mb ram just isn't enough for the LiveCD on this system.

I suggest the moderators mark this thread 'solved,' though I didn't find a LiveCD resolution.

---

### Post by dentonlt on 2007-04-16
ALSA 1.0.10 (under xubuntu) on the VAIO z505sx ... stinks.  Like many other computers, the nm256 audio driver locks up booting 9/10 times.

Solution formed from other threads in the forums:
1. try ctrl-c just as the nm256 driver starts to load - that will keep it from loading.
2. make a blacklist file under /etc/modules/ and put the nm256 ALSA driver there.
3. load oss drivers instead of alsa

Works for some people.  I can boot now, but still no sound.

Best option seems to be recompiling to a newer version of the ALSA driver (1.0.11+).

---

