---
title: "Hibernate/Suspend not working"
date: 2008-11-26
forum: Hardware
---

### Post by blackvaio on 2008-11-26
Hi,

I've installed ubuntu hardy on my sony vaio tz21WN but hibernate and suspend doesn't seem to work. When i try to hibernate, i get balck screen with a blinking cursor.

Does anyone has any idea?

Thanks

---

### Post by icanfly0307 on 2008-11-26
Does your hard drive light show any activity or is it blinking? If it is, it's writing the stuff over from your RAM to your swap drive. The more RAM you have, the longer the hibernation process will take.

---

### Post by blackvaio on 2008-11-28
Hi,

Thanks for the reply, yes hard drive light blinks for some time and then nothing. I still see the blank screen after even a long time.

Any ideas?

Thanks

---

### Post by icanfly0307 on 2008-11-28
How much RAM do you have? What's the size of your swap space? If your swap is smaller than your amount of RAM, your computer won't hibernate properly.

---

### Post by blackvaio on 2008-11-28
Hi,

I've got 1gb ram. How to check swap space?

Thanks

---

### Post by icanfly0307 on 2008-11-28
Go to a terminal and post the entire output of *sudo fdisk -l*. This should give you a list of your partitions and your swap size.

---

### Post by blackvaio on 2008-11-28
Thanks for the reply mate

Here is what i get executing the command

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x30fcbbd9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1032     8281088   27  Unknown
/dev/sda2   *        1032        8813    62507480    7  HPFS/NTFS
/dev/sda3            8814       14593    46427850    5  Extended
/dev/sda5            8814       14351    44483953+  83  Linux
/dev/sda6           14352       14593     1943833+  82  Linux swap / Solaris

cheers

---

### Post by icanfly0307 on 2008-11-28
I was doing a bit of Googling and I came up with a few pages that said that this was a bug in Hardy. Just to be sure, could you please post the output of *cat /var/log/pm-suspend.log*.

---

### Post by blackvaio on 2008-11-28
here it is:

Fri Nov 28 01:01:51 GMT 2008: running hibernate hooks.
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/00clear =====
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/05led =====
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/10NetworkManager =====
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/20video =====
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/49bluetooth =====
===== Fri Nov 28 01:01:51 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/50modules =====
===== Fri Nov 28 01:01:54 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/90clock =====
===== Fri Nov 28 01:01:55 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/94cpufreq =====
===== Fri Nov 28 01:01:55 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/95anacron =====
===== Fri Nov 28 01:01:55 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/95led =====
===== Fri Nov 28 01:01:55 GMT 2008: running hook: /usr/lib/pm-utils/sleep.d/99video =====
Fri Nov 28 01:01:55 GMT 2008: done running hibernate hooks.


Is it of any use?

Thanks again

---

### Post by icanfly0307 on 2008-11-28
Hmmm... Everything looks to be in order in that file. It's really surprising that your computer doesn't shut its screen off when it's actually turned off it's graphics card!!! Do you have ACPI turned on? Try standby instead of hibernation and see if it works. That would narrow down onto the problem. :)

---

### Post by blackvaio on 2008-11-29
Hi,

yeah it looks weired i have even try suspend but still the same thing. It looks like hibernate works fine but it just don't turn off the power don't know why:(

cheers

---

### Post by icanfly0307 on 2008-11-29
What type of processor do you have? If it's a 64-bit like an Intel Core 2 Duo or something like that, its a known bug within Hardy:

[https://lists.ubuntu.com/archives/kernel-bugs/2008-June/037622.html](https://lists.ubuntu.com/archives/kernel-bugs/2008-June/037622.html)

---

