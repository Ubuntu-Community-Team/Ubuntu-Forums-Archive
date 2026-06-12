---
title: "Advent Milano acpi=off"
date: 2012-02-17
forum: Hardware
---

### Post by grazie on 2012-02-17
I've acquired an Advent Milano 10.2 netbook which I can only get to boot if I add the kernel parameter "acpi=off". It came with a dead wireless card which I've removed, but it's not helped. I've searched the net but can't find anything that helps. [This page ]("http://www.lesswatts.org/projects/acpi/debug.php") was useful, but I've not got any further than establishing that only the "acpi=off" parameter will work.

Also, I can install W7, but not long after installation you get a BSOD and then it'll only boot in Safe Mode + networking.

Given that the machine won't work with either Linux or Windows I'm pretty sure there's some kind of hardware problem but I've not been able to establish what. Am I risking damaging the machine if I continue to use it with "acpi=off"?

---

### Post by grazie on 2012-02-22
**Nobody has any suggestions?** For what it's worth, this is how I'm working around the problem for the time being. It may be useful to others with a similar fault.

Powering up the netbook with the battery disconnected means that Linux will boot without the kernel parameter "acpi=off" - it nearly always works fine. Also Windows will boot without a BSOD. The same applies with the battery attached if it's fully charged, i.e. the battery charge level indicator LED is green.

Note, reconnecting the battery after booting will almost certainly result in crashing the machine. If you need to charge the battery, then it must be done with the machine turned off or with the machine booted with "acpi=off" or in Safe Mode for Windows.

This thread applies to [COLOR="SeaGreen"][all variants][/COLOR]. Also, the BIOS has no way to change ACPI settings.

Could a duff battery be causing the problem?

---

### Post by tpost001 on 2012-06-05
OMG!  This problem has bugged me for a long time.  I have an old Dell Inspiron 600m with Windows XP on it.  Windows works fine, but I never could get it to work in any flavor of Ubuntu or Linux Mint without the acpi=off boot parameter.  All the lights would flash and the session would freeze before I could ever get to the login screen.  I, too, added all the RAM I could get (2 MB, originally 512 KB).  The only way I could get it to work is with acpi=off.  I tried now to run it without the battery and no special boot parameters and I got to the login screen and made it to the desktop.  

So I have to ask the same question?  Could a faulty battery be causing the problem?  I don't want to run with acpi=off as I noticed the processor just gets very hot and the fan never comes on.  I notice that the battery indicator always tells me that the battery is not present, although it is plugged in.  But on the Windows side, the battery works apparently fine and I have a few hours before its used up.  Is the battery sending some kind of signal that Linux does not like?

Well my joy was short lived.  Before, without acpi=off, the computer would freeze (and all the lights would start flashing) before I even got to the login screen.  Now without the battery plugged in, I get passed that and can even run a program (like Firefox) but suddenly the screen turns blank (no flashing lights).  So something else is still not right.  Anyone have any ideas?

---

### Post by wildmanne39 on 2012-06-05
Hi, it is most likely a video card driver, I have an old laptop that I use to have to start with acpi=off until the first boot then I would install the driver and it would work.

Have you tried the other options from this link?

you should leave acpi=off as a last resort.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

I recommend lubuntu because it is lighter on resources.
Thanks

---

