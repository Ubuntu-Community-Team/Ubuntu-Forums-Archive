---
title: "Can't run on AMD Turion 2 = Overheating"
date: 2009-06-27
forum: Installation &amp; Upgrades
---

### Post by mickamd on 2009-06-27
Hi guys,

Got a laptop, pretty recent Compaq Presario CQ60.
It overheats big time when I have 9.04 running (Either 32 or 64 bits), live CD or installed.
It is very sluggish and shuts down itself after a few minutes.
CPU 1/2 is stuck at 100%.

I tried the noapic nolapic in the menu.lst, no luck

I was so pissed because I was hoping to have Ubuntu installed today, so I decided to install PCBSD to give it a try.
PCBSD installer crashed after 5mn, invoking CPU high temperature.

So what, AMD Turion 2, not Linux/Unix friendly ?

Seems this overheating issue is referrenced all over since 2006, but I can't find a solution.

Anyone?

Thanks in advance

---

### Post by mickamd on 2009-06-28
I tried Windows 7 this morning.
Same issue.
Looks like a CPU driver problem.
Went on AMD support, can't find anything about that, although everybody is complaining about the same problem with many different brands, toshiba, HP etc. and brand new installation of different Linux flavours.

There must have a solution somewhere.

Anyone?

---

### Post by mickamd on 2009-06-28
Ok after further investigation I decided to apply latest BIOS update. Bios update from May 2009 (The latest as of time of writting). Went from 0.24 to 0.33 (F.3A)

This fixed my issue.
Windows 7 is no longer overheating, well the CPU...

My laptop model is Compaq Presario CQ60-114EM

Off I go to install Ubuntu now :-)

---

### Post by Done_Fishin on 2009-06-28
if you have a phoenix BIOS or one that doesn't support ACPI then try acpi=off after tapping F6 twice, the second one brings up a menu where with either enter or spacebar you can select the highlighted line (use arrow-keys for up down, esc to exit)

in Windows you hit F7 when you see the F6 statement at the bottom of the screen, disables ACPI& installs APM.

---

### Post by mickamd on 2009-06-28
> **Done_Fishin said:**
> if you have a phoenix BIOS or one that doesn't support ACPI then try acpi=off after tapping F6 twice, the second one brings up a menu where with either enter or spacebar you can select the highlighted line (use arrow-keys for up down, esc to exit)

in Windows you hit F7 when you see the F6 statement at the bottom of the screen, disables ACPI& installs APM.

Hi,

I got it actually.
I rebooted on Ubuntu but same, CPU was 100%.
Laptop was still overheating :-( And some fan was still spinning like mad 100% of the time.

So I restarted on Windows and I remembered I had a a "happy fan" issue with my desktop when I first installed my NVIDIA card.

So I simply installed the proper NVIDIA driver on the laptop (Like I did on the desktop before) and this time it fixed the issue for good. No more overheating.

So the laptop was overheating because of the NVIDIA GPU being not managed by an OS rather than the motherboard CPU itself.

Unbuntu was proposing me (In the driver interface) to upgrade my NVIDIA driver when I tried the liveCD 2 days ago.

I tried again Ubuntu but this time it did not proposed me to install the NVIDIA driver. It was loaded with a generic VGA driver.

I need to figure out the way to install the proper driver right after the installation...

Cheers guys.

HTH

---

### Post by rowanparker on 2009-08-04
Hello, I was wondering if you ever solved this/these problems? I was considering buying this laptop and installing Ubuntu on it (wouldn't keep Vista even if I was paid to do so). Do you reccommend I don't buy it?
Thanks, Rowan.

---

