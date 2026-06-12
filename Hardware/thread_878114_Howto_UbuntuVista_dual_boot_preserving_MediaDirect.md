---
title: "Howto: Ubuntu/Vista dual boot preserving MediaDirect button on Dell XPS M1530"
date: 2008-08-02
forum: Hardware
---

### Post by LargeHadronCollider on 2008-08-02
I was so happy that I could work this out, that I thought I'd share it on the forum - I know there are several different howtos out there about this MediaDirect button issue, but no single one worked for me.

**So this is the problem:**
- When you get a Dell XPS M1530 (M1330 is probably the same) with Dell MediaDirect 3.5 installed, you have the nice feature that this additional button with a house symbol on it, next to the power button, launches MediaDirect - a stand-alone media player running on a cut-down Windows XP so that you can watch movies without having to fully boot Vista or any other OS.
- This nice function gets lost as soon as you touch the partitioning e.g. during the (K)Ubuntu installation, and the MediaDirect functions turns into a self-destroy button (I just got blue screens, and normal booting was messed up too, after that).
- On top of that, you might encounter the problem that Ubuntu installation fails because it cannot install the GRUB bootloader for no apparent reason - it just reports a failure at 94% of the installation.

**The solution I found results in:**
- 1 single partition for Vista, 1 single partition for Ubuntu (further sub-partitioning might be possible, but I didn't try)
- Dell MediaDirect and Dell Utility partitions are preserved and functional
- The intended functionality of the MediaDirect button is preserved
- Dual boot Vista/Ubuntu when pressing the normal power button, boot managing completely controlled by Vista (no GRUB). We use the Vista boot manager in conjunction with NeoGRUB (that's basically GRUB for Vista, as I understand it), with the tool EasyBCD for Vista - completely free and officially supported by Microsoft. ([http://neosmart.net](http://neosmart.net))
- A completely newly set up system, losing all previous data on the disk (there's a price for everything I suppose)

Stuff used:
- All Dell installation CDs (most importantly, Vista reinstall and MediaDirect reinstall CDs)
- Ubuntu 8.04 64-bit Live CD
- The program EasyBCD for Vista (not open source, but available totally free of charge at [http://neosmart.net](http://neosmart.net), officially supported and recommended by Microsoft apparently)

Steps involved:
**1.) Prepare hard disk with MediaDirect CD**
!!! Backup all data from your harddisk, it will get erased completely in this step !!!
- Insert the Dell MediaDirect CD and boot from it. It gives you two options to organize your disk: only 1 partition for windows, or 1 partition for windows plus 1 "data" partition. Both options will also create the Dell utility partition and the MediaDirect partition, both of which we will NEVER TOUCH.
- Choose option 2 - one Vista partition, one Data partition (the latter of which will be turned into our Ubuntu partition) and choose the size of the Windows partition. The remaining space will be allocated to our ubuntu partition. After this is done (~1-2 secs), eject the CD and insert the Ubuntu Live CD.

**2.) Install Ubuntu**
- After preparing the disk (step 1), boot from the Ubuntu CD and start the installer (at least that's the way I do it). Follow the installer instructions until you reach disk partitioning. Choose "manual partitioning", and you will be presented with the partition table. This will show, in this order: a) The utility partition, b) the Vista partition you created, c) the data partition, d) the MediaDirect partition. The last two will be in the extended partition.
- Select the 'data' partition (c) and reformat it as ext3 (or whatever filesystem you prefer), set mountpoint to "/", and click ok, then Next. It will warn you that you have no swap partition, but we will set up a swap *file* instead later in Ubuntu (that's how you do it nowadays). Click ok again.
- Continue until you reach the last step, and click on the Advanced... button. **We do not want to install GRUB**, therefore uncheck the check box. Finish the installation.
- After the installation and still in Ubuntu Live, find out what partition exactly you just installed Ubuntu on (for later for the bootloader configuration). Normally this will be /dev/sda5 - verify this by mounting it ('sudo mount /dev/sda5 /mnt') and checking its contents: If you go to /mnt and see folders like home, src, usr, etc, then this is it. Note: This will be device /dev/sda5, and in GRUB notation this is (hd0,4) - the 'a' translates to '0', the '5' translates to '4'.
- Now you have Ubuntu installed on your former 'data' partition, but you can't boot it because it is installed in a logical partition and there is no boot loader, but we will fix this with Vista. After the Ubuntu installation, reboot the computer, insert the Vista installation CD and boot from it.

**3.) Install Windows Vista**
- Boot from the Vista CD and install it on the other partition, that is intended for Vista.

**4.) Install Dell MediaDirect**
- Start up Vista and insert the MediaDirect reinstallation CD. It only gives you the option to press Enter to install MediaDirect, or Esc to abort. Press enter and wait until MediaDirect is installed.
- Test it: Shut down your computer and press the MediaDirect button. This should start not Vista, but directly MediaDirect from the MediaDirect partition. If it works, go on to step 5. If not, I'm afraid you have to start over at step 1.
- Turn off your computer and reboot Vista.

**5.) Configure the bootloader**
- We will use Vista's own bootloader, in conjunction with NeoGRUB, which is basically a Vista implementation of GRUB and very useful.
- In Vista, download and install EasyBCD from [http://neosmart.net](http://neosmart.net) - it's completely free of charge, though not open source.
- Start EasyBCD. Click straight on the Add/Remove Entries button, where there will be only the Windows Vista entry. In the lower part of the window, under "Add an Entry", look for the NeoGrub tab and click on Install NeoGRUB. After ca. 1 sec, the status bar will inform you that NeoGrub has been successfully installed (it goes to C:\NST, actually).
- Still in the NeoGrub tab, click on Configure. Notepad opens and lets you edit the menu.lst file for NeoGrub. Since we use NeoGrub only to boot Ubuntu, my file looks like this:
```

default 0
timeout 1
title Ubuntu 8.04 64-bit

# If you do the partitioning exactly as I described, this will be correct.
# Otherwise, replace with the true linux partition number
root (hd0,4)
# The i8042.nomux=1 option is to make the touchpad work correctly
# Set these two options to the exact filenames in your /boot directory in Linux
kernel /boot/vmlinuz-2.6.24-19-generic root=/dev/sda5 ro quiet splash i8042.nomux=1
initrd /boot/initrd.img-2.6.24-19-generic

```
- Save it, and then that's it!

If you reboot your computer, you will be presented with the Windows Vista boot menu, that will let you choose between Vista and 'NeoGrub bootloader'. If you choose the NeoGrub entry, what will happen is that it will load NeoGrub, which in turn only contains the entry for Ubuntu.
If you turn off your computer and press the MediaDirect button, MediaDirect will start (no more self-destruction button), which is quite neat whether you use MD or not.

You now need to launch Ubuntu and set up a swap file, for this see: [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Disadvantages of this method:
- You have to go through 2 bootloaders to launch Ubuntu
- After every kernel update, you have to update the NeoGrub menu.lst file from within Vista to the new kernel image name.

I hope this is useful to anybody who encounters the same problem I did, and who is happy with just 1 partition for Windows and 1 partition for Linux. I'm personally not a fan of having an OS and a Data partition, so this is fine for me.

---

### Post by mittko on 2008-08-04
Thanks a lot for all this info! I have just received my XPS 1530, and am thinking about Vista/Ubuntu dual boot installation process. I have a question though:

1. You are not mentioning anything about drivers - do you install them after this whole process? 

Also, have you noticed any other problems since you have done the dual-boot in that order (i.e. Media Direct>Ubuntu>Vista)?
Thanks.

---

### Post by sayad on 2008-08-04
Thanx for tha reply too , actually i am installing vista soon on my laptop and that information was really required.
I still have to ask one thing , why ssingle partion in vista ?

---

### Post by LargeHadronCollider on 2008-09-06
I did install the drivers and everything only after the last step of this process, to first make sure that the entire boot setup works as desired (i.e., does the bootloader work and boot both operation systems correctly, does the MediaDirect button still work) before investing any time in configuring Vista.
But if you are confident, you can of course also install all drivers straight after Vista is on your system, it shouldn't affect the rest of the system.

My system works still perfectly since I've done this, without any problems!
But just one remark: the way I have described setting up the NeoGRUB bootloader, you would have to manually adapt the kernel and initrd filenames in the NeoGRUB configuration file in Vista after a kernel update (when the version number changes), as the filenames are hardcoded in my example.

Hope this works for you.

---

