---
title: "Hardware clock - system clock"
date: 2005-06-23
forum: Hardware &amp; Laptops
---

### Post by lance_delacroix on 2005-06-23
When I was installing Kubuntu, I remember a prompt that asked me if my hardware clock was set to GMT.  I said yes, for God knows what reason, even though it was really set to GMT -4.  Now whenever I exit, the OS resets my clock four hours back.  I tried changing the time zone, but that's hard to do when the time zone is correct.  Is there somewhere where I can go in and change the setting I made initially, so that the OS doesn't reset my clock to GMT?

TIA

---

### Post by didit on 2005-06-23
perhaps, you could change your hardware's clock in BIOS setting?

---

### Post by lance_delacroix on 2005-06-23
[QUOTE=didit]perhaps, you could change your hardware's clock in BIOS setting?[/QUOTE]

I could, but I'm afraid Kubuntu would set it back each time I exit.  One of the shutdown messages says something like, "Synching hardware clock to system clock," which I think means that it is looking at that setting that's telling it that the hardware clock should be set to GMT.  I think it gets the time from a time server and then sets the hardware clock.

---

### Post by didit on 2005-06-23
Do you see any files in directory  /usr/share/zoneinfo?

---

### Post by astoltz on 2005-06-23
Linux has two clocks - one hardware, one software.  Ubuntu keeps the hardware clock set to GMT and displays the correct local time in software by knowing the timezone.  Sounds like you've got the hardware clock set wrong somehow.  First be sure your system (soft) clock and timezone are set corrrectly, then try ```
sudo hwclock --systohc
``` That should set the hardware clock from the system clock.

Windows only knows about the hardware clock so if you're dual booting you'll have to set the hardware clock to local time.  See [this thread](http://ubuntuforums.org/showthread.php?t=6285) for more info.

---

### Post by lance_delacroix on 2005-06-23
Thanks for the tips!  I think they will get me on my way.

---

### Post by coolclassic on 2005-06-23
If yu are still having problems why not use an NTP server this will  set your clock every time your on the internet.

---

### Post by Aliby on 2006-01-16
*Simply*

sudo gedit /etc/default/rcS

# Set UTC=yes if your system clock is set to UTC (GMT), and UTC=no if not.
UTC=no

---

