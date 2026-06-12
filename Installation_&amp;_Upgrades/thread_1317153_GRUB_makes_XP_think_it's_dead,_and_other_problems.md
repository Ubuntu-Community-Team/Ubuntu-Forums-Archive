---
title: "GRUB makes XP think it's dead, and other problems"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by Veteropinguis on 2009-11-06
I have XP on one hard drive and Ubuntu on another. I installed Karmic yesterday, everything went great. Except that since I'd installed Karmic with my XP drive unplugged, it wasn't showing up in GRUB. I found out I just had to run ```
sudo update grub
``` and XP showed up when I next rebooted.

I choose to boot to XP- and it says that Windows can't start because ```
<Windows root>/system32/ntoskrnl.exe is missing or corrupt, blah blah blah
``` This is *exactly* what has happened in the past every single time I have tried to install Ubuntu as a dual-boot, including with Wubi.

I unplug the SATA cable from the Ubuntu drive and turn my computer back on. **Windows boots with no problems.**

I replug the SATA cable, and GRUB is gone, but XP is fine. I checked my cable connections, but it seems like XP must have mucked with the MBR.

So...what do I do? I don't want to have to open my case every time I have to boot in to XP. But, if I can't figure out why GRUB is making XP pretend to commit suicide I'm going to end up having to give up on Ubuntu :( Realistically I'm not going to unplug everything, pull my tower out from its annoying little computer desk hutch, open the cover, plug in a hard drive, screw the cover back on, plug everything in, and put the case back whenever I want to play a game or otherwise need to get at XP.

I know everyone's swamped with polishing Karmic (which is fantastic btw, great work all around) but if anyone could help me with this GRUB problem that would be great.

---

### Post by oldfred on 2009-11-06
You should not have to open the computer. At the very least you can set which drive is first by using the BIOS. In fact I think your switching cables may have changed the boot order so windows still boots first. Try changing the boot order in BIOS to see if you get back to grub.

You say you also had the same error before? You may have an issue with your windows that the windows boot ignores? Someone else may have seen this error.

---

### Post by khelben1979 on 2009-11-06
I recognize this problem and I haveto switch harddrives in BIOS every time in order for me to switch operating system. Works with no problems over here.

So I agree with oldfred here.

---

### Post by Veteropinguis on 2009-11-06
I got back to GRUB by changing the BIOS boot order, thanks guys. Is there a way to select which partition boots first, if that makes sense? Might be the trick if I get this error again, should I ever have to run a dual-boot off of one hard drive.

So I got GRUB back, but when I select XP it says: ```
unaligned pointer 0x25

Aborted. Press any key to exit.
```

I hit the space bar and it takes me to a screen where the Intel Boot Agent GE v1.2.36 displays my MAC address, says my GUID is a bunch of Fs, and looks for DHCP offers. When it doesn't get them (my wired connection works perfectly) it says there's a disk boot failure. This happened before when I tried to boot to Windows with my Karmic drive unplugged. I didn't insert a system disk, and hit enter. That took me back to GRUB. Now it says ```
unaligned pointer 0x7fe90a74
Aborted. Press any key to exit.
```

And the boot agent comes back.

In GRUB it says that XP is on dev/sda1.

My Karmic CD is on the desk ready to go. What should I do? All I can really do in a terminal is open Firefox and gedit, and sudo apt-get install, but I'll run any commands/post any output you guys need.


Okay, this is new. I tried to go in to recovery mode, which took me to a menu. I thought I was selecting cancel (since cancel was highlighted) but instead I think I selected 'Recovery shell'. I believe I am in a shell with no networking. I entered my username and password, now it looks like my whole screen is a terminal. Does that affect anything I'd have to do?

---

### Post by Veteropinguis on 2009-11-07
I tried to reinstall GRUB from the LiveCD but it didn't work.

I used [https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD). When I got to ```
To install GRUB 2 to the MBR, next you need to run grub-install /dev/sda
``` I got a grub-probe error. Ubuntu said it couldn't find a GRUB drive for /dev/sdb1 (my *nix drive) and to check my device map, and ```
Auto-detection of a filesystem module failed, please specify the module with the option '--modules' explicitly
```

I unmounted the drives and fscked sdb, which said: ```
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel. Building a new DOS disklabel with disk identifier 0x3f6a2e66.
The number of cylinders for this disk is set to 18700, which could cause problems with software that runs at boot time or booting and partitioning software from other OSs
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)
```

Then this:

```
[CODE]root@ubuntu:/# mount
/dev/sdb1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
```[/CODE]

The awesome Linux guy I was getting help from said everything should be okay, so I tried running grub-install again, got the same error.

I then decided to just reinstall Karmic with my BIOS properly configured and both drives plugged in.

I'm really immensely pleased with how fast the installation goes in Karmic. I've been at 89% for a while since I'm importing about 26 GB of files from my XP drive- but the importing has taken longer than the rest of the installation. I'll edit this post tomorrow morning, since I'm going to sleep now- wanted to keep this current while I'm still kind of coherent.

---

### Post by Veteropinguis on 2009-11-07
Bloody hell, my pointers are still messed up.

In the LiveCD I can mount both drives, the 160 GB has Ubuntu on it and is a fresh install. Apparently that didn't fix grub.

I opened up a terminal and did the following:

```
sudo nano/etc/default/grub
```

I removed the quote marks from the "10" for the timeout and saved.

```
sudo update-grub
```

grub-probe: error: cannot find a device for /

At this point I'm sure I'm doing a bunch of stupid stuff. I'm going to quit while I'm ahead (I didn't accidentally install Ubuntu over Windows) and log for now, for real this time.

---

### Post by Herman on 2009-11-07
Maybe you should first try running grub-mkdevicemap and then try running grub-install again and see if it helps. ```
sudo **grub-mkdevicemap**
```
Or just re-run grub-install, because that will also make you a new device.map 

I'm guessing your Windows hard drive might be your second hard drive?
In GRUB Legacy, it used to be necessary to use a pair of 'map' commands in the menu.lst boot entry for Windows in the second hard disk. That was to 'trick Windows into thinking it was in the first hard disk'. Otherwise one could go and edit boot.ini in Windows and tell Windows it's in the number 2 hard disk and boot without the 'map' commands. It's important for something to tell Windows where it is in the computer or it won't be able to find its own files. 
I don't know if that has anything to do with your problem or not, but you did install Ubuntu without your Windows disk plugged in, then expect GRUB to be able to boot Windows without an up to date device.map. Therefore I'm guessing GRUB might not know Windows is in a second hard disk, hence your problem. I'm only guessing, I hope I'm being helpful.


[]("http://ubuntuforums.org/showthread.php?t=1306900")

---

### Post by Herman on 2009-11-07
**[B]How To Re-install GRUB 2 **without the need to chroot[/B] from a Ubuntu Live CD (or from another installed GRUB 2 operating system )

The commands below '*should*' be able to be used from another operating system such as a Live CD. 

1. The operating system needs to be mounted first, just go 'Places'-->'Removable Media' or just 'Places' and look under 'Computer' for the disk or partition you want to mount and click on it.
You should see an icon for it on your desktop, but what you may not see is the 'mount point', which will normally be located in your /media directory.

2. Find the name of the mount point,
```
ls /media
```The file path that is returned from the above command will be needed for making up the next command. The name of the mount point might be a file system LABEL or UUID number, but for my example I'll just use the word 'disk' for short. 

Hint: It's will make your life a lot easier if you take a few minutes to set a nice user-freindly file system label in your linux file systems, [How To Set File System Labels With GParted]("http://members.iinet.net.au/%7Eherman546/p10.html#Set_File_System_Labels_with_GParted").

3. Run grub-setup,
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```The -d option tells GRUB to use files from a specified directory.

