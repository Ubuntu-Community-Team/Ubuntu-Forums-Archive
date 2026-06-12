---
title: "GRUB on 2 Hard Disk Systems boot selection with BIOS"
date: 2009-03-17
forum: Installation &amp; Upgrades
---

### Post by markosjal on 2009-03-17
I recently did an anstall of Ubuntu that was different than previous installs, ajd wanted to document what happened here , as I was somewhat dissatified with how Ubuntu chose to install without asking nor informing me. 

I added a second Hard disk, that I wanted to install Ubuntu on , and not touch my windows partition, I figured I could install to the new drive and use the BIOS boot options to select which drive to boot to. Unfortunately, Ubuntu did not advise nor ask about installing GRUB menu onto my windows drive. Now my install of ubuntu is dependent on the GRUB menu on that windows drive. I can not simply elect to remove that WIndows drive nor do anything should it fail. The installation of Ubuntu is not completely on the new drive. I can not tell my BIOS to boot to that drive and have it do so successfully. 

I think this is something that one might even consider a bug, and that the installer should at least INFORM at installation that it will install the GRUB menu on the windows drive, and most probably should present an option.

The installation in the form it is is less useful than I had planned due to that GRUB dependency that does not exist on the Ubuntu system disk. I also dislike that my good windows configuration was modified by the ubuntu install without being informed.

I am sure it is probably resolvable after a day of reading forums and working to take it off of the windows drive and get the Ubuntu drive to boot alone, but that just makes more work.

---

### Post by upchucky on 2009-03-17
you had to have selected the dual boot option for grub to install to the win mbr. the only thing ubuntu did was tell grub to set up a dual boot thus overwriting the mbr for windows, this is not actually part of windows, just the master boot record area of the drive.

this is fixable, remove the windows entry in the menu.lst file of grub.
then use your win cd to fixmbr for windows.

install ubuntu to the second drive, and install grub to the second drive. use the bios select to tell pc which os to boot.

i have xp on one drive, ubuntu on a different drive and experimental linux booting on a usb drive. 

you may need advanced supergrub to set everything up properly. it is sometimes a help to only have one drive in the system at a time, then install on each drive one at a time.

---

### Post by markosjal on 2009-03-18
As I said, sounds like a day to fix it. 

Actually it did not ask. I said I wanted to install to a drive that had CentOS4 on it and it asked if I wanted to reformat it and I sad YES. At no time did it indicate that the GRUB installer was being installed on my windows drive (at least not in any clear form)
 

I should not have to reinstall Ubuntu to get it to boot off the Ubuntu drive. There must be something like fixmbr for ubuntu. BTW it would be DUMB to fixmbr on the windows disk BEFORE fixing the ubuntu install, or the ubuntu install will be rendered useless.

In my opinion , it should be a CLEAR option as most BIOS now support selecting boot device in BIOSs and/or at the BIOS startup screen, thereby making the GRUB selection just an unnecessary step.

---

### Post by meierfra. on 2009-03-18
> As I  said, sounds like a day to fix it. 

Nope. Only takes a few minutes:

To fix your problem, you need to install grub to the MBR of the second drive and and repair the MBR of the first drive.
Open a terminal in Ubuntu (Applications->Accessories->Terminal

** Step 1 Install Grub to the MBR of the second hard drive.**


```

sudo grub

```

and at the "grub>" prompt.



```

 find /boot/grub/stage2

```

This will return (hdX,Y), where X and Y are some numbers, like (hd1,0)

Still at the "grub>" prompt:




```

root (hdX,Y)
setup (hdX)
quit

```

(here X and Y need to be replaced by the numbers you got from "find /boot/grub/stage2")


** Step 2) Install a Windows Style MBR to the first hard drive: **


```

sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

```

(Here "/dev/sda" needs to be the device name of your first drive. It probably is "/dev/sda" but you should double check via "sudo fdisk -lu")


Reboot.  You   should  now be able to boot into Windows and Ubuntu by switching the boot order in the bios. 
If you would like to boot into Window from the Grub Menu, post the output  of "sudo fdisk -lu" and I can show you how to edit "menu.lst"


********************************************************************************

---

### Post by enjoi19 on 2009-03-18
wait here are you saying half the windows system is on the new drive, and half on the old one?

---

### Post by upchucky on 2009-03-22
srry if this is a bit late, been very busy.

It is not dumb, unless you are dual booting.
You said you are not dual booting, but you are doing a bios selectable boot, so it does not matter which mbr you fix first.

Editing grub is the ubuntu fixmbr process.

Every bootable hard drive, usb drive, live cd must have a mbr if it is to be bootable as a stand alone device.

If you are dual or multiple booting then the mbr of one device must have all the info to allow booting of other devices.

Grub is actually Grand Unified Bootloader, this was created because the bios chip on motherboards can't possibly store all the thousands of drive configurations ever made. In short, this means that a grub like step is really needed to be able to boot multiple drives. 

In your case, because you want to bios select when either booting Windows or Ubuntu, you use the windows mbr when booting windows, and use grub when booting Ubuntu.

For more clarity, physically disconnect the windows drive then install ubuntu on the second drive. reconnect the windows drive. you now have a Bios selectable bootable windows or Ubuntu. (of course this would be after you have fixed the Windows MBR using fixmbr on your Windows installation cd)

Or as an alternative, do as Meierfra posted in this thread, and you come to the same results.

No one said anything about windows being half on any drive.

Be very careful to read about what you are trying to do in the future, it can save you and others the frustration and headaches caused because a simple instruction step was missed or not read at all.

These are concepts that you must understand to be able to do your own administration

> **markosjal said:**
> As I said, sounds like a day to fix it. 

Actually it did not ask. I said I wanted to install to a drive that had CentOS4 on it and it asked if I wanted to reformat it and I sad YES. At no time did it indicate that the GRUB installer was being installed on my windows drive (at least not in any clear form)
 

I should not have to reinstall Ubuntu to get it to boot off the Ubuntu drive. There must be something like fixmbr for ubuntu. BTW it would be DUMB to fixmbr on the windows disk BEFORE fixing the ubuntu install, or the ubuntu install will be rendered useless.

In my opinion , it should be a CLEAR option as most BIOS now support selecting boot device in BIOSs and/or at the BIOS startup screen, thereby making the GRUB selection just an unnecessary step.

Good luck and I hope you enjoy your new ubuntu world.

---

### Post by markosjal on 2009-03-23
Upchucky,

I want to point out that the installer was not PERFECTLY CLEAR , in fact I believe it was even misleading, as there was nothing OBVIOUS that indicated that my windows drive was to me modified. PERIOD

---

