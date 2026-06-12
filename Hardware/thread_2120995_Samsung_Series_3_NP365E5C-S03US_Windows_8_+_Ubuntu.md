---
title: "Samsung Series 3 NP365E5C-S03US Windows 8 + Ubuntu Dual Boot Success!"
date: 2013-02-28
forum: Hardware
---

### Post by slooksterpsv on 2013-02-28
For those of you who have heard of (wow quick comment, I don't like this new vb board, I'd rather have the old one) the UEFI Firmware bug with the Samsung Series laptops I haven't encountered it, but if you have the NP365E5C and want to dual-boot Windows 8 and Ubuntu 12.10 64-bit here's how I did it:

1. **Disable** Fastboot under advanced, **disable** Secure Boot, and change boot mode to **UEFI and Legacy** in the UEFI/BIOS (under boot I believe) area (press F2 during startup). If Windows won&#8217;t boot, be sure to change the boot load options and change it to the Windows Boot Loader.

NOTE: STEP 1 MUST BE DONE ALL 3 MUST BE CHANGED IN ORDER FOR THIS TO WORK!!!!!!!!!!!

2. Shrink drive C in Windows 8, via Disk Management (Window key + R and type in diskmgmt.msc), to the size you want: 60GB is sufficient for me

3. Use a USB Thumb Drive and Ubuntu 12.10 64-bit and use Unetbootin to rip it to the drive I used version 583 which is the latest at the time of this posting.

4. Reboot the computer, Press F10 and select the USB Key.

5. During install it may want you to completely WIPE the hard drive, DON&#8217;T DO THIS! Instead change it to say Something Else. Now Make a new partition to be / with Ext4 and using the area that says Free Space, set it to the size you want minus at least 2GB (or 2048MB) for Swap, add your Swap to what&#8217;s left of the free space (I do 4096MB of Swap). Leave GRUB to install on /dev/sda

6. Make sure you&#8217;re connected to the internet and install!

7. Reboot.

8. When starting the computer you will have to press F10 and either select Ubuntu or Windows. Windows was still default on mine so I booted into Windows to make sure it worked. Then I rebooted and select Ubuntu. You will have to do this each time as Grub2 wouldn't pick up on the Windows 8 installation for me.

POST INSTALL:

Now you may notice some graphical glitches when you start Ubuntu, go to AMD's site and download the AMD Catalyst 13.1 drivers - open a terminal and install the linux-headers-3.5.0-17-generic and linux-headers-3.5.0-17 drivers. Unzip the Catalyst 13.1 zip file and change the permissions to have execute via:

cd Downloads
chmod +x ./amd[press tab here and it will auto fill].run

Now run it with sudo:

sudo ./amd[press tab here and it will auto fill].run

Follow the installation window when it appears. Reboot and viola Ubuntu 12.10 64-bit with Windows 8 64-bit dual-boot =D No bricks yet =D

---

### Post by nik1979 on 2013-03-06
Thanks for this, will try it out in the week end. I have just gotten a Series 3 NP370R4E-S06. Any drawbacks in your experience? I've not used windows since 2010.

---

### Post by slooksterpsv on 2013-03-17
It's been running great; I didn't like Unity so I removed the AMD drivers, installed Gnome Shell and GDM and am running Gnome 3.0 =D

---

