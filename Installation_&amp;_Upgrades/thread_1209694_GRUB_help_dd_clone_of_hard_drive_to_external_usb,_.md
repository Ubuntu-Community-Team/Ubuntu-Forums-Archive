---
title: "GRUB help: dd clone of hard drive to external usb, but can't boot windows"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by geologic on 2009-07-10
Did a dd backup from my internal sata hard drive to an external usb2 pata hard drive of identical sizes (320Gib). The cloning seems to have gone smoothly.

My old partition is something like this:
sda1 Winxp64 ntfs
sda2 fat32 (storage only)
sda3 Ubuntu 9.04 ext3
sda5 swap

When I boot off the new partition, Grub shows up just as it did before, and I can boot of the Ubuntu partition, but nothing happens when I try to boot off Windows.

I've removed the internal hard drive for trouble shooting, and like I said with the default grub parameters, in this case:
root (hd0,2)
Ubuntu boots fine.

For windows grub boots using (off the top of my head):
root (hd0,0)
savedefault
makeactive
chainloader +1

I don't get any kind of error messages when I boot windows.

Any ideas what I might need to do to get Windows to boot? I'm guessing it has to do with it being USB, and if it were possible to place the drive internally, it would boot fine. But that's not an option, and I'd like to have this drive working as an external backup, ready to go incase something happened to the internal.

Thanks

---

### Post by csabo2 on 2009-07-10
Greetings,
Haven't tested this myself, but here you go :)


[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)

---

### Post by unlimitedz on 2009-07-10
When you select "windows" from the Grub boot menu, Press F8 after you select it in the boot list.  Do you get the "Safe mode, Safe mode with networking, etc..." options?

---

### Post by geologic on 2009-07-10
> **unlimitedz said:**
> When you select "windows" from the Grub boot menu, Press F8 after you select it in the boot list.  Do you get the "Safe mode, Safe mode with networking, etc..." options?

Actually I get nothing, it's just a blank screen. I can still try pressing f8 to see if that triggers something.

---

### Post by csabo2 on 2009-07-10
> **geologic said:**
> Actually I get nothing, it's just a blank screen. I can still try pressing f8 to see if that triggers something.

Geo,
did you read the URL i posted?

---

### Post by geologic on 2009-07-10
> **csabo2 said:**
> Geo,
did you read the URL i posted?

Looking it over now. Thanks.
Maybe I'm a bit daft, but not quite getting how that will apply to my situation.

To clarify I don't seem to be having a problem booting ubuntu from usb -- which seems to be what the article is about -- rather its the windows portion.
But from that link, I found two other posts which might help, gonna read over them and try a few things.

[http://ubuntuforums.org/showthread.php?t=992426](http://ubuntuforums.org/showthread.php?t=992426)
[http://ubuntuforums.org/showthread.php?t=1056601](http://ubuntuforums.org/showthread.php?t=1056601)

---

### Post by unutbu on 2009-07-10
geologic, would you also run [boot_info_script]("http://ubuntuforums.org/showpost.php?p=6725571&postcount=3") and post the RESULTS.txt file? 

When you cloned the internal hard drive, did you clone the Windows partition as well?
Does this mean you have two Windows partitions (one on the internal and one on the external drive?) If so, which Windows partition are you trying to boot?

Also note: If you plan on having both drives connected at the same time, all partitions should have unique UUIDs. If you did a dd clone of the internal, the external drive will have exactly the same UUIDs as the internal. That could be messing things up because GRUB (and /etc/fstab) may be referring to partitions based on UUID.

The solution to the UUID problem is to assign new UUIDs to the cloned partitions (or edit /boot/grub/menu.lst to not use UUIDs). We can help you do that if it becomes clear that that is the problem. But first it would be helpful to see the RESULTS.txt file.

Also, if you plan on having both the internal and external drives connected at the same time, please run the boot_info_script with both drives connected -- it can affect how GRUB numbers the hard drives.

---

### Post by geologic on 2009-07-10
The entire drive was cloned, so yes this included two OSs: windows and ubuntu.

Point taken about the UUID, which had not occurred to me. However, in this case I am actually not trying to boot with the internal hard drive attached. I have physically removed the internal hard drive, and am booting with only the external hard drive plugged in thru usb.

I'm in the middle of trying to get the system booting in ubuntu, so that I can run the script. Will post as soon as i have the results.

---

