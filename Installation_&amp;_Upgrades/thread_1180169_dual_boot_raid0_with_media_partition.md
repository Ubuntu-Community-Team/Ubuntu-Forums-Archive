---
title: "dual boot raid0 with media partition"
date: 2009-06-06
forum: Installation &amp; Upgrades
---

### Post by linux newb on 2009-06-06
hi all, ive been trying to figure out how to set this thing up, and so far i can get my kubuntu installation to boot.i cant get my media partition or windows to mount through gparted, is there some sort of method to this madness? its driving me mad lol.

---

### Post by ronparent on 2009-06-06
Your message doesn't give much to work on. 1st off, if you plan to boot from a raid0, you should probably try to install 8.10. 2nd, you should visit this site for how to perfom an install to raid0: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

3rd, how are you getting your kubuntu to boot (from the live cd)? There is no way I know of to mount partitions from gparted. If you are booting and/or using your raid drives from windows, I presume you have a raid in your mb chipset. If that is the case you have to install dmraid and use it to activate your raid. Instructions for that are at the above fakeraid site. Basically activating the raid set with dmraid creates so called symbolic links in /dev/mapper. Once this is accomplished you will mount your raid partitions by using a mount command to mount the link(s) in /dev/mapper to the mount point(s) you create in your file system for that purpose (ie /media/winXP, /media/winmedia, etc.). If you tell us where you are in the install process and where you are trying to go then we can help.

Just one important caution. DO NOT try to create a partition on a raid drive for installing until you know how to activate your raid first. Unactivated, both raid drives will show in gparted as unallocated. If you try to create a partition on the drives in a raid0 set showing as unallocated space you will TRASH your raid0. Thus you will lose everything on the drives! Better yet, if you have a spare drive available (anything over 10 gb) install kubuntu to that (it will be much simpler).

---

### Post by linux newb on 2009-06-09
Sorry i should have elaborated, i was in a hurry, ive done all this and no what i am doing as far as setting up fake raid. ive had it set up before where windows was installed first then linux, but since i tried to upgrade to 9.04 and it didnt recognize the fakeraid setup already installed and my sstem wouldnt boot, and as well i wiped out the whole array, rebuilt it and reinstalled windows and linux ```
grub> device (hd0) /dev/mapper/nvidia_djgahabd
device (hd0) /dev/mapper/nvidia_djgahabd      
grub> find /boot/grub/stage1
find /boot/grub/stage1      
 (hd0,4)                    
grub> root (hd0,4)          
root (hd0,4)                
grub> setup (hd4)
setup (hd4)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd4)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,4)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd4) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 21: Selected disk does not exist
```
this is what happens to me now when i take this path. and it wouldnt overwrite the windows mbr 
now the only way i could get grub to properly install is if i install linux, then windows then go back and mount the linux partition and install grub, but then the crapy part i go to add the windows partition to grub and its all good up uuntil i try to boot windows and it says it is unsupported or non excecuteable  but i can and am using linux now but any way please reply i need help on this bad seein as i am a linux newb.

---

### Post by ronparent on 2009-06-10
When you find (hd0,4) and set it as your root, everything is fine up to this point. However the next command should be **setup (hd0)**. Do that and everything will fall into place.

---

### Post by Speckay on 2009-06-10
Personally, I just installed Ubuntu 9.04 on my RAID 0 last night. Using the alternate CD, I didn't have to do anything to GRUB to get it to work.

All I did was originally, used the "shrink" option in disk management (in Vista) to make some empty space. Then when I booted off the alternate CD, it asked me if I wanted to activate the SATA RAID drives, I said yes, and I just told it to use the largest contiguous free space (guided). It did what it wanted, installed GRUB with no problems, and works great. Only thing I had to do was edit /etc/fstab to get it to mount my Windows partition on the RAID disk. The only other thing is I have two options for Windows when I boot up my computer through GRUB, but only one of them works (something I'll have to remove later).

I don't know if you would want to try that, but I thought it was going to be a lot harder than it was.

---

### Post by linux newb on 2009-06-14
> **ronparent said:**
> When you find (hd0,4) and set it as your root, everything is fine up to this point. However the next command should be **setup (hd0)**. Do that and everything will fall into place.

so coreect me if wrong, instead of "setup (hd4)", i should put "setup (hd0)"?

---

