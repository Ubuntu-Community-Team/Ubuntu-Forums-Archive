---
title: "Hard drive mount issues."
date: 2013-01-12
forum: Hardware
---

### Post by Lost Ninja on 2013-01-12
A little bit of a linux neophyte been at it for a long time but the last few months have been the first time I've used it seriously.

I have a fairly new (to me) PC with several hard drives. These drives comprise a 160Gb boot drive which contains a Win 7 boot partition (plus the 100Mb partition that windows needs) /sda1 /sda2. A linux swap partion (/sda5) and my linux partition (/sda6). No idea where /sda4 went.

I then have two further HDDs and this is where my issues start. The large is linux_store, I keep my documents and games on this and it is supposed to mount into /media/linux_store. I have the /etc/fstab set up like so:
```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=8d209dec-55fa-4ca4-a526-94f3033a594f /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=1eb605d3-02d7-4b53-ad6d-f8af93f18c48 none            swap    sw              0       0
# Linux Store
uuid=29678c28-0f8a-4cdf-a57d-f1d17d2a6e10 /media/linux_store ext4 defaults 0 0
# Windows Store
uuid=790B86C54DB0FF37 /media/windows_store ntfs defaults 0 0
```

Both the windows_store & linux_store are visible when the PC is booted and I can use/create/read files on both. However when I boot I get an error about there being an error mount linux_store (I'd guess the same for windows_store) and get the option to (S)kip or (M)anually change something.

If I look into the /media/ directory as root (sudo dolphin) I get presented with other mount points after have physically clicked on the drives in the devices section of dolphin.

However I want the drives to mount on boot so files that I use from them (specifically linux_store) are available without having to open and close things to get them seen again.

I am unsure how to proceed.

I also have an extra Home folder present in Dolphin when I enter as my normal user (ie not as Root) which appears linked to /root (but cannot open), if I delete this (remove link?) it reappears after my next boot.

edit: In case it will help:
```
/dev/sda1: LABEL="System Reserved" UUID="2E7AAAF07AAAB44D" TYPE="ntfs" 
/dev/sda2: UUID="426AB7F26AB7E139" TYPE="ntfs" 
/dev/sda5: UUID="1eb605d3-02d7-4b53-ad6d-f8af93f18c48" TYPE="swap" 
/dev/sda6: UUID="8d209dec-55fa-4ca4-a526-94f3033a594f" TYPE="ext4" 
/dev/sdb1: LABEL="linux_store" UUID="29678c28-0f8a-4cdf-a57d-f1d17d2a6e10" TYPE="ext4" 
/dev/sdc1: LABEL="win_store" UUID="790B86C54DB0FF37" TYPE="ntfs" 

```

---

### Post by ahallubuntu on 2013-01-12
Don't use /media to mount drives with fstab.  Use the /mnt folder instead.  /media should be reserved for Nautilus mounting media.  For example, use sudo to create a /mnt/linux-store directory, then mount that drive/partition there using fstab.

After you've edited fstab, use this command to test its syntax and mount all partitions in it:

```
sudo mount -a
```

It should return nothing after you hit enter if all is well.

If you get an error from that, then fix the problem in your fstab file and try again.  Once it's clean, you shouldn't have any more boot issues.

---

### Post by Lost Ninja on 2013-01-12
Okay it seems that the UUID I provided were wrong, when I retried with the /dev/sdb1 (etc) it works fine. What is the likely reason that the UUIDs supplied (from blkid) would be incorrect? I just copy/pasted them from the terminal.

Also with the /etc/fstab now working is there any need to sort out why the UUIDs don't work?

---

