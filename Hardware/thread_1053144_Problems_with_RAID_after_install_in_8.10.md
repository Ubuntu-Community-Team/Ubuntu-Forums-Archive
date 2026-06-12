---
title: "Problems with RAID after install in 8.10"
date: 2009-01-28
forum: Hardware
---

### Post by jhava on 2009-01-28
Hello all,

I just installed Ubuntu 8.10 from Alternate 64AMD CD onto an Intel Server Motherboard 3200 with RAID 1 configured with 2 320 GB SATA HD.

RAID controller configuration went well (there are two options, Intel Matrix or LSI, I've configured LSI) and Ubuntu detected the raid disk and installed properly.

But after reset, it cannot boot and goes to (initramfs) prompt.

I checked several FAQs and forums and checked all parameters.

I am able to see the RAID partition and mount it from this prompt.

ls /dev/mapper shows something like:

ddf1_4c539202020202020808629250000000036b1cd3100000a28
ddf1_4c539202020202020808629250000000036b1cd3100000a281
ddf1_4c539202020202020808629250000000036b1cd3100000a285

The second partition is /
The third partition is swap

If I check boot/grub/menu.lst, it says that the boot device is:

/dev/mapper/ddf1_4c539202020202020808629250000000036b18b1e00000a281


but if I change it to the current ID, it's of no use, this number changes everytime I boot.

(check the sequence of 8 digits begining with 36b1)

Has anyone come across this ? Why the device number is changing ?

Tried doing it by UUID, but this is in reference to the real hardware UUID, not to the virtual HD created by dmraid.

Regards,

JHAVA

---

### Post by samborambo on 2009-01-28
RAID drivers for your board may be buggy - log a bug report.

Is there a good reason why you're not using software RAID in Ubuntu? For levels 0, 1 and 10, software RAID has pretty much the same performance as hardware or host RAID - often there are cases where software RAID performs even better.

There are plenty of howtos on setting up software RAID.

Also, to get the best performance from your swap partition, put it at the beginning of the disk (the outer edge) as this area is read faster.

---

### Post by jhava on 2009-01-29
Thank you, actually, the RAID gets detected pretty well, so I doubt it's a driver problem. The problem is in the constant changing of the device naming. I think this is related to UDEV from what I was able to discover. It seems that some UDEV dmraid or dmsetup rules takes a parameter that changes in every boot, but I still do not understand quite well the rules files to touch.

On the other hand your suggestion of putting the swap file at front is great. I never thought it. Usually systems files goes first for pretty much the same reason but you want to give virtual mem better performance than system files. Thank you.

As to performance, I am not familiar with performance testing (had not have enough systems to test) so I go with recomendations. Customers believe that software RAID can be buggy or it's the worst performance option, and in this case they have asked for the next best alternative at latin american budgets, of course. Fakeraid will do.

What I could not find out yet is this: Is it a hardware raid or a fake raid ?  This motherboard is Intel Server Board S3200SHV, and it now brings the option of enabling RAID as Intel Matrix (which we know is Fakeraid) and LSI, which Intel has incorporated in some motherboards since last year agreement with LSI. I opted for LSI mode. Nowhere could I find if this option is Fakeraid or hardwareraid. Intel does not specify or I'm too dumb to find it.

Regards,

JHAVA

---

### Post by jhava on 2009-01-29
Finally solved !!!
The thing is that I partitioned the RAID device using standard partitions instead of LVM. Once I did it with LVM, now grub points to the LVM and boots always !!! Maybe it was my mistake but in all my readings nothing suggested me that is was compulsory to install LVM if you had RAID.

After testing RAID with Intel Matrix option and LSI option I'm more convinced that LSI option on that intel motherboard is a hardware RAID and Intel Matrix option is FakeRaid, but no certain way to tell. If anybody can shed some light on how to tell...

Regards,

JHAVA

---

### Post by zzzuppermen on 2009-01-29
Had the same problem with a Mylex (now LSI) eXtremeRaid 2000. I didn't wanted to go for LVM, so I used a small PATA to hold /boot and /tmp and the rest went on the RAID. Also, for some reason the installer could not create more then 6 partitions (1 primary and 5 extended) on the array, so for a higher number LVM is the obvious choice.

And yeah, the swap thing is inspiring!

---

### Post by Cracauer on 2009-01-29
I know I sound like a broken record, but if this is for anything else than raid-0, don't use that onboard SATA raid stuff.

md is what you want most of the time.

---

### Post by knn23 on 2009-07-28
Hello all, 

I had the same problem with ubuntu 9.04.  For one week, I tried to install the ubuntu desktop using the dmraid but none of the walktroughs worked for the configuration of our pc. So I have tried to install using the Alternate CD and everything went smoothly. However, when it comes to the restart, it did not boot :(. By the way before installing ubuntu we had another problem. If [FONT=Arial Black]Intel Matrix[/FONT] option is selected at the [FONT=Fixedsys]BIOS [/FONT]it does not see our DVDROM, "I don't have any idea why it is like that :confused:". If the [FONT=Arial Black]LSI [/FONT]option is selected we can boot from the CD. However, as i mentioned, this time it does not boot from the hard disk that we installed the "/boot" file. So, we decided to install  by using the [FONT=Arial Black]LSI [/FONT]option, after installation finishes, we have just changed the option to [FONT=Arial Black]Intel Matrix  [/FONT]and we are finally able to boot the "RAID 1 enabled system". We have tried it about one week, everything seems to be working seamlessly.

---

