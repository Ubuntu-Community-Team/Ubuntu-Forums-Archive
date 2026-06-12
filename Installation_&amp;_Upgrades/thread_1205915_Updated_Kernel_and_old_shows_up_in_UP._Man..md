---
title: "Updated Kernel and old shows up in UP. Man."
date: 2009-07-06
forum: Installation &amp; Upgrades
---

### Post by zoomy942 on 2009-07-06
So I updated to 2.6.30 kernel and it works great, but everytime i reboot my tablet PC, the update manager offers the older one as an update.  I attached a screenshot.  What can I do to prvent this?  I googled around and i didnt see anything about this.

---

### Post by ptn107 on 2009-07-06
You installed 2.6.30 but you also left the default Ubuntu kernel 2.6.28 installed, that's why it tells you there is an update to it.  FYI you can have many kernels installed independently of each-other.

You can either:
1) Update the older kernel keeping both 2.6.30 and the newer 2.6.28 around,
or
2) Remove the 2.6.28 kernel and leave 2.6.30 installed by itself (not smart).  Copy and paste the following in a terminal to remove the default kernel:
```
sudo aptitude purge linux-image-2.6.28-11-generic linux-headers-2.6.28-11 linux-headers-2.6.28-11-generic linux-restricted-modules-2.6.28-11-generic -y
```

Rule of thumb is to always leave at least one other working kernel in addition to the one you normally use.

---

### Post by raymondh on 2009-07-06
or install startupmanager (from synaptic or terminal) and use that GUI to set defaults (and others).  It also writes to the menu.lst.

---

### Post by Favux on 2009-07-06
I second startupmanager.

---

### Post by zoomy942 on 2009-07-06
so, this is something new.  i ran that terminal command and it still showed up (screenshot) so you guys are saying use startup manager.  will that make it so it doesnt want to update this?  and if i update it, will it somehow start using it?

I ask becasue my tablet was affected by the Intel Storage controller bug in that older kernel and thats why i was have file system corruption.

---

### Post by zoomy942 on 2009-07-06
so i tried startup manager and i didnt get too far.  and i went to remove the old kernels and i got this

---

### Post by zoomy942 on 2009-07-07
I'm wondering if i did something wrong when i installed the 2.6.30 kernel.  I googled that error i posted above this but it was too long of an error so i had a heck of a time finding useful results

---

### Post by zoomy942 on 2009-07-07
so i tried manually removing each one it says was there and got all this.

```
zimmerman@zimmerman-laptop:~$ sudo aptitude purge linux-image-2.6.28-13-generic linux-headers-2.6.28-13 linux-headers-2.6.28-13-generic linux-restricted-modules-2.6.28-11-generic -y
[sudo] password for zimmerman: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  linux-image-generic linux-restricted-modules-2.6.28-13-generic 
The following packages will be REMOVED:
  linux-image-2.6.28-13-generic{p} 
The following partially installed packages will be configured:
  linux-image-2.6.29-020629-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 112MB will be freed.
The following packages have unmet dependencies:
  linux-image-generic: Depends: linux-image-2.6.28-13-generic but it is not installable
  linux-restricted-modules-2.6.28-13-generic: Depends: linux-image-2.6.28-13-generic but it is not installable
The following actions will resolve these dependencies:

Remove the following packages:
linux-generic
linux-image-generic
linux-restricted-modules-2.6.28-13-generic
linux-restricted-modules-generic

Score is -34

Writing extended state information... Done
(Reading database ... 122329 files and directories currently installed.)
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
Removing linux-restricted-modules-2.6.28-13-generic ...
update-initramfs: Generating /boot/initrd.img-2.6.28-13-generic
Removing linux-image-generic ...
(Reading database ... 122260 files and directories currently installed.)
Removing linux-image-2.6.28-13-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.29-02062905-generic
Found kernel: /boot/vmlinuz-2.6.29-020629-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

Purging configuration files for linux-image-2.6.28-13-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.29-02062905-generic
Found kernel: /boot/vmlinuz-2.6.29-020629-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Setting up linux-image-2.6.29-020629-generic (2.6.29-020629) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing linux-image-2.6.29-020629-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29-020629-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done

Current status: 0 updates [-1].
zimmerman@zimmerman-laptop:~$ sudo aptitude purge linux-image-2.6.29-020629-generic linux-headers-2.6.29-020629 linux-headers-2.6.29-020629-generic linux-restricted-modules-2.6.28-11-generic -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  linux-image-2.6.29-020629-generic{ap} 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 90.4MB will be freed.
Writing extended state information... Done
(Reading database ... 119660 files and directories currently installed.)
Removing linux-image-2.6.29-020629-generic ...
dpkg (subprocess): unable to execute pre-removal script: Exec format error
dpkg: error processing linux-image-2.6.29-020629-generic (--purge):
 subprocess pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29-020629-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

zimmerman@zimmerman-laptop:~$ sudo aptitude purge linux-image-2.6.29-02062905-generic linux-headers-2.6.29-02062905 linux-headers-2.6.29-02062905-generic linux-restricted-modules-2.6.28-11-generic -y
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following packages will be REMOVED:
  linux-image-2.6.29-02062905-generic{p} 
The following partially installed packages will be configured:
  linux-image-2.6.29-020629-generic 
0 packages upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 92.8MB will be freed.
Writing extended state information... Done
(Reading database ... 119660 files and directories currently installed.)
Removing linux-image-2.6.29-02062905-generic ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/last-good-boot
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.29-020629-generic
Found kernel: /boot/memtest86+.bin
Replacing config file /var/run/grub/menu.lst with new version
Updating /boot/grub/menu.lst ... done

The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Purging configuration files for linux-image-2.6.29-02062905-generic ...
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.30-020630-generic
Found kernel: /boot/vmlinuz-2.6.29-020629-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

dpkg - warning: while removing linux-image-2.6.29-02062905-generic, directory `/lib/modules/2.6.29-02062905-generic' not empty so not removed.
Setting up linux-image-2.6.29-020629-generic (2.6.29-020629) ...
dpkg (subprocess): unable to execute post-installation script: Exec format error
dpkg: error processing linux-image-2.6.29-020629-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.29-020629-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

Current status: 25555 new [-1].
zimmerman@zimmerman-laptop:~$ 
```

---

### Post by zoomy942 on 2009-07-07
i thought maybe a fresh install and go straight to 2.6.30 kernel, but i dont want to mess with that if all that stuff is going to start erroring anyway.

---

### Post by zoomy942 on 2009-07-07
after some googling i found this too..

```
zimmerman@zimmerman-laptop:~$ dpkg --list 'linux-image*'
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  linux-image    <none>         (no description available)
un  linux-image-2. <none>         (no description available)
pn  linux-image-2. <none>         (no description available)
pn  linux-image-2. <none>         (no description available)
pF  linux-image-2. 2.6.29-020629  Linux kernel image for version 2.6.29 on x86
pn  linux-image-2. <none>         (no description available)
ii  linux-image-2. 2.6.30-020630  Linux kernel image for version 2.6.30 on x86
pn  linux-image-ge <none>         (no description available)
zimmerman@zimmerman-laptop:~$ 



```

---

