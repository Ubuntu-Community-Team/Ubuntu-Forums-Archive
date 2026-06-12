---
title: "Problem using Avast to scan NTFS Partition"
date: 2008-09-20
forum: General Help
---

### Post by hawkeye53 on 2008-09-20
Hi,

New to the forum and Ubuntu. I have a dual boot Ubuntu and XP. I am trying to use Avast to scan the NTFS partition. Do I first have to mount the NTFS partition or will Avast do that? If so, can someone point me to _simple_ instructions for that? I've seen and tried many sets of instructions, but they either don't work or I'm missing something on doing the mount. All help would be greatly appreciated. 

Hawkeye

---

### Post by prshah on 2008-09-20
> **hawkeye53 said:**
> 
I am trying to use Avast to scan the NTFS partition. Do I first have to mount the NTFS partition or will Avast do that? 


Your NTFS partition should already be accessible, look under "/media/" for a directory with the label of your NTFS partition. ie, if your NTFS partition label is "MAIN", it will be accessible under "/media/MAIN".

If you have to mount the partition manually, Here's an easy way: First, Open a terminal (Applications, Accessories, Terminal), then install pmount with the command```
sudo apt-get install pmount
```

Once installed, you can mount the NTFS partition with the command ```
pmount /dev/sda1
``` Replace /dev/sda1 with the partition device (ID) of the NTFS partition. If you don't know your NTFS partition device, give the command ```
sudo fdisk -l | grep -i ntfs
```

Now you can scan the NTFS partition by instructing Avast to check the /media/MAIN (whatever your partition is called).

If you have manually mounted the partition, don't forget to unmount it when done using / scanning it```
pumount /dev/sda1
```

---

### Post by hawkeye53 on 2008-09-20
Hi!

Thanks for taking time with this. I get an error. I pasted everything below, but the main point is that I get a

Error: device /dev/sda2 is not removable

I'd like to learn to mount the volume correctly, but now I'm wondering if I maybe don't need to mount the partition, but rather, I'm using avast incorrectly. Do you know how to scan an NTFS volume with avast?

Hawkeye

craig@craig-laptop:~$ sudo fdisk -l | grep -i ntfs
[sudo] password for craig: 
/dev/sda2   *           7        8844    70991235    7  HPFS/NTFS
/dev/sda5            8845        9481     5116671    7  HPFS/NTFS
craig@craig-laptop:~$ sudo apt-get install pmount
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-19-generic linux-headers-2.6.24-19
Use 'apt-get autoremove' to remove them.
Suggested packages:
  cryptsetup
The following NEW packages will be installed:
  pmount
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
Need to get 86.0kB of archives.
After this operation, 672kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe pmount 0.9.16-4 [86.0kB]
Fetched 86.0kB in 0s (89.1kB/s)
Selecting previously deselected package pmount.
(Reading database ... 116066 files and directories currently installed.)
Unpacking pmount (from .../pmount_0.9.16-4_i386.deb) ...
Setting up pmount (0.9.16-4) ...

craig@craig-laptop:~$ pmount /dev/sda2
Error: device /dev/sda2 is not removable
craig@craig-laptop:~$ pmount /dev/sda5
Error: device /dev/sda5 is not removable
craig@craig-laptop:~$

---

### Post by prshah on 2008-09-21
> **hawkeye53 said:**
> 
but the main point is that I get a
Error: device /dev/sda2 is not removable

I'd like to learn to mount the volume correctly, 


Sorry, this is my mistake. Apparently pmount cannot be used to mount fixed devices (I've just realized that now).

You can check if your ntfs partitions are mounted (and where) with```
mount | grep -i -E sda2\|sda5
``` 

If they're not shown, you can (correctly) mount your ntfs partitions as follows:```

sudo mount /dev/sda2 /media/sda2/ -o defaults,umask=007,gid=46
sudo mount /dev/sda5 /media/sda5/ -o defaults,umask=007,gid=46

```

Ensure the "/media/sda2" and "/media/sda5" directories exist and are not already mounted, then mount with the above commands, and unmount with```
sudo umount /dev/sda2
sudo umount /media/sda5
``` (The point being, you can use either the mount point, or the device to unmount).

Since I have no experience with Avast, I cannot help you out there.

---

### Post by hawkeye53 on 2008-09-24
Sorry to be a pest, but this doesn't work either. Here's the error text.

Also, it gives a suggestion on how to force a shut down, but that requires "root" and I must not know how to do that or I don't have the right password.

craig@craig-laptop:~$ sudo mount /dev/sda2 /media/sda2/ -o defaults,umask=007,gid=46
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2/ ntfs-3g force 0 0
craig@craig-laptop:~$

---

### Post by prshah on 2008-09-25
> **hawkeye53 said:**
> 
craig@craig-laptop:~$ sudo mount /dev/sda2 /media/sda2/ -o defaults,umask=007,gid=46
$LogFile indicates unclean shutdown (0, 0)
Failed to mount '/dev/sda2': Operation not supported
Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have Windows then disconnect the external devices by
          clicking on the 'Safely Remove Hardware' icon in the Windows
          taskbar then shutdown Windows cleanly.

Choice 2: If you don't have Windows then you can use the 'force' option for
          your own responsibility. For example type on the command line:

            mount -t ntfs-3g /dev/sda2 /media/sda2/ -o force

    Or add the option to the relevant row in the /etc/fstab file:

            /dev/sda2 /media/sda2/ ntfs-3g force 0 0
craig@craig-laptop:~$

This means that you have not cleanly shutdown in Windows. Reboot into windows, and shutdown cleanly. Are you unable to use Windows because of virus / worm / spyware? Then boot into "safe mode with command prompt" (keep tapping F8 _after_ grub screen, _before_ windows splash screen, ie, press enter to select Windows in the grub options, then _immediately_ keep tapping F8), run chkdsk on all your ntfs partitions, and shutdown (you may want to note these commands down)```

chkdsk c: /f

``` You will be asked to check on system restart; give Yes, restart the system with ```
shutdown -r now
``` (Or press Ctrl+Alt+Del and select reboot). Reboot _again_ in Windows, normal mode this time. When you get to the login (Welcome) screen, _don't_ login, but restart from the login screen itself, by clicking the icon to the bottom left of the screen, and selecting restart.

If for any reason, you can't get Windows to shutdown properly, then you have to "force mount" your ntfs partition which is risky (in real-world terms, only slightly risky, but in legal-speak: CAVEAT EMPTOR - let the buyer beware; at your own risk).

To force mount the ntfs partition, modify the mount command I've given slightly```

sudo mount /dev/sda2 /media/sda2/ -o defaults,umask=007,gid=46[color=red],force[/color]
sudo mount /dev/sda5 /media/sda5/ -o defaults,umask=007,gid=46[color=red],force[/color]
```

Force mounting should not be done unless you have no other option.

---

