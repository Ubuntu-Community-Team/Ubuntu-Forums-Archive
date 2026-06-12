---
title: "grub 2 question"
date: 2009-11-04
forum: Installation &amp; Upgrades
---

### Post by ratcheer on 2009-11-04
I am reading that a lot of people are upgrading to grub2 after upgrading to 9.10 and that it is solving many of their problems.

I upgraded to 9.10 and had several minor problems which, I think, are all fixed, now. I am booting to the correct kernel, as shown by "uname -r". So, should I do the grub2 upgrade, or just leave well enough alone?

Or, is there a way to tell if, somehow, I already installed grub2 in the Ubuntu upgrade process?

Thanks,
Tim

---

### Post by ratcheer on 2009-11-04
Never mind:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

Short answer - I need to perform the upgrade of grub, myself.

Tim

---

### Post by ratcheer on 2009-11-04
It never fails. I upgraded grub to grub2 and now I can no longer boot my Ubuntu machine. It reports Stage 1.5, then fails with "Error 15".

I'm off to do more research. Any help will be appreciated.

Thanks,
Tim

---

### Post by ratcheer on 2009-11-04
All I'm coming up with is to boot the machine to a live CD and repairing it from there. Complex, but should be doable.

[https://wiki.ubuntu.com/Grub2#Error+15+-+File+not+found](https://wiki.ubuntu.com/Grub2#Error+15+-+File+not+found)

Tim

---

### Post by drs305 on 2009-11-04
> **ratcheer said:**
> It never fails. I upgraded grub to grub2 and now I can no longer boot my Ubuntu machine. It reports Stage 1.5, then fails with "Error 15".

I'm off to do more research. Any help will be appreciated.

Thanks,
Tim

If it's still reporting stage 1.5 then you haven't completed the upgrade. The link you went to (GRUB2) should give you help on 1) booting from the grub or grub-rescue prompt or 2) reinstalling GRUB 2 if that becomes necessary.

---

### Post by ratcheer on 2009-11-04
Thanks. But, I do not get to a grub or grub-rescue prompt. Everything stops with the Error 15.

I see my error, now, but it is too late to do anything about it. When upgrade-from-grub-legacy showed me the list of possible boot devices, I only had one, so I assumed it was selected and continued. However, the best documentation says that you MUST type the spacebar to select an entry before continuing. I am apparently not the only person to miss this requirement, because a Google search shows people with the same problem, all over the place.

I am following the prescription to reinstall grub2 using a LiveCD.

Tim

---

### Post by wkulecz on 2009-11-04
If it ain't broke, don't fix it.

If grub boots your system, what does grub2 bring to the party?

You need grub2 if you install to ext4, other than than, I don't see any benefit, unless maybe it supports RAID5 booting.

--wally.

---

### Post by ratcheer on 2009-11-04
> **wkulecz said:**
> If it ain't broke, don't fix it.

If grub boots your system, what does grub2 bring to the party?

You need grub2 if you install to ext4, other than than, I don't see any benefit, unless maybe it supports RAID5 booting.

--wally.

I agree. I wish I hadn't decided to mess with it. But, again, it is too late now.

Tim

---

### Post by ratcheer on 2009-11-04
> **ratcheer said:**
> All I'm coming up with is to boot the machine to a live CD and repairing it from there. Complex, but should be doable.

