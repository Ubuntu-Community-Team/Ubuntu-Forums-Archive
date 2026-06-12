---
title: "Grub Error 18 out of nowhere"
date: 2008-07-25
forum: Hardware
---

### Post by Neovos on 2008-07-25
Very peculiar problem. I performed a couple updates last night (don't remember which ones, nor did I bother to look) and the next time I rebooted, it gave me grub error 18. 

I believe that particular error is regarding where the boot info is on the disk. If it's past the 8gb mark or something, then bios can't see it. But the weird thing is that this is a brand new Asus M51sn laptop and Hardy installed first time flawlessly on it and has worked until now.So my guess is that as the drive has been filling up the data got moved past that 8bg point? 

Anyway that doesn't seem to be the problem anymore though. What I ran into is when I booted up the live disc, and made an attempt to copy my /boot file from the old drive (In the middle of making a /boot partition) it hung a bit, gave a bunch of errors saying it can't find the folder (even though it can mount ok, and gets recognized in fdisk -l, mount, and I can see it's properties, I just can't ever see its contents) then after like 5 minutes when I wasn't paying attention, displayed the folders contents:

```
ubuntu@ubuntu:~$ sudo mkdir /media/boot
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda3 /media/boot
ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda2 /media/ubuntu
ubuntu@ubuntu:~$ sudo cp -r /media/ubuntu/boot/* /media/boot/
cp: cannot stat `/media/ubuntu/boot/*': No such file or directory
ubuntu@ubuntu:~$ cd /media/ubuntu
ubuntu@ubuntu:/media/ubuntu$ ls
ls: cannot access initrd: No such file or directory
ls: cannot access lib: No such file or directory
ls: cannot access srv: No such file or directory
ls: cannot access boot: No such file or directory
ls: cannot access opt: No such file or directory
AdobeReader.desktop  dev     initrd.img      media  root  tmp      vmlinuz.old
bin                  etc     initrd.img.old  mnt    sbin  usr
boot                 home    lib             opt    srv   var
cdrom                initrd  lost+found      proc   sys   vmlinuz

```
It's boggling the mind. The last time I had something like this problem it was a hard drive failure on another computer and I had to loose all my data. So here are some questions:

1)Does anyone know any advanced mount options to change the max speed at which an os will read/write the drive? I'm thinking I might be able to get some data out of it if I can make entry to it "softer." Or just any compatibility mounting options from the terminal

2)Anyone else have an all of a sudden error 18 after updates in the past day or two?

3)Do I understand the grub error 18 correctly? Does a bios have problems if the boot is on a drive larger then 8gb, or if the boot is farther then 8gb from the start of the drive?

Oh and what I had setup before was a 5gb swap partition (sda1), then a 250 gb main partition with the boot on there(sda2) and it's always worked. Thats why I'm weary of it not being a simple fixable error 18 and being something worse....

---

### Post by Fondor1 on 2008-07-28
[http://ubuntuforums.org/showthread.php?t=870285](http://ubuntuforums.org/showthread.php?t=870285)

This thread has someone with the same issue, but I can't really be of any help unfortunately. :(

What version of Ubuntu are you running?

---

