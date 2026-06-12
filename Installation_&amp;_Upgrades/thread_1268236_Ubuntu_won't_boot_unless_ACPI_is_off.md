---
title: "Ubuntu won't boot unless ACPI is off?"
date: 2009-09-16
forum: Installation &amp; Upgrades
---

### Post by Incendia on 2009-09-16
Hello everyone :]
I have a Packard Bell Easynote SL51, and I am really interested in trying Ubuntu.
However, the livecd won't boot unless I turn ACPI off and the other options when pressing F6 off.
I tried different distributions but they too won't load without ACPI off.
So, I decided to try it with it off, and when I go to install it near the end it says the installer crashes and takes me to a Ubuntu LiveCD Desktop.
When I installed OpenSUSE with ACPI off, it didn't diplay my battery life and stuff.
Although OpenSUSE didn't work with my wireless nor my sound card (which Ubuntu does on the LiveCD desktop).
I would really like to switch to Linux; I hope my laptop isn't Windows-only.
Many thanks,
Incendia. ;)

---

### Post by Incendia on 2009-09-17
Anyone?  :(

---

### Post by RJARRRPCGP on 2009-09-17
> **Incendia said:**
>  when I go to install it near the end it says the installer crashes and takes me to a Ubuntu LiveCD Desktop.


A possible cause is a bad HDD or a bad cable connection to your HDD.

---

### Post by Incendia on 2009-09-18
> **RJARRRPCGP said:**
> A possible cause is a bad HDD or a bad cable connection to your HDD.
It might have something to do with how I am partitioning it then :/
Do you know about the ACPI? That's most important really, once that is sorted I can have linux on my laptop :]

---

### Post by presence1960 on 2009-09-18
what are the specs of your machine?

if they are not powerful try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

---

### Post by Incendia on 2009-09-18
> **presence1960 said:**
> what are the specs of your machine?

if they are not powerful try the alternate text based installer. get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

They are powerful ;]
Well, powerful enough.

250 HDD
3 GB RAM
250MB Ati Radion Graphics
2.1GHz Dual-Core AMD Turion x2 running at ~4.2Ghz.

---

### Post by presence1960 on 2009-09-18
> **Incendia said:**
> They are powerful ;]
Well, powerful enough.

250 HDD
3 GB RAM
250MB Ati Radion Graphics
2.1GHz Dual-Core AMD Turion x2 running at ~4.2Ghz.

That is plenty!

I would start at the beginning. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it to a CD?
Did you burn the CD at a slow speed (4x-8x is perfect)?
Did you choose check disk for defects when booting the Live Cd?
Did you run a "Live session" by choosing "try ubuntu without any changes" prior to trying to install? If the live session ran well try using the "install" icon on the desktop of the Live session.
I see you have an ATI card, try F4 when you boot the Live CD & choose safe graphics mode.
If all else fails I would try the alternate text based installer. It usually works where the Live CD will not. You can't run a live session & it isn't pretty like the Live CD, but has more support for options the Live CD does not (such as RAID or LVM). Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

[ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") - if you have newer hardware that should not be a problem. Check your BIOS and see if it has a setting for ACPI.

---

### Post by Incendia on 2009-09-18
> **presence1960 said:**
> That is plenty!

I would start at the beginning. Did you [MD5SUM]("https://help.ubuntu.com/community/HowToMD5SUM") the iso prior to burning it to a CD?
Did you burn the CD at a slow speed (4x-8x is perfect)?
Did you choose check disk for defects when booting the Live Cd?
Did you run a "Live session" by choosing "try ubuntu without any changes" prior to trying to install? If the live session ran well try using the "install" icon on the desktop of the Live session.
I see you have an ATI card, try F4 when you boot the Live CD & choose safe graphics mode.
If all else fails I would try the alternate text based installer. It usually works where the Live CD will not. You can't run a live session & it isn't pretty like the Live CD, but has more support for options the Live CD does not (such as RAID or LVM). Get it [here]("http://www.ubuntu.com/getubuntu/downloadmirrors#alternate").

[ACPI]("http://en.wikipedia.org/wiki/Advanced_Configuration_and_Power_Interface") - if you have newer hardware that should not be a problem. Check your BIOS and see if it has a setting for ACPI.

I did do a MD5SUM :]
I did burn it at a slow speed :]
I checked it for defects, I did that before turning ACPI off.
Live won't load without ACPI off, but I did try that way too and it failed.
Just tried the F4 method but it still wants ACPI off.
It isn't just that the livecd won't work, even when I have installed it with WUBI it won't load into linux with ACPI.
Where would I find the ACPI option on my BIOS?

---

### Post by presence1960 on 2009-09-18
I have a Biostar TF7050-M2 Mobo and in BIOS it is under Power Management Setup. I have the ability to turn ACPI off or on.

---

### Post by Incendia on 2009-09-19
> **presence1960 said:**
> I have a Biostar TF7050-M2 Mobo and in BIOS it is under Power Management Setup. I have the ability to turn ACPI off or on.

Mmm I don't have that option. :/
Do you want me to post my hardware details?
Windows works fine with my ACPI.
I'll post my dxdiag. :]

---

### Post by Incendia on 2009-09-19
[attach]129071[/attach]

---

### Post by Incendia on 2009-09-24
Ok. I got it installed by using the alternate CD with acpi=off and nolacpi. Obviously my computer didn't like the Live CD. However, I'm now having problems with my wireless. It works, just, but ocasionally it stops downloading and pauses for about a minute - then continues.
I thought I should try and use ndiswrapper and install the windows drivers for the wireless.
Or have you got any other suggestions?

---

### Post by Incendia on 2009-09-26
bump. ;]

---

### Post by presence1960 on 2009-09-26
I know it can be tough waiting for an answer. Unfortunately i have no experience with wireless. Someone who does will eventually see your post. Hopefully it will be soon, or you can start a new thread with "wireless" or something in the title to attract attention to it. That is actually the best idea and since it is a new and separate problem there is no big deal about starting another thread. Mark this thread solved since the install worked. You can do that by selecting the "mark thread as solved" option under thread tools at the top.

---

