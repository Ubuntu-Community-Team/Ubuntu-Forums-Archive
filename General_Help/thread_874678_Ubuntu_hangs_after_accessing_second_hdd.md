---
title: "Ubuntu hangs after accessing second hdd"
date: 2008-07-30
forum: General Help
---

### Post by mun_ramo on 2008-07-30
Hi, I am a newbie in linux. I have just installed Ubuntu Hardy Heron on my desktop. I can run everything except my second hdd. When my ubuntu boot up it does not mount my second hdd but I can still see the partition names. If i where to click on the any partion icon and access my 2nd hdd or mount it, I can go in but after a few seconds it will hang with the hdd light on my cpu on. The mouse nor the keyboard would den cease to respond. In the end I have to hard boot my computer.

My desktop spec:
Pentium 4 2.66Ghz
512mb RAM
40Gb Hdd (1st drive)
80Gb hgg (2nd drive - split into many partition)
Nvidia 6200

Please help.:confused:

---

### Post by vanadium on 2008-07-30
This is not normal behaviour and could indicate hardware issues with that drive. Currently, these partitions are mounted "on demand" by gnome. I suggest we test mounting them in the "old fashionned" way to see if the problem persists or not. If the problem persists mounting the drives in an alternate way, chances become likely that this is indeed a hardware issue.

To get started with this, open a command terminal, copy/paste the following commands in the terminal and copy/paste all output back here.

```

sudo fdisk -l
mount
cat /etc/fstab

```

After that, I will provide you some commands that will mount the partitions manually. We can then see if there is any error during the mounting itself or not, and whether accessing the drive still is problematic.

---

### Post by mun_ramo on 2008-07-30
Thanks! Here is the output:

mun@mun-desktop:~$ sudo fdisk -l

Disk /dev/sda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x191c191b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4678    37576003+  83  Linux
/dev/sda2            4679        4865     1502077+   5  Extended
/dev/sda5            4679        4865     1502046   82  Linux swap / Solaris

Disk /dev/sdb: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0ec79990

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1590    12771643+   c  W95 FAT32 (LBA)
/dev/sdb2            1591        9964    67264155    f  W95 Ext'd (LBA)
/dev/sdb5            1591        4342    22105408+   b  W95 FAT32
/dev/sdb6            4343        7113    22258026    b  W95 FAT32
/dev/sdb7            7114        9964    22900626    b  W95 FAT32

mun@mun-desktop:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/mun/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=mun)

mun@mun-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=139a284e-fbc9-44ff-9f33-b1ed3e6e5fc9 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=837f8c69-e525-4b78-b594-71866fead560 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by vanadium on 2008-07-30
Excellent. Your second hdd, /dev/sdb, contains all fat32 partitions which normally should mount without a problem. I propose now that you mount the partitions manually using the command line. The commands should not give any error, otherwise it is the mounting itself that is a problem.

Open the terminal (Applications - Accessories - terminal). Type the following code and if any output, post the output back here. If the commands are "silent", all is OK.

```

cd
mkdir sdb1
sudo mount /dev/sdb1 sdb1
sudo touch sdb1/this_is_a_testfile

```

[edit] After the first "sudo ..." command, you need to provide your login password: you are assuming root privileges now[/edit]

The first "cd" is not really needed: just to make sure you are in your users home directory (which you are at first when opening a terminal)

If you do not see any output, then you have successfully mounted and written to the first of your partitions on drive b.

Now open nautilus, the file browser (Places - Home folder). You will see a directory "sdb1" there. Double-click in it to see whether you can browse it. You should see the dummy file "this_is_a_testfile" we created and you should see the contents of the drive. You will not be able to write for now.

If all goes well, then there is indication that the problem was somehow related to the gnome mounting system (gnome virtual file system).

Try now to subsequently mount the other partitions as well: execute the same commands, but substituting "sdb1" for "sdb5", then "sdb6" and finally "sdb7" and each time check the behaviour of the system.

---

### Post by mun_ramo on 2008-07-30
Ok I believe I can successfuly mount the first partition sdb1 as there is no output but right after I entered in the:

```
sudo touch sdb1/this_is_a_testfile
```

The hdd light infront of my cpu lights up and shortly the whole system hangs.

Update: I restarted my computer and tried to mount my partition using the mount commmand u gave me. It does work. I skipped the touch command and when to the Places - Home folder. I saw the sdb1 folder with a small lock in the icon. I tried going in and immediately the hdd light came on and the system hangs again....

---

### Post by vanadium on 2008-07-30
This shows it is not the mounting in any case. In the mean time, you probably rebooted your system again so that now it is back where we started.

Anyway, before proceeding, check first if you also have this with sdb5. This will probably be "yes". If no, then it must be the partition sdb1.

Next becomes more difficult. I am providing some ideas. From the information you gave, I suspect there is no Windows anymore on that desktop. Otherwise, an obvious next test would be whether there are similar problems accessing the drive from within MS Windows. You could try if there are issues accessing it from the Ubuntu live CD or perhaps from the live CD of another Linux distro to make sure it is not due to your currently installed Ubuntu (I really don't think this is likely).

Next is to check the hardware: open the computer (I assume this concerns a desktop), remove excessive dust and check whether the connections of the problem drive are tightly and neatly in place (eventually remove the connection, remove dust and place it carefully back).

If the problem is still not solved, then there is a "destructive" option that you should try only if you have a backup of all data on that drive. That would involve to try repartitioning and reformatting the drive, which obviously would wipe its current contents.

---

### Post by mun_ramo on 2008-07-30
I tried it with sdb5 still the same problem. I am now trying the live cd. I am assuming it work not work also. Alright done, it still hang on me except that it took a little bit long to hang.

Before Ubuntu, I was running Xp on it. So far I have not experience this problem under Windows.

I have opened the cpu up. I have opened up the innards, did everything. Boot up and mount sdb5, managed to mount but hangs again shortly. Darn. I'm contemplating to remove the drive, make it an external drive, test it as a usb mass storage device... I wonder will it still be the same? If it is or not, I just back up all my stuffs on to my other desktop and follow the "destructive" option. What do you think? I wonder what is the cause of this. :(:confused:

---

### Post by vanadium on 2008-07-30
I really suspect a hardware problem. Some OS reponds quicker to a hardware problem than another. At one time, my Windows ME installation would after a few seconds show a blue screen of death. A few months later, I got issues with Ubuntu booting, and an error message hinted me that it was the USB 2 card. Guess what: after removing the USB 2 card, Windows ME booted again normally.

It will be up to you what to do next. Indeed,you are strongly urged to back up the data if you can. Then you could indeed try repartioning and reformatting, but I do not guarantee that it will work after that, but it might.

---

### Post by mun_ramo on 2008-07-30
Thanks alot. I shall try and do what ever I can. I shall update this tread again tommorow. If still does not work I guess I will have to try another linux distro. The last and final option will be reverting to windows. Sigh. If so do you have any recommended distro that I can try out? ](*,)

---

