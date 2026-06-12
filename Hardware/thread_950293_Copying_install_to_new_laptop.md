---
title: "Copying install to new laptop"
date: 2008-10-17
forum: Hardware
---

### Post by hoborocket on 2008-10-17
I currently have a Thinkpad that's on its last legs. I'm getting a new HP tablet laptop tomorrow, and I want to clone over the install of HH from the old to the new, on its own partition so I can dual vista and ubuntu.

I'm thinking I should use livecd + gparted to shrink the existing Vista partition and make an empty ext3 partition + swap + whatever else the thinkpad has on it, but I'm not sure how to copy the files over without mucking up the permissions and stuff. I don't have an external enclosure, so my best option will be tossing the Thinkpad drive in another tower running a livecd and share the drive over the network. Can that work?

I expect to have to iron out some kinks related to dropping an OS from one set of hardware to another, but I've been told it can be managed.

Late edit: This just occured to me after posting this. New laptop's 64 bit, old was 32 bit. Is that going to kill this whole idea? If so, what's my best bet for preserving my settings and programs?

---

### Post by kpkeerthi on 2008-10-17
32-bit should work just fine on your 64-bit hardware.

Here are the steps I did when I moved the install from my laptop to another person's:

My partition layout in the old laptop looked like this:
/dev/hda1
/dev/hda2
/dev/hda3

Boot with Ubuntu Live Cd and create the partition layout, using gparted, in the new laptop using Ubuntu Live CD. The new layout is as below:
/dev/sda1 for root 
/dev/sda2 for home
/dev/sda3 for Swap

While in the Live mode, mount /dev/sda1 as /New and mount and mount /dev/hda1 as /Old. 

Sync both the folders using rsync:
sudo rsync -a /Old /New
	The -a switch preserves permissions.

Edit /New/etc/fstab and change it match the new partition layout (rename hda to sda)

Unmount /New and /Old and [install GRUB]("http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/") to the MBR of your new drive

* Once everything goes fine, verify blacklisted modules. unblacklist them if required as the hardware might be different. Additional modules required on the new laptop should be autoloaded as it is handled by udev.

---

### Post by hoborocket on 2008-10-17
Is it possible to mount the old drive over the network like that? I don't have an enclosure, sadly, just a drive adapter to toss it in a desktop.

---

### Post by kpkeerthi on 2008-10-17
You can rsync over network.

[Links]("http://www.google.com/search?q=rsync+over+network")

---

