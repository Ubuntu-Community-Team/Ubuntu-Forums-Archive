---
title: "Revoving Ubuntu installation on multiboot drive"
date: 2009-08-09
forum: Installation &amp; Upgrades
---

### Post by Nuuk on 2009-08-09
I've got Windows XP on my C drive, Ubuntu 7.04 on the D drive. I want to try installing Ubuntu 9.04 in place of the 7.04.

But what happens if I wipe the D drive? GRUB would be destroyed so would the PC still offer me the chance to boot into Windows? Or would I be in trouble?

If so which is the best way to go about the upgrade. I can't go up in steps as neither 7.10 nor 8.04 will install on that PC for some reason.

---

### Post by presence1960 on 2009-08-09
it would be helpful if you not use windows lingo. In Linux drives & partitions are not designated as C:, D:, E:, etc. They are designated by sda, sdb, sdc, etc. Boot into Ubuntu, open a terminal and run ```
sudo fdisk -l
``` BTW that is a lowercase L at the end of that command. You will quickly see what I am saying. Try to refer to your partitions & drives this way.

If you install Ubuntu 9.04 over your existing Ubuntu GRUB will be written with the new install.

---

### Post by Nuuk on 2009-08-09
Thanks, and sorry for the terminology. 

So I don't need to remove 7.04, just run the installation CD for 9.04 and let it install itself?

---

### Post by howefield on 2009-08-09
> **Nuuk said:**
> So I don't need to remove 7.04, just run the installation CD for 9.04 and let it install itself?

Sort of ;)

Have you run Jaunty live cd to make sure everything appears to work ? (seeing as you said 7.10 & 8.04 didn't). Assuming it does, you can use partition editor from the live cd to wipe 7.04, having first made a backup of any files you want to keep.

The tell 9.04 to install to your newly wiped drive/partition.

---

### Post by Nuuk on 2009-08-09
I've got to the partition stage and I obviously don't want to install over Windows and 7.04.

So I have gone to the manual partition page but am now stuck.

What I have shown is

sda1 (ntfs) 15.3 gb (XP)
sda8 (ext3) 11.6 gb  (U7.04)
sda9 (linux swap) 643 mb
sda5 (ntfs) 18.4 gb
sda6 (ntfs) 18.4 gb
sda7 (ntfs) 12.3 gb

I've got the options to edit or delete those partitions.

---

### Post by presence1960 on 2009-08-09
> **Nuuk said:**
> I've got to the partition stage and I obviously don't want to install over Windows and 7.04.

So I have gone to the manual partition page but am now stuck.

What I have shown is

sda1 (ntfs) 15.3 gb (XP)
sda8 (ext3) 11.6 gb  (U7.04)
sda9 (linux swap) 643 mb
sda5 (ntfs) 18.4 gb
sda6 (ntfs) 18.4 gb
sda7 (ntfs) 12.3 gb

I've got the options to edit or delete those partitions.

Highlight sda8 and click edit. Set the parameters - very important you set mount point as /. Tick the format box and then proceed with the install. This will format the sda8 partition and install 9.04 to it.

---

### Post by Nuuk on 2009-08-09
Thanks, it is installing files now.

---

### Post by presence1960 on 2009-08-09
> **Nuuk said:**
> Thanks, it is installing files now.

Let us know how you fare. Enjoy Ubuntu!

---

### Post by Nuuk on 2009-08-09
Executing 'grub-install (hd0)'failed. This is a fatal error.

It's booted into Ubuntu indicating Live Session User. Does that mean it has not installed? :confused:

Time for a cycle ride!

---

### Post by Nuuk on 2009-08-10
Same again today (after 94% of the installation). The CD is OK because it works on the other PC. 

Is it failing to install GRUB because there is a previous version on the drive? If so,how can I get around that?

---

### Post by Nuuk on 2009-08-12
Looks like my mistake was not ticking the format box on sda8.

After that was done, 9.04 went on without a hitch. Thanks for all the help. :)

---

