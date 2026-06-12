---
title: "Installing Gentoo in unallocated space via ubuntu"
date: 2008-05-22
forum: Gentoo and derivatives
---

### Post by marty1011 on 2008-05-22
Hello. I am very new to linux and I want to install Gentoo in a 7 gb unallocated space created by resizing Ubuntu using Ubuntu LiveCD. However I do not know what to do from here on. I am trying to follow this [http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#fdisk](http://www.gentoo.org/doc/en/handbook/handbook-x86.xml?part=1&chap=4#fdisk).
I do not want to use fdisk as mentioned there since I am afraid I will wipe off my Vista and Ubuntu (I am running dual-boot). And also I cannot create a new partition in that unallocated space since I have 4 primarty partitions already. Vista (sda1-ntfs), Ubuntu (sda3-ext3), sda4 is extended and linux-swap is sda5 under sda4 and a recovery section for Vista in sda2.  Can someone please guide me?

Any help will be appreciated.

---

### Post by medic2000 on 2008-05-23
Make a backup for important files. Then download the gparted live cd and resize it!

---

### Post by marty1011 on 2008-05-23
> **medic2000 said:**
> Make a backup for important files. Then download the gparted live cd and resize it!

I have acquired the gparted the live cd. However gparted fails to start x11. Is it possible to use gparted from ubuntu to accomplish this? And what should I do after I resize the partition?

Thanks a lot for your help.

---

### Post by HunterThomson on 2008-05-24
I have always wanted to install gentoo.... I have spent the last week reading about it and downloaded the install cd KDE and level3. I would also like to here what people here say about installing gentoo with ubuntu.

---

### Post by MONODA on 2008-05-24
be warned that installing gentoo might take a few days.(no joke)

---

### Post by marty1011 on 2008-05-24
> **marty1011 said:**
> I have acquired the gparted the live cd. However gparted fails to start x11. Is it possible to use gparted from ubuntu to accomplish this? And what should I do after I resize the partition?

Thanks a lot for your help.

Nevermind. I have figured out how to make it work. Thanks.

---

### Post by marty1011 on 2008-05-24
> **MONODA said:**
> be warned that installing gentoo might take a few days.(no joke)

I know but I am up for the challenge.:)

---

### Post by marty1011 on 2008-05-24
Ok. I have created a new logical partition inside my Extended partition. Thanks a lot guys.

---

### Post by marty1011 on 2008-05-26
I have been using the gentoo handbook but I got stuck at the grub config. I don't know how to add gentoo in /boot/grub/menu.lst of Ubuntu partition.
Also I am not very sure with the command ```
cp arch/x86/boot/bzImage boot/kernel-2.6.24-gentoo-r8
``` Any help regarding these will be appreciated.

---

### Post by trimeta on 2008-05-26
For the grub config, what problems have you had in particular? Make sure to read the bit about how Grub's partition terminology works; if your Gentoo partition is on /dev/sda7, you'd need to have the root line read "root (hd0,6)", because Grub zero-indexes. Could you give us a bit more information about your setup, in particular your partitioning scheme, with stuff like how many primary, how many logical, what each of them does, etc.?

---

### Post by marty1011 on 2008-05-27
Hi.
here is my partition scheme:

sda1----ntfs----vista   boot(flag)
sda2----ntfs----vista recovery
sda3----ext3----Ubuntu
sda4----Extended
  sda5----linux swap
  sda6----gentoo

sorry I cannot provide the fdisk result. I am reinstalling Gentoo at the moment.

Thanks
Edit: Since I do not have a separate boot partition I don't have to add it in the fstab of gentoo right? (please correct me if I am wrong). All I have to do is just add the root and the swap right?
So it would look something like:
/dev/sda6   /mnt/gentoo   ext3   noatime  0 1
/dev/sda5   none          swap   sw       0 0

---

### Post by regomodo on 2008-05-28
> **marty1011 said:**
> Hi.
here is my partition scheme:

sda1----ntfs----vista   boot(flag)
sda2----ntfs----vista recovery
sda3----ext3----Ubuntu
sda4----Extended
  sda5----linux swap
  sda6----gentoo

sorry I cannot provide the fdisk result. I am reinstalling Gentoo at the moment.

Thanks
Edit: Since I do not have a separate boot partition I don't have to add it in the fstab of gentoo right? (please correct me if I am wrong). All I have to do is just add the root and the swap right?
So it would look something like:
/dev/sda6   /mnt/gentoo   ext3   noatime  0 1
/dev/sda5   none          swap   sw       0 0

yeah, if you have no partition for /boot you can leave the BOOT part of fstab commented or omitted.

---

### Post by trimeta on 2008-05-28
Actually, since sda6 is the root of your Gentoo system, you'd want your fstab to look like:

```

/dev/sda6  /        ext3   noatime              0 1
/dev/sda5  none     swap   sw                   0 0
```

/mnt/gentoo is where you had things on the liveCD, but for the actual system you need to mount the root (that is, /) to something, and since that's where you installed Gentoo, that's where you mount it.

Edit: Oh, and don't forget the following line; it's probably already in the example, but just in case.

```

shm        /dev/shm tmpfs  nodev,nosuid,noexec  0 0
```

As for Grub, with the setup you have you'd want something like:
```

title Gentoo
root (hd0,5)
kernel /boot/whatever_you_called_your_kernel root=/dev/sda6 other_kernel_options
```

Edit: Possible problem: I'm referring to the /etc/fstab on your Gentoo partition. Don't modify the one on your Ubuntu partition, that can have whatever you want (/mnt/gentoo is fine for allowing you to access your Gentoo partition data while running Ubuntu). You just need to make sure that the Gentoo partition's own /etc/fstab has something mounted to / in its /etc/fstab, otherwise it won't boot.

---

### Post by regomodo on 2008-05-29
> **trimeta said:**
> Actually, since sda6 is the root of your Gentoo system, you'd want your fstab to look like:

```

/dev/sda6  /        ext3   noatime              0 1
/dev/sda5  none     swap   sw                   0 0
```

/mnt/gentoo is where you had things on the liveCD, but for the actual system you need to mount the root (that is, /) to something, and since that's where you installed Gentoo, that's where you mount it.

Woops, did not read that far down. Mounting on /mnt/gentoo will not work.

---

### Post by marty1011 on 2008-06-11
Thanks a lot, I have fixed the problem. Sorry for the late reply (been busy with school finals).

Regards
marty

---

### Post by regomodo on 2008-06-11
> **marty1011 said:**
> Thanks a lot, I have fixed the problem. Sorry for the late reply (been busy with school finals).

Regards
marty

Haha, tell me about it. Got to pull about 2 more all-nighters and i'll be done by Friday. Wahay!

(Yes, i'm procrastinating.)

---

