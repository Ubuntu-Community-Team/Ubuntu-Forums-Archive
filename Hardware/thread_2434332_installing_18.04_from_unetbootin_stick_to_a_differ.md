---
title: "installing 18.04 from unetbootin stick to a different usb device"
date: 2020-01-03
forum: Hardware
---

### Post by mark allyn on 2020-01-03
Hello everyone,

I have a live 18.04 image on a unetbootin stick.  My question is how to install from the unetbootin stick to a different usb device.  I don't want to install to my hard drive because I have Win7 running from it and I don't want to partition it.  

A related question is how to get out of the unetbootin desktop.  I don't see an exit control.  Do I just bring up a terminal and do something on the command line to exit unetbootin gracefully?

Thanks,
Mark Allyn

---

### Post by yancek on 2020-01-03
I'm not sure what you mean by the 'unetbootin desktop'.  If you have used unetbootin to put a live version of Ubuntu on a usb with the installer, you should see the standard Ubuntu desktop and use the icon in the extreme upper right to get shutdown options.  I guess that might depend on the desktop you are using.  You should also be able to use the shutdown or reboot commands from a terminal.

If you want to install to another usb, you need to first determine what the device is by using the command:  sudo fdisk -l while booted into Ubuntu on the live usb.

---

### Post by mark allyn on 2020-01-03
Hello Yancek,

Thanks for the response.  I'm new to 18.04 and so I didn't know the meaning of the icons in the upper corner.  But, I did find finally the logout option.  Thanks.

If I try to install by clicking on the "install unbuntu 18.04.3 LTS" icon on the uninstalled desktop, somewhere in the sequence of choice screens there is, I'm sure, some screen on which I could enter the name of the usb drive and install to that location.  But, I don't know how to get to that screen.  I take your point of about using fdisk comman to identify the target drive--this is definitely helpfrul (really essential), but I don't know where to put that info into the installation command sequence.

Hope that's clear!

Regards, 
Mark

---

### Post by oldfred on 2020-01-03
You need to use the Something Else install option.
Most Windows 7 systems are BIOS/MBR. With Ubuntu you can use the newer gpt partitioning with BIOS, but have to add a 1 MB unformatted partition with bios_grub flag. UEFI normally uses gpt partitioning with an ESP - efi system partition which is FAT32. 

My full  installs to flash drives used gpt and I had both an ESP & bios_grub back when I was transitioning from old BIOS system to newer UEFI system. Flash drive would only boot in one or the other mode, but only a reinstall of grub was required to convert boot mode.


