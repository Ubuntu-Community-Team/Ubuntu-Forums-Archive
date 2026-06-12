---
title: "Cloned drive does not boot"
date: 2016-04-10
forum: Hardware
---

### Post by doug23 on 2016-04-10
Running Ubuntu 14.04 - mate desktop.  System running fine but wanted to update older boot disk from 160G to 1TB.  I analysed many ways to do this and decided on clonezilla. All went well but the new drive won't boot. I ran boot-repair and it said it fixed things but still not booting. Computer finds no boot devices. The diagnostic info is at paste.ubuntu.com/15749290

The boot disk is sda - sda1 - boot, sda2 - ubuntu, sda3 - swap  - the partitions have been resized to use the entire disk.

The original install was a dual boot dual drive win10/Ubuntu on a Lenovo H50. I would really like to take this back to the simplest boot method I could maybe eliminating the boot partition altogether if possible. I will NOT be using dual boot on this system ever again so removing that is not a problem. All I want to do is boot Ubuntu. n the original configuration on the 160G drive I had win10 and Ubuntu on two different drives. As you can see from the diagnostics it is using EFI but if that is not a desirable thing and if it makes things simpler I could eliminate that also.

This is not an emergency as the original drive is running and booting. I could totally remake this 1TB drive if needed. Perhaps just recreating a boot disk without a boot partition. I just need the steps to do that or anything else that would be suggested.

---

### Post by weatherman2 on 2016-04-10
So to be clear: sdb (another 1TB disk) is just a data drive?

Can you choose a boot menu at boot time?  Not sure how to do it on a Lenovo; on a Dell or Acer, for example, generally you can hit the F12 key to get a boot menu and choose what device to boot from.  If you can get a boot menu, what happens?  Do you even see your disk as an option to boot from?   I recently moved my Ubuntu + Windows SSD from one Acer laptop to another.  I had to use efibootmgr to create a firmware entry on the new laptop for my SSD - otherwise, there was no option to boot from it.  Boot repair could not fix my scenario but I think is supposed to fix stuff like that.

FYI, you don't have a boot partition now.  You have an EFI partition (would be mounted in /boot/efi in Ubuntu).  Are you saying you had a separate /boot partition (not EFI) on your old disk but not your new one?  Or you meant you wanted to get rid of the EFI partition (which you were calling a boot partition)?

It seems you can convert to "legacy" (BIOS) mode from EFI but I've never done it.  Try this:

[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_Legacy_mode)

but that assumes in your Lenovo BIOS you an option to disable secure boot and switch to "Legacy" mode.  Follow the instructions above to create a small /boot partition then run the boot repair as described - and hope it works!

---

### Post by yancek on 2016-04-10
You posted conflicting information.  First you say that you had a dual boot of Ubuntu and windows 10 on the smaller drive then you say you had the "original configuration on the 160G drive I had win10 and Ubuntu on two different drives".  So did you have Ubuntu/windows on the same drive on separate partitions or on different drives?

Clonezilla gives you the option to clone the entire drive or to clone a specific partition.  If you clone the partition with the old style MBR you won't be cloning the MBR as it is outside the partitions.  If you are using UEFI and have both drives, I would think you would need to modify the efi files for Ubuntu to point to the larger drive.  Not sure how to do that because I don't use EFI.

Your grub.cfg menuentries use UUIDs so the UUIDs for the partitions on the 1TB drive are not going to be the same.  Boot the original Ubuntu and run:  sudo blkid and you will then see the UUIDs for all the partitions on both drives.  Then mount the partition of Ubuntu on the cloned drive and compare the UUIDs there in /boot/grub/grub.cfg to the output of the blkid command you ran earlier.

---

### Post by doug23 on 2016-04-10
OK to answer the questions.

sdb is a separate 1TB data drive and not in the equation.

I had another drive with the 160G sda that had windows 10 on it. I then installed Ubuntu on the 160G drive. I later remover the windows 10 drive and installed the 1TB data drive. This all works. I then cloned the 160G (Ubuntu) to another 1TB drive and I now want to boot from that and take the 160G out of service.

At no time was there more than one OS on a drive.

The sda 160G was cloned. The new drive is identical. It has the same blkid's as the original drive. I also checked fstab and grub.config and the ID's match. It is essentially a copy of the original drive.

sda* that you see in the pasted info is the 1TB cloned drive that won't boot. The old drive is not attached at that point.

---

### Post by doug23 on 2016-04-10
Since I don't need uefi - I am never going to dual boot and my bios support using both legacy and uefi boot either separately exclusively or looking for both - can I just do this to go back to legacy boot and get rid of uefi or is that not a good idea?

If Ubuntu is installed on a GPT disk (you can check it via the 'sudo parted -l' command), use Gparted to create a BIOS-Boot partition (1MB, unformatted filesystem, bios_grub flag) at the start of its disk.

