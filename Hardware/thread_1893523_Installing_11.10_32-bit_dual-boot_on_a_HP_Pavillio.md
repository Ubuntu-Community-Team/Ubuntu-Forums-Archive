---
title: "Installing 11.10 32-bit dual-boot on a HP Pavillion DV6-6140us Llano system"
date: 2011-12-10
forum: Hardware
---

### Post by SmallWorld on 2011-12-10
I just installed Ubuntu 11.10 32-bit Desktop Edition in a dual-boot configuration on a two-day-old HP Pavillion DV6-6140us with Windows 7 preinstalled.  Installing Ubuntu took a few hours and caused me a bit of frustration, so I figured I'd clean up my notes and share them.

The DV6-6140us runs an AMD Llano APU, consisting of an AMD A8-3500M CPU and an AMD Radeon HD 6620G GPU.  These chips, as of 09Dec2011, do not work with Ubuntu 11.10 without some tweaking, which I will describe below.

Windows 7 comes preinstalled with four primary partitions:
--SYSTEM, which contains a Windows bootloader if I understand right.
--C, which contains the Windows OS and user files. 
--D:RESTORE, which contains the Windows restoration drive
--HP_TOOLS, which contains some software allowing a user to update the BIOS while running Windows.

Because a hard drive can have a maximum of four primary/extended partitions, I needed to delete one partition to make room for Ubuntu.  The HP_TOOLS partition isn't really necessary.  The only time it's truly handy is when the computer is new and you need to update a bunch of drivers all at once.

Boot into Windows, run the HP Support Assistant to check for and update all the drivers and flash the BIOS.  Once that is done there is no longer any need for HP_TOOLS.

Restart Windows for good measure, then uninstall HP Support Assistant.  The reason to uninstall is I've read that if you delete HP_TOOLS and then run HP Support Assistant, it will forcibly rewrite HP_TOOLS which would be disastrous.  You can always reinstall HP Support Assistant, and HP_TOOLS for that matter, via free utility software on the HP web site.

Restart again for good measure.  Then click on the windows icon at the lower left of the screen, right click on My Computer, select Properties, select Manage, then find and select Disk Management.  Right click on your C drive where it is displayed in the lower part of the screen.  Shrink it significantly.  This will make room for the Ubuntu install.  I also used this room later on to install a large FAT32 partition to share files between Windows and Ubuntu.  So I shrunk the C drive down to 120GB.  Disk Management will shrink the C drive without requiring a reboot.

At this point I installed the free version of MiniTool Partition Wizard for the following two things, but you might be able to do the following two things with Disk Management: 1) Delete the HP_TOOLS partition.  2) Create a logical partition for data if you want to.  This is when I made my FAT32 parition.  It should be a logical partition, and should not be flagged as bootable.  Make sure to leave at least 60GB or so of empty space for Ubuntu.

Now download the Ubuntu 11.10 32-bit Desktop edition installer.  I chose 32-bit over 64-bit simply because I've had some sour experiences with 64-bit on a different computer a couple years ago.  Then either burn the installer onto a disk, or install on a USB drive per the instructions on the Ubuntu website.  I went with USB.

Now, with the wifi Fn key showing a white light (wifi power on), and nothing but the power cord connected to the computer, restart the computer.  Modify the BIOS settings (by hitting F10 on startup) to boot from CD/USB if you haven't already done so.

If you let the Ubuntu booter boot automatically, you'll end up with a black screen due to display driver issues.  To prevent this from happening, when the Ubuntu boot menu appears, hit Tab while the first selection on the list is highlighted ("Try Ubuntu" or something like that), scroll right, and after the "--" add a space and the following:
```
nomodeset
```
And boot up.  This should keep the screen working and drop you into a command line.
Then:
```
sudo -s
apt-get remove xserver-xorg-video-radeon

```
Confirm, let it do its thing, then:
```
service lightdm start
```
This would get Ubuntu up and running from the USB/CD.

In Ubuntu, connect to the internet via wifi.  Ubuntu will offer to download and install a proprietary driver for the STA wifi.  Don't do it, as the wifi already works fine and the new driver screws things up.  I also tried installing the system while connected to the internet via ethernet, but that also screwed things up.

So, with Ubuntu running and wifi connected, run the Install Ubuntu program or whatever it's called (on the desktop).  Choose to install updates and restricted drivers when it gives you the option to do so.  When it asks you if you want to remove Windows or install Ubuntu alongside, choose to do "Something Else".

