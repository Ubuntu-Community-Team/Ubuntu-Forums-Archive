---
title: "Kernel Panic on HP Pavillion (during BOOT)"
date: 2011-06-09
forum: Hardware
---

### Post by DiogoDTX on 2011-06-09
Hi guys!

I haven't found a solution for this problem here in the forum, so I'm posting my issue.

This is my laptop:

**HP PAVILLION**
**Product Number** WA789UA#ABC[B]
Microprocessor[/B] Intel Core i5-430M processor 2.26GHz with Turbo Boost Technology up to 2.53 GHz    [B]
Memory[/B] 4GB DDR3 System Memory (2 DIMM)**Video Graphics** Nvidia GeForce GT 230M **Hard Drive **640GB (5400RPM)
**Network Card **Integrated 10/100/1000 Gigabit Ethernet LAN 
**Wireless Connectivity **802.11b/g/n WLAN 

I have installed (a couple of weeks ago) Ubuntu 11.04 64bit as the default (only) OS in my machine.. and I just loved it!

The problem is:

Today (and also a couple of days ago) I got a crash when booting up the system.

The CAPS LOCK key was blinking (I saw that it means kernel panic) and the system wouldn't boot.

Just now I had to restart the computer 3 times holding the power key to try and boot it.

I wonder if it has anything to do with drivers problems or the installed version being the 64bit.

As this problem has happened twice now, I'm afraid that eventually the system won't boot up at all.

Should I install the 32bit version or what?

Thanks in advance!!!

---

### Post by DiogoDTX on 2011-06-09
Anyone?

---

### Post by belltown on 2011-06-09
Go to System>Administration>Log File Viewer. Select kern.log for the date when you had the failure to boot and see if there are any messages in there that give a clue as to what went wrong.

---

### Post by minsung0315 on 2011-06-22
I also have the same problem on a HP pavillion, a dv6 from 2010.

I believe this is the problem, except I don't know how to solve it:

Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.132664] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  270.41.06  Mon Apr 18 14:53:56 PDT 2011
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.258813] ppdev: user-space parallel port driver
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553438] ioremap error for 0xbf7fc000-0xbf7fd000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553446] ioremap error for 0xbf7fd000-0xbf7fe000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553452] ioremap error for 0xbf7fb000-0xbf7fc000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553457] ioremap error for 0xbf7fa000-0xbf7fb000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553465] ioremap error for 0xbf7f9000-0xbf7fa000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553469] ioremap error for 0xbf7ea000-0xbf7eb000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553473] ioremap error for 0xbf7e7000-0xbf7e8000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553477] ioremap error for 0xbf7e3000-0xbf7e4000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553480] ioremap error for 0xbf7e2000-0xbf7e3000, requested 0x10, got 0x0
Jun 22 06:34:56 CHOI-Ubuntu kernel: [   20.553484] ioremap error for 0xbf7e1000-0xbf7e2000, requested 0x10, got 0x0

Any ideas folks?

---

### Post by PuerkitoBio on 2011-10-25
Same here, on ubuntu 11.10 64bits (had the same problem with 11.04), Ubuntu is my one and only OS, and at boot, I get frequent kernel panics. Booting in recovery mode always works (so far). I checked the kern.log, could not find any useful information (to my untrained eyes, at least). There's the nvidia problem, which is known and logged as a Linux bug, I believe. I added the "NOAPIC" info in the grub config, but it didn't seem to help. I may try the acpi=off, now...

My next laptop will be 100% hardware compatible with Linux, that's for sure, but I switched from Windows to Ubuntu after I got my Pavilion, so I'm stuck with it for a while. Anyone who can help, it will be greatly appreciated. Other than this annoyance, I'm absolutely sold to Ubuntu!

---

### Post by PuerkitoBio on 2011-10-26
After some investigation, it seems I get a kernel panic every time I try to boot on the battery (not plugged in).

---

