---
title: "Pxe boot install issues. &quot;Check root=bootarg&quot;"
date: 2008-08-04
forum: Hardware
---

### Post by Vesperatus on 2008-08-04
Good afternoon,

I'm trying to take my first cup of ubuntu but for some reason, it's fighting with me. I made an overdose of mandriva and wanted to try ubuntu. 

Since my laptop ( Toshiba Sattelite M40 ) cd-rom is busted and it wont boot from usb, i deceided to pxe boot it like I did to install mandriva-2008. 

I downloaded this iso -> ubuntu-8.04.1-desktop-i386.iso, mounted it to my server hard-drive, configured tftpboot, dhcpd and received the pxe boot prompt and can select my boot option. Then, i can see the vmlinuz and initrd.gz loading and the boot process starts.

After a few seconds, it hangs for about 3 to 5 minutes and drops me to a shell with the following message : 

```
Check root= bootarg cat /proc/cmdline
or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exists. Dropping to a shell.
```

My pxelinux.cfg/default is the following :

```
label 1
kernel pxeboot-ubuntu/vmlinuz
append initrd=pxeboot-ubuntu/initrd.gz noapic acpi=off

```

Now what ?! :(

Hope someone can help me ;)

---

### Post by Vesperatus on 2008-08-05
I kept looking for a solution regarding that issue and saw a few erros related with previous kernels. One thing that caught my eye is the line :

```
ALERT! does not exists. Dropping to a shell.
```

Usually, in the previous errors I saw on differents forums, there is supposed to be something between "ALERT!" and "does not exists". 

Any suggestions on what I could do at the command line I receive right after to debug further ?

---

### Post by Vesperatus on 2008-09-08
Well, it's been a month now and I did not find anything on the internet. 

If anyone has a least some pointers to start finding the issue here, I would be very happy.

---

### Post by Randati on 2008-09-08
I have same problem on my desktop.
I changed my kernel line in menu.lst to (now you don't have to wait couple of minutes):
```
kernel /casper/vmlinuz root=UUID=A6F5-D423
```
("ls /dev/disk/by-uuid/ -al" to get right uuid.)

Then I created /etc/fstab and wrote this:
```
/dev/sda2	/	auto	defaults	1 1
proc		/proc	proc	defaults	0 0
```

And now I get this:
```
Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
Done.
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init

```

So, what's going on?

---

### Post by Randati on 2008-09-11
Almost forgot. I finally solved how to install Ubuntu without CD, USB or something like that.

**How to install Ubuntu from hard drive**
1. Create small (1 GB) FAT32 partition.
2. Extract LiveCD there.
(3. Install GRUB if you haven't got it.)
4. Add something like this to menu.lst:
```
title Install Ubuntu

root (hd0,1)

kernel (hd0,1)/casper/vmlinuz file=(hd0,1)/preseed/ubuntu.seed root=(hd0,1) boot=casper initrd=/casper/initrd.gz ramdisk_size=130048 root=/dev/ram rw quiet splash -- 

initrd=/casper/initrd.gz
```
5. Reboot and you should have "LiveHDD"!

This didn't work on my C drive which is NTFS, but if you have FAT32, you should try it.

---