The installer recognizes all three of the remaining Windows partitions.  In the empty space you created by shrinking the C drive earlier, create a swap partition (I used 3GB), an ext4 logical/extended partition with a mount point of /, and flag the ext4 partition space for formatting.  If you want to create any other logical partitions now's the time.  I already had a FAT32 partition in there as I mentioned earlier, but this is optional.

Continue the installation.  When the installation is finished, let the system restart.

The drivers are still messed up at this point.  When GRUB appears, choose to boot to Ubuntu in Recovery mode.  In Recovery mode choose to continue to Resume normal boot, but immediately hold down the shift key until it dumps you into a command-line login.  Log in, then:
```
sudo nano /etc/apt/sources.list
```

Look for the Partner repositories and activate them by removing the two the #'s at the start of the two lines.  Press CTRL+X then Y to save and exit.  Then:
```
sudo apt-get update
sudo apt-get install fglrx
reboot

```

Then the system should work perfectly.  AMD Catalyst Control Center will be installed and running.  Run Update Manager and if desired switch to gdm or XFCE or whatever. The proprietary Broadcom STA wireless driver installs itself at some point but now works fine and doesn't screw anything up. The Additional Drivers program offers a post-release update package to FGLRX but the package installation failed for me so don't do it.  Oh, and Windows works just fine.  Done.

Sorry to complicate things with my FAT32 partition, but who knows, maybe that's what made this installation work so I hate to leave that step out of my explanation.  Good luck all.

---

### Post by guleblanc on 2011-12-13
Thanks a bunch.  I was thinking about buying one of these, but I didn't know if Ubuntu would work well on it.  It sounds like you have been successful.

This will be very useful and helpful in the future.  (I still
have to convince my wife that I need to part with $700 for a
new computer.)

---

### Post by Dlambert on 2011-12-13
Why not use 64 bit?  Isn't it supported by that CPU?

---

### Post by SmallWorld on 2011-12-22
The CPU is indeed 64-bit.  As suggested briefly in the explanation, the only reason I went 32-bit is some personal bitterness lingering from a 64-bit install I did on a different (64-bit) computer in the past.

32-bit has always worked for me, and all my preferred software works with it without any of those infuriating 32vs64bit library conflicts, so I haven't bothered to go 64-bit yet.  Maybe when 12.04 LTS comes out I'll finally go 64-bit, and I'll try to post notes if I do.

If anyone tries installing Ubuntu 64-bit on a DV6-6140us, please let this thread know how it goes.

For reference I got mine brand new for $600+tax during a rebate-oriented sale at Office Depot in early December 2011.  I think Office Depot is selling it for $650+tax now.

---

### Post by sturdy on 2011-12-25
Hi SmallWorld,

I just wanted to say "THANKS'. It took three tries but I made it. It appears the updates to fglrx are the problem but I have no clue about how to fix. They should not be installed. Your install got me up and running...thanks again
sturdy

---

### Post by hostage_devil on 2012-01-07
how i can install kubuntu 11.10 or anythings linux on hp 6170???
i can boot from live linux but it can't  Diagnosis hard partion table , just be install in all hard !!  plz help me !!

---

### Post by silverhaze06 on 2012-01-07
> **sturdy said:**
> Hi SmallWorld,

I just wanted to say "THANKS'. It took three tries but I made it. It appears the updates to fglrx are the problem but I have no clue about how to fix. They should not be installed. Your install got me up and running...thanks again
sturdy

I have them installed and my computer is working fine. Following this thread was a huge help to get it to perform well. [http://ubuntuforums.org/showthread.php?t=1857911]("http://ubuntuforums.org/showthread.php?t=1857911")

---

### Post by ozybard on 2012-02-28
Many thanks for posting this.  I had major dramas getting 11.10 installed on an HP Omni 120 all in one.  Ended installing 10.10 then upgrading to get it working but your notes, if I had found them before I started would have saved me a heap of time.  Thanks for sharing:D

---

### Post by tristangrimaux on 2012-03-09
Great post! You saved me a lot of time. I did skip the fat32 partition because there was no need to do that, and everything went smoothly.

Congrats!

---

### Post by SmallWorld on 2012-09-10
Today I finally got around to upgrading Ubuntu 11.10 32-bit on this machine to 12.04.1 64-bit.  It was a lot easier than the above install, props to AMD/ATI for getting their drivers right.

Details are at: [http://ubuntuforums.org/showthread.php?p=12231010]("http://ubuntuforums.org/showthread.php?p=12231010")

---

