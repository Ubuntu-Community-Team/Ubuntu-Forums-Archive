---
title: "Just upgraded to Hardy but new kernel boots into command line only."
date: 2008-07-11
forum: General Help
---

### Post by Universal344 on 2008-07-11
I very recently upgraded from Gutsy to Hardy.  When I rebooted I had two kernels, 2.6.24-19 generic, which booted into a command line only environment and 2.6.22-14 generic (my old kernel) which booted into Hardy fine.  I have a couple of questions.  First I'd like to confirm that I can remove the bad kernel through synaptic by right clicking and saying remove completely.  Second, isn't the kernel that boots (2.6.22-14 generic) quite old?  If so how can I get a newer kernel that will boot into hardy correctly?

Thanks in advance and I apologize for my bad grammer.

---

### Post by damis648 on 2008-07-11
> **Universal344 said:**
> I very recently upgraded from Gutsy to Hardy.  When I rebooted I had two kernels, 2.6.24-19 generic, which booted into a command line only environment and 2.6.22-14 generic (my old kernel) which booted into Hardy fine.  I have a couple of questions.  First I'd like to confirm that I can remove the bad kernel through synaptic by right clicking and saying remove completely.  Second, isn't the kernel that boots (2.6.22-14 generic) quite old?  If so how can I get a newer kernel that will boot into hardy correctly?

Thanks in advance and I apologize for my bad grammer.

Are you thrown into Busybox with a (initramfs) prompt?

---

### Post by Universal344 on 2008-07-11
I do remember see the (initramfs) prompt yes.

---

### Post by damis648 on 2008-07-11
> **Universal344 said:**
> I do remember see the (initramfs) prompt yes.

Ok. In the GRUB menu before selecting the non-functioning kernel, press "e". You will see another menu. Go down to the second line and press "e" again. In the editable line that appears, remove "quiet" and "splash" from the end and press enter. Now press "b". Wait for the busybox (the (initramfs) prompt), and tell us the error messages that appeared right before that.

---

### Post by Universal344 on 2008-07-11
Before I do, what exactly will this do to my system?  I only ask out of curiosity and precaution.

---

### Post by calvinps on 2008-07-11
I have a Dual boot system (Ubuntu on Windows Local Disk) and the (initramfs) command prompt came up a few times. If you power off then power on again it might work round the bad kernel and go straight to the old one. Thats how I managed to get it working anyway but I dont know if it will on yours. Try it and see.

---

### Post by damis648 on 2008-07-11
> **Universal344 said:**
> Before I do, what exactly will this do to my system?  I only ask out of curiosity and precaution.

This will just stop the Ubuntu bootsplash from appearing and show you the terminal output of the boot sequence. It will not be permanent, and will reappear on the next boot. By doing this, we can view all errors.

---

### Post by calvinps on 2008-07-11
Deleted.

---

### Post by Universal344 on 2008-07-11
Ok I will try it then

---

### Post by damis648 on 2008-07-11
> **Universal344 said:**
> Ok I will try it then

Good luck!

---

### Post by Universal344 on 2008-07-11
Sorry for the wait I didn't get all of it the first time so I had to do it again.  This was the error:
```
ALERT! /dev/dish/by-uuid/*(strings of numbers and letters separated by hyphens)* does not exist.  Dropping to shell!
```

Not exactly the most reassuring message now is it:-|.

I have to go for the night but I should be back on tomorrow afternoon or evening, thanks!

---

### Post by damis648 on 2008-07-11
> **Universal344 said:**
> Sorry for the wait I didn't get all of it the first time so I had to do it again.  This was the error:
```
ALERT! /dev/dish/by-uuid/*(strings of numbers and letters separated by hyphens)* does not exist.  Dropping to shell!
```

Not exactly the most reassuring message now is it:-|.

I have to go for the night but I should be back on tomorrow afternoon or evening, thanks!

