---
title: "How to &quot;install&quot; 13.10 to USB"
date: 2014-01-21
forum: Hardware
---

### Post by mcflurry124 on 2014-01-21
I would like to install Ubuntu 13.10 to a 4GB USB drive so I can take Ubuntu and boot and use it on multiple computers. I do not, however, want to make just a bootable drive that simply wants to install it to another device, etc. I want to make a dedicated install on the USB as if it were a hard drive. I know there is a way to do it inside of the installer, but I am not tech savvy enough to know how to do it correctly. Help going through this would be much appreciated.

---

### Post by oldfred on 2014-01-21
You need 8GB flash drive as a minimum for full install.

       Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

 With grub2 persistent C.S.Cameron 12.04
[http://ubuntuforums.org/showthread.php?t=2128205](http://ubuntuforums.org/showthread.php?t=2128205)
[http://ubuntuforums.org/showthread.php?t=2042965](http://ubuntuforums.org/showthread.php?t=2042965)

      
 [https://help.ubuntu.com/community/LiveCD/Persistence](https://help.ubuntu.com/community/LiveCD/Persistence)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by ajgreeny on 2014-01-21
4GB is not large enough, you need more than that for a full installation; 8GB minimum.

You then need to use the option of "Something Else" at the installation stage, choose the USB drive you want to use and then also make sure that grub is installed to the root of that drive, ie /dev/sdb, or whatever the drive device name is.  DO NOT put grub on a partition, always put it on the root of any device.  Then continue in the usual way.

---

### Post by mcflurry124 on 2014-01-21
Thank you oldfred and ajgreeny, you both helped a lot. I have another flash drive I can use, which is an 8gb that I'll use for now, but I think a friend will let me use a bigger one later. I read the third link posted by oldfred and I believe that will help me through the install process. again, thank you.

---

### Post by oldfred on 2014-01-22
For full install is really is just like any install to a second drive. You have to use Something else or manual install and create / (root) partition, format as ext4 and tell it to mount / as /.  Later we will change the ext4 to not use journal to reduce writes. Ext4 is better than ext2.
And on partition screen at bottom is the combo box on where to install grub2 boot loader. You must specify the drive that is the flash drive, not default sda. Attached from my install, but it was to sdc and combo box has not been changed from default yet.

       Full install - C.S.Cameron post #2
[http://ubuntuforums.org/showthread.php?t=2116798](http://ubuntuforums.org/showthread.php?t=2116798)
Full install of 12.04 to 64GB USB device C.S.Cameron post #3
[http://ubuntuforums.org/showthread.php?t=2092077](http://ubuntuforums.org/showthread.php?t=2092077)
Full install of 12.04 to USB device C.S.Cameron post #5
[http://ubuntuforums.org/showthread.php?t=2060493](http://ubuntuforums.org/showthread.php?t=2060493)

 With SSD or Flash (trim does not work on flash) drives, Use ext4 without journal:
sudo tune2fs -O ^has_journal /dev/sda1
sudo tune2fs -o discard /dev/sda1
No swap or set swapiness or install 'Dynamic Swap Space Manager' from the Ubuntu Software Center
After installing, change the fstab so that everything gets mounted with noatime.

---

### Post by sudodus on 2014-01-22
For a full install it is important to have a fast USB pendrive, otherwise the system will be quite slow. I have just published some data about pendrives. See this [link to USB 2 and USB 3 speed tests for installers]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085") and [this link to a bootability test]("http://ubuntuforums.org/showthread.php?t=2196858&p=12907221#post12907221").

---

