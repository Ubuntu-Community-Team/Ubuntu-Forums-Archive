---
title: "External Hard Drive Won't Boot"
date: 2012-10-23
forum: Hardware
---

### Post by Rhianon on 2012-10-23
Hi there, I'm brand new to Ubuntu and am having issues installing to an external hard drive.  I have a Dell Inspiron 1525 with a busted internal HD. So, I installed 12.04 onto a WD passport with 160 Gigs, hoping to run it off that instead. Install went fine and when I was prompted to restart the computer it booted up perfectly. However, minutes later, it would freeze. I then shut down the laptop and restart only to get a message telling me there are no bootable devices. Boot Menu is set with USB devices as priority. Even though it won't boot from external, when booting from a live CD all the files on the hard drive appear to be intact. Also, the device won't boot on any computer, not just the Inspiron. If anyone can help I'd be extremely thankful!

---

### Post by oldfred on 2012-10-23
Welcome to the forums.

From liveCD with USB drive plugged in. Lets see what configuration looks like. Also what video card/chip do you have.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Rhianon on 2012-10-23
Here's my video card, more specific system info, and how ubuntu automatically partitioned my drive. I did it manually a few times but was concerned that was the reason it wasn't booting so I left it to it's own devices. If you need anything else let me know. I appreciate your response! Also I'm going to try the boot repair right now and will get back with that link. Thanks again.

---

### Post by oldfred on 2012-10-23
It looks like you are running the 32bit version on a 64bit system. You may be better with the 64 bit version since you have 4GB of RAM.

Linus does not like PAE or 32 bit.
[http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/](http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/)

[http://ubuntuforums.org/showthread.php?t=2028717](http://ubuntuforums.org/showthread.php?t=2028717)
Ubuntu 12.10: 32-bit vs. 64-bit Linux Performance
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1210_3264&num=1)
Assuming your hardware is x86_64 capable (basically any modern Intel/AMD CPU) and have at least 2GB of RAM, you really should be running the 64-bit version.
Essentially says if you can use the 64bit kernel you should.April 2011
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

If you do elect to reinstall I normally suggest this:

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by Rhianon on 2012-10-23
[http://http://paste.ubuntu.com/1300964/](http://http://paste.ubuntu.com/1300964/)

Just ran the boot repair and that's the link it gave me. While it didn't fix the problem, GRUB now shows up every time I boot as opposed to very rarely as it did before.  I think I should also mention that the only time the drive doesn't work is from a cold boot. If i simply restart, it boots fine. 

Thanks for all your help. I'm downloading the 64 bit version of Ubuntu right now, I'll let you know if that helps. In the meantime I'm going to reinstall with the drive configuration you provided.

Also, after running boot repair it said something along the lines of "Your boot files are too far from the beginning of the drive for BIOS to see" and then told me to add a 200 Megabyte "/boot" partition. Is this something you would recommend? I've heard it's unnecessary, especially for users like me who are not dual-booting.

Again, thank you so much for helping me with this!

---

### Post by oldfred on 2012-10-23
If you do the smaller system partition and separate larger /home then that also keeps all the boot files close to the beginning of the drive, actually all the system then is close together and nearer the beginning of the drive. Then you do not need the separate /boot. It has been an issue with very large over 500GB drives, but the only confirmed work around seems to be to have boot files in the first 100GB of drive. I still think it may be BIOS & grub issues combined as some users have no issue.

To be able to create your own partitions, you can either partition in advance with gparted from liveCD/USB and use Something else to choose which partition is /home, which is / (root) and what formats. If you already have a swap partition,  it finds that automatically. You can essentially do the same using Something Else during install, but create, format & choose use of each partition.

If you are able to get to grub menu, then it may be video issue, but generally the Intel drivers just work.

---

### Post by Rhianon on 2012-10-24
64 bit fixed the problem!! Thank you so much for putting in the time to help me fix this! Boots fine every time!

---

### Post by oldfred on 2012-10-24
Just changing to 64 bit does not always help, but reconfiguration may. 

Glad you resolved the issues.

---

