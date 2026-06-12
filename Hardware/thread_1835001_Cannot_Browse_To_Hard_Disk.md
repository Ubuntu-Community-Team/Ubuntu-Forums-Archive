---
title: "Cannot Browse To Hard Disk"
date: 2011-08-28
forum: Hardware
---

### Post by johny why on 2011-08-28
hi,

linux noob, trying to mkdir on my hard disk, but cannot find the hard disk in mnt or in dev. 

i see a whole bunch of sda's in terminal window when i dir in /dev, and Disk Utility says the hard disk is /dev/sda and the partition is /dev/sda1. The Disk Util also displays an "Unmount" button. 

but i cannot cd to any of the sda's, and they are not visible in the window browser.

incidentally, cannot mount or browse to the CD drive, although it also is displayed in the Disk Utility.

it's a Dell Latitude

help!
thanks

---

### Post by ktmom on 2011-08-28
I'm thinking you are trying to do things the hard way ;-)

I am assuming you are booted into Ubuntu and at the desktop, is that correct?

Have you tried going to the menu "Places" and clicking on "Home Folder"?  That will open a file browser (like windows explorer) at your home folder.  Most user folder would then be created under this point.  In the file browser menu "File", there is an option to "create folder".  It will create a directory and then allow you to name it.

If you try this in the terminal window (the "command line"), once the terminal is open, you are typically in the logged on user's home directory.  To get to somewhere else, you would cd to the path such as: cd /home/ktmom/Desktop/pictures; or the like.

It kinda sounds like you may be doing this alreay, but are either unclear where you are in the tree, or are trying to get to a second hard drive.  Is that the case?

---

### Post by johny why on 2011-08-28
hi

i'm trying to create a folder on the hd for the process here:
[http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__p__585740612#entry585740612](http://www.neowin.net/forum/topic/305843-use-lilo-or-grub-to-mount-and-boot-from-iso/page__p__585740612#entry585740612)

not sure how to proceed

thanks

---

### Post by ktmom on 2011-08-28
Do you have an ISO file that you want to run from disk already downloaded?  What these instructions are telling you to do is to create a folder where the ISO file can be mounted.  That is typically in the /mnt directory.  So their instructions are to use "LiveISO" as the folder name.  That means you have to use the command: sudo mkdir /mnt/LiveISO

sudo tells the system to use the full administrative permissions to create the folder.  If you try it as your user, you will get a error that permission is denied.

then they tell you to mount the ISO file (so you can copy the contents) and you will need to use the sudo command again.

Now comes where I think you are hung up at; you need to copy the contents of the ISO to the partition you made.  That is the disk you are trying to find.  When you made the partition, you should have seen something like sda3 (* see below) or something similar.  This is the partition identifier you would use in place of the hda4 they describe.  To make a folder on a partition it must be mounted giving the operating system access to it.

There is a program in the Ubuntu Software Center called: Disk Utility, Manage Drives and Media.  If you install this app and start it from the System -> Administration menu, you should be able to identify the Hard Drive partition you made and also mount the drive so you can create the folder.  The mount point (displayed in Disk Utility after mounting the drive) is what you need to substitute for the path "/mnt/hda4/KNOPPIX".  I expect it will look something like "/media/your-partition/KNOPPIX".

* as a side note - the hda vrs sda is the interface.  hda were the older IDE or parallel drives.  Most computers these days use serial drives or SATA.

---

### Post by johny why on 2011-08-28
i checked Disk Utility. The hard disk partition is sda1.

the instructions assume that sda1 will be inside my /mnt directory, don't they?

but it's not. it's not inside dev either.

when i enter ```
mkdir /mnt/sda1/puppy
``` or ```
sudo mkdir /mnt/sda1/puppy
``` i get:
```
mkdir: cannot create directory `/mnt/sda1/puppy': No such file or directory
```

---

### Post by ktmom on 2011-08-28
```
Here's how to boot a LiveCD from HD (using grub, Knoppix [or knoppix based LiveCD iso] and a Linux system):

Step 1
-create a mountpoint to mount the ISO with loopback:
mkdir /mnt/LiveISO

Step 2
-mount the image:
mount -t iso9660 -o loop,ro /DOWNLOADS/Knoppix-3.7-en.iso /mnt/LiveISO

Step 3
-create a directory on the device where you are going to boot from:
mkdir /mnt/hda4/KNOPPIX

Step 4
-copy the contents of the mounted image to that directory:
cp /mnt/LiveISO/KNOPPIX/* /mnt/hda4/KNOPPIX/

Step 5
-copy kernel and initrd files to yor boot device:
cp /mnt/LiveISO/boot/* /boot/

Step 6 (and beyond)
-edit the menu.list located in /boot/grub and add an entry like this to it:
{...clipped...}

```

No, the instructions assume the place you want to mount the ISO file you are trying to run from disk in the /mnt directory and you have ***already*** created a mount point and mounted the partition at /mnt/hda4/ and - in the case of step 3 - you are now adding a directory called KNOPPIX.

These instructions were not written for novices.  There is a bit of assumed *nix knowledge required to easily follow them.

Is sda1 mounted?  Have you looked at the mount point using Disk Utility?  If it's not mounted, you'll not be able to copy files (or create the directory to copy them to).  If it's not mounted, and you really, really want to do things from the command line, then you can make a directory in /mnt for your partition, then make a directory to hold your ISO files.

```
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
df -H
```

The df -H command will show you that sda1 is now mounted at /mnt/sda1. 

Now you can make your directory;
```
sudo mkdir /mnt/sda1/puppy
```

Why are you planning to run puppy from the HD?

---

### Post by johny why on 2011-08-28
thanks, that worked!

hm, but now i cannot find the menu.list file for grub. when i run grub from the terminal, i get "'grub' is not currently installed". same for lilo. 

i restarted, and i see the bootloader is gnu grub. now looking for puppy syntax for grub.cfg. 

i'm installing puppy to the hard drive, because this Dell Latitude won't boot off a usb, and the CD is not functioning.

---

### Post by ktmom on 2011-08-28
If you are using a newer Ubuntu, you don't have grub.  It's grub2.  Look in the [community help pages]("https://help.ubuntu.com/community") for grub2.

---

### Post by johny why on 2011-08-28
fantastic! i got puppy into the grub menu, with these codes:
[http://puppylinux.org/wikka/Puppy52LuciInstallFrugalHDD](http://puppylinux.org/wikka/Puppy52LuciInstallFrugalHDD)

i can at lease initiate the puppy boot. 

but now puppy is freezing in the middle of the boot, but that's an issue for a different thread:
[http://208.109.22.214/puppy/viewtopic.php?t=71184&sid=4cef6f403f2f7c4abd56af1b12181eb5](http://208.109.22.214/puppy/viewtopic.php?t=71184&sid=4cef6f403f2f7c4abd56af1b12181eb5)

thanks for your awesome help.

---

### Post by ktmom on 2011-08-28
Glad to have helped a bit.  Good luck with puppy.

Could you edit the title to indicate the thread is solved please.  Use the thread tools link at the top.

---

