---
title: "Battery Absent On HP Split 13x2 Laptop"
date: 2015-08-22
forum: Hardware
---

### Post by pearj2 on 2015-08-22
I have an HP Split 13x2 laptop with Ubuntu Mate installed.

dmesg shows "ACPI: Battery Slot [BAT0] (battery absent)".

The battery icon shows "No battery present".

...I'm only able to run on AC power.

---

I have tried:
* Default and adjusted settings in BIOS.
* Live versions of Ubuntu, Lubuntu and Ubuntu Mate.
* Release 15.04 and 14.04 for all flavors above.
* Installed ACPI.
* Installed batmon.
* Installed ibam.
* Added to grub default boot line "acpi_osi=", then "acpi_osi=!Linux" then "acpi_osi=Linux".

I have not tried recompiling the kernel, as several posts state the recompiling didn't work for them if not on a Toshiba.

---

I'd really like to get this working...the laptop is needed for work done in areas where AC power won't always be present.

Has anyone gotten this to work on their HP? If so, how?

Has anyone had a similar issue with their laptop and fixed it even if not an HP?

Is there anything I should change in BIOS that might help?

Any ideas in general?

---

### Post by Yellow Pasque on 2015-08-22
Make sure you have the latest BIOS. [http://www8.hp.com/us/en/support-search.html?tab=1#qryterm=split%2013x2&search_searchtype=s-002](http://www8.hp.com/us/en/support-search.html?tab=1#qryterm=split%2013x2&search_searchtype=s-002)

---

### Post by pearj2 on 2015-08-22
Thank you for that link - unfortunately it doesn't show a bios update is available.

---

### Post by Yellow Pasque on 2015-08-22
I know it's an old bug report, but there may be some tricks to see if you can detect battery here: [https://bugzilla.kernel.org/show_bug.cgi?id=7200](https://bugzilla.kernel.org/show_bug.cgi?id=7200)

---

### Post by pearj2 on 2015-08-22
Thank you again Temujin - I looked over the link extensively, but don't know how to "add a patch".

I'm willing to try, but need instruction (sorry).

Additionally, I wanted to add that the battery doesn't show in Linux Mint, or Puppy Linux... I'm going to try CentOS now (really want to stay with .deb repositories though).

I have to leave for a jam session, but will check back tonight. Please add any instruction for me to try (and thank you for your help).

---

### Post by Yellow Pasque on 2015-08-22
No, I wasn't referring to the patch (that got added to the kernel a long time ago). I meant plugging/unplugging the AC adapter a few times and/or running this command a few times
```
cat /proc/acpi/battery*
```

---

### Post by pearj2 on 2015-08-23
I see, ok. Removing the AC cord immediately shut the machine down.

On running the command:

me@laptop:~$ ls /proc/acpi
button  wakeup
me@laptop:~$ cat /proc/acpi/battery*
cat: /proc/acpi/battery*: No such file or directory
me@laptop:~$ cat /proc/acpi/battery*
cat: /proc/acpi/battery*: No such file or directory
me@laptop:~$ cat /proc/acpi/battery*
cat: /proc/acpi/battery*: No such file or directory

ugh, still no joy

---

### Post by Yellow Pasque on 2015-08-23
> Removing the AC cord immediately shut the machine down.

If you boot to the BIOS/setup screen and unplug the AC, does the same thing happen? If it does, it would lead me to believe it's a hardware issue.

---

### Post by pearj2 on 2015-08-23
Yes, the same thing happens. I don't believe it's a "hardware issue" - the battery worked fine when it had Windows 8 on it...

---

### Post by Yellow Pasque on 2015-08-23
If the machine automatically shuts down when AC is unplugged in the BIOS screen (before any OS loads), then something is probably wrong hardware-wise (bad battery or bad connection). I don't think shutting down automatically when the AC is unplugged is designed behavior, whether you're at the BIOS screen or have an OS loaded. (Don't quote me on that though, because I'm much more familiar with desktops/servers than laptops).

> the battery worked fine when it had Windows 8 on it... 
Unless you still have Windows 8 on there and verify it still functions correctly, then that's meaningless.

---

### Post by pearj2 on 2015-08-23
Would that be the case if the battery had no charge?

---

### Post by astralnysledz on 2015-08-23
> **pearj2 said:**
> Would that be the case if the battery had no charge?

If the battery has no charge, it should still be recognized through ACPI by any Linux distribution, unless it's completely dead and non-functional. I often worked with laptops with different battery issues and even if the ACPI monitor is not able to read the state of the battery, the laptop should not power down when removing the AC adapter. 

Furthermore, I completely agree with the observation that if the laptop shuts down in BIOS, it means a hardware problem. Either somehow the battery got discharged and died completely or there is a hardware malfunction preventing the laptop from accessing the battery.

Does the BIOS actually see the battery or not at all?
Do you have any means of removing the battery and testing on a different similar laptop?

---

### Post by pearj2 on 2015-08-23
I understand BIOS is prior to the OS load... I'm saying if the battery is totally dead (no charge), then wouldn't it still shut off if I removed the power?

The battery can not easily be removed. I only have this brick - no other brick to test on.

---

### Post by astralnysledz on 2015-08-23
> **pearj2 said:**
> I understand BIOS is prior to the OS load... I'm saying if the battery is totally dead (no charge), then wouldn't it still shut off if I removed the power?

The battery can not easily be removed. I only have this brick - no other brick to test on.

You are completely right :). If the battery is discharged (dead or simply empty), the computer will naturally shut down once you detach the AC cable. Normally laptops shut down when the battery charge/load is around 5%. This much is reserved for safety measures (proper shutting down of the system, emptying cache, stopping drives, etc.). However, it is possible for the battery to charge, but not load, because it is no longer capable of storing charges. It will be recognized by the OS, it will be charged, but more complex acpi monitors will show maximum capacity as 0%.

I just read a bit about your laptop and it is more of a 2-in-1 or a tablet with a detachable keyboard. I am afraid that besides helpful advice I cannot offer much more :(.

---

### Post by Yellow Pasque on 2015-08-23
I see you filed a bug report (you should post the link when you do that): [https://bugs.launchpad.net/ubuntu/+bug/1487734](https://bugs.launchpad.net/ubuntu/+bug/1487734)

FWIW, it seems some other folks with a Split x2 product also have batteries that lived a short life: [http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/HP-Split-X2-Battery-2-plugged-in-but-not-charging/td-p/4820156](http://h30434.www3.hp.com/t5/Other-Notebook-PC-Questions/HP-Split-X2-Battery-2-plugged-in-but-not-charging/td-p/4820156)

---

### Post by pearj2 on 2015-08-26
Yep, filled out a bug report - but it's not getting any activity...  What do I have to add to the report to have some one look at it?

Yes - it's a "2 in 1" type thing. (Monitor becomes a tablet).

I was going to try putting w7 on it to see if the battery was recognized. From there I may request a copy of w8 that came with it, then try to resinstall that to see if the battery works. If no, then there's a problem with the battery, and I'll have to contact HP.

---

### Post by Yellow Pasque on 2015-08-26
> **pearj2 said:**
> What do I have to add to the report to have some one look at it?

There's no magic incantation. The ratio of people helping on bug reports to the number of bug reports filed is very low. As the bot points out, attach logs using the command:
```
apport-collect 1487734
```
(and then set the status back to 'New')

It would also help if you confirmed that the battery works on Windows (i.e. isn't defective hardware) and/or tried the latest upstream kernel to make sure it isn't a kernel bug that's been fixed already:

[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc8-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.2-rc8-unstable/)

---