It is GPT - current sda1 is 512M - I guess I could leave it or change to smaller size. Delete and recreate.

Start Boot-Repair, click on "Advanced options", go to the "GRUB location" tab.

Untick the "Separate /boot/efi partition" option

Click the "Apply" button.

Set up your BIOS so that it boots the HDD in Legacy mode (see the ""Set up the BIOS in UEFI or Legacy mode" paragraph above). 


Does this sound reasonable or would it be the wrong thing to do. Seems less complicated than uefi.

---

### Post by weatherman2 on 2016-04-11
Nothing to lose by trying.  If it fails, clone it again.

---

### Post by doug23 on 2016-04-11
Ok I followed the directions here - 

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

converting Ubuntu boot to legacy mode.  I followed the directions. boot-repair did a lot of stuff including my cutting and pasting several times to run things in a terminal window.

So I am now booting non UEFI for Ubuntu. The Lenovo H50 is set to boot in CSM - both legacy and UEFI.

Other documents that might help others -

 [https://help.ubuntu.com/community/CreateBootPartitionAfterInstall](https://help.ubuntu.com/community/CreateBootPartitionAfterInstall)

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)

---

### Post by yoshii on 2016-04-11
I didn't read this whole thread but this might help:  

Run Gparted and don't do any modifications but get info on your partitions:  write down on paper the UUID for each partition, especially the one you want to boot.  
Then quit Gparted and sudo gedit /etc/fstab of the partition that you want to boot.  Then make sure that /etc/fstab contains the correct UUID for the boot partition.  
Make sure to preserve the syntax/format.  Then save the fstab and quit/reboot.  This might be something you are missing.  If it isn't, sorry for going offtrack.

---

### Post by sudodus on 2016-04-11
If you clone a drive with GPT, the target drive must have exactly the same size (not one single byte different). Otherwise the partition table will be corrupted and needs fixing. In a recent project I made a small shellscript that can do such fixing, except if the end of the last partition is beyond the end of the target drive.

See this link: [Clone drive with GPT - gpt-fix](http://ubuntuforums.org/showthread.php?t=2320200)

---

### Post by doug23 on 2016-04-11
In answer to the first question on UUID's - the cloned drive had exactly that same UUID as the original including fstab and grub.cfg and in the end that was not an issue. There was no reason to change them. I am cloing to use the new drive so it matters little that it was the same as the cloned from drive.

On the GPT... well that might be true and I suspect boot-repair should be aware of that and fix it. Maybe it did because I did change partition size and location with gparted. In the end I think the major problem was the UEFI boot. When I told boot-repair to go back to legacy boot it worked fine. When using legacy boot with GPT you need to create a boot partition of at least 1M and mark it as grub flag. I already had a 512M boot partition for UEFI so I just used that. I could reduce its size and expand the second partition down but I didn't bother for a few hundred megs. Beside leaving it there means I could go back to UEFI but I will probably never do that.

That would have been a funny statement 15 or 20 years ago when giving up 500 megs would have been crazy.

Booting is a complicated process made more complicated by our friend Microsoft. Since I never plan to use any of their products on the same machine as Linux except maybe in virtualbox.

---

### Post by weatherman2 on 2016-04-11
> **sudodus said:**
> If you clone a drive with GPT, the target drive must have exactly the same size (not one single byte different). Otherwise the partition table will be corrupted and needs fixing. In a recent project I made a small shellscript that can do such fixing, except if the end of the last partition is beyond the end of the target drive

Clonezilla should take care of that automatically - certainly did the last time I cloned a GPT drive with Clonezilla.

---

### Post by weatherman2 on 2016-04-11
> **yoshi2 said:**
> I didn't read this whole thread but this might help:  

Run Gparted and don't do any modifications but get info on your partitions:  write down on paper the UUID for each partition, especially the one you want to boot.  
Then quit Gparted and sudo gedit /etc/fstab of the partition that you want to boot.  Then make sure that /etc/fstab contains the correct UUID for the boot partition.  
Make sure to preserve the syntax/format.  Then save the fstab and quit/reboot.  This might be something you are missing.  If it isn't, sorry for going offtrack.

Clonezilla generally handles all of that automatically.  The OP's problem was that he got rid of Windows 10 during the clone, and that seems to have confused Clonezilla.  The last time I cloned my GPT dual boot drive (Ubuntu 12.04 on LVM + Windows 8, EFI and secure boot) with Clonezilla, the new drive booted perfectly without any manual intervention except for one issue.  (No swap partition was created on the clone for some reason, but that was easily fixed.)  I was surprised that something so complicated was handled so well.

I have cloned many drives manually using Gparted, dump, and rsync depending on the situation.  In that case, I usually wind up creating new partitions with different UUIDs, then just change the fstab on the clone.  A little more work but still fairly easy.

---

