---
title: "Help Needed: Dual Boot Vista x64/Ubuntu 8.04 with RAID 1"
date: 2008-07-15
forum: General Help
---

### Post by NP9262 Owner on 2008-07-15
Hello there. Help needed please !

I tried installing Ubuntu and then got a Grub error 21 message at boot up. I used to know quite a lot about computers, ya know, but that was when we all used monochrome screens. So here is what I did and what happened:

Just got yesterday a Sager NP 9262 laptop with 3 200gig drives (two in RAID 1-mirror and a third one non-RAID). Vista x64 was installed on the RAID drives and I wanted to install Ubuntu Hardy Heron (8.04) on the third drive, which was formatted in NTFS already but empty. So:

1) I booted from the Ubuntu CD and it listed the three drives as SCSI1, SCSI2 and SCSI3. From the drive space used and left, it was obvious the third drive was SCSI3. So I told Ubutntu to create a partition there after the NTFS one (shrinking it a bit) and to install.

2) Ubuntu then asked for the MBR Grub install (this is where I messed up, I guess). Was I supposed to install Grub on sda1 (windows/Longhorn Bootloader), sdb1 (windows/Longhorn Bootloader) or sdc1 (empty)? I thought that installing to sda1 or sdb1 could mess up things since the RAID was not detected, so I did what a careful noob would do: I left to default value (hd0).

3) Installation ran ok but a boot up, Vista just loaded without a bootloader. Then, on second boot after Ubuntu install, I think I saw for a brief moment the windows BSD (Blue Screen of Death) before entering boot loop. And on third boot, I got this dreaful message:

---

Grub loading stage 1.5

Grub loading please wait...
error 21

---

and voila. No more Vista, no more Ubuntu. Tada! I do know for sure that Ubuntu did install correctly on the third hard drive (the one that is not in RAID array), but obviously something went wrong with the bootloader.

Actually, I do not really care about having Grub or the Vista bootloader at startup. I was just hoping to boot with grub and take the info in menu.lst to inject it in vista bootloader with EasyBCD. I think installing Ubuntu to another drive should be simple, but I never found on the net a tutorial for installing Grub in a RAID1 MBR.

Anyway, if someone knows what happened and how to do correct this, please help ! Thanks !

---

### Post by quantum-positron on 2008-08-06
As far as I am aware you cannot use a hardware raid to accomplish this. You must use a software raid. I am currently working on the same problem with RAID 0 when I have found a solution I will post.

---

### Post by dafemec on 2008-08-18
Any news from either of you on this front?  I have run into the same problem and have not been able to solve it.  Thanks!

---

### Post by fjgaude on 2008-08-18
I'm not sure I can help, but here goes:

Put **grub** on your third non-raid drive:

```
sudo grub
grub> find /boot/grub/stage1
```

Notice the drives that have useable grub stages on them.

Then:

```
grub> root (hd2,1)
grub> setup (hd2)
gruv> quit
```

Then if necessary, out of grub and onto another command line:

```
sudo grub-install /dev/sdc
```

Then you will need to install **dmraid** to be able to see the NTFS raid1.

After the install:

```
sudi dmraid -ay
```

will show what the /dev/mapper/intel_xxxyyyzzz name looks like. Then putting a line in your /etc/fstab file will auto load whenever you boot into Ubuntu.

Let us know how you are doing, okay?

---

