---
title: "Ubuntu hard drive disappeared"
date: 2012-11-14
forum: Hardware
---

### Post by MadCityGeoff on 2012-11-14
Hi, everyone. The Ubuntu hard drive on my system is no longer visible in the BIOS or accessible in any way. I was running a triple-boot system with the following drives:
 
256 GB Crucial SSD with Windows 7
1 TB WD Caviar Black with Windows 8
1 TB WD Caviar Green with Ubuntu Oneric
 
Everything was working fine. I formatted the Ubuntu drive with a separate /boot partition and I used the Windows boot manager (configured with EasyBCD) to select the OS. 
 
I decided to reinstall Windows 8 on a second Crucial SSD. As soon as I installed the new SSD, I turned on the system and found that the hard drive with Ubuntu was no longer visible. It's not listed in the BIOS or visible in the Windows disk manager. The boot menu still shows Ubuntu, but if I select it I get the Grub text prompt.
 
I tried pulling out the Ubuntu drive and reinstalling it in a different drive bay. No luck. The new SSD and the old drives with Windows are there, but the Ubuntu drive just disappeared. I'd really appreciate any suggestions.

---

### Post by ahallubuntu on 2012-11-14
Unplug your other drives except for the Ubuntu hard drive.

Then boot your Ubuntu CD and repair Grub using the chroot method:

[https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot)

Now you should be able to boot the Ubuntu drive again assuming it wasn't corrupted.  You should be able to plug the other drives back in and boot it from the BIOS boot menu again.

Finally, assuming you did this before, copy the new boot sector back to a file with something like this:

sudo dd if=/dev/sda of=./ubuntu.bin count=1 bs=512

and then copy the file ubuntu.bin to the C: of the Windows drive where you were using the Windows boot manager to boot.

---

### Post by oldfred on 2012-11-15
Windows can only boot from one partition. So when you install multiple copies of Windows it searches for other installs and the newest one moves all its boot files to the first one. You probably are booting with Windows 8 from your Windows 7 partition and have no boot files in Windows 8. 

So Windows overwrote your EasyBCD settings in the Windows 7 BCD with a new Windows 8 BCD.

Since you have multiple drives you should just install grub2's boot loader to the Ubuntu drive.

ahallubuntu's full chroot procedure will work. That is the fall back when a couple of others do not work.

If you want a gui, you can download this into your Ubuntu  liveCD or download a full repair ISO to make into a CD or flash drive.

Post the link to the BootInfo report that this creates.

It may offer to install grub to all drives, better to just install to the Ubuntu drive.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

Or a two line command to mount partition with install and install grub2's boot loader to your Ubuntu drive:

[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

### Post by Yellow Pasque on 2012-11-15
I hope it's not a dead drive :\
You mention installing in a different bay, but did you try a different SATA plug? The first thing to do is try the drive alone as others have suggested.

---

