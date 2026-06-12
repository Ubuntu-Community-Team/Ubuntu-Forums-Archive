---
title: "Yet another HDA intel victim"
date: 2007-01-18
forum: Hardware &amp; Laptops
---

### Post by Chaffar on 2007-01-18
Ok I hit a wall and I have no clue what to do next :-k 

Like most people that bought a laptop that comes with HDA-intel (Toshiba P105-S9722 in my case), I have no sound and no solution.

I'm running ALSA 1.0.14rc2. When I boot with *acpi=off no acpi*, I DO get sound, but nothing else works, the network card etc... , and if I install the Nvidia drivers, KDM crashes. 
The notable thing is that without *acpi=off no acpi*, I get this error at boot:
> [17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179570.244000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 000
0:01:00.0
[17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.0
[17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.1
[17179570.244000] PCI: Cannot allocate resource region 7 of bridge 0000:00:1c.2
[17179570.244000] PCI: Cannot allocate resource region 8 of bridge 0000:00:1c.2
[17179570.244000] PCI: Cannot allocate resource region 9 of bridge 0000:00:1c.2
[17179570.244000] PCI: Failed to allocate mem resource #6:20000@d0000000 for 000
0:01:00.0
When I boot with acpi=off, this doesn't happen, but I have no network card, and potentially no 3D card :( 

Is there a way to modify which IRQ goes to which component, or maybe disabling stuff I don't need to free up IRQ ports ?

---

### Post by XhwMikey on 2007-01-23
Chaffar,

   I have the same lappy, and I've run into the same issue.  I am running with acpi=off and I have 3d and network - including wireless.  I am still researching the ultimate answer - I'd like to have acpi, but it appears to be slow going.

XhwMikey

---

### Post by arg_ on 2007-01-24
I am on the same boat with a Toshiba P100 and ALSA 1.0.14.  With ACPI=off I do have sound but I prefer the ACPI functions over sound, so my laptop atm is mute :(
Have tried various possible workarounds I have seen but still no joy.
I am too looking for a definite solution

---

### Post by Healey on 2007-01-25
Hi

Just thought I would join the list 

I have a similar "cannot allocate resource" problem using a Compaq presario c310 running Dapper. I also had the same problem when using Edgy. Dapper appears to run slightly better.

My laptop does not freeze, I do have sound but the volume is very low.

I have done a lot of searching on this and it appears to be related to the Bios. I am not experienced enough to know if this is correct or not !!

I have checked my Bios version and it is the newest version Compaq has to offer

Anybody know of a fix for this ??

Regards

Healey

---

### Post by klaas on 2007-01-31
This is how i fixed this problem for my Toshiba Satellite P100-343 (bios 3.30): [http://www.ubuntuforums.org/showthread.php?t=349491](http://www.ubuntuforums.org/showthread.php?t=349491).

Greetz,
Klaas

---

### Post by eggdeng on 2007-01-31
Have you tried adding

```
options snd-hda-intel model=ref
```

at the end of  /etc/modprobe.d/alsa-base & rebooting?

---

### Post by Healey on 2007-02-02
Hi Thanks for your reply

I tried adding the text as you sugested but it did not do anything for me, good or bad !


Any other ideas

Best Regards

Healey

---

### Post by longfeather on 2007-11-01
Hope this helps:

I installed a fresh install of Ubuntu 7.10 on a Compaq Presario C500 with an Intel 82801G HDA contoller (rev 01).  The install went fine with exception to the sound not working.  I had "PCI: Cannot allocate resource region" messages on boot and in my syslog.  I managed to get the sound working by passing "pci=routeirq" to the kernel via the GRUB menu.lst file.  The fix can be found here:

[http://www.islandlinux.org/howto/ubuntu-7-10-sound-issue-compaq-presario-c500-laptop-resolved]("http://www.islandlinux.org/howto/ubuntu-7-10-sound-issue-compaq-presario-c500-laptop-resolved")

---

### Post by gene6482 on 2007-11-01
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				For the Toshiba p100-p105 users, there is an open bug report.  There are also a couple of workarounds to get it working in the mean time.

---

