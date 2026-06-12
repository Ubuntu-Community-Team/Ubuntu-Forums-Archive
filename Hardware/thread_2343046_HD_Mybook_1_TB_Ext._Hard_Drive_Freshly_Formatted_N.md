---
title: "HD Mybook 1 TB Ext. Hard Drive Freshly Formatted NTFS Not Recognized by anything"
date: 2016-11-12
forum: Hardware
---

### Post by yarddogg772 on 2016-11-12
I really pulled a stupid this time. I have a HD Mybook 1 TB External Hard drive that I use for storage. For some reason I got it in my head that I needed to do some "maintenance" on it. It was working just fine before I broke what wasn't broken. I was using windows 8.1 when I decided I would reformat the hard drive. I copied all the files on it over to my laptop, then using windows 8.1 I completely formated the hard drive. It is formatted using NTFS. I was in a hurry that day for whatever reason, and I never installed any firmware back onto it to make it useable. I then copied all the files back from my laptop to the hard drive. Ever since then, this hard drive is not recognized by anything. Windows noticed when I plugged it in to USB, but would not mount it. I tried all the typical windows methods of mounting it to no avail. Since then I've also wiped windows 8.1 cause I hate it, and I've installed Xubuntu on my laptop. I had already tried to mount the disk on my tower with Xubuntu and had no luck so wiping windows and installing Xubuntu on my laptop is really not a concern to me.

Onto the subject. I have tried every typical suggested method of mounting this stubborn dumb device that I can find on the web but there seems to be no help because this hard drive is basically a blank without any firmware to utilize by conventional methods. Gparted does not see it, NTFS-3G does not see it, Thunar does not see it. I ran the command sudo fdisk -l, it is not listed, I tired lsusb, it is not listed. I ran the command sudo dmesg and I could see when I plug the device in but it says, 

[ 4470.045196] usb 5-1: new full-speed USB device number 18 using xhci_hcd
[ 4470.045570] usb 5-1: Device not responding to setup address.
[ 4470.249559] usb 5-1: Device not responding to setup address.
[ 4470.453163] usb 5-1: device not accepting address 18, error -71
[ 4470.453226] usb usb5-port1: unable to enumerate USB device


This is the only info of the hard drives existence. Before you ask, the hard drive works great, the USB cable is in good shape, the USB ports work fine with all other devices, and it was all working fine before I killed it. Right now I'm trying to recover the files from it, then I might Bomb it and format the hard drive to something useable for Linux. This drive is basically a blank page except for the files on it that I want to recover. If I can just get it mounted I could extract the files and format it from there, any suggestions?

---

### Post by oldfred on 2016-11-12
Windows 8 or later uses fast start up or always on hibernation. And that leaves every NTFS partition mounted when you shutdown Windows and the Linux NTFS driver cannot see it. You have to turn off fast start up in Windows and correctly unmount it before removing it from USB port. I know now difficult with Windows gone.

You should not need any extra drivers. That may have been if you used proprietary formats or partitioning with Windows as many vendors seem to do that.
And that may be the entire issue. You have a proprietary formatted hard drive that only works with Windows and that vendors utilities.

[http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html](http://nixliving.blogspot.com/2010/01/enjoy-your-wd-my-book-1tb-drive-no-more.html)

---

### Post by yarddogg772 on 2016-11-12
I've read that article, but I don't think it will help. He is talking about a command that will bypass the smartware preinstalled on the my book. This Mybook has no smartware whatsoever. Even before I formatted it this last time, there was no firmware on it. I had already wiped the smartware from it so I could use it between linux and windows. Even when it was working, if I opened it in windows, I could see all the files linux had put on it to make it work. All I can say, is that this hard drive is blank formatted as NTFS. There is nothing to make it run. I need to somehow install the directories to make it useable again. I don't mind reformatting it to fat 32 but I want to get the files off of it first.

---

### Post by yarddogg772 on 2016-11-12
I accidentally fixed it. I was reading that it could be a bios setting problem. My computer uses secureboot. I had secureboot disabled in order to use Android x86 on a virtual machine because secure boot doesn't like virtual machines. I did not however notice the option to delete secureboot certificates. I deleted the secureboot saved content, set my bios back to original, then rebooted. I unplugged the power from the HD hard drive but left the usb plugged in, powered it back up, then the system detected it. I can see all the files now. I knew it was something dumb because like I stated, there was already no firmware on it. Funny thing is, I had tried unplugging the power to the wd hard drive, and unplugging the power and even removing the battery from the laptop when I was using windows, and non of it worked. I can't remember if I had tried those things with the new Xubuntu install, so now I don't know if it was as simple as powering down the device, or if it was something to do with the bios, and maybe secureboot. It's fixed now and that's what matters. This makes me wonder now if secureboot was preventing me from running Android X86 properly, as I am still unable to launch google store games, particularly by Gameloft games.

---

### Post by oldfred on 2016-11-12
It was probably more the full cold boot. I unmount flash drives and have had issues getting that flash drive to show again. Once unmounted it sometimes seems to want to stay unmounted.

But Secure boot issues may be related to booting any other system. Do not know about Android and even how that works.
I keep secure boot off for now. Someday in future may need to have it but not now.

---