[https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](https://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29)

Older 14.04 screenshots, but newer versions very similar.
[https://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](https://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by C.S.Cameron on 2020-01-04
Full Install to USB

Full installs are more stable and secure than persistent installs, but not as quick to make. They are better at utilizing disk space as no fixed size casper-rw file or partition is required. They are not very good for use of installing Ubuntu.

Following is a step by step how to install 18.40 on a 16GB flash drive with options for separate Home partition and Windows compatible data partition:

- Create a live USB or DVD using SDC, UNetbootin, mkusb, etc.
- Turn off and unplug the computer. (See note at bottom)
- Remove the cover.
- Unplug the power cable from the hard drive or unplug the hard drive from the laptop.
- Plug the computer back in.
- Insert the flash drive.
- Insert the Live USB or Live DVD.
- Start the computer, the USB/DVD should boot.
- Select language.
- Select install Ubuntu.
- Select Keyboard layout
- Select "Continue".
- Select installation type and "Download updates while installing Ubuntu" and Select "Install third-party software ...", (optional).
- Select "Continue".
- At "Installation type" select "Something else". (Full disk encryption is not working with flash drives).
- Select "Continue".
- Confirm target device is correct.
- Select "New Partition Table".
- Click Continue on the drop down.

(Optional FAT32 data partition for use on Windows machine)

- Click "Free space" and "+".
- Make "Size..." about 2000 MB.
- Select "Primary".
- Location = "Beginning of this space".
- "Use as:" = "FAT32 file system".
- "Mount point" =  "/windows".
- Select "OK"

- Click "free space" and then "+".
- Select "Primary", "Size ..." = 4500 to 6000 MB, "Beginning of this space", Ext4, and Mount point = "/" then OK.

(Optional home partition)

- Click "free space" and then "+".
- Select "Primary", "New partition size ..." = 1000 to 6000 MB, Beginning of this space, Ext2, and Mount point = "/home" then OK.

(Optional swap space, allows hibernation)

- Click "free space" and then "+".
- Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning of this space and "Use as" = "swap area" then OK.

(Important)

- Confirm "Device for boot loader installation" points to the root of the USB drive. Default should be OK if HDD was unplugged.
- Click "Install Now".

- Select your location.
- Select "Continue".
- Insert your name, computer name, username, password and select if you want to log in automatically or require a password.cscameron
- Select "Continue".
- Wait until install is complete.
- Turn off computer and plug in the HDD.
- Replace the computer's cover.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the USB drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR as default location for boot loader is sda, any items in the internal drive's grub will be added to the USB's grub.
You may do an update-grub later.

---

### Post by mark allyn on 2020-01-04
Mr/Ms Cameron:

Thanks for the very detailed response to my query.   It is much appreciated.   Owing to the presence this morning of my grandson ("the small tornado") I have not yet had a chance to follow your procedure.  Later today I should have the time.  I'll give you feedback. 

Regards,
Mark

---

### Post by yancek on 2020-01-04
The link below is also a fairly detailed explanation of dual booting windows 7 and Ubuntu which includes images of the various screens you will see in the different steps.  You don't need to have an internet connection or to select that option during the install, totally optional.  You can open a terminal in Ubuntu by holding down the Ctrl+Alt+t key simultaneously to run:  sudo fdisk -l or other command.  If you look at the installation process and images at the link below you will there is an Installation Type window (2nd page) which shows all this info.  You need to have a basic familiarity with Linux drive/partition naming conventions so if you are not familiar with that either do an online search or post back.

[https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653](https://www.lifewire.com/ultimate-windows-7-ubuntu-linux-dual-boot-guide-2200653)

---

### Post by mark allyn on 2020-01-05
Good morning CSCameron and Yancek:

CSCameron:  Later in the day I painstakingly followed a variation on your instructions and successfully (almost) installed ubuntu 18.04 on an external usb drive from a unetbootin stick.  I say almost because when I boot up from the new external drive, I can't get any networking functionality.  Everything else seems to work just fine.  But, without a network ubuntu is severely impaired.  

Yancek:  Thanks for your assistance.  If, by dual booting, you mean creating a separate linux partition on my hdd, that was something I was seeking to avoid by installing ubuntu on an external usb device.  Perhaps you mean something else?

Regards,
Mark

---

### Post by mark allyn on 2020-01-05
Hello OldFred,

Sorry I am slow to respond to your post.  As mentioned to CSCameron, I finally did get 18.04 installed on a flash drive using the "something else" control.  Where I ran into some difficulty was in partitioning the flash drive.  I kept misunderstanding how to use the "free space" control.  Eventually I stumbled on the correct method.  It was also then that I discovered--as you indicate in your post to me--that I also needed an EFI partition.  Once I did that, everything fell into place with just one exception--on which I'm still working.

Namely, when I boot up from the usb drive, I can't get networking to work.  I know WiFi is working because when I boot up in Win7 on the same machine, I have plenty of WiFi.  At the moment I am clueless.  If you have a thought, I'd be delighted.

Kind regards indeed,
Mark Allyn

---

### Post by oldfred on 2020-01-05
Did WiFi work on live installer?
Do you have wire connection for Ethernet, that makes it easier to update.

Some WiFi need drivers not included in live installer and need to be downloaded.

All my systems just work, or I mostly only use wired connections with my desktop systems. So I do not know wireless issue.
Post in the networking & Wireless forum.
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

But first run the script as suggested in sticky notes, and post it. If necessary run script & copy somewhere to another system that you can then upload it.
Before Posting Sticky Thread
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)

---

### Post by mark allyn on 2020-01-07
Hello OldFred,

Sorry I'm slow to respond.  Got hung up trying to fix a broken printer.  Anyway, the answer to your first question is that wireless worked just fine using the unetbootin stick.  I'm suspecting therefore that I may need indeed to download a driver.  From where, I'm not sure.

Regards,
Mark

---

### Post by oldfred on 2020-01-07
I would have thought that then the install would have included the driver.
Did you check the include proprietary drivers during install?
Or do you have UEFI Secure Boot on and then have you assign your own Secure Boot key as Ubuntu cannot sign other proprietary drivers.

Best to post in Wireless sub-forum as those in that forum know these type of issues better.
You may just need to add/change repository to flash drive installer & install from there. Or if you have wired connection then can install over Internet.

---

