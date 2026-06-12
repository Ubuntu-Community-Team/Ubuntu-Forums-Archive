---
title: "chain load Xp and Vista to Grub"
date: 2008-10-12
forum: General Help
---

### Post by acdcfan on 2008-10-12
hi all ):P
According to my Windows Device manager I have XP on hdd0, Vista hdd1 and Ubuntu on hdd2 partition 1
How can I chain load them to GRUB so that I can boot straight into it, instead of going from grub boot loader to Windows boot loader. Grub is installed on the same partition where Ubuntu is. 
This is what I tried but it doesn't work.

gksudo gedit /boot/grub/menu.lst &

title Windows (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

title Windows (hd2)
root (hd2,0)
map (hd0) (hd2)
map (hd2) (hd0)
makeactive
chainloader +1

When I enter first command it takes me straight to Vistas boot loader but second command takes me to Press any key to boot......:confused:

If there is anything else you need to know please let me know. I really want to fix this

thanks 
acdcfan:biggrin:

---

### Post by meierfra. on 2008-10-12
Move the files "boot.ini", "ntdetect.com" and "ntldr" from the vista partition to the  XP partition.

---

### Post by meierfra. on 2008-10-12
I just saw your other thread. Since you have four hard drives, you also might try

title Windows (hd3)
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
makeactive
chainloader +1

---

### Post by acdcfan on 2008-10-12
> **meierfra. said:**
> Move the files "boot.ini", "ntdetect.com" and "ntldr" from the vista partition to the  XP partition.

Is this the only option or are there some more?

---

### Post by acdcfan on 2008-10-12
> **meierfra. said:**
> I just saw your other thread. Since you have four hard drives, you also might try

title Windows (hd3)
root (hd3,0)
map (hd0) (hd3)
map (hd3) (hd0)
makeactive
chainloader +1

Good luck

---

### Post by meierfra. on 2008-10-12
> Is this the only option or are there some more?

If you want Grub to be your primary boot loader, this is your only option. But if you just want to have only ONE boot menu with all your choices can also 

1)  Add ubuntu to the Vista Boot loader.

or 

2)  Use Grub4Dos.


> Good luck 

But "root (hd3,0)" only has a chance to succeed after you moved the three boot files.

---

### Post by acdcfan on 2008-10-14
> **meierfra. said:**
> If you want Grub to be your primary boot loader, this is your only option. But if you just want to have only ONE boot menu with all your choices can also 

1)  Add ubuntu to the Vista Boot loader.

or 

2)  Use Grub4Dos.




But "root (hd3,0)" only has a chance to succeed after you moved the three boot files.

I want to have one boot loader. How would I go about adding Ubuntu to Vistas boot loader. I have tried Using EasyBCD and it didn't work. I tried selecting Grub isn't installed to MBR and without it but had no luck....

regards
acsdcfan

---

### Post by meierfra. on 2008-10-14
> I want to have one boot loader. 

