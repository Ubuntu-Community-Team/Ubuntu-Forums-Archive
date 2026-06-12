---
title: "Dapper to Edgy upgrade broke hibernation and swap"
date: 2007-01-29
forum: Hardware &amp; Laptops
---

### Post by User2323 on 2007-01-29
I have a Dell laptop. I had Dapper installed and hibernation was working fine. After I upgraded to Edgy and tried hibernating, it looked like it worked fine when the computer turned off, but when I turned it back on it went through a regular startup. Now if I try hibernating again, it says swap couldn't be found or something like that and doesn't even shut down. When I saw this message, I checked my swap space in System Monitor, and it's been disabled.

Is there a way to fix swap and hibernation?

---

### Post by Dodongo Dislikes Smoke on 2007-02-04
I had the same issue with hibernate killing my swap partition on my desktop.  I was able to get my swap partition recognized again by doing the two commands that hal10000's suggested to volkyl [in this thread]("http://www.ubuntuforums.org/showthread.php?t=343570") with the appropriate changes (my swap partition was hda5 rather than volkyl's hdb2, use fdisk -l to check yours).

Unfortunately I have no idea how to keep hibernate from doing it again.

---

### Post by User2323 on 2007-02-05
Thanks, I think that worked. I don't know what to do about hibernation, I guess I'll have to wait for Feisty and hope that fixes it.

---

### Post by User2323 on 2007-02-06
Oops, I thought it worked because I saw Activating swap while booting, but System Monitor says there's no swap. :(

---

### Post by leafw on 2007-02-06
I have the same problem in a new Thinkpad T60
My swap was off after resuming from sleep, when my modem was off in the BIOS. Otherwise fine.

I have found that the modem **must** be enabled in the BIOS for the sleep to work while plugged to the AC (if not plugged to AC, the laptop fails most of the time to go to sleep).

Hibernate usually works, but not always, haven't found a pattern yet.

What the problem is I have no idea, but all seem related to the modem and the sound driver (there is no sound if the modem is disabled), at least on a thinkpad. And to the frequency scaling (powernowd) perhaps for on-battery inability to reliably enter sleep mode.

---

### Post by red_five on 2007-05-03
I'm running into this problem as well with my Dell Latitude c610. Maybe once I upgrade to 1GB RAM it'll help, but every time I hibernate, swap won't mount upon resume, and I have to do a mkswap/swapon. Also, it won't actually resume, just take me to a normal login. Any chance that Feisty resolves this behavior?

---

