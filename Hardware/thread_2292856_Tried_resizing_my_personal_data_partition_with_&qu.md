---
title: "Tried resizing my personal data partition with &quot;KDE Partition Manager&quot;..."
date: 2015-08-31
forum: Hardware
---

### Post by anders-the-coolest on 2015-08-31
Hello Ubuntu Forums.

i have a horrible little problem here. I newly converted to linux, having some experience from before, and im currently using Kubuntu for the sake of simplicity. I had two partitions, one with windows 8 and another one with my data files, to make OS installs painless. After getting around the basics of KDE, i thought i would want to resize my data partition, cause i had a lot of wasteful partitions (Push button reset, Recovery,) from my earlier windows 8 installation. My setup was like this:

/dev/sda1 : EFI, NTFS partition
/dev/sda2: Recovery, NTFS partition
/dev/sda3: Windows 8, NTFS partition
/dev/sda4: Data partition, NTFS partition
/dev/sda5: Push button reset, NTFS partition

After my installating of KDE, i removed the wasteful EFI, Recovery, and Push button reset partitions in order to save up to 50gb. I then had this setup:

unallocated: 828.98 MB
/dev/sda3: Kubuntu, ext3 partition       <---- My Kubuntu partition
unallocated: 51.80 GB
/dev/sda4: Data, 683.59GB       <---- The corrupt bastard

I used the KDE Partition Manager to resize my Data partition in order to gain more space on it, cause that partition easily fills up pretty quickly and i want to take advantage of all my space. As i pressed resize and waited for the operation, i thought i had done an error, and stupidly hit "cancel" on the operation window. After that, the whole Data partition became... unknown.

If i try to use testdisk or ntfsfix, they simply wont fix it. ntfsfix says something about the partition being corrupt, while testdisk wont show the partition at all.


I gladly appreciate any help on this. this partition contains pretty much many documents, games, music, photos, and beyond which i find very important to revive.

---

### Post by dino99 on 2015-08-31
you does not says how you have resized the partition, because it is always done with:
- the windows tool to shrink its partition(s)
- always done with unmounted partition: meaning you boot with the cd/usb first, then the partition can be modified safely
- use 'gparted live' for Linux partition(s)

but i'm not trying to make you scared

when partition(s) are resized after installation, they get a new uuid. So the boot loader (grub) does not know about the new uuid. That is why 'sudo update-grub' is always ran by the user in such a case to get it updated.

now if you boot and get a 'grub-rescue' terminal prompt, you need to run: > sudo grub-install /dev/sda if ubuntu is installed on sda, otherwise set the good partition. If you have a doubt, you can list all the partitions with > sudo blkid

if you does not get a 'grub-rescue' prompt, then boot with a live cd/usb, and run the given command above

---

### Post by anders-the-coolest on 2015-08-31
> **dino99 said:**
> you does not says how you have resized the partition, because it is always done with:
- the windows tool to shrink its partition(s)
- always done with unmounted partition: meaning you boot with the cd/usb first, then the partition can be modified safely
- use 'gparted live' for Linux partition(s)

but i'm not trying to make you scared

when partition(s) are resized after installation, they get a new uuid. So the boot loader (grub) does not know about the new uuid. That is why 'sudo update-grub' is always ran by the user in such a case to get it updated.

now if you boot and get a 'grub-rescue' terminal prompt, you need to run:  if ubuntu is installed on sda, otherwise set the good partition. If you have a doubt, you can list all the partitions with 

if you does not get a 'grub-rescue' prompt, then boot with a live cd/usb, and run the given command above

im not sure if we are on the same page here...


my kubuntu partition "/dev/sda3" works perfectly fine. i can boot into it without any problems (also i dont have the grub window show up when i boot though, i just go straight into KDE)

my data partition "/dev/sda4" is the problematic partition here. using your command "sudo blkid", i got the following output:

```

[FONT=monospace][COLOR=#000000]/dev/sda3: UUID="ab790e4a-ee14-4aeb-9cb9-3f6d23d035bb" TYPE="ext3" PARTLABEL="Ba" PARTUUID="a1f69cbf-b865-4c7a-b6ef-9c933dd1bf51"[/COLOR]
/dev/sda4: PARTUUID="0fde8a5e-56e5-b59a-9e66-f447459c17d7"
[/FONT]

```


also, i didnt use any partition tool from windows. i only used KDEs partition manager, and i did the resize when the disk was unmounted ofcourse.

---

### Post by yancek on 2015-08-31
Cancelling a resize operation is bound to lead to problems.  If testdisk doesn't show the partition, what happens when you try to mount it from Kubuntu, same result?

Also, I notice you had an EFI partition which would suggest you were using UEFI to boot rather than the older MBR.  If that is the case and you deleted the EFI partition, I don't see how windows would boot.  Generally this is a FAT32 partition?  You might try downloading and running boot repair on Kubuntu.  Make sure to select the option to Create BootInfo Summary and post the output here rather than try to do any repairs.  There are several members here who are well versed in UEFI.

---

### Post by anders-the-coolest on 2015-09-01
> **yancek said:**
> Cancelling a resize operation is bound to lead to problems.  If testdisk doesn't show the partition, what happens when you try to mount it from Kubuntu, same result?

Also, I notice you had an EFI partition which would suggest you were using UEFI to boot rather than the older MBR.  If that is the case and you deleted the EFI partition, I don't see how windows would boot.  Generally this is a FAT32 partition?  You might try downloading and running boot repair on Kubuntu.  Make sure to select the option to Create BootInfo Summary and post the output here rather than try to do any repairs.  There are several members here who are well versed in UEFI.

im not dual booting, i only have a partition with kubuntu and a partition with my personal data files, which is a big partition. im using legacy boot instead of UEFI.

---

