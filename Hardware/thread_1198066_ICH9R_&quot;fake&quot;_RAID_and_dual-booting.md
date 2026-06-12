---
title: "ICH9R &quot;fake&quot; RAID and dual-booting"
date: 2009-06-26
forum: Hardware
---

### Post by Objekt on 2009-06-26
I have a motherboard (Asus P5E3 WS Pro) with the Intel ICH9R chipset, which includes a "fake" /aka firmware RAID.  I started using it for Windows several months ago, running a RAID 1 configuration.

About a week ago, I used the Kubuntu 64-bit alternate desktop CD to install Kubuntu 9.04.  It detected the RAID and installed to it.  For the next several reboots, I had a GRUB menu come up and could boot either Win XP or Kubuntu with no problem.

Then last night I tried running Kubuntu, and suddenly it couldn't see the RAID.  I got as far as the Kubuntu loading screen, which sat there for a while, then...

several error messages indicating it couldn't find the RAID, and I was thrown to a busybox prompt.

What gives?  Is it just impossible to run Kubuntu on one of these firmware RAIDs and have it coexist with a Windows install?

---

### Post by ronparent on 2009-06-28
To verify the issue of whether the raid exists, try typing **ls /dev/mapper** into the busybox prompt. Unless the command returns one or more 'lnks' with names ending in digits beginning with one, the raid drive(s) have not been activiated by the boot process. You might also observe during the initial boot if the raid indicate as healthy. Has there been a kernel update since the initial installation?

---

### Post by Objekt on 2009-06-29
The RAID controller says everything is fine during startup, when all the various hardware is doing self-tests (network controller, disk controller, etc.).

No updates to the kernel.  I hardly used this install for about a week, then suddenly it can't start up.

I tried that command at the busybox prompt.  I did see some devices, including the RAID, so I don't know why it can't boot.  Maybe it's just trying to boot the wrong partition or something.

Perhaps I can run a Live CD session of Kubuntu, do that command at the console, & post the results.  I will also try to post my menu.lst.

---

### Post by Objekt on 2009-07-01
When I run the ls /dev/mapper command at the Busybox prompt, I get this list:
```
control
isw_bgbaadaae_SATARAID-1
isw_bgbaadaae_SATARAID-11
isw_bgbaadaae_SATARAID-12
isw_bgbaadaae_SATARAID-13
isw_bgbaadaae_SATARAID-15
isw_bgbaadaae_SATARAID-16
isw_bgbaadaae_SATARAID-17
```

So clearly the RAID is visible.  However, I noticed that the RAID is referred to differently in my menu.lst file.  For example, here is the entry for booting Kubuntu 9.04 normally:
```
title Ubuntu 9.04, kernel 2.6.28-11-generic
root (hd0,2)
kernel /vmlinuz-2.6.28-11-generic root=/dev/mapper/isw_bgahgbcfa_SATARAID-15 ro quiet splash
initrd /initrd.img-2.6.28-11-generic

```

I notice that the menu.lst file refers to a partition named "isw_bgahgbcfa_SATARAID-15" but at the Busybox prompt, the system tells me it only sees things named "isw_bgbaadaae_SATARAID-1" and so on.

(FWIW, the "15" refers to it being the 5th partition.  That's correct; I have a number of NTFS and ext3 partitions on the RAID, with the kernel located on the fifth one.)

It looks like the middle part of the name somehow got changed.  What could have caused that?

My next move is to edit the menu.lst file so that it refers to the RAID the same way Busybox sees it.  Maybe then I will be able to boot.

Update: Nope, that didn't work either.  For some reason, I now get thrown to a grub prompt, not even a grub menu.  Fortunately, using the SuperGRUB disc, I was still able to boot Windows.

---