[https://wiki.ubuntu.com/Grub2#Error+15+-+File+not+found](https://wiki.ubuntu.com/Grub2#Error+15+-+File+not+found)


I am having no luck with this procedure. It seems to mount my root partition, successfully. But then, when I try to mount the boot partition, it says it is a swap partition (which is true) and refuses to mount it. And when I try to remap the other partitions, the command seems to succeed, but when I do the chroot, they are not available, so it cannot find the dpkg-reconfigure command.

I am screwed.

Tim

---

### Post by Merovius on 2009-11-04
I had this error after a clean install of Karmic. I was only shown one of my sata drives during the install. It was the one I wanted Ubuntu on so I went ahead and installed. Grub2 was installed to this partition when previous installs had put it on the drive with Windows on it (that I could not see or was not showing up during the install.) When I rebooted and took out the install CD I had error 15. I figured out after a bit that in my bios it was set to boot first from the DVD drive and second from the Windows drive. (I could only set 2 possible boot choices.) When I changed the boot order to DVD then Ubuntu drive everything started to work. Grub2 loads and shows me my Ubuntu install and my Windows install and all is well.

Might want to check your boot order. Just a thought.

---

### Post by Merovius on 2009-11-04
Forgot to mention that after some reading I came to the conclusion that the Karmic installer or partitioner or Grub installer (not sure which) does not see all of the partitions on the system and can do some weird stuff during install.

This is the first Ubuntu install that I could not see my Windows install in the partitioning stage. I made the mistake and thought Grub would be installed to the first drives first partition. (as it always had before) I was wrong.

---

### Post by drs305 on 2009-11-04
> **ratcheer said:**
> **But then, when I try to mount the boot partition, it says it is a swap partition** (which is true) and refuses to mount it. And when I try to remap the other partitions, the command seems to succeed, but when I do the chroot, they are not available, so it cannot find the dpkg-reconfigure command.Tim

Can you explain this? A boot partition shouldn't be a swap partition. Do you have a separate /boot partition? Also, all you do prior to the chroot is mount the partition(s) and /dev. Perhaps this link presents it a little differently:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

---

### Post by ratcheer on 2009-11-04
Final update for the evening. I have had it, I'm going to bed.

I finally got the boot partition mounted with "sudo mount -t tmpfs /dev/sda1".

But, while the remap command ("sudo mount --bind /dev /mnt/dev") appears to execute, successfully, it apparently has no real effect. So, after running "sudo chroot /mnt", it cannot find the commands needed to fix or reinstall grub-pc.

Tim

---

### Post by ratcheer on 2009-11-04
> **drs305 said:**
> Can you explain this? A boot partition shouldn't be a swap partition. Do you have a separate /boot partition? Also, all you do prior to the chroot is mount the partition(s) and /dev. Perhaps this link presents it a little differently:

[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")

When I do the "sudo fdisk -l" command at the very beginning of the procedure, it shows that the Boot partition is /dev/sda1, which is the "Swap / Solaris" partition.

Thanks.

Tim

---

### Post by drs305 on 2009-11-04
> **ratcheer said:**
> When I do the "sudo fdisk -l" command at the very beginning of the procedure, it shows that the Boot partition is /dev/sda1, which is the "Swap / Solaris" partition.

Hope you sleep well. I think you may be mixing a "bootable" partition with a /boot partition. A partition may have an asterisk * next to it, indicating it is bootable. That is not the same a /boot partition. A /boot partition is a separate partition in which your kernels and, normally, your Grub configuration files are stored (in a subfolder). Most users don't have a separate /boot partition - you would have had to specially designate one during the installation.


>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1959    15735636   83  Linux
/dev/sda5           10403       10925     4200966   82  Linux swap / Solaris
In my case, sda1 is *bootable*, but it is not the /boot partition. I know it says "Boot", but this just adds a bit of confusion.  sda5 is my swap partition.

With this in mind, revisit the LiveCD installation procedures. Assuming you *do not* have a separate /boot partition, try running through the commands again.

Note: The Grub 2 wiki is about to be deprecated to the Ubuntu help.ubuntu.com Grub2 documentation. The information may be located in a different part of the document but it will still be there.

---

### Post by Merovius on 2009-11-05
I myself had separate bootable /boot partitions. When I did my install Grub2 ended up on the same drive/partition as Ubuntu. This was not bootable as it was not set as active or bootable and was not set to be booted from in the bios.

An upgrade did not cause the same problem. A clean install which did not recognize all the partitions did. I found Grub2 was not always doing what I thought it would. I ended up with error 15 because of it. Once I set the partition as active (the previous post reminded me of that) and reset the bios boot order all was fine.

---

### Post by ratcheer on 2009-11-05
> **drs305 said:**
> Hope you sleep well. I think you may be mixing a "bootable" partition with a /boot partition. 

Thank you. Yes, I was confused about that. I will re-try the procedures without trying to mount that.

I have worked with UNIX systems, professionally, for many years, but never as a system administrator. Now that I am having to do these things for myself, I have much more appreciation for the complexities they deal with.

Thanks very much,
Tim

---

### Post by ratcheer on 2009-11-05
It didn't help. I have managed to log in to ubuntuforums from the LiveCD-booted Ubuntu PC. Here is the log of what is happening:

```

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdbc9dbc9

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         122      979933+  82  Linux swap / Solaris
/dev/sda2             123        2554    19535040    5  Extended
/dev/sda3            2555        6201    29294527+  83  Linux
/dev/sda4            6202        9729    28338660   83  Linux
/dev/sda5             123        2554    19535008+  83  Linux
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /mnt
ubuntu@ubuntu:~$ sudo mount --bind /dev/ /mnt/dev
ubuntu@ubuntu:~$ sudo chroot /mnt
bash: groups: command not found
root@ubuntu:/# grub-install /dev/sda
bash: grub-install: command not found 
root@ubuntu:/# sudo grub-install /dev/sda
bash: sudo: command not found
root@ubuntu:/# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              19G  1.2G   17G   7% /
none                   19G  1.2G   17G   7% /sys
udev                  502M  152K  502M   1% /dev
none                  502M  152K  502M   1% /dev/pts
none                  502M  152K  502M   1% /dev/shm
none                   19G  1.2G   17G   7% /var/run
none                   19G  1.2G   17G   7% /var/lock
none                   19G  1.2G   17G   7% /lib/init/rw
/dev/sda4              19G  1.2G   17G   7% /usr
df: `/proc/sys/fs/binfmt_misc': No such file or directory

```When I am chroot'ed, it cannot find the commands I need to install grub. I believe I have followed the documented procedure to the letter.

So, I still need help.

Tim

---

### Post by ratcheer on 2009-11-05
Ta da! I think I have figured it out. The problem is that I installed with /usr in its own partition. Since I wasn't mounting it (because the procedures do not mention such a situation), after chroot'ing the system could not find anything stored under /usr.

```

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# which grub-install
/usr/sbin/grub-install
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda


```

I will finish up the procedure and reboot. Be right back with results.

Tim

---

### Post by ratcheer on 2009-11-05
And my system is up and I'm back in business!

This was a major aggravation, but I caused it myself and I learned a lot in fixing it.

Thanks again to everyone who replied, especially **drs305**.

Tim

---

### Post by Jeffrey Green on 2009-11-05
> **ratcheer said:**
> Ta da! I think I have figured it out. The problem is that I installed with /usr in its own partition. Since I wasn't mounting it (because the procedures do not mention such a situation), after chroot'ing the system could not find anything stored under /usr.

```

ubuntu@ubuntu:~$ sudo mount /dev/sda4 /mnt/usr
ubuntu@ubuntu:~$ sudo chroot /mnt
root@ubuntu:/# which grub-install
/usr/sbin/grub-install
root@ubuntu:/# grub-install /dev/sda
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)    /dev/sda


```I will finish up the procedure and reboot. Be right back with results.

Tim

Now it's my turn. Not the same problem but similar. But don't really know if reinstalling GRUB2 will help me. When I installed Ubuntu 9.10, I also had Windows Vista so I wanted to do a dual boot install. I installed the Ubuntu to a USB external HDD. Long story short, I no sooner finished the install when, after rebooting, I was presented with the Grub rescue mode. So I think Grub2 is correctly installed. The real problem is when I follow the Ubuntu help at [https://help.ubuntu.com/community/Grub2#Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Rescue%20Mode), I get to a point where I realize that no matter what I do, it will be to no avail unless I can get GRUB2 to find what it's looking for.  > If GRUB 2 fails to find a useable *grub.cfg* and is unable to transfer control to a kernel it will drop to a *grub-rescue>* prompt., i.e.  File not found and the grub-rescue prompt.

Question relating to proper forum etiquette. :rolleyes: This is not technically an upgrade to Grub2 question. ;) Should I start a new thread for this topic? :confused:
OK, sock it to me.  A forum newbie, Jeffrey Green

---

### Post by ratcheer on 2009-11-05
As your problem seems to be quite different, it would probably be best to either create a new thread or find an existing thread with a very similar problem. But I'm not going to jump up and down and bite your head off.

Tim

---

### Post by Tompalaz on 2010-02-13
My friend have a similar problem as [http://ubuntuforums.org/showthread.php?t=1320046](http://ubuntuforums.org/showthread.php?t=1320046)

My friend has a external disk with Karmic on it. However it doesn't seems like it want to boot. Grub reports error 15.

His internal disk with Windows is encrypted, so if we/I fail and write grub to the internal disk he will loose his data.

I don't have access to the computer but fdisk give something like:
Internal:
sda (Encrypted Windows)

External disk:
sdb (FAT)
sdb5 (Linux)

And if I'm right, grub2 is supposed to be installed to sdb?
When we tried that, grub sais error 15.

So, I turn to you guys.

---

