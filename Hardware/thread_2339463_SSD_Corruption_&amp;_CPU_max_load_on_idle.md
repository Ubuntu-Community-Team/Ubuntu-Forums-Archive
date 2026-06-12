---
title: "SSD Corruption &amp; CPU max load on idle"
date: 2016-10-09
forum: Hardware
---

### Post by ryadav on 2016-10-09
I bought a new SSD - Crucial MX300 and I am seeing two issues.

1) My CPU load goes to 100% on all cores during idle, my system begin to get sluggish and keeps freezing on any i/o ops on the SSD like coping files, formatting.

2) My SSD get corrupted coming out of RAM suspend.

Seems to me SSD doesn't work well on Linux, I am using kernel 4.4.0-38-generic

I tried switching my BIOS setting from IDE to AHCI, however about 39% into the install I get an error saying something is read only? tried 3 times.

Using IDE setting from the BIOS, fresh install goes well, but I have 2 issues mentioned earlier.

Is there anything I can try to fix these issue, I have already logged a bug with kernel here: 

[https://bugzilla.kernel.org/show_bug.cgi?id=176921](https://bugzilla.kernel.org/show_bug.cgi?id=176921)

---

### Post by frostschutz on 2016-10-09
These SSD work fine for everyone else, so that kernel bug report probably isn't going anywhere.

> I tried switching my BIOS setting from IDE to AHCI, however about 39%  into the install I get an error saying something is read only? tried 3  times.

Any more details on that? Errors in dmesg? Run the installer in debug mode, show logs?

---

### Post by ryadav on 2016-10-10
Well I don't know about "everyone" else but for me I've tired 2 different SSD manufactures with the same result in the bug.

How how I install in debug mode if I am using the install CD, where do I find the logs, on the corrupt SSD I am installing to?

What logs?

---

### Post by oldfred on 2016-10-10
SSD require AHCI for trim to work.

So what motherboard and rest of system?
It may be a setting on motherboard to make it work.

---

### Post by ryadav on 2016-10-10
Solved my problem, it seems some of the hard drive where no compatible with AHCI mode. Since my BIOS (groups) drive cables, I had to move my SSD to another cable. Once I did this all my problem disappeared, the CPU load is gone, no corruption of reboot or suspending to RAM and waking up.

So AHCI mode is required and have to make sure not to mix IDE and AHCI drive in the same group if your BIOS groups cables.

---

