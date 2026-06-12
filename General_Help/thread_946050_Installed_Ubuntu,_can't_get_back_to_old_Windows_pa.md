---
title: "Installed Ubuntu, can't get back to old Windows partition?"
date: 2008-10-12
forum: General Help
---

### Post by Tsura on 2008-10-12
Sorry I'm extremely new to the Linux world, I've recently installed Ubuntu on my computer (wiping Vista off the face of my computer's planet once and for all).

I made the switch, though, from my Windows XP Service Pack 3 partition to my added Ubuntu (I was hoping to dual boot).

Unfortunately, it seems as if Ubuntu replaced my XP SP3 boot config, and I don't know how to bring it back. I was wondering if anyone could give me any pointers, as searching only brought me results on how to go back to Ubuntu (when I want to go back to Windows instead :P)

Many thanks.

---

### Post by *B* on 2008-10-12
you might want to check out this thread:
[http://ubuntuforums.org/showthread.php?t=945886](http://ubuntuforums.org/showthread.php?t=945886)
its the same thing, except the OP there had 2 seperate disks, whereas from what I understand, you have one drive with multiple partitons.

---

### Post by jamesrl on 2008-10-12
Usually you just have to edit your /boot/menu.lst to make sure there is a windows like entry.

They give an example for windows in the file.

```

# title		Windows
# root		(hd0,0)
# makeactive
# chainloader	+1

```
You'll have to change (hd0,0) to whichever hard drive (first number starting from 0) and partition (second number starting from 0) that windows is on.  If you need to see what partitions you have type (-l as in list):
```
sudo fdisk -l
```
and you'll get output like:
```

 Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           6       48163+  de  Dell Utility
/dev/sda2   *           7        2938    23549952    7  HPFS/NTFS
/dev/sda3            2939       19196   130592385    f  W95 Ext'd (LBA)
/dev/sda5            2939        4243    10482349+  83  Linux
/dev/sda6            4244       18935   118013458+  83  Linux
/dev/sda7           18936       19196     2096451   82  Linux swap / Solaris

```
which says that on my laptop the Vista partition is on /dev/sda2 or (hd0,1) (sda corresponds to 0, being the 2nd sda corresponds to the 1).

---

### Post by crazyness003 on 2008-10-12
You might wanna include how you installed Ubuntu. During the repartitioning phase, if you do a "guided" repartition, it likes to erase anything else on that one drive. If you did that, there's a 99% chance your Win Partition and int contents is gone.
Else, maybe grub didn't detect your windows partition (assuming its not wiped off). Because grub allows you to boot win through a chainloader. If possible, try to use gparted to tell us if your other partition is even there, then we may be able to work it out.

You can install gparted like so:
In termial, type
```
sudo apt-get install gparted
```When prompted, enter your password (the one you set up when you installed). Remember, this requires root privileges, so be careful (even thought its only gonna download and install gparted)

Then run gparted by typig 
```
gksu gparted
```Again, prompt for password and root privileges, so be careful what you do while in the program. it may cause more havoc.

Take a screenshot or explain what you see so we can better understand whats on your HDD

EDIT: [jamesrl]("http://ubuntuforums.org/member.php?u=82343") had a better idea than me, stick with his plan.

---

### Post by WWSmith36 on 2008-10-12
Please open terminal and post the output of these commands

```
sudo fdisk -lu
cat /boot/grub/menu.lst
```

And also let us know which OS was installed first - WinXP or Vista.  This is very important to know.

Thank you

---

### Post by Tsura on 2008-10-13
Thanks so much for the quick support.

I've tried jamesrl option, the output I get is:
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1cc31cc3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *           1       60801   488384001    f  W95 Ext'd (LBA)
/dev/sda5           18241       53090   279932593+   7  HPFS/NTFS
/dev/sda6           53091       60801    61938576    7  HPFS/NTFS
/dev/sda7               1       18240   146512705+  83  Linux

```

and my /boot/grub/menu.lst file

```

splashimage (hd0,6)/boot/grub/splashimages/KUBUNTU_splashscreen_blue_neon_logo_03.xpm.gz
hiddenmenu
default 0
timeout 10

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=3aa7d807-7ae8-4b87-bc15-738b8680fb91 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title Ubuntu intrepid (development branch), kernel 2.6.27-7-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3aa7d807-7ae8-4b87-bc15-738b8680fb91 ro quiet splash
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-7-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=3aa7d807-7ae8-4b87-bc15-738b8680fb91 ro  single
initrd /boot/initrd.img-2.6.27-7-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-4-generic
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=3aa7d807-7ae8-4b87-bc15-738b8680fb91 ro quiet splash
initrd /boot/initrd.img-2.6.27-4-generic

title Ubuntu intrepid (development branch), kernel 2.6.27-4-generic (recovery mode)
root (hd0,6)
kernel /boot/vmlinuz-2.6.27-4-generic root=UUID=3aa7d807-7ae8-4b87-bc15-738b8680fb91 ro  single
initrd /boot/initrd.img-2.6.27-4-generic

title Ubuntu intrepid (development branch), memtest86+
root (hd0,6)
kernel /boot/memtest86+.bin

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
lock
root (hd0,5)
chainloader +1
savedefault
makeactive

```

And it still doesn't work :confused:

---

### Post by caljohnsmith on 2008-10-13
A big part of your problem is that Windows is on either sda5 or sda6, and both of those are logical partitions; it is easiest to boot Windows from a primary partition, but it is also possible to boot Windows from a logical partition with some hassle. Just curious, but how did Windows end up on a logical partition? If you installed Windows to the logical partition, then it would have put its boot files on some available primary partition, but you don't have any primary partitions. Therefore I doubt Windows XP would have let you install it directly to your logical partition. 

Was Windows ever booting at some point? Is it a new install? And is the Ubuntu a fresh install? If you just installed them both recently, I would recommend simply saving your important files from both Ubuntu and Windows, wipe your HDD clean, set up your partitions in a little more friendly manner for Windows, and reinstall XP first followed by Ubuntu. If that is not a good option for you at this point, you can probably get Windows booting with some work like I mentioned before. If you want to do that, please post the output of:
```
sudo mkdir /media/sda5 /media/sda6
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6
ls -l /media/sda5 /media/sda6
```
And we can go from there. :)

---

### Post by Tsura on 2008-10-13
I think it's better to explain my OS install history now, and this would probably explain my previous issue for when I installed XP SP3

So what happened was I installed Vista SP1, got tired of it, installed XP SP3. 

Then I installed Ubuntu, I did it MANUALLY (as I didn't feel like loosing any data :P). This meant that I had to wipe clean my Vista partition, and I did, and I made sure to backup any important data.

I'm pretty sure now, that I wiped my primary partition clean and it is now ext3 Ubuntu.

I was hoping to just go back to my XP partition, and find a good time to reinstall everything (like you suggested) to be more organized.

For now though, would running the commands you suggested help?

---

### Post by Tsura on 2008-10-13
> **caljohnsmith said:**
> A big part of your problem is that Windows is on either sda5 or sda6, and both of those are logical partitions; it is easiest to boot Windows from a primary partition, but it is also possible to boot Windows from a logical partition with some hassle. Just curious, but how did Windows end up on a logical partition? If you installed Windows to the logical partition, then it would have put its boot files on some available primary partition, but you don't have any primary partitions. Therefore I doubt Windows XP would have let you install it directly to your logical partition. 

Was Windows ever booting at some point? Is it a new install? And is the Ubuntu a fresh install? If you just installed them both recently, I would recommend simply saving your important files from both Ubuntu and Windows, wipe your HDD clean, set up your partitions in a little more friendly manner for Windows, and reinstall XP first followed by Ubuntu. If that is not a good option for you at this point, you can probably get Windows booting with some work like I mentioned before. If you want to do that, please post the output of:
```
sudo mkdir /media/sda5 /media/sda6
sudo mount /dev/sda5 /media/sda5
sudo mount /dev/sda6 /media/sda6
ls -l /media/sda5 /media/sda6
```
And we can go from there. :)
I have the output for you.

> 
/media/sda5:
total 1341
-rwxrwxrwx 2 root root 1179648 2008-06-06 17:49 541829578_MVM_0.tmp
drwxrwxrwx 1 root root    4096 2008-04-26 12:59 Ableton Live Library
drwxrwxrwx 1 root root    4096 2008-04-26 11:04 ableton_suite_instruments
drwxrwxrwx 1 root root    4096 2008-09-06 21:46 Downloads
drwxrwxrwx 1 root root   32768 2008-10-12 12:17 FF DL
-rwxrwxrwx 1 root root     420 2008-04-15 20:41 file_id.diz
drwxrwxrwx 1 root root    8192 2008-10-03 20:31 Games
drwxrwxrwx 1 root root    4096 2008-07-17 14:53 Important **** on C
drwxrwxrwx 1 root root       0 2008-10-01 20:53 LimeWire
drwxrwxrwx 1 root root       0 2008-04-08 17:25 Movies
drwxrwxrwx 1 root root       0 2008-08-04 18:03 msdownld.tmp
drwxrwxrwx 1 root root    4096 2008-10-12 22:54 Music
-rwxrwxrwx 2 root root    1222 2008-08-07 23:12 Music - Shortcut.lnk
drwxrwxrwx 1 root root    4096 2008-05-18 22:11 My First Ever Project
drwxrwxrwx 1 root root    4096 2008-07-17 17:45 Program Files
drwxrwxrwx 1 root root    4096 2008-10-03 22:08 Project Resources
drwxrwxrwx 1 root root   24576 2008-07-29 15:29 Rapidshare Downloads
drwxrwxrwx 1 root root    4096 2008-07-17 16:38 $RECYCLE.BIN
drwxrwxrwx 1 root root    4096 2008-10-04 16:42 RECYCLER
-rwxrwxrwx 2 root root     352 2008-10-01 22:42 Shortcut to FF DL.lnk
drwxrwxrwx 1 root root    4096 2008-10-01 22:17 System Volume Information
drwxrwxrwx 1 root root       0 2008-07-29 18:46 temp
-rwxrwxrwx 1 root root   17659 2008-04-15 20:41 tsrh.nfo

/media/sda6:
total 2095204
drwxrwxrwx 1 root root       4096 2008-10-02 19:55 Documents and Settings
drwxrwxrwx 1 root root          0 2008-10-01 23:23 MSOCache
-rwxrwxrwx 1 root root 2145386496 2008-10-12 17:43 pagefile.sys
drwxrwxrwx 1 root root      28672 2008-10-06 21:54 Program Files
drwxrwxrwx 1 root root          0 2008-10-02 15:23 RECYCLER
drwxrwxrwx 1 root root       4096 2008-10-01 22:15 System Volume Information
drwxrwxrwx 1 root root       4096 2008-10-03 19:40 wamp
drwxrwxrwx 1 root root      45056 2008-10-06 21:55 WINDOWS
drwxrwxrwx 1 root root      16384 2008-10-01 22:55 WINDOWS.0


sda6 is my XP partition, it seems.

---

### Post by caljohnsmith on 2008-10-13
OK, it looks like you have XP on sda6, but as I suspected, you don't have any of your Windows boot files. If you want to get XP booting, you will probably need your XP Install CD--do you have that? Do you want to mess with trying to get XP booting or can you simply save your files and start over again like I mentioned in my previous post?

---

### Post by Tsura on 2008-10-13
> **caljohnsmith said:**
> can you simply save your files and start over again like I mentioned in my previous post?
If I were to do that, what would you recommend I do from there.

---

### Post by caljohnsmith on 2008-10-13
After saving your files to somewhere else, you could boot your Live CD, open Ubuntu's partition editor gparted:
```
gksudo gparted
```
Delete all your existing partitions, and set up new partitions. The layout I might suggest is:
[LIST]
[*]Making the first partition a primary partition formatted to NTFS for your Windows XP
[*]Create another primary partition after that formatted to NTFS for your data files currently in sda5
[*]Create an extended partition with the remaining space
[*]Create 2 logical partitions inside the extended partition: 
[LIST=1]
[*]A ext3 logical partition for the main Ubuntu install
[*]A logical partition for swap space
[/LIST]
[/LIST]
You can add extra logical partitions if you want more for other data storage, etc.

---

### Post by Tsura on 2008-10-13
And I would install Windows XP and afterwards Ubuntu?

---

### Post by caljohnsmith on 2008-10-13
> **Tsura said:**
> And I would install Windows XP and afterwards Ubuntu?
Yes, otherwise Windows will overwrite Grub in the MBR (Master Boot Record) if you install Windows after Ubuntu. It's not too tough to fix, but it is better if you can just install Windows first. Good luck and let me know how it goes. :)

---

### Post by Tsura on 2008-10-13
> **caljohnsmith said:**
> Yes, otherwise Windows will overwrite Grub in the MBR (Master Boot Record) if you install Windows after Ubuntu. It's not too tough to fix, but it is better if you can just install Windows first. Good luck and let me know how it goes. :)
This will take a while :P 

Thank you so *so* much for your help :)

---

### Post by crazyness003 on 2008-10-14
I hope you waited a bit though, before you go with reinstalling (even though reinstalling is best, it is a long process, and if anyone else who has this problem, dosnt have the option of a reinstall we might be "cheating them" out of a good solution.

**If you havent reinstalled yet:**
 Since you have XP in your grub boot load menu, can you see it when the grub menu comes up right after you hit the power button (called stage 1.5)? 
If so, can you select the XP installation (title [FONT=Courier New]Windows XP[/FONT]) The last entry in you menu?
And if so, what error message do you get?
Please if you can, write down that error and post it here. You may only need to copy a couple of files to your XP partition through Ubuntu (another awesome reason to have linux installed on your computer). 
Usualy the *boot.ini* or the *ntldr* files cause this kind of mayhem. If they are missing or corrupt (which happens very often) then you have a "tanked" windows partition. Fixable through a Linux Live CD or the Recovery Console on the windows CD [SIZE=1](i wont capitalize windows for personal reasons)[/SIZE]

**If you did reinstall:**
You probably made the better choice. It is a longer process, but clean installs are most likely to work better than trying to fix something (esp windows). Since you also backed up everything (a practice that needs to be practiced more often) then you should have no potential glitches. Congrats. And welcome to "Fixing your 'High Speed Idiot*' 101"

* High Speed Idiot = your computer, my computer, his computer, their computer etc.

**ALSO**
If you feel that your problem is solved, please use the "thread tools", "Mark thread as [SOLVED]". It helps, trust me. Thanks

---