Ah, ok. This can mean several things. First off, what partition is ubuntu installed on? (hda1, hda2, sda1, sda2, etc.) When you boot up, press "e" on the dysfunctional kernel again. Go to the second line again, press "e", and, as before, remove "quiet" and "splash". Now scroll the cursor over with the arrow keys and change the string
```
root=UUID=(string of numbers)
```
to
```
root=/dev/xxxx
```
replacing xxxx with the partition that ubuntu is installed on. Now press enter and "b" again and see if it boots correctly now.

---

### Post by Universal344 on 2008-07-12
My copy of Ubuntu is running on a partition named sda6.

So just to be clear, I replace "root=UUID=(string of numbers)" with "root=/dev/sda6".

---

### Post by avtolle on 2008-07-12
> **Universal344 said:**
> My copy of Ubuntu is running on a partition named sda6.

So just to be clear, I replace "root=UUID=(string of numbers)" with "root=/dev/sda6".
Yes, replace root=UUID=(string of numbers) with root=/dev/sda6. Then press Enter and b again to see whether it will boot.

---

### Post by Universal344 on 2008-07-12
Ok then, I'll try and post results.

---

### Post by Universal344 on 2008-07-12
Ok, well it didn't work but before (or it might have been after not 100% sure) the ALERT! message came up I got this one:
```
Check root=bootarg cat /proc/cmdline or modules, devices: cat /proc/modules ls /dev
```

Oh, and the Alert message changed to:

```
ALERT /dev/sda6 does not exist.  Dropping to a shell!
```

---

### Post by avtolle on 2008-07-12
Just in case sda6 might be wrong, could you do```
sudo fdisk -l
```(that's a lower-case "ell" not the numeral "1") and give us the output from that command?

---

### Post by Universal344 on 2008-07-12
here's the results:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x602b3822

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15298   122880000    7  HPFS/NTFS
/dev/sda2           15298       30596   122880000    7  HPFS/NTFS
/dev/sda3           30597       60801   242621662+   5  Extended
/dev/sda5           46384       60801   115812553+  bc  Unknown
/dev/sda6           30597       36675    48829504+  83  Linux
/dev/sda7           36676       36918     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order

```

---

### Post by avtolle on 2008-07-12
It appears the boot flag is not set at /dev/sda6. Perhaps this is the (pardon me) the "root" of the problem? 

I believe you should boot from a Live CD, get gparted running, and navigate to that partition and make it bootable. Then shut down from the Live CD session, and boot.

---

### Post by Universal344 on 2008-07-12
Do I have to boot from live cd?  I have gParted on my machine.

---

### Post by avtolle on 2008-07-12
Is /dev/sda6 mounted? Can it be unmounted? If it cannot, I'd say it is in use, and I think that to do anything with a partition, it must be unmounted, thus the suggestion of use of the Live CD.

---

### Post by Universal344 on 2008-07-12
I see why you suggested live cd now.  Yes its mounted and cannot be unmounted.  OK, I may not get to this until tomorrow because I may have go into my windows partition and create another iso image of the file and put it on a cd if I cannot find my original live cd.  Thanks!

---

### Post by avtolle on 2008-07-12
Best of luck to you. I cannot be around tomorrow, but I'm sure others will be able to give more able assistance than I in any case.

---

### Post by bigcheese13 on 2008-07-13
Hi,

I'm new to the linux world and have encountered the same problem as Universal, and i followed most of this thread's instructions with similar results up until i got to ```
sudo fdisk -l
``` with these results:

```
Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       15355   123339006    7  HPFS/NTFS
/dev/sda2           15356       30020   117796612+  83  Linux
/dev/sda3           30021       30394     3004155    5  Extended
/dev/sda5           30021       30394     3004123+  82  Linux swap / Solaris

```

After that post i was unclear as to what to do next and i guess my questions are 
1. what is gparted?
2. Is the live CD the same as what i installed linux from manually?

If you could clear up the directions, or rather bring them down to my level, i'd really appreciate it.

Thanks!

---

