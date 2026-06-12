---
title: "ALSA problem of snd-atiixp"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by apparle on 2009-05-11
I was wondering whether this bug has been fixed in latest version or not.
[http://bugzilla.kernel.org/show_bug.cgi?id=7467](http://bugzilla.kernel.org/show_bug.cgi?id=7467)
From same link
> Problem Description:
Loading 'snd-atiixp' kernel module gives:
-----------------------------------------------------------
atiixp: codec read timeout (reg 0)
atiixp: codec read timeout (reg 3c)
atiixp: codec read timeout (reg 1c)
AC'97 2 does not respond - RESET
AC'97 2 access is not valid [0xffffffff], removing mixer.
atiixp: no codec available
ACPI: PCI interrupt for device 0000:00:14.5 disabled
-----------------------------------------------------------
'codec read timeout' lines are repeating many times. Due to 
[https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2081](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=2081) it is ACPI problem. 



I get the same problem for my motherboard Foxconn RC4107MA-RS2
From feisty to jaunty I am getting the same problem.
What is this problem. Could anyone explain?

How to fix it......currently I am using OSS drivers which work but workaround are needed to make the system compatible

---

### Post by apparle on 2009-05-28
bump.

Is there anyway I can check whether this bug has been fixed in latest kernel.....it is very old bug.
I also foud a new link
[http://marcin.juszkiewicz.com.pl/2006/11/13/sound-is-working-on-dfi-rs482/](http://marcin.juszkiewicz.com.pl/2006/11/13/sound-is-working-on-dfi-rs482/)
Although I have a diffrent motherboard the problem is same.
> Now it is time to wait until this will go into mainline.
Has this patch been integrated into the Kernel

Anyways....can anyone provide a link for a HowTo to install this patch

---

### Post by apparle on 2009-07-22
I found out that the patch was for atiixp.c file in alsa driver source and it had been applied, but it was for a diffrent motherboard.

Finally found out how to make ALSA drivers work for Foxconn RC4107MA-RS2
Add this line to the file /etc/modprobe.d/alsa-base.conf
```
options snd-atiixp ac97_codec=0
```

This make the driver take the ac97_codec directly instead of probing it because probing it results in codec timeout error

---