4. If the command fails with feedback about not being able to access a device.map file, you might need to try again and specify the exact device.map file to use with the -m option,
```
sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda
```See, only three or maybe four steps! ;)

---

### Post by GrantBarry on 2009-11-07
This message is displayed when the NT Loader cannot find the Kernel (ntoskrnl). I suggest looking at your BOOT.INI file in the root of your Windows partition. This is a hidden file.

If the disk or partition number has changed, then your boot.ini file is out of sync. You will probably need to update the rdisk and partition values.

The BOOT.INI file will look similar to this:

[COLOR=Sienna][boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect [/COLOR]

Here is a short description of each setting:

- **multi(0)**: The adapter of the hard disk that Windows is on. Keep it set to 0.
- **disk(0)**: The physical disk number to load Windows from if multi is not used. Since we're using multi, keep this 0 as well.
- **rdisk(x)**: The physical disk number to load Windows from. rdisk() begins counting from 0, so the first drive on your system is rdisk(0), the second is rdisk(1), and so on and so forth. These numbers do not relate to the SATA channel numbers or the IDE primary/secondary - master/slave connections, but to the order of your drives as seen by the BIOS, so that rdisk(0) is the drive you are booting from etc.
- **partition(y)**: The number of the partition on the drive rdisk(x). partition(y) starts counting from 1, so the first partition is partition(1), the second is partition(2), etc. partition(y) counts primary partitions first then counts logical partitions. The extended partition (the "container" for logical partitions) itself isn't counted, though. These numbers are taken from the Partition Table in the Master Boot Record, which will generally be the order in which they were created, which will not necessarily be the same as the order in which they appear on the disk


There are XP Recovery Console commands which will recreate/rebuild your BOOT.INI - spend some time on Google for that.

---

### Post by Herman on 2009-11-07
```
bootcfg /rebuild
```

---

### Post by Veteropinguis on 2009-11-07
Remade the directories and reinstalled GRUB. Ubuntu boots (I got an unaligned pointer warning twice but I just rebooted and it worked, that's fine with me) and XP seems to need a new boot.ini. Thanks for all your help, everyone.

**If you have the same problem I had, follow Herman's instructions. I didn't need to run the bootcfg command.**

> **Herman said:**
> **[B]How To Re-install GRUB 2 **without the need to chroot[/B] from a Ubuntu Live CD (or from another installed GRUB 2 operating system )

The commands below '*should*' be able to be used from another operating system such as a Live CD. 

1. The operating system needs to be mounted first, just go 'Places'-->'Removable Media' or just 'Places' and look under 'Computer' for the disk or partition you want to mount and click on it.
You should see an icon for it on your desktop, but what you may not see is the 'mount point', which will normally be located in your /media directory.

2. Find the name of the mount point,
```
ls /media
```The file path that is returned from the above command will be needed for making up the next command. The name of the mount point might be a file system LABEL or UUID number, but for my example I'll just use the word 'disk' for short. 

Hint: It's will make your life a lot easier if you take a few minutes to set a nice user-freindly file system label in your linux file systems, [How To Set File System Labels With GParted]("http://members.iinet.net.au/%7Eherman546/p10.html#Set_File_System_Labels_with_GParted").

3. Run grub-setup,
```
sudo grub-setup -d /media/disk/boot/grub /dev/sda
```The -d option tells GRUB to use files from a specified directory.

4. If the command fails with feedback about not being able to access a device.map file, you might need to try again and specify the exact device.map file to use with the -m option,
```
sudo grub-setup -d /media/disk/boot/grub -m /media/disk/boot/grub/device.map /dev/sda
```See, only three or maybe four steps! ;)

---