As far as I know that is not possible. But it is possible to just use one boot menu,  from which you can call the different boot loader (and you won't even notice that different boot loaders are involved). 

Using the grub menu  is the easiest way to accomplish this. Just follow post #2 and use EasyBCD to removed XP from the Vista boot menu.

> How would I go about adding Ubuntu to Vistas boot loader.  

Since Vista and Ubuntu are on different hard drive and you have four different hard drives, this is a little tricky. You have  to install grub in a special way to the boot sector of the Ubuntu partition. After that you should be able to use EasyBCD (without selecting "Grub is not installed to the boot sector") to add Ubuntu to the Vista boot menu.

For detailed help, post "sudo fdisk -l". Are you able to choose the exact boot order in your bios? (That is, choose which hard drive comes first, which one second, and so on)

Using "Grub is not installed to the boot sector" should also work. But I'm not familiar  enough with NeoGrub to give you detailed instruction. Did you get any error messages while trying to boot Ubuntu from the Vista menu?  Did you first select Vista at the grub menu, and then Ubuntu at the Vista menu? Or did boot directly into Vista by switching the boot order in the bios?

---

### Post by TeXtonyx on 2008-10-14
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

The above link is to Easybcd for changing Vista's bootloader.
It has a link to a pictorial guide for Fedora and Ubuntu. Here is
a link to the Ubuntu: [http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)
You want the section title "Adding Ubuntu to the Vista Bootloader"

I have a technical explanation of how to this manually if you want.

---

### Post by acdcfan on 2008-10-16
> **meierfra. said:**
> As far as I know that is not possible. But it is possible to just use one boot menu,  from which you can call the different boot loader (and you won't even notice that different boot loaders are involved).

You are correct in what you're saying. I want to have one boot menu

> **meierfra. said:**
> Using the grub menu  is the easiest way to accomplish this. Just follow post #2 and use EasyBCD to removed XP from the Vista boot menu.

 

Since Vista and Ubuntu are on different hard drive and you have four different hard drives, this is a little tricky. You have  to install grub in a special way to the boot sector of the Ubuntu partition. After that you should be able to use EasyBCD (without selecting "Grub is not installed to the boot sector") to add Ubuntu to the Vista boot menu.

For detailed help, post "sudo fdisk -l". Are you able to choose the exact boot order in your bios? (That is, choose which hard drive comes first, which one second, and so on)

Here is Fdisk -l output 

[B]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92341f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001   83  Linux
/dev/sda2           30402       60802   244188160    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x250024ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x251e251d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      121601   976760001    7  HPFS/NTFS
rastko@rastko-desktop:~$ [/B]


> **meierfra. said:**
> Using "Grub is not installed to the boot sector" should also work. But I'm not familiar  enough with NeoGrub to give you detailed instruction. Did you get any error messages while trying to boot Ubuntu from the Vista menu?  Did you first select Vista at the grub menu, and then Ubuntu at the Vista menu? Or did boot directly into Vista by switching the boot order in the bios?

For some reason every time I try to add Ubuntu using EasyBCD it is pointing to drive D which is XP drive 
It looks like that I have installed Grub on the same drive as Ubuntu. When I boot of Ubuntu drive in the GRUB boot loader as get to select windows boot loader which takes me Vistas boot loader where I can choose between XP or Vista. 
I will reboot to be able to take picture of GRUB menu and will came back to this post using Vista

---

### Post by acdcfan on 2008-10-16
> **meierfra. said:**
>  Did you get any error messages while trying to boot Ubuntu from the Vista menu?  Did you first select Vista at the grub menu, and then Ubuntu at the Vista menu? Or did boot directly into Vista by switching the boot order in the bios?

When I am in Grub and select first option I boot into Ubuntu...
See picture below. I am booting of a Ubuntu drive which is controlled by SATA PCI controller 
[B]
[http://img261.imageshack.us/img261/6280/img0013ja5.jpg](http://img261.imageshack.us/img261/6280/img0013ja5.jpg) [/B]

Then is I select last option Winodws Vista/Longhorn loader it takes me to.... See picture below  
[B]
[http://img261.imageshack.us/img261/1566/img0015fy7.jpg](http://img261.imageshack.us/img261/1566/img0015fy7.jpg)
[/B]
Here is EasyBCD debug mode when I added Ubuntu to it 

[B]Windows Boot Manager
--------------------
identifier              {9dea862c-5cdd-4e70-acc1-f32b344d4795}
device                  partition=D:
description             Windows Boot Manager
locale                  en-US
inherit                 {7ea2e1ac-2e61-4728-aaa3-896d9d0a9f0e}
default                 {64be9db8-d1ef-11dc-8f1e-bd9fc23203cd}
displayorder            {466f5a88-0af2-4f76-9038-095b170dc21c}
                        {64be9db8-d1ef-11dc-8f1e-bd9fc23203cd}
                        {72e04054-75b8-11dd-ad74-0019dbf71e06}
toolsdisplayorder       {b2721d73-1db4-4c62-bf78-c548a880142d}
timeout                 30

Windows Legacy OS Loader
------------------------
identifier              {466f5a88-0af2-4f76-9038-095b170dc21c}
device                  partition=D:
path                    \ntldr
description             Earlier Version of Windows

Windows Boot Loader
-------------------
identifier              {64be9db8-d1ef-11dc-8f1e-bd9fc23203cd}
device                  partition=C:
path                    \Windows\system32\winload.exe
description             Microsoft Windows Vista
locale                  en-US
inherit                 {6efb52bf-1766-41db-a6b3-0ee5eff72bd7}
osdevice                partition=C:
systemroot              \Windows
resumeobject            {64be9db9-d1ef-11dc-8f1e-bd9fc23203cd}
nx                      OptIn

Real-mode Boot Sector
---------------------
identifier              {72e04054-75b8-11dd-ad74-0019dbf71e06}
device                  partition=D:
path                    \NST\nst_grub-A88AD4CD91ECA583BFD18092505D3D31.mbr
description             Ubuntu [/B]

I don't got into Bios to change boot drives either. Only error I get is when trying to boot into Ubuntu via Vistas boot loader, after I used EasyBCD. 

And this a picture of my Device manager 

[http://img49.imageshack.us/img49/7039/captureiq6.jpg](http://img49.imageshack.us/img49/7039/captureiq6.jpg)

Sorry for a long post but I hope this clears it up

---

### Post by meierfra. on 2008-10-16
It looks like that all your XP and Vista Boot files are actually on the XP partition and not on the Vista partition. Just to confirm could you post the output of

```
sudo mount /dev/sdb1 /mnt
ls -l /mnt

```


Am I correct that sdb1 is your XP partition and sdc1 your Vista Partition?

Also set your bios to boot from the XP drive and see whether that gives  you the Vista boot menu.

You have two options:

[B]
 If want to use the Grub Menu
[/B]

Move the  files "bootmgr" and the folder "boot" from the XP partition to the Vista partition

Then boot from a XP CD, type "r" to enter the recovery console. Type 

```
map
```


 to determine the drive letter of your XP partition. Then 

```
fixboot X:
```
(replace X by the XP drive letter). Type "exit" to reboot.


Once everything is working, use EasyBCD to deleted XP from the Vista Boot loader.


** If you want to use the Vista Boot menu**


In an ubuntu terminal:


```
sudo grub
```
and at the "grub>" prompt

```

device (hd1)  /dev/sda
device (hd0) /dev/sda
root (hd1,0)
setup (hd0,0)
quit
```


Then set your bios to boot from the XP drive. If possible, set the Ubuntu drive to be second in the boot order in the bios. Use EasyBCD ( without checking the "linux is not installed to the boot sector" option) to add Ubuntu to the Vista boot loader.

(I'm not quite sure that EasyBCD can handle your setup, so if this does not work, I can show you how to add Ubuntu to the Vista bootloader using the Vista commandline)

---

### Post by acdcfan on 2008-10-17
> **meierfra. said:**
> It looks like that all your XP and Vista Boot files are actually on the XP partition and not on the Vista partition. Just to confirm could you post the output of

```
sudo mount /dev/sdb1 /mnt
ls -l /mnt

``` 

here is output but I think something is wrong here
 
[B] sudo mount /dev/sdb1 /mnt ls -l /mnt
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
[/B]


> **meierfra. said:**
> Am I correct that sdb1 is your XP partition and sdc1 your Vista Partition?

Yer you are... 


.

> **meierfra. said:**
> You have two options:

[B]
 If want to use the Grub Menu
[/B]

Move the  files "bootmgr" and the folder "boot" from the XP partition to the Vista partition

Then boot from a XP CD, type "r" to enter the recovery console. Type 

```
map
```


 to determine the drive letter of your XP partition. Then 

```
fixboot X:
```
(replace X by the XP drive letter). Type "exit" to reboot.

Prefer Vistas boot menu


> **meierfra. said:**
> ** If you want to use the Vista Boot menu**


In an ubuntu terminal:


```
sudo grub
```
and at the "grub>" prompt

```

device (hd1)  /dev/sda
device (hd0) /dev/sda
root (hd1,0)
setup (hd0,0)
quit
```

I will try this one but I am getting error 12 **Invalid device requested**


> **meierfra. said:**
> Then set your bios to boot from the XP drive. If possible, set the Ubuntu drive to be second in the boot order in the bios. Use EasyBCD ( without checking the "linux is not installed to the boot sector" option) to add Ubuntu to the Vista boot loader.

I will try this one too but 

> **meierfra. said:**
> (I'm not quite sure that EasyBCD can handle your setup, so if this does not work, I can show you how to add Ubuntu to the Vista bootloader using the Vista commandline)

But this one looks like what I want. So can we go straight to this one instead please?  


> **meierfra. said:**
> Once everything is working, use EasyBCD to deleted XP from the Vista Boot loader.

I will do this later

---

### Post by meierfra. on 2008-10-17
I don't have much time right now. But you need to press "enter" after each line of:

> sudo mount /dev/sdb1 /mnt

ls -l /mnt


Also did you try booting from  your XP drive?  If yes, what was the outcome?


> 
Originally Posted by meierfra. View Post
Once everything is working, use EasyBCD to deleted XP from the Vista Boot loader.

I will do this later

Oops. The "delete XP from the Vista boot loader" belongs into the "use grub menu part". So don't do this. (I fixed my previous post accordingly)

---

### Post by meierfra. on 2008-10-17
> 
sudo grub

device (hd1)  /dev/sda
device (hd0) /dev/sda
root (hd1,0)
setup (hd0,0)
quit

I will try this one but I am getting error 12 Invalid device requested

Did you press "enter" after each line?
Did you use copy and paste or did you type it your self?
Did you forget the "root (hd1,0)" line?
I suggest to try again.   Press enter after each line  and use copy and paste to avoid typos.  Just for double checking add a couple of lines:

```
sudo grub 
```
and when at the "grub>" prompt:


```
find /boot/grub/stage2
```

this should return :
(hd0,0)


```
device (hd1) /dev/sda

device (hd0) /dev/sda

find /boot/grub/stage2
```
(now it should return:
(hd0,0)
(hd1,0))

```
root (hd1,0)

setup (hd0,0)

```


If you still get "Errror 12" we will have to check out your partition table (although judging from the "fdisk -l" output there does not seem to be anything wrong with it)

---

### Post by meierfra. on 2008-10-17
Don't follow the instruction in this post before you successfully completed the instructions in the previous post.

The next step is to copy the boot sector of the Ubuntu partition to a file on the XP partition:

```
sudo mount /dev/sdb1 /mnt
sudo dd if=/dev/sda1 of=/mnt/Ubuntu.bin count=1
```
(be very careful with the "dd" command. It can be dangerous)

Next  you need to instruct the Vista Boot loader to use "Ubuntu.bin" to boot Ubuntu:


Boot into Vista, click on Start. Type "cmd" and press "CTRL+SHIFT+ENTER". This will run a command line as administrator.

Type

```

    bcdedit /create /d "Ubuntu" /application BOOTSECTOR

    bcdedit /set {ID} device boot

 (where ID is the  very long number which you will get after the first command)
    
     bcdedit /set {ID} PATH \Ubuntu.bin

     bcdedit /displayorder {ID} /addlast 

     bcdedit /timeout 5 

```

(The last line  sets the time (in seconds) until the Vista  boots the default entry. )


Finally, set your bios to boot  from the XP drive. Also set Ubuntu to be second in the boot order in the bios. (if you cannot choose Ubuntu to be second, you  might have to repeat the instruction in the previous post with modified numbers). You should get the Vista Boot Menu, with entries for Vista, XP and Ubuntu.

---

### Post by JeeZiTsDave on 2008-10-17
I think to chainload two operating systems in GRUB, you have to edit some kind of configuration file.

I heard this because of some guy that wanted to allow OSx86 in his GRUB.  However, it involves text based configuration which means that if you get the wrong code into the configuration file, you might not be able to boot back into Ubuntu to revert the changes.  I believe that there is a graphical Ubuntu application to change the BCD.

Hope this helps!

---

### Post by acdcfan on 2008-10-22
> **meierfra. said:**
> I don't have much time right now. But you need to press "enter" after each line of:




Also did you try booting from  your XP drive?  If yes, what was the outcome?




Oops. The "delete XP from the Vista boot loader" belongs into the "use grub menu part". So don't do this. (I fixed my previous post accordingly)

here is the output of
sudo mount /dev/sdb1 /mnt

ls -l /mnt 

[B][I]rastko@rastko-desktop:~$ sudo mount /dev/sdb1 /mnt
rastko@rastko-desktop:~$ ls -l /mnt
total 4500850
-rwxrwxrwx 1 root root        230 2008-07-31 21:13 config.xml
drwxrwxrwx 1 root root          0 2006-11-02 23:41 Documents and Settings
drwxrwxrwx 1 root root          0 2008-03-29 10:18 Intel
-rwxrwxrwx 1 root root     904704 2006-12-01 22:37 msdia80.dll
drwxrwxrwx 1 root root          0 2008-02-05 21:42 MSOCache
drwxrwxrwx 1 root root          0 2008-06-29 14:56 NVIDIA
-rwxrwxrwx 1 root root 4607848448 2008-10-21 19:30 pagefile.sys
drwxrwxrwx 1 root root          0 2008-03-21 21:47 PerfLogs
drwxrwxrwx 1 root root       8192 2008-10-04 21:54 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-16 22:09 Program Files
drwxrwxrwx 1 root root      20480 2008-10-05 16:53 Program Files (x86)
drwxrwxrwx 1 root root       4096 2008-02-02 20:21 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-02-03 21:51 RECYCLER
-rwxrwxrwx 2 root root         52 2008-09-04 20:59 Run_ppccfg.cmd
-rwxrwxrwx 1 root root         45 2008-09-04 21:00 Run_ppc.cmd
drwxrwxrwx 1 root root          0 2008-10-02 20:27 SP
drwxrwxrwx 1 root root      24576 2008-10-22 18:45 System Volume Information
drwxrwxrwx 1 root root          0 2008-07-27 09:01 temp
drwxrwxrwx 1 root root       4096 2008-06-14 16:27 Users
-rwxrwxrwx 1 root root       4096 2008-06-17 22:36 VSNAP.IDX
drwxrwxrwx 1 root root      40960 2008-10-04 21:50 Windows
[/I][/B]

---

### Post by acdcfan on 2008-10-22
> **meierfra. said:**
> Did you press "enter" after each line?
Did you use copy and paste or did you type it your self?
Did you forget the "root (hd1,0)" line?
I suggest to try again.   Press enter after each line  and use copy and paste to avoid typos.  Just for double checking add a couple of lines:

```
sudo grub 
```
and when at the "grub>" prompt:


```
find /boot/grub/stage2
```

this should return :
(hd0,0)

It actually returned (hd2,0)


> **meierfra. said:**
> 

```
device (hd1) /dev/sda

device (hd0) /dev/sda

find /boot/grub/stage2
```
(now it should return:
(hd0,0)
(hd1,0))

```
root (hd1,0)

setup (hd0,0)

```

How do I do this one 


> **meierfra. said:**
> If you still get "Errror 12" we will have to check out your partition table (although judging from the "fdisk -l" output there does not seem to by anything wrong with it)

No errors this time but do I use gksudo gedit ?

---

### Post by acdcfan on 2008-10-22
> **meierfra. said:**
> I don't have much time right now. But you need to press "enter" after each line of:

Also did you try booting from  your XP drive?  If yes, what was the outcome?


No I didn't yet, I was too busy to start my computer in the last couple of days..... Work related

---

### Post by meierfra. on 2008-10-22
> rastko@rastko-desktop:~$ ls -l /mnt
...

Strange.   sdb1 does not contain the boot files.

Please post:

```
sudo fdisk -lu
sudo umount /mnt   
sudo mkdir /mnt/sdc1
sudo mkdir /mnt/sdh1
sudo mount /dev/sdc1 /mnt/sdc1
sudo mount /dev/sdh1 /mnt/sdh1
ls -l /mnt/sdc1
ls -l /mnt/sdh1

```
(ignore any error messages after "sudo umount /mnt"  I just want to make sure that sdb1 is no longer mounted at /mnt)



> It actually returned (hd2,0)

That's surprising, but O.K.


> How do I do this one 

Open a terminal, type "sudo grub" and at the grub prompt:

```
device (hd1)  /dev/sda

device (hd0) /dev/sda

root (hd1,0)

setup (hd0,0)

quit
```

Use copy and paste, hit "enter" after each line. Before "quit" copy the whole terminal and post it here (Just for double checking)

---

### Post by TeXtonyx on 2008-10-22
I saw a snapshot of the choice to boot Vista, or an earlier version
of the OS. That happens when you install Vista on top of an existing
XP installation. If you look at C:\, you will see bootmgr and ntldr there.

I point this out because this 'earlier version of OS' it not on
some other XP partition, you will not boot another XP installation.
If you want to boot a different XP partition it needs to have the
boot files installed, you need to know its partition, which isn't
the same as the Vista partition where you can also boot an XP OS.

Do not forget to intall grub in the Ubuntu boot partition, not to 
the MBR. It is part of the instructions of the manual Vista boot
loader method. "Step 1 &#8211; Install GRUB on the Linux partition (outside of MBR)
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

That screen you saw with the choice of Vista and 'earlier OS' 
should eventually have Ubuntu on it and if you have another XP
OS installed, a choice to boot to that XP partition which is not
the same XP OS offered in 'earlier OS'.

On one of my computers, I have XP and Ubuntu on first drive.
I have Vista and OpenSuse on the other drive. I boot to XP,
which lets me pick Ubuntu or OpenSuse. I used the install grub
to the boot partition method and I used 512 boot sector method.
From Ubuntu, I can choose Vista. When you use Vista bootloader,
and choose Ubuntu, it still opens the grub menu.lst and you
choose Ubuntu again, so this doesn't work quite as directly as
you might have hoped. The main reason to boot this way which
requires putting Linux into the boot sector and a Linux.bin is
that if Linux fails it doesn't interfere with Windows. And if
Windows fails you can still boot Linux with the Super Grub disk.
Neither grub nor XP or Vista will offer an all inclusive direct
solution (I doubt grub will boot the Vista choice of 'earlier 
version OS'). I think you need to choose earlier OS from Vista.

If you are having trouble understanding what is on your partitions and
where, I think you could profitably augment your information by using
Vista/XP Administrative Tools -> Computer Management -> Disk Management
which provides a more pictorial view. You should be able to use EasyBCD,
everybody else can, which is why I think you could use more information.

---

### Post by acdcfan on 2008-10-23
> **meierfra. said:**
> Strange.   sdb1 does not contain the boot files.

Please post:

```
sudo fdisk -lu
sudo umount /mnt   
sudo mkdir /mnt/sdc1
sudo mkdir /mnt/sdh1
sudo mount /dev/sdc1 /mnt/sdc1
sudo mount /dev/sdh1 /mnt/sdh1
ls -l /mnt/sdc1
ls -l /mnt/sdh1

```
(ignore any error messages after "sudo umount /mnt"  I just want to make sure that sdb1 is no longer mounted at /mnt)

Here are the results [B][COLOR="Red"]rastko@rastko-desktop:~$ sudo fdisk -lu
[sudo] password for rastko: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92341f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   488392064   244196001   83  Linux
/dev/sda2       488392704   976769023   244188160    7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x250024ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976751999   488375968+   7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x251e251d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1953520064   976760001    7  HPFS/NTFS
rastko@rastko-desktop:~$ sudo unmount /mnt
sudo: unmount: command not found
rastko@rastko-desktop:~$ sudo umount /mnt
umount: /mnt: not mounted
rastko@rastko-desktop:~$ sudo mkdir /mnt/sdc1
rastko@rastko-desktop:~$ sudo mkdir /mnt/sdh1
rastko@rastko-desktop:~$ sudo mount /dev/sdc1 /mnt/sdc1
rastko@rastko-desktop:~$ sudo mount /dev/sdh1 /mnt/sdh1
rastko@rastko-desktop:~$ ls -l /mnt/sdc1
total 4500850
-rwxrwxrwx 1 root root        230 2008-07-31 21:13 config.xml
drwxrwxrwx 1 root root          0 2006-11-02 23:41 Documents and Settings
drwxrwxrwx 1 root root          0 2008-03-29 10:18 Intel
-rwxrwxrwx 1 root root     904704 2006-12-01 22:37 msdia80.dll
drwxrwxrwx 1 root root          0 2008-02-05 21:42 MSOCache
drwxrwxrwx 1 root root          0 2008-06-29 14:56 NVIDIA
-rwxrwxrwx 1 root root 4607848448 2008-10-23 19:05 pagefile.sys
drwxrwxrwx 1 root root          0 2008-03-21 21:47 PerfLogs
drwxrwxrwx 1 root root       8192 2008-10-04 21:54 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-16 22:09 Program Files
drwxrwxrwx 1 root root      20480 2008-10-05 16:53 Program Files (x86)
drwxrwxrwx 1 root root       4096 2008-02-02 20:21 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-02-03 21:51 RECYCLER
-rwxrwxrwx 2 root root         52 2008-09-04 20:59 Run_ppccfg.cmd
-rwxrwxrwx 1 root root         45 2008-09-04 21:00 Run_ppc.cmd
drwxrwxrwx 1 root root          0 2008-10-02 20:27 SP
drwxrwxrwx 1 root root      24576 2008-10-22 19:56 System Volume Information
drwxrwxrwx 1 root root          0 2008-07-27 09:01 temp
drwxrwxrwx 1 root root       4096 2008-06-14 16:27 Users
-rwxrwxrwx 1 root root       4096 2008-06-17 22:36 VSNAP.IDX
drwxrwxrwx 1 root root      40960 2008-10-04 21:50 Windows
rastko@rastko-desktop:~$ ls -l /mnt/sdh1
total 12
drwxrwxrwx 1 root root    0 2008-10-02 20:21 ~MSSETUP.T
drwxrwxrwx 1 root root 8192 2008-07-01 20:58 Original back up
drwxrwxrwx 1 root root    0 2008-09-21 23:03 $RECYCLE.BIN
drwxrwxrwx 1 root root    0 2008-07-05 13:29 RECYCLER
drwxrwxrwx 1 root root 4096 2008-07-05 12:09 System Volume Information
drwxrwxrwx 1 root root    0 2008-10-19 20:35 Vista back up
drwxrwxrwx 1 root root    0 2008-06-17 16:52 VProRecovery
drwxrwxrwx 1 root root    0 2008-10-21 19:59 XP Pro back up
[/COLOR][/B]


> **meierfra. said:**
> 
That's surprising, but O.K.

Thats what I thought when I saw that GRUB is install on the same drive as Ubuntu. I am sure I point it to XP drive during the install 



> **meierfra. said:**
> 
Open a terminal, type "sudo grub" and at the grub prompt:

```
device (hd1)  /dev/sda

device (hd0) /dev/sda

root (hd1,0)

setup (hd0,0)

quit
```

Use copy and paste, hit "enter" after each line. Before "quit" copy the whole terminal and post it here (Just for double checking)

I will try this now and reboot. 
Will post results, 

After inputting sudo grub command as per above, there were 2 lines saying that something failed but that is not fatal. I am posting with Vista. 
Going back to Ubuntu to attempt above command and post result of an error

Here is terminal output with error message 
[B][COLOR="Red"]      [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]

grub> device (hd1) /dev/sda

grub> device (hd0) /dev/sda

grub> root (hd1,0)

grub> setup (hd0,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 d (hd0,0) /boot/grub/stage2 p /boot/grub/me
nu.lst "... succeeded
Done.

grub> 
[/COLOR][/B]
 
Grub command find /boot/grub/stage2 returns hd0,0....Meierfra your guidance is so appreciated by me. I am not very religious person but God bless you

---

### Post by acdcfan on 2008-10-23
> **TeXtonyx said:**
> I saw a snapshot of the choice to boot Vista, or an earlier version
of the OS. That happens when you install Vista on top of an existing
XP installation. If you look at C:\, you will see bootmgr and ntldr there.

I understand what you're saying. Xp was the first OS to go in and then Vista. Booting that way is Ok. I know I can see bootmgr but I didn't see ntldr file

> **TeXtonyx said:**
> I point this out because this 'earlier version of OS' it not on
some other XP partition, you will not boot another XP installation.
If you want to boot a different XP partition it needs to have the
boot files installed, you need to know its partition, which isn't
the same as the Vista partition where you can also boot an XP OS.

What I would like to be able to do is to have one boot menu, rather the going through 2. Meierfra understood what I want. As you can see Grub stage 2 was at hd2,0 which according to windows disk management is Ubuntu installation. Now grub stage 2 returns hd0,0.


> **TeXtonyx said:**
> Do not forget to intall grub in the Ubuntu boot partition, not to 
the MBR. It is part of the instructions of the manual Vista boot
loader method. "Step 1 – Install GRUB on the Linux partition (outside of MBR)
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

I believe that was the case but trying to use EasyBCD and edit Vistas boot loader to add Ubuntu was not working because EasyBCD was looking to find boot files at D drive=XP drive. I think I posted debug mode of EasyBCD output after I tried to add Ubuntu to it with grub being on hd2,0

> **TeXtonyx said:**
> That screen you saw with the choice of Vista and 'earlier OS' 
should eventually have Ubuntu on it and if you have another XP
OS installed, a choice to boot to that XP partition which is not
the same XP OS offered in 'earlier OS'.

I am trying to understand this. 


> **TeXtonyx said:**
> On one of my computers, I have XP and Ubuntu on first drive.
I have Vista and OpenSuse on the other drive. I boot to XP,
which lets me pick Ubuntu or OpenSuse. I used the install grub
to the boot partition method and I used 512 boot sector method.
From Ubuntu, I can choose Vista. When you use Vista bootloader,
and choose Ubuntu, it still opens the grub menu.lst and you
choose Ubuntu again, so this doesn't work quite as directly as
you might have hoped. The main reason to boot this way which
requires putting Linux into the boot sector and a Linux.bin is
that if Linux fails it doesn't interfere with Windows. And if
Windows fails you can still boot Linux with the Super Grub disk.
Neither grub nor XP or Vista will offer an all inclusive direct
solution (I doubt grub will boot the Vista choice of 'earlier 
version OS'). I think you need to choose earlier OS from Vista.

So you are saying that I can not have one boot menu, and that I need to got through 2 instead of 1 

> **TeXtonyx said:**
> If you are having trouble understanding what is on your partitions and
where, I think you could profitably augment your information by using
Vista/XP Administrative Tools -> Computer Management -> Disk Management
which provides a more pictorial view. You should be able to use EasyBCD,
everybody else can, which is why I think you could use more information.

I posted a link to a screen shot of Vistas disk management. XP and Vista are on separate hard drive and Ubuntu on a 250Gb partition out of 500. Other 250 is free

---

### Post by meierfra. on 2008-10-23
It seems that installing grub was successful. 

But we still have not found your boot files. Looking at your "ls" output from post 18 and 23 it seems that the device names for you hard drive are changing.  So sometimes your Windows drive is sdb and other times sdc.
Thus we need to look at sdb and sdc  at the same time. Post the output of 

```
sudo fdisk -lu
sudo mkdir /mnt/sdb1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdc1 /mnt/sdc1
ls -l /mnt/sdb1
ls -l /mnt/sdc1
```

>  are saying that I can not have one boot menu, and that I need to got through 2 instead of 1 
Technically you will be going through two boot menus. But if you use "hiddenmenu" and "timemout 1" in menu.lst, you will not notice  the grub menu. 
("hiddenmenu" means that the grub menu will not be displayed. "timeout 1" means that Ubuntu will be booted automatically after 1 second.)

---

### Post by TeXtonyx on 2008-10-23
Quote:
are saying that I can not have one boot menu, and that I need to got through 2 instead of 1

Yes, you can make the transition just about automatic. I told you
about this in case you were thinking the Vista bootloader could
directly replace grub and menu.lst , just in case you thought that
you could bypass having the Ubuntu bootloader work correctly. 

If I missed where you implied that you wanted it to _appear_ that
you had just one bootloader for purely cosmetic reasons rather than
one bootloader handling all the functionality (so you could bypass
any concern about grub/menu.lst) excuse me. I'm used to customers
arriving at odd conclusions so perhaps I was too suspicious. It's
also why I usually repeat things twice, redundantly. :-)

The grub bootloader process has to work properly even if you don't see
the menu and even if the default boots within an unnoticeable second. So
you can't circumvent having grub/menu work right even if you don't see 
it. Just ignore my comment if you weren't even thinking such a thing! And
just wanted it to look smooth.

---

### Post by TeXtonyx on 2008-10-24
I have more skills with Windows than Linux, but reading through 
these posts left me with some questions.
----------------------------------

acdcfan wrote:
According to my Windows Device manager I have XP on hdd0, Vista 
hdd1 and Ubuntu on hdd2 partition 1
[first command]

title Windows (hd1)
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
chainloader +1

When I enter first command it takes me straight to Vistas boot loader but second command takes me to Press any key to boot.....
-----------------------------------

TeX: He said he booted to Vista. hd2 = sdc doesn't seem to be a
possibility with the above configuration. Yet it seemed like both
of you agreed that Vista was on sdc?

Quote:
Originally Posted by meierfra. 
Am I correct that sdb1 is your XP partition and sdc1 your Vista Partition?

acdcfan replied: Yer you are... 

-----------------------------------

Another seeming discrepancy:
"According to my Windows Device manager I have XP on hdd0, Vista hdd1 and Ubuntu on hdd2 partition 1"

Here is Fdisk -l output

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92341f71

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 83 Linux
/dev/sda2 30402 60802 244188160 7 HPFS/NTFS

 Device Boot Start End Blocks Id System
/dev/sdb1 * 1 60800 488375968+ 7 HPFS/NTFS

 Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60801 488384001 7 HPFS/NTFS

------------------------------------

Tex: fdisk reports that Linux is installed on sda1 and shares
with sda2=NTFS
How does that fit with acdcfan's report that the Windows device
manager says Linux is on sdc1? And not on sda1? The two reports
from [http://img49.imageshack.us/img49/7039/captureiq6.jpg](http://img49.imageshack.us/img49/7039/captureiq6.jpg) and
fdisk are very conflicted.

----------------------------------- and finally

here is the output of
sudo mount /dev/sdb1 /mnt

ls -l /mnt 

"drwxrwxrwx 1 root root 0 2008-03-21 21:47 PerfLogs"

---------------

TeX: This doesn't look like the root of an XP directory, so it
doesn't support the assumption that XP is on sdb1. I've seen 
PerfLogs on Vista partitions, not XP as far as I can recall. 

The image of the device manager report of drives. It has drive
D: listed first and on a different drive than C: listed second.
I think C: and D: may be two partitions but on the same drive. 
That still doesn't explain why Linux doesn't show up as unknown
but healthy for drive 0 or drive 1, but only NTFS, contrary to
the fdisk report.

---

### Post by acdcfan on 2008-10-24
> **TeXtonyx said:**
> I have more skills with Windows than Linux, but reading through 
these posts left me with some questions.
----------------------------------


-----------------------------------
[QUOTE=TeXtonyx;6023698]
TeX: He said he booted to Vista. hd2 = sdc doesn't seem to be a
possibility with the above configuration. Yet it seemed like both
of you agreed that Vista was on sdc?

I came to that conclusion by looking at the used space on each drive at initial Ubuntu install. I know I Can identify XP by 9 or 10Mb of unformatted/unused space 
This is how I came to that conclusion 

XP 500gb hd0 (usdes psace 150Gb) and it has 9mb of unallocated space
Vista 500gb hd1 used space 46
Ubuntu 250gb hd2,1 
first partitition dev/sda1 250gb. second partition dev/sda2 250gb no used space... which is my 3rd hdd
sdb 500gb used space smiliar to vistas .
sdc 500 gb used space similar to Xp with 9mb of free space
sdd 1000gb exetrnal hdd 
 

> **TeXtonyx said:**
> Quote:
Originally Posted by meierfra. 
Am I correct that sdb1 is your XP partition and sdc1 your Vista Partition?

acdcfan replied: Yer you are... 


I was bloody wrong all this time 
-----------------------------------
> **TeXtonyx said:**
> 
Another seeming discrepancy:
"According to my Windows Device manager I have XP on hdd0, Vista hdd1 and Ubuntu on hdd2 partition 1"

Here is Fdisk -l output

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92341f71

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 83 Linux
/dev/sda2 30402 60802 244188160 7 HPFS/NTFS

 Device Boot Start End Blocks Id System
/dev/sdb1 * 1 60800 488375968+ 7 HPFS/NTFS

 Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60801 488384001 7 HPFS/NTFS

------------------------------------

Tex: fdisk reports that Linux is installed on sda1 and shares
with sda2=NTFS
How does that fit with acdcfan's report that the Windows device
manager says Linux is on sdc1? And not on sda1? The two reports
from [http://img49.imageshack.us/img49/7039/captureiq6.jpg](http://img49.imageshack.us/img49/7039/captureiq6.jpg) and
fdisk are very conflicted.

----------------------------------- and finally

here is the output of
sudo mount /dev/sdb1 /mnt

ls -l /mnt 

"drwxrwxrwx 1 root root 0 2008-03-21 21:47 PerfLogs"

Is there anything else that I can do just to prove that I do have 3Hdd in my rig. 
Something must be very screwed up 

---------------
> **TeXtonyx said:**
> 
TeX: This doesn't look like the root of an XP directory, so it
doesn't support the assumption that XP is on sdb1. I've seen 
PerfLogs on Vista partitions, not XP as far as I can recall. 

The image of the device manager report of drives. It has drive
D: listed first and on a different drive than C: listed second.
I think C: and D: may be two partitions but on the same drive. 
That still doesn't explain why Linux doesn't show up as unknown
but healthy for drive 0 or drive 1, but only NTFS, contrary to
the fdisk report.

Tex 
I assure you that I have 3 hard drives in my computer and one USB external drive. 
 I know I purchased 2 500Gb HDD at time of built. 
XP is on its own drive, Vista is on its own drive and Ubuntu on partitioned 500gb drive. I can show you BIOS output that I have 3 hdd, at least BIOS can not tell a lie. 
XP drive is is SATA port 3, Vista drive in SATA port 4 and Ubuntu is on pci SATA controller and that is the part I can not figure out

---

### Post by TeXtonyx on 2008-10-24
Tex
I assure you that I have 3 hard drives in my computer and one USB external drive.
I know I purchased 2 500Gb HDD at time of built.
XP is on its own drive, Vista is on its own drive and Ubuntu on partitioned 500gb drive. I can show you BIOS output that I have 3 hdd, at least BIOS can not tell a lie.
XP drive is is SATA port 3, Vista drive in SATA port 4 and Ubuntu is on pci SATA controller and that is the part I can not figure out

TeX: Ok. Just to check, when you used Easybcd, did you change the
the active window from "Windows" to "Linux" in the area where one
adds an entry. Ubuntu should be found under Linux ... just an idea

[http://www.linuxquestions.org/questions/linux-software-2/grub-problem-error-21-sata-controller-promise-pdc20376-390669/](http://www.linuxquestions.org/questions/linux-software-2/grub-problem-error-21-sata-controller-promise-pdc20376-390669/)

His problem sounds sort of like yours, he had a Promise controller.
I notice other sata problems using "Search" at the top of the
Ubuntu forum page. I think of having a Windows bootloader and a
grub bootloader, each capable of booting all OS, as having backup.

---

### Post by meierfra. on 2008-10-24
> I was bloody wrong all this time 

No, you were not.  As I said in post 25, XP seems to be sometimes on  sdb and other times on sdc.  Don't worry about it, it shouldn't cause any problems.  Just post the information I requested in post 25, so that I can see where the boot files are located.

---

### Post by TeXtonyx on 2008-10-24
I found this post which seems relevant. I think the most likely 
location of the sets of boot files is sda. From Vista, one should
be able to click on XP drive 0, and see what boot files are found.
-----------------------------

Heron won't boot -> Grub error 22
I solved it !!

When i installed ubuntu under the livecd my first obboard hardrive was hd2 because my 2 sata hardrives on a pci controller where seen as hd0 and hd1 by the livecd system.

When i rebooted the machine finds my oboard controller first and used the / drive as hd0 instead of hd2 and therefore the grub settings are incorrect.

When i manually change the grub entry like the above poster suggests i was able to actually get it to boot normally and 8.04 works absolutly fine for me but the same happens as in the livecd my harddrive is found as hd2 again so when trying to do the 'find' command under grub is still find my root as (hd2,2) wich would be correct for the os but not for grub... so this command won't fix the problem and root=(hd0,2) is not accepted by grub because it says "the file or partition does not excist." wich is true aswell

The answer is to simply change the entry's for all tree boot option from hd2,2 to hd0,2 in /boot/grub/menu.lst ones you have initially booted by using e (edit) command in grub when it fails.

i hope this helped anyone ho has a similar problem !!

-------------------------------------------------------

TeX: It seems like the sata controller must be part of the reason
that sudo fdisk -l is returning sda as housing Ubuntu, when in
fact Ubuntu is on the third drive, sdc.

---

### Post by acdcfan on 2008-10-25
> **meierfra. said:**
> No, you were not.  As I said in post 25, XP seems to be sometimes on  sdb and other times on sdc.  Don't worry about it, it shouldn't cause any problems.  Just post the information I requested in post 25, so that I can see where the boot files are located.

Here is the output  

[COLOR="Red"]rastko@rastko-desktop:~$ sudo fdisk -lu
[sudo] password for rastko: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x250024ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976751999   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x251e251d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92341f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001   83  Linux
/dev/sdc2       488392704   976769023   244188160    7  HPFS/NTFS

Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1              63  1953520064   976760001    7  HPFS/NTFS
rastko@rastko-desktop:~$ sudo mkdir /mnt/sdb1
rastko@rastko-desktop:~$ sudo mount /dev/sdb1 mnt/sdb1
fuse: failed to access mountpoint mnt/sdb1: No such file or directory
rastko@rastko-desktop:~$ sudo mount /dev/sdc1 /mnt/sdc1
rastko@rastko-desktop:~$ ls -l /mnt sdb1
ls: cannot access sdb1: No such file or directory
/mnt:
total 2050016
-rw-r--r--  1 root root 2097152000 2008-08-31 11:21 2000Mb.swap
drwxr-xr-x  2 root root       4096 2008-10-26 10:58 sdb1
drwxr-xr-x 23 root root       4096 2008-10-17 18:31 sdc1
drwxr-xr-x  2 root root       4096 2008-10-23 19:20 sdh1
rastko@rastko-desktop:~$ ls -l /mnt/sdc1
total 5125124
drwxr-xr-x   2 root root       4096 2008-08-29 22:09 bin
drwxr-xr-x   3 root root       4096 2008-10-17 18:31 boot
lrwxrwxrwx   1 root  999         11 2008-09-01 04:08 cdrom -> media/cdrom
drwxr-xr-x   4 root root       4096 2008-07-02 18:26 dev
drwxr-xr-x 124 root root      12288 2008-10-26 10:59 etc
drwxr-xr-x   3 root root       4096 2008-09-01 04:16 home
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 initrd
lrwxrwxrwx   1 root root         33 2008-10-17 18:31 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root  999         33 2008-09-01 12:18 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root      12288 2008-09-29 14:37 lib
drwx------   2 root root      16384 2008-09-01 04:08 lost+found
drwxr-xr-x   4 root root       4096 2008-10-26 10:57 media
-rw-r--r--   1 root root 5242880000 2008-08-30 21:15 media.swapfile
drwxr-xr-x   5 root root       4096 2008-10-26 10:58 mnt
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 opt
drwxr-xr-x   2 root root       4096 2008-04-15 13:53 proc
drwxr-xr-x   2 root root       4096 2008-09-07 14:40 $RECYCLE.BIN
drwxr-xr-x   2 root root       4096 2008-10-03 20:34 Recycled
drwxr-xr-x  13 root root       4096 2008-10-22 19:21 root
drwxr-xr-x   2 root root       4096 2008-10-17 18:30 sbin
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 srv
drwxr-xr-x   2 root root       4096 2008-04-19 13:05 sys
drwxrwxrwt  14 root root       4096 2008-10-26 10:57 tmp
drwxr-xr-x  12 root root       4096 2008-08-31 12:32 usr
drwxr-xr-x  15 root root       4096 2008-07-02 18:34 var
lrwxrwxrwx   1 root root         30 2008-10-17 18:31 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root  999         30 2008-09-01 12:18 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic
rastko@rastko-desktop:~$ 
[/COLOR]

Should I be worried about message above 
*"fuse: failed to access mount point mnt/sdb1:No such file or directory*

Guys I don't know how to thank you enough for taking time to help me.

Regards 
acdcfan

---

### Post by meierfra. on 2008-10-25
> Should I be worried about message above
"fuse: failed to access mount point mnt/sdb1:No such file or directory

No, you just had a typo:

It's supposed to be  "sudo mount /dev/sdb1 /mnt/sdb"  not  "sudo mount /dev/sdb1 mnt/sdb". Please use copy and paste instead of typing the commands yourself.  


Well, the device names are shifting around even more than I thought. The ubuntu drive is now sdc and your 1000GB drive sdd. Are you doing anything which might cause these changes? 

I'm pretty sure that the boot files are on the XP partition, so we could continue without  definite proof. But it still I still want to give it one more try:
Post the output of 

```
sudo fdisk -lu
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdc1 /mnt/sdc1
ls -l /mnt/sda1
ls -l /mnt/sdb1
ls -l /mnt/sdc1
```


Did you try booting from the XP drive yet? (that would also confirm that the boot files are on the XP drive)

---

### Post by meierfra. on 2008-10-25
If you want you can also start on adding Ubuntu to the Vista boot loader.
Since you device names are shifting, I'm changing the instructions slightly.


```

cd  ~/Desktop
sudo dd if=/dev/sdX1 of=Ubuntu.bin count=1
sudo chown rastko Ubuntu.bin
```

Here /dev/sdX1  has  to be your Ubuntu partition. So you need to look at "sudo fdisk -lu"  to determine what "X" is. If the Ubuntu partition happens to be "/dev/sdc1" use "/dev/sdc1" in place of "/dev/sdX1", ...

(be very careful with the "dd" command. It can be dangerous)

You should now have a file with the name "Ubuntu.bin" on your desktop. Just move this file to your XP partition.

Next you need to instruct the Vista Boot loader to use "Ubuntu.bin" to boot Ubuntu:


Boot into Vista, click on Start. Type "cmd" and press "CTRL+SHIFT+ENTER". This will run a command line as administrator.

Type

```


    bcdedit /create /d "Ubuntu" /application BOOTSECTOR

    bcdedit /set {ID} device boot

 (where ID is the  very long number which you will get after the first command)
    
     bcdedit /set {ID} PATH \Ubuntu.bin

     bcdedit /displayorder {ID} /addlast 

     bcdedit /timeout 5

```

(The last line sets the time (in seconds) until the Vista boots the default entry. )

---

### Post by acdcfan on 2008-10-26
> **meierfra. said:**
> No, you just had a typo:

It's supposed to be  "sudo mount /dev/sdb1 /mnt/sdb"  not  "sudo mount /dev/sdb1 mnt/sdb". Please use copy and paste instead of typing the commands yourself.  

Thanks I will do that 


> **meierfra. said:**
> Well, the device names are shifting around even more than I thought. The ubuntu drive is now sdc and your 1000GB drive sdd. Are you doing anything which might cause these changes? 

No. I am not doing anything.... Wouldn't know how to change partitions. If you say that Ubuntu is sdc partition now, I believe this is how it should be, if Windows device manager is anything to go by.
I just start the computer, let it go through BIOS post process. Let it get to GRUB boot loader and boot Ubuntu.
 
> **meierfra. said:**
> 
I'm pretty sure that the boot files are on the XP partition, so we could continue without  definite proof. But it still I still want to give it one more try:

I am sure too, because I knwo for the fact that XP was first OS to be installed. 
> **meierfra. said:**
> 
Post the output of 

```
sudo fdisk -lu
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdc1 /mnt/sdc1
ls -l /mnt/sda1
ls -l /mnt/sdb1
ls -l /mnt/sdc1
```

Let me restart. 

> **meierfra. said:**
> 
Did you try booting from the XP drive yet? (that would also confirm that the boot files are on the XP drive)

I am going to try to boot form disk in SATA port 4 but that's where Vista is. XP should be in SATA port3

**I tried booting of drive in SATA port4 and nothing. just a flashing "-". Just for testing purposes tried booting of SATA port 3 drive and got only Vistas boot loader screen with options of earlier version of windows or Vista**

---

### Post by TeXtonyx on 2008-10-26
Here is an earlier fdisk report:
-------------------------------
Here is Fdisk -l output

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x92341f71

Device Boot Start End Blocks Id System
/dev/sda1 * 1 30401 244196001 83 Linux  <------
/dev/sda2 30402 60802 244188160 7 HPFS/NTFS

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 60800 488375968+ 7 HPFS/NTFS

Device Boot Start End Blocks Id System
/dev/sdc1 * 1 60801 488384001 7 HPFS/NTFS
------------------------------------------

Here is the latest fdisk report in Post #32

astko@rastko-desktop:~$ sudo fdisk -lu
[sudo] password for rastko:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x250024ff

Device Boot Start End Blocks Id System
/dev/sda1 * 63 976751999 488375968+ 7 HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x251e251d

Device Boot Start End Blocks Id System
/dev/sdb1 * 63 976768064 488384001 7 HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92341f71

Device Boot Start End Blocks Id System
/dev/sdc1 * 63 488392064 244196001 83 Linux <-----
/dev/sdc2 488392704 976769023 244188160 7 HPFS/NTFS
-------------------------------------------------

TeX: Notice that the reports switch sda and sdc information.
The first report has Linux on sda and the second report on sdc.
From your description and the Windows pictorial report, we know
that the second report is correct. The HPFS/NTFS partition on
/dev/sdc2 is called M: in the Windows report, 007's boss.

I have a theory that perhaps all the boot files are on drive 0=XP
and this is confusing Easybcd, maybe fdisk. Not sure about the
sata controller yet. Perhaps the boot files should be changed so
that if Vista files are all on XP they can be moved over to Vista.
If all the boot files are on XP, what happens if that drive goes down? 
How to boot Vista? Too much like having all your shifty eggs in one basket.
The question is if both XP and Vista boot files are all on the XP partition?

---

### Post by acdcfan on 2008-10-26
> **meierfra. said:**
> 

```
sudo fdisk -lu
sudo mkdir /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
sudo mount /dev/sdc1 /mnt/sdc1
ls -l /mnt/sda1
ls -l /mnt/sdb1
ls -l /mnt/sdc1
```


Here it is again

[COLOR="DarkRed"]rastko@rastko-desktop:~$ sudo fdisk -lu
[sudo] password for rastko: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x250024ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   976751999   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x251e251d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   976768064   488384001    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x92341f71

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *          63   488392064   244196001   83  Linux
/dev/sdc2       488392704   976769023   244188160    7  HPFS/NTFS

Disk /dev/sdh: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x969b09a3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1              63  1953520064   976760001    7  HPFS/NTFS
rastko@rastko-desktop:~$ sudo mkdir /mnt/sda1
rastko@rastko-desktop:~$ sudo mount /dev/sda1 /mnt/sda1
rastko@rastko-desktop:~$ sudo mount /dev/sdb1 /mnt/sdb1
rastko@rastko-desktop:~$ sudo mount /dev/sdc1 /mnt/sdc1
rastko@rastko-desktop:~$ ls -l /mnt/sda1
total 2096033
-rwxrwxrwx 1 root root          0 2008-02-01 22:09 AUTOEXEC.BAT
drwxrwxrwx 1 root root       4096 2008-03-21 21:58 Boot
-rwxrwxrwx 1 root root        355 2008-02-03 09:31 Boot.BAK
-rwxrwxrwx 1 root root        355 2008-05-29 18:14 boot.ini
-rwxrwxrwx 1 root root     333203 2008-01-19 16:45 bootmgr
-rwxrwxrwx 1 root root       8192 2008-02-03 09:31 BOOTSECT.BAK
drwxrwxrwx 1 root root       4096 2008-10-21 19:27 BOSPL
drwxrwxrwx 1 root root       4096 2008-10-02 20:27 Config.Msi
-rwxrwxrwx 1 root root          0 2008-02-01 22:09 CONFIG.SYS
drwxrwxrwx 1 root root       4096 2008-06-15 19:25 Documents and Settings
-rwxrwxrwx 1 root root     171136 2007-03-17 20:41 grldr
drwxrwxrwx 1 root root          0 2008-02-01 22:13 Intel
-rwxrwxrwx 1 root root          0 2008-02-01 22:09 IO.SYS
-rwxrwxrwx 1 root root          0 2008-02-01 22:09 MSDOS.SYS
drwxrwxrwx 1 root root          0 2008-02-02 17:04 MSOCache
drwxrwxrwx 1 root root          0 2008-10-16 17:20 NST
-rwxrwxrwx 1 root root      47564 2004-08-03 22:38 NTDETECT.COM
-rwxrwxrwx 1 root root     250032 2004-08-03 22:59 ntldr
-rwxrwxrwx 1 root root 2145386496 2008-10-22 18:45 pagefile.sys
drwxrwxrwx 1 root root      12288 2008-10-02 20:35 Program Files
drwxrwxrwx 1 root root          0 2008-02-02 20:21 $RECYCLE.BIN
drwxrwxrwx 1 root root          0 2008-02-02 10:17 RECYCLER
drwxrwxrwx 1 root root       4096 2008-10-25 17:40 System Volume Information
drwxrwxrwx 1 root root          0 2008-06-15 19:30 VProRecovery
drwxrwxrwx 1 root root      98304 2008-10-02 20:35 WINDOWS
rastko@rastko-desktop:~$ ls -l /mnt/sdb1
total 4500850
-rwxrwxrwx 1 root root        230 2008-07-31 21:13 config.xml
drwxrwxrwx 1 root root          0 2006-11-02 23:41 Documents and Settings
drwxrwxrwx 1 root root          0 2008-03-29 10:18 Intel
-rwxrwxrwx 1 root root     904704 2006-12-01 22:37 msdia80.dll
drwxrwxrwx 1 root root          0 2008-02-05 21:42 MSOCache
drwxrwxrwx 1 root root          0 2008-06-29 14:56 NVIDIA
-rwxrwxrwx 1 root root 4607848448 2008-10-26 12:05 pagefile.sys
drwxrwxrwx 1 root root          0 2008-03-21 21:47 PerfLogs
drwxrwxrwx 1 root root       8192 2008-10-04 21:54 ProgramData
drwxrwxrwx 1 root root       8192 2008-09-16 22:09 Program Files
drwxrwxrwx 1 root root      20480 2008-10-25 12:02 Program Files (x86)
drwxrwxrwx 1 root root       4096 2008-02-02 20:21 $Recycle.Bin
drwxrwxrwx 1 root root          0 2008-02-03 21:51 RECYCLER
-rwxrwxrwx 2 root root         52 2008-09-04 20:59 Run_ppccfg.cmd
-rwxrwxrwx 1 root root         45 2008-09-04 21:00 Run_ppc.cmd
drwxrwxrwx 1 root root          0 2008-10-02 20:27 SP
drwxrwxrwx 1 root root      24576 2008-10-27 00:09 System Volume Information
drwxrwxrwx 1 root root          0 2008-07-27 09:01 temp
drwxrwxrwx 1 root root       4096 2008-06-14 16:27 Users
-rwxrwxrwx 1 root root       4096 2008-06-17 22:36 VSNAP.IDX
drwxrwxrwx 1 root root      40960 2008-10-04 21:50 Windows
rastko@rastko-desktop:~$ ls -l /mnt/sdc1
total 5125124
drwxr-xr-x   2 root root       4096 2008-08-29 22:09 bin
drwxr-xr-x   3 root root       4096 2008-10-17 18:31 boot
lrwxrwxrwx   1 root  999         11 2008-09-01 04:08 cdrom -> media/cdrom
drwxr-xr-x   4 root root       4096 2008-07-02 18:26 dev
drwxr-xr-x 124 root root      12288 2008-10-26 13:12 etc
drwxr-xr-x   3 root root       4096 2008-09-01 04:16 home
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 initrd
lrwxrwxrwx   1 root root         33 2008-10-17 18:31 initrd.img -> boot/initrd.img-2.6.24-21-generic
lrwxrwxrwx   1 root  999         33 2008-09-01 12:18 initrd.img.old -> boot/initrd.img-2.6.24-19-generic
drwxr-xr-x  16 root root      12288 2008-09-29 14:37 lib
drwx------   2 root root      16384 2008-09-01 04:08 lost+found
drwxr-xr-x   4 root root       4096 2008-10-26 13:07 media
-rw-r--r--   1 root root 5242880000 2008-08-30 21:15 media.swapfile
drwxr-xr-x   6 root root       4096 2008-10-26 13:12 mnt
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 opt
drwxr-xr-x   2 root root       4096 2008-04-15 13:53 proc
drwxr-xr-x   2 root root       4096 2008-09-07 14:40 $RECYCLE.BIN
drwxr-xr-x   2 root root       4096 2008-10-03 20:34 Recycled
drwxr-xr-x  13 root root       4096 2008-10-22 19:21 root
drwxr-xr-x   2 root root       4096 2008-10-17 18:30 sbin
drwxr-xr-x   2 root root       4096 2008-07-02 18:16 srv
drwxr-xr-x   2 root root       4096 2008-04-19 13:05 sys
drwxrwxrwt  14 root root       4096 2008-10-26 13:12 tmp
drwxr-xr-x  12 root root       4096 2008-08-31 12:32 usr
drwxr-xr-x  15 root root       4096 2008-07-02 18:34 var
lrwxrwxrwx   1 root root         30 2008-10-17 18:31 vmlinuz -> boot/vmlinuz-2.6.24-21-generic
lrwxrwxrwx   1 root  999         30 2008-09-01 12:18 vmlinuz.old -> boot/vmlinuz-2.6.24-19-generic
rastko@rastko-desktop:~$ 
[/COLOR]

It seems that the last two times Linux partition has been reported correctly sdc1

---

### Post by acdcfan on 2008-10-26
> **TeXtonyx said:**
> Here is an earlier fdisk report:
TeX: Notice that the reports switch sda and sdc information.
The first report has Linux on sda and the second report on sdc.
From your description and the Windows pictorial report, we know
that the second report is correct. The HPFS/NTFS partition on
/dev/sdc2 is called M: in the Windows report, 007's boss.

Thats is second partitions with no OS on it. On the first part we have Ubuntu 
> **TeXtonyx said:**
> 
I have a theory that perhaps all the boot files are on drive 0=XP
and this is confusing Easybcd, maybe fdisk. Not sure about the
sata controller yet. Perhaps the boot files should be changed so
that if Vista files are all on XP they can be moved over to Vista.
If all the boot files are on XP, what happens if that drive goes down? 
How to boot Vista? Too much like having all your shifty eggs in one basket.
The question is if both XP and Vista boot files are all on the XP partition?

With easyBCD I have created back of Boot loader so if boot loader fails I can restore it.

---

### Post by TeXtonyx on 2008-10-26
If it turns out all the boot files are on XP, here is how to 
separate them, if you need to do that at some step.

[http://themudcrab.com/separatevistaxp.php](http://themudcrab.com/separatevistaxp.php)

Where are the Booting Files?

In order to view the booting files, you need to enable viewing of 
Hidden and System files and folders.

---

### Post by acdcfan on 2008-10-26
> **TeXtonyx said:**
> If it turns out all the boot files are on XP, here is how to 
separate them, if you need to do that at some step.

[http://themudcrab.com/separatevistaxp.php](http://themudcrab.com/separatevistaxp.php)

Where are the Booting Files?

In order to view the booting files, you need to enable viewing of 
Hidden and System files and folders.

What are the files I need to look for?
I found following files
BOOT.BAK, BOOTSEC.BAK, Boot.ini and bootmgr on XP drive. I couldn't find any files on Vista drive. Do I need to look for other files

Using EasyBCD I made a back up and put it in two different locations. Partition M and external drive K. Also copied following files across: boot.ini, bootmgr and folder called Boot

---

### Post by TeXtonyx on 2008-10-26
Yes, those are the files. I'm pretty sure you should have seen the
XP boot files, boot.ini, ntldr, ntdetect.com. Yes all the boot files
seem to be on XP.

The directions in the link I gave you arent that straight-forward
nor that simple, as your method. There is a folder involved too.

But, before going forward with that link, I think you should wait 
for the input of meierfra, even though I think separating the
boot files is a good idea. If all the boot files were located on
Vista, rather than XP, copying boot.ini, ntldr and ntdetect.com
to XP would nearly be sufficient. I think moving the Vista boot 
files to the Vista partition from XP is more complicated. Maybe 
meierfra will suggest to do something else first.

---

### Post by acdcfan on 2008-10-26
> **TeXtonyx said:**
> Yes, those are the files. I'm pretty sure you should have seen the
XP boot files, boot.ini, ntldr, ntdetect.com. Yes all the boot files
seem to be on XP.

All of which I have copied to two different locations

> **TeXtonyx said:**
> The directions in the link I gave you arent that straight-forward
nor that simple, as your method. There is a folder involved too.

But, before going forward with that link, I think you should wait 
for the input of meierfra, even though I think separating the
boot files is a good idea. If all the boot files were located on
Vista, rather than XP, copying boot.ini, ntldr and ntdetect.com
to XP would nearly be sufficient. I think moving the Vista boot 
files to the Vista partition from XP is more complicated. Maybe 
meierfra will suggest to do something else first.

Copmplicated I agree.... 
You would need two computers to google any potential problems that may arrise in porcess

---

### Post by TeXtonyx on 2008-10-26
I don't know enough about how grub works. I know it scans the drives
and writes a file called menu.lst. There is a section in menu.lst
for Other OS such as Windows. Abbreviated, it looks something like,

Title XP
root (hd0,0)

-----

Title Vista
root (hd1,0)

------------

That is when the boot files are separated each to their own, on
each drive. Suppose all the boot files are on XP = (hd0,0)
How does grub automatically generate two different ways, like in
the above diagram of Title XP and Title Vista, of boot options?
I'm not sure grub is smart enough to see files like bootmgr/Vista
and boot.ini/XP and know it should create two ways to boot the 
OS's, or how grub would write menu.lst so as to distinguish them.
Nor, if this is indeed a difficulty, if it somehow impacts fdisk
discovering drives and correctly identifying them; how did the
two conflicting reports of fdisk about sda and sdc come to pass?

Perhaps meierfra has insights into this since this is his area of
expertise. Like I say, separating the boot files(2 sets) seems like 
a good idea, but look before you leap. When there are complicated
instructions, one way to follow them without the internet is to
print out all the instructions before launching into the project.
Or buy a Mac OS laptop with a wireless connection. :-)

---

### Post by meierfra. on 2008-10-26
> ls -l /mnt/sda1
drwxrwxrwx 1 root root 4096 2008-03-21 21:58 Boot
-rwxrwxrwx 1 root root 355 2008-05-29 18:14 boot.ini
-rwxrwxrwx 1 root root 333203 2008-01-19 16:45 bootmgr
-rwxrwxrwx 1 root root 47564 2004-08-03 22:38 NTDETECT.COM
-rwxrwxrwx 1 root root 250032 2004-08-03 22:59 ntldr


OK. all the boot files are on the XP drive.


>  I tried booting of drive in SATA port4 and nothing. just a flashing "-". Just for testing purposes tried booting of SATA port 3 drive and got only Vistas boot loader screen with options of earlier version of windows or Vista


That's exactly how it is supposed to be at this stage.

Since we will  use the Visa boot loader as the primary boot loader, there is no reason to move or copy any of the boot files. Copying boot files to other locations doesn't  cause any problems. So  just follow the instructions from my previous post (post 34)


Then set your bios to boot from the XP drive. If possible, set the Ubuntu drive to be second in the boot order in the bios.
Booting  from the XP drive will give you the Vista's boot menu, which now should have XP, Vista and Ubuntu on  it. Hopefully selecting Ubuntu will give  you the Grub Menu. But selecting Ubuntu at the grub menu, will produce a Grub Error.  We will worry about that later. (You still will be able to boot into Ubuntu by booting from the Ubuntu drive)

---

### Post by TeXtonyx on 2008-10-28
Well, acdcfan, how did it go?
The silence is a conspicuous pointer.

---

