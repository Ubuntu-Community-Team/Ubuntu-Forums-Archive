---
title: "[SOLVED] Sound on Laptop Does Not Work at All on Ubuntu 7.10"
date: 2007-11-17
forum: Hardware &amp; Laptops
---

### Post by Sam Plamondon on 2007-11-17
The sound on my Dell Inspiron 1521 laptop does not work at all on my Ubuntu 7.10 Desktop x86 Edition.  I am dual-booting with Windows Vista Home Premium, and the sound works fine on Windows.  My sound card is an "ATI Technologies Inc SBx00 Azalia", and my audio controller is a Sigmatel STAC9205 Codec.  How can I get my sound to work?

---

### Post by Sam Plamondon on 2007-11-17
Also, this message pops up when I click on the Volume Applet located on the top panel:

"No volume control GStreamer plugins and/or devices found."

---

### Post by Sam Plamondon on 2007-11-18
This is what I found when I entered "lspci -v" in the terminal:

00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia
........Subsystem: Dell Unknown device 01fc
........Flags: slow devsel, IRQ 17
........Memory at febfc000 (64-bit, non-prefetchable) [size=16K]
........Capabilities: <access denied>

So, my sound card is an ATI Azalia.

---

### Post by Sam Plamondon on 2007-11-18
Well, I solved the problem.  I just entered "sudo apt-get install linux-backports-modules-generic" in the Terminal, and then rebooted, and my sound was working.
I found out how to do this at this thread:  "http://ubuntuforums.org/showthread.php?t=467324".

---

### Post by LarryEdwards on 2007-11-27
I had the same problem on my Toshiba laptop - no sound.  Alsamixer in the terminal gave me very little.  I ran your script, rebooting and now - still no sound, but Alsamixer in the terminal show several columns which I can adjust.  I guess I am increasing the sound (potential).  Anyway, my situation seems much better but I still have no sound.  Any ideas?

---

### Post by th3t1nm4n on 2008-01-23
Larry, try your headphone jack maybe. My headphone jack works but not the built-in speakers.

---

### Post by Bear on 2008-01-31
> **Sam Plamondon said:**
> Well, I solved the problem.  I just entered "sudo apt-get install linux-backports-modules-generic" in the Terminal, and then rebooted, and my sound was working.
I found out how to do this at this thread:  "http://ubuntuforums.org/showthread.php?t=467324".

Thanks Sam Plamondon that worked for me too. Thanks again.

---

### Post by kronictokr on 2008-04-15
i can confirm this enables the sound in dell inspiron 1521, it worked for me

---

