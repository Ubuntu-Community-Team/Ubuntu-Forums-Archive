---
title: "Uninstalled second HD, now won't boot"
date: 2009-01-01
forum: Installation &amp; Upgrades
---

### Post by lildoggie on 2009-01-01
Hi,

I apologize if there are other articles on this, but my search didn't result in anything that worked for me...

My system had 2 HDs in it: 1 80G running XP, and 1 120G running Ubuntu.  Grub would ask which I wanted to run, defaulting to Ubuntu, and all worked just great.

I decided I wanted to use the 80G drive in a different machine, but when I removed it, I got an error that the computer couldn't load the operating system.   I figured, "OK, so the boot loader is on the 80G drive.  All I need to do is install a boot loader (i.e. grub) on the 120G."

Well, this seemed trivial, but it hasn't worked out that way.  I'm sure I'm making some simple mistake, but I can't find it....

I tried booting from a "SystemRescueCD" and doing the instructions to install grub as follows:
```
sudo grub
grub> find /boot/grub/stage1 <-- find all Linux partitions
grub> root (hd1,2) <-- select the partition that has
/boot/grub/menu.lst
grub> setup (hd0) <-- drive that boots – usually hd0
grub> quit
```
Unfortunately, the "find" command didn't find anything (though the stage1 file definitely exists in the /boot/grub directory).

I knew there was only 1 HD in the system, and that it was set up with only 1 partition, so I tried ```
root (hd0,0)
setup (hd0)
``` which just results in a blinking cursor when I try to boot (i.e. no error about not being able to load the op sys, but no booting progress, either).

I also tried using a LiveCD for 8.10, but the same commands didn't make any difference.  

In addition, I tried the set of commands for mounting the drives manually: ```
$ sudo mkdir /mnt/root
$ sudo mount -t ext3 /dev/sda6 /mnt/root
$ sudo mount -t proc none /mnt/root/proc
$ sudo mount -o bind /dev /mnt/root/dev
$ sudo chroot /mnt/root /bin/bash
``` which was supposed to be followed by executing the previous commands as well.  However, I couldn't get the chroot to succeed, as it said it couldn't find /bin/bash.

Incidentally, if I put the 80G HD back in, everything boots just fine, so I know the installation is all still OK.  I really want to keep the same installation setup that I've already got rather than reinstalling and reconfiguring everything...

Any thoughts on how I can get this thing to boot properly?

Thanks!

andy

---

### Post by Pumalite on 2009-01-01
Put the second hard drive back in and post:
sudo fdisk -lu

---

### Post by lildoggie on 2009-01-01
Here is the output:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  SystemDisk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156296384    78148161    7  HPFS/NTFS

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63      498014      248976   83  Linux
/dev/hdb2          498015   234436544   116969265    5  Extended
/dev/hdb5          498078   234436544   116969233+  8e  Linux LVM
```
Thanks!

---

### Post by caljohnsmith on 2009-01-01
In order to get a clearer picture of your setup, how about booting your Live CD (the Ubuntu install CD), open a terminal (Applications > Accessories > Terminal) and do:
```
cd ~/Desktop && wget 'http://home.comcast.net/~ubuntu_grub/boot_info_script.txt' && sudo bash boot_info_script.txt
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your problem might be.

---

### Post by doglover56 on 2009-01-01
What about the ide cable, the jumpers on the drive?
Since it is the only drive in the machine, do you
have it configured properly to even be recognized?
If you removed the master, some hardware won't deal
with just a slave drive, etc.

Irwin

---

### Post by lildoggie on 2009-01-01
Thanks for the script.  I ran it, and have attached the results (to make the size of the reply more manageable).

Does this help?

Thanks!

andy

---

### Post by lildoggie on 2009-01-01
> **doglover56 said:**
> What about the ide cable, the jumpers on the drive? Since it is the only drive in the machine, do you have it configured properly to even be recognized? If you removed the master, some hardware won't deal with just a slave drive, etc.Thanks for the reply.  I've got both drives configured as "cable select" and then put the master header on the single drive when I unplugged the other one, so I'm pretty sure that's not the issue, unfortunately (it'd sure be nice if it were that simple!)

---

### Post by caljohnsmith on 2009-01-01
Your device labels are changing, because the original fdisk output that you posted does not match the drives shown in the output of that script. How about doing the following:
```
sudo fdisk -l
```
And if for whichever drive is the Ubuntu drive, for example sdb, do:
```
sudo grub
grub> device (hd0) /dev/[COLOR="Blue"]sdb[/COLOR]
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
So be sure not to change anything else about the above commands except for "sdb" in case the Ubuntu drive is different. Next, to install a Windows MBR to your Windows drive do:
```
sudo lilo -M  /dev/[COLOR="Blue"]sda[/COLOR] mbr
```
But replace "sda" with the Windows drive if it is different. Then you should be able to boot either drive independent of each other, and regardless if you remove one from your setup. How about giving that a shot and let me know how it goes.

---

### Post by lildoggie on 2009-01-01
Thanks for the reply.  I did as you suggested including the "device (hd0) /dev/hdb"  (in my case), and the results looked encouraging when I ran "setup (hd0)"

Unfortunately, when I try to boot it, I still just get the black screen with the blinking cursor in the top corner... 

Any other ideas?  I'm guessing there's something going on that I've forgotten about (or didn't know about in the first place)...

andy

---

### Post by caljohnsmith on 2009-01-01
Did you run the lilo command? Because otherwise you might be trying to boot your Windows drive which also has Grub installed in the MBR. Which drive do you boot on start up?

---

### Post by lildoggie on 2009-01-01
> **caljohnsmith said:**
> Did you run the lilo command? Because otherwise you might be trying to boot your Windows drive which also has Grub installed in the MBR. Which drive do you boot on start up?
No, I didn't -- but I disconnected the windows drive and changed the cables so the Ubuntu drive is the primary drive (and the only drive).  The reason I didn't run the Lilo command is that I'm planning to wipe that drive anyway...

All this hassle makes me wonder if it might be easier to wipe that disk (other than the boot stuff), copy all the ubuntu stuff over (only about 8 or 9 GB worth), and then get it working on the smaller drive (though I ultimately would like to have the larger drive with Ubuntu on it...)

whaddya think?

andy

---

### Post by caljohnsmith on 2009-01-01
Instead of using "cable select", since that drive is now the master drive, can you set its jumper to master and see if that makes a difference? If not, you might have an issue with how the drive is configured in BIOS.

---

### Post by lildoggie on 2009-01-01
> **caljohnsmith said:**
> Instead of using "cable select", since that drive is now the master drive, can you set its jumper to master and see if that makes a difference? If not, you might have an issue with how the drive is configured in BIOS.Unfortunately, that makes no difference.  If I set the jumper to "master" it actually didn't recognize it at all, but removing the jumper helped the system to recognize the drive just fine (but the result was the same as when using "cable select").

The drive in the BIOS is configured using AUTO settings, and shows 120GB (which it is).  That's also the same settings used when booting with the other drive (which is configured with AUTO settings and shows 80GB, which is also accurate).

Any other ideas?

Thanks!

andy

---

### Post by caljohnsmith on 2009-01-01
If you change the AUTO setting for the drive in BIOS, what are the other options? How about trying them to see if it makes any difference? You can revert back to AUTO after trying.

---

### Post by lildoggie on 2009-01-01
> **caljohnsmith said:**
> If you change the AUTO setting for the drive in BIOS, what are the other options? How about trying them to see if it makes any difference? You can revert back to AUTO after trying.Unfortunately, it's either AUTO or OFF (which doesn't scan for it at all)....

---

### Post by caljohnsmith on 2009-01-01
I don't know then, because if your BIOS doesn't give you any other HDD-related options, I'm not sure what else you can do to get it working. So you're sure your BIOS doesn't have any settings like LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc that you can tweak? If not, I guess your idea of putting Ubuntu on the other drive sounds like it may be your best option. Good luck and let me know how it goes. :)

---

### Post by lildoggie on 2009-01-01
> **caljohnsmith said:**
> I don't know then, because if your BIOS doesn't give you any other HDD-related options, I'm not sure what else you can do to get it working. So you're sure your BIOS doesn't have any settings like LBA, CHS, RAID, AHCI/HCI/EHCI vs. IDE, IDE-emulation, ACPI, DMA, etc that you can tweak? If not, I guess your idea of putting Ubuntu on the other drive sounds like it may be your best option. Good luck and let me know how it goes. :)
Yeah, I'm thinking that may be the best option at this point....  What's the best way to wipe that drive and copy the Ubuntu installation over to it?  Since it's just 9GB or so, and the target drive is smaller, I know I can't use dd to do it...

thoughts?

---

### Post by caljohnsmith on 2009-01-01
> **lildoggie said:**
> Yeah, I'm thinking that may be the best option at this point....  What's the best way to wipe that drive and copy the Ubuntu installation over to it?  Since it's just 9GB or so, and the target drive is smaller, I know I can't use dd to do it...

thoughts?
Assuming your Ubuntu partition is small enough to fit on your smaller drive, you could use Ubuntu's partition editor gparted to simply copy/paste the Ubuntu partition to the new drive. You would first want to delete whichever existing partitions you have on that drive with gparted, and once that space is unallocated, gparted should let you do a simple copy/paste of the Ubuntu partition. How about giving that a shot and let me know how it goes.

---

### Post by lildoggie on 2009-01-01
> **caljohnsmith said:**
> Assuming your Ubuntu partition is small enough to fit on your smaller drive, you could use Ubuntu's partition editor gparted to simply copy/paste the Ubuntu partition to the new drive. You would first want to delete whichever existing partitions you have on that drive with gparted, and once that space is unallocated, gparted should let you do a simple copy/paste of the Ubuntu partition. How about giving that a shot and let me know how it goes.My partition takes the full size, so it won't fit -- can gparted change the size of the partition as well so that I can make it fit?  Since the new partition is NTFS, I obviously would want to reformat it (though I guess I don't need to do that if I'm doing a partition copy, right?)

---

### Post by caljohnsmith on 2009-01-01
> **lildoggie said:**
> My partition takes the full size, so it won't fit -- can gparted change the size of the partition as well so that I can make it fit?  Since the new partition is NTFS, I obviously would want to reformat it (though I guess I don't need to do that if I'm doing a partition copy, right?)
Since your existing Ubuntu partition is too big for your smaller drive, I think instead what I would do is create an ext3 partition on the smaller drive, and then copy over your entire Ubuntu install with "cp -ax". I've done that before so I know it works, there are only a few details to take care of after doing that. Once you create the new partition on the smaller drive, say "sdaX", and if your current Ubuntu is on say "sdbY", then you could do the following from the Live CD:
```
sudo mkdir /mnt/sdaX /mnt/sdbY
sudo mount /dev/sdaX /mnt/sdaX
sudo mount /dev/sdbY /mnt/sdbY
sudo cp -ax /mnt/sdbY/* /mnt/sdaX/.
```
Afterwards, you would have to reinstall Grub, transfer the UUID of your old partition, and maybe tweak your menu.lst, but that's about all. I can help you with the details if you want, so if you want to use that method, first copy over Ubuntu and post the new output of:
```
sudo fdisk -lu
```
And identify your partitions. We can work from there if you want.

---

### Post by lildoggie on 2009-01-01
Sounds good.  I'll see what I can figure out and get back to you.

Thanks!

andy

---

### Post by lildoggie on 2009-01-01
Ok, so I booted to the LiveCD, ran gparted, and tried to resize my ntfs partition (it's got a little more than 20G free, so I was going to try to make an ext3 partition about that size).  Didn't work (I tried putting the free space at the beginning of the disk -- no go, and at the end of the disk -- also no go...)

I suppose I can just format the entire partition as ext3, but that seems a bit drastic (though maybe it's my only hope at this point)...  Would that affect the bootable status of the drive?  (that's the one thing I *really* don't want to do!)

Is there something else I could do to create the ext3 partition on the 80gig drive?  (sorry for the simple questions -- I'm feeling mighty clueless on all this!)

Thanks!

andy

---

### Post by caljohnsmith on 2009-01-02
Is your NTFS partition almost full? Although gparted is supposed to have the capability to handle a fragmented file structure for NTFS partitions, you could first try defragmenting your NTFS partition and see if that helps. Otherwise I'm not sure why gparted wouldn't let you resize the partition. After defragmenting, how about running gparted with the following command from a terminal:
```
gksudo gparted
```
And then gparted will output all of its errors and other messages to the terminal. Please let me know what error/warning messages gparted outputs to the terminal when you try to resize the partition. That might give us some clues what is going on.

---

### Post by lildoggie on 2009-01-02
The NTFS partition has over 20G free, so it should have plenty of space.  I didn't think about defragmenting, so I'll give that a shot and see if it changes, and let you know...

Thanks!

andy

---

### Post by lildoggie on 2009-01-02
Well, now the XP installation won't even boot (I don't know how long it's been since it's been successfully booted, as I've been running Ubuntu pretty much exclusively on it -- just kept it around "just in case" (so I'm glad I didn't need it!)

So, with that as the situation, I don't see much harm in just wiping that partition completely and doing the copy as you suggested (as long as it doesn't mess up the boot-ability of the system).  

What's the best way to format that drive?  I believe my current Ubuntu installation is ext2 -- I'm guessing that my 6.06 installation can use ext3, correct?

Thanks!

andy

---

### Post by caljohnsmith on 2009-01-02
> **lildoggie said:**
> 
What's the best way to format that drive?  I believe my current Ubuntu installation is ext2 -- I'm guessing that my 6.06 installation can use ext3, correct?

Thanks!

andy
Yes, I would go ahead and use ext3. If you want a quick and geeky way of "formatting" the drive, you could do:
```
sudo dd if=/dev/zero of=/dev/[COLOR="Blue"]sdX[/COLOR] count=1
```
And replace "sdX" with the drive you want to format (and as you can imagine, please be careful to pick the correct drive). You can see a list of drives and their partitions by doing:
```
sudo fdisk -l
```
The first "dd" command above will zero-out the MBR (Master Boot Record) of the drive so that the drive appears clean and ready for repartitioning. It doesn't actually "format" the whole drive with zeroes since that is not really necessary, it just makes the drive appear blank and unpartitioned. Then when you open gparted on it, first select Device > Create Partition Table, create an MS-DOS partition table on it, and then you should be ready to partition it as you please.

---

### Post by lildoggie on 2009-01-02
So, just to be clear: the dd command that zeros out the MBR won't affect the ability to boot from that disk, right?

thanks!

andy

---

### Post by caljohnsmith on 2009-01-02
> **lildoggie said:**
> So, just to be clear: the dd command that zeros out the MBR won't affect the ability to boot from that disk, right?

thanks!

andy
After moving your partition over to the drive, you will have to install Grub to the MBR to make the drive bootable, so zeroing the MBR beforehand is not a problem. :)

---

### Post by lildoggie on 2009-01-02
ok, cool.  Can I do this from my existing boot since it's on the separate drive, or do I need to boot from the Live CD?

---

### Post by lildoggie on 2009-01-02
I also noticed in gparted that I could just select the partition, right-click on it, and select "Format as ...  ext3" -- would that be a reasonable approach to doing this?

thanks!

andy

---

### Post by lildoggie on 2009-01-02
OK....    just to make sure I'm doing the right things here...

Just being dense: One of your instructions was to create an MS-DOS partition table -- what is the purpose of doing that?

Since I want to move my existing data over, I believe I need to have (should have?) the following partitions:
- boot (optional, but I hear it's nice to have)
- swap
- data 
- home  (could be included with data, but I hear it can be good to have the home dir info separate).

Is this correct?  If so, what's the best way to do it right?  I just want to make sure that I get it set up correctly and don't mess it up on the way over!

---

### Post by caljohnsmith on 2009-01-02
> **lildoggie said:**
> ok, cool.  Can I do this from my existing boot since it's on the separate drive, or do I need to boot from the Live CD?
You don't want to be booted into the Ubuntu install that you are going to copy with gparted, so I would definitely do it from the Live CD. And you can format your new partition doing the right-click method that you mentioned if you want, just don't accidentally format your original Ubuntu install. And about setting up the partitions, it would be simpler to just copy over whatever existing Ubuntu partitions you all ready have, because it will take a bit of work if you want to create all those new partitions for Ubuntu and get it working if your original Ubuntu install only has one main partition. It's up to you though.

---

### Post by lildoggie on 2009-01-02
> **caljohnsmith said:**
> You don't want to be booted into the Ubuntu install that you are going to copy with gparted, so I would definitely do it from the Live CD. And you can format your new partition doing the right-click method that you mentioned if you want, just don't accidentally format your original Ubuntu install. And about setting up the partitions, it would be simpler to just copy over whatever existing Ubuntu partitions you all ready have, because it will take a bit of work if you want to create all those new partitions for Ubuntu and get it working if your original Ubuntu install only has one main partition. It's up to you though.OK, sounds good.

As far as copying the existing partitions, how would you recommend doing that?  does the "cp" command you previously mentioned handle that?

I believe my existing installation was set up with LVM -- I'm guessing that won't pose any problem with the copying, etc, correct?  (trying to ask all the questions ahead of time so as not to get in the middle and have one of those "oh, you should have done *this* first" situations....)

---

### Post by caljohnsmith on 2009-01-02
> **lildoggie said:**
> OK, sounds good.

As far as copying the existing partitions, how would you recommend doing that?  does the "cp" command you previously mentioned handle that?

I believe my existing installation was set up with LVM -- I'm guessing that won't pose any problem with the copying, etc, correct?  (trying to ask all the questions ahead of time so as not to get in the middle and have one of those "oh, you should have done *this* first" situations....)
Once you've created your new Ubuntu partition, how about posting the output of:
```
sudo fdisk -lu
```
And we can go from there.

---

### Post by lildoggie on 2009-01-02
OK,I did the right-click -> format as ext3, and it completed successfully (though it shows 73GB free and 1.3 GB used, which I didn't expect -- is that part of ext3's bookkeeping?).  I did it while still booted up since I had unmounted everything on that drive (though I realize I'll need to boot to the liveCD for data transfer)...

Here's the output of fdisk -lu:

```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   156296384    78148161   83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63      498014      248976   83  Linux
/dev/hdb2          498015   234436544   116969265    5  Extended
/dev/hdb5          498078   234436544   116969233+  8e  Linux LVM
```

Do you need any other info?

Thanks for all your help!

andy

---

### Post by caljohnsmith on 2009-01-02
I forgot you have that LVM partition; do you know how to mount your hdb5 LVM partition? I haven't dealt much with LVMs. How about trying:
```
sudo mkdir /mnt/hdb5
sudo mount /dev/hdb5 /mnt
```
If the mount command returns an error, then how about trying:
```
sudo apt-get install lvm2
sudo vgscan
sudo pvscan
sudo lvscan
```
And please post the output of all the above commands.

---

### Post by Pumalite on 2009-01-02
This also works:

the solution to mounting the LVM format drives is to fist issue the lvmdisplay command as root, which givces back a lot of info...
Code:
[root@localhost root]# lvdisplay
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol00
  VG Name                VolGroup00
  LV UUID                Mva5QJ-HfKU-IKMZ-HJAF-9Mfj-zniB-T0e17W
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                36.62 GB
  Current LE             1172
  Segments               1
  Allocation             next free (default)
  Read ahead sectors     0
  Block device           253:0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol01
  VG Name                VolGroup00
  LV UUID                9vHldZ-Lexf-PfYX-BT5x-Dnj3-PYGz-benvcd
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                512.00 MB
  Current LE             16
  Segments               1
  Allocation             next free (default)
  Read ahead sectors     0
  Block device           253:1

"LV Name" is the important information here. In my case we have LogVol00 as the main drive contents and LogVol01 as the swapspace (which is exactly what I am told if I try to mount it)

...mounting the drive is simplty then a matter of substitution with teh usual /dev/ name...

[root@localhost root]# mount /dev/VolGroup00/LogVol00 /mnt/hdb
...autocompletion (hitting the TAB key) also works here!

---

### Post by lildoggie on 2009-01-02
I tried the mount, and it told me I needed a filesystem type, so I used "sudo mount -t ext3 /dev/hdb5 /mnt" and got the error "/dev/hdb5 already mounted or /mnt busy"

So here's the output of the other commands:

```
$ sudo vgscan:
  Found volume group "Ubuntu" using metadata type lvm2

$ sudo pvscan:  
  PV /dev/hdb5   VG Ubuntu   lvm2 [111.55 GB / 0    free]
  Total: 1 [111.55 GB] / in use: 1 [111.55 GB] / in no VG: 0 [0   ]

$ sudo lvscan:
  ACTIVE            '/dev/Ubuntu/root' [109.33 GB] inherit
  ACTIVE            '/dev/Ubuntu/swap_1' [2.22 GB] inherit

```

I also just saw Pumalite's post, and using that, I was able to mount the root partition on /mnt/hdb5...

So that might make things a bit easier...

What's next?

Thanks!

andy

---

### Post by caljohnsmith on 2009-01-02
Great, thanks for sharing that Pumalite; I'm glad you have your LVM partition mounted now, Andy. How about posting the output of:
```
sudo mkdir /mnt/hdb1
sudo mount /dev/hdb1 /mnt/hdb1
ls -l /mnt/hdb1 /mnt/hdb5
```

---

### Post by lildoggie on 2009-01-02
You got it:
```
/mnt/hdb1:
total 42219
-rw-r--r-- 1 root root  239811 2006-12-12 09:25 abi-2.6.12-10-386
-rw-r--r-- 1 root root  239770 2005-10-10 07:16 abi-2.6.12-9-386
-rw-r--r-- 1 root root  266735 2006-12-08 12:34 abi-2.6.15-27-386
-rw-r--r-- 1 root root  266735 2007-07-18 17:36 abi-2.6.15-28-386
-rw-r--r-- 1 root root  266735 2008-11-24 12:52 abi-2.6.15-53-386
drwxr-xr-x 2 root root    1024 2009-01-01 05:36 bin
-rw-r--r-- 1 root root   64125 2006-12-12 08:55 config-2.6.12-10-386
-rw-r--r-- 1 root root   64135 2005-10-10 06:12 config-2.6.12-9-386
-rw-r--r-- 1 root root   69967 2006-12-08 10:50 config-2.6.15-27-386
-rw-r--r-- 1 root root   69967 2007-07-18 16:49 config-2.6.15-28-386
-rw-r--r-- 1 root root   69967 2008-11-24 10:47 config-2.6.15-53-386
drwxr-xr-x 2 root root    1024 2009-01-01 05:35 dev
drwxr-xr-x 2 root root    1024 2009-01-01 14:36 grub
-rw-r--r-- 1 root root 5289555 2007-01-31 20:41 initrd.img-2.6.12-10-386
-rw-r--r-- 1 root root 4937619 2005-12-29 07:35 initrd.img-2.6.12-9-386
-rw-r--r-- 1 root root 6776228 2007-01-31 20:42 initrd.img-2.6.15-27-386
-rw-r--r-- 1 root root 6826359 2008-12-30 19:02 initrd.img-2.6.15-28-386
-rw-r--r-- 1 root root 6830098 2008-12-30 19:04 initrd.img-2.6.15-53-386
drwxr-xr-x 2 root root   12288 2005-12-29 07:31 lost+found
-rw-r--r-- 1 root root   94760 2005-10-25 04:32 memtest86+.bin
drwxr-xr-x 2 root root    1024 2009-01-01 05:34 proc
-rw-r--r-- 1 root root  897419 2006-12-12 09:25 System.map-2.6.12-10-386
-rw-r--r-- 1 root root  897159 2005-10-10 07:16 System.map-2.6.12-9-386
-rw-r--r-- 1 root root  725967 2006-12-08 12:34 System.map-2.6.15-27-386
-rw-r--r-- 1 root root  727165 2007-07-18 17:36 System.map-2.6.15-28-386
-rw-r--r-- 1 root root  727244 2008-11-24 12:53 System.map-2.6.15-53-386
-rw-r--r-- 1 root root 1207198 2006-12-12 09:25 vmlinuz-2.6.12-10-386
-rw-r--r-- 1 root root 1206555 2005-10-10 07:16 vmlinuz-2.6.12-9-386
-rw-r--r-- 1 root root 1414752 2006-12-08 12:34 vmlinuz-2.6.15-27-386
-rw-r--r-- 1 root root 1415298 2007-07-18 17:36 vmlinuz-2.6.15-28-386
-rw-r--r-- 1 root root 1414999 2008-11-24 12:52 vmlinuz-2.6.15-53-386

/mnt/hdb5:
total 168
drwxr-xr-x   2 root root  4096 2008-12-30 18:54 bin
drwxr-xr-x   3 root root  4096 2009-01-01 05:46 boot
lrwxrwxrwx   1 root root    11 2005-12-29 07:32 cdrom -> media/cdrom
drwxr-xr-x   2 root root  4096 2005-12-29 07:35 debootstrap
drwxr-xr-x  14 root root 28672 2009-01-01 20:02 dev
drwxr-xr-x 118 root root  8192 2009-01-02 12:00 etc
drwxr-xr-x  11 root root  4096 2009-01-02 11:35 home
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 initrd
lrwxrwxrwx   1 root root    29 2008-12-30 19:04 initrd.img -> boot/initrd.img-2.6.15-53-386
lrwxrwxrwx   1 root root    29 2007-05-20 14:08 initrd.img.old -> boot/initrd.img-2.6.15-28-386
drwxr-xr-x  20 root root  8192 2008-12-30 18:54 lib
drwxr-xr-x   2 root root 49152 2005-12-29 07:32 lost+found
drwxr-xr-x   5 root root  4096 2005-12-29 07:32 media
-rw-r--r--   1 root root  5310 2009-01-01 13:06 menu.lst
drwxr-xr-x   6 root root  4096 2009-01-02 12:00 mnt
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 opt
drwxr-xr-x   2 root root  4096 2005-10-05 03:37 proc
drwxr-xr-x   9 root root  4096 2007-05-20 14:35 root
drwxr-xr-x   2 root root  8192 2009-01-01 20:01 sbin
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 srv
drwxr-xr-x   2 root root  4096 2005-10-09 15:03 sys
drwxrwxrwt  15 root root  4096 2009-01-02 11:40 tmp
prw-r-----   1 root root     0 2007-01-31 20:55 usplash_fifo
drwxr-xr-x  12 root root  4096 2007-01-31 18:55 usr
drwxr-xr-x  15 root root  4096 2006-06-20 13:24 var
lrwxrwxrwx   1 root root    26 2008-12-30 19:04 vmlinuz -> boot/vmlinuz-2.6.15-53-386
lrwxrwxrwx   1 root root    26 2007-05-20 14:08 vmlinuz.old -> boot/vmlinuz-2.6.15-28-386
```

---

### Post by Pumalite on 2009-01-02
This also works:

the solution to mounting the LVM format drives is to fist issue the lvmdisplay command as root, which givces back a lot of info...
Code:
[root@localhost root]# lvdisplay
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol00
  VG Name                VolGroup00
  LV UUID                Mva5QJ-HfKU-IKMZ-HJAF-9Mfj-zniB-T0e17W
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                36.62 GB
  Current LE             1172
  Segments               1
  Allocation             next free (default)
  Read ahead sectors     0
  Block device           253:0
   
  --- Logical volume ---
  LV Name                /dev/VolGroup00/LogVol01
  VG Name                VolGroup00
  LV UUID                9vHldZ-Lexf-PfYX-BT5x-Dnj3-PYGz-benvcd
  LV Write Access        read/write
  LV Status              available
  # open                 0
  LV Size                512.00 MB
  Current LE             16
  Segments               1
  Allocation             next free (default)
  Read ahead sectors     0
  Block device           253:1

"LV Name" is the important information here. In my case we have LogVol00 as the main drive contents and LogVol01 as the swapspace (which is exactly what I am told if I try to mount it)

...mounting the drive is simplty then a matter of substitution with teh usual /dev/ name...

[root@localhost root]# mount /dev/VolGroup00/LogVol00 /mnt/hdb
...autocompletion (hitting the TAB key) also works here!

---

### Post by caljohnsmith on 2009-01-02
OK, I forgot you all ready have a boot partition (hdb1);  Do you want to incorporate that into your main Ubuntu partition hda1, or do you want a separate boot partition? If you want a separate boot partition, you could delete hda1, create a new primary ext partition ~200 MB as the front of the hda drive as the boot partition, and then use the rest of the space to recreate the main Ubuntu ext3 partition as hda2. Or if you just want to put your boot partition into your main hda1 partition that you currently have, we could easily do that too. It's up to you, let me know what you want. And just to let you know, I have to go and won't be back for about an hour, so we can pick up then if you like. :)

---

### Post by lildoggie on 2009-01-02
OK.  I've repartitioned the drive to have a 200MB primary boot ext3 partition at the beginning of the drive, then created an extended partition with the remaining amount, then created a new logical ext3 partition within the extended partition.

Output of fdisk -lu:
```
Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63      401624      200781   83  Linux
/dev/hda2          401625   156296384    77947380    5  Extended
/dev/hda5          401688   156296384    77947348+  83  Linux

Disk /dev/hdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders, total 234441648 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63      498014      248976   83  Linux
/dev/hdb2          498015   234436544   116969265    5  Extended
/dev/hdb5          498078   234436544   116969233+  8e  Linux LVM
```
I'm just wondering -- since I've got so much free space on my 120G drive (hdb5), would it be possible to resize the logical volume so it'd fit on the smaller drive?  And if so, is there any risk that I'd lose any of my data?  

I really don't want to lose any of that information, since I've been bad and haven't backed it up -- though I'm right now backing up /home using 
```
sudo tar cvpzf /home/backup.tgz --exclude /home/backup.tgz /home
```
but it's taking a LONG time....

Other than that, I think I'm about ready to go with moving things...

---

### Post by caljohnsmith on 2009-01-02
OK, that looks great. So how about going ahead and copying things over, so first mount all your partitions:
```
sudo mkdir /mnt/hda1 /mnt/hda5 /mnt/hdb1 /mnt/hdb5
sudo mount /dev/hda1 /mnt/hda1
sudo mount /dev/hda5 /mnt/hda5
sudo mount /dev/hdb1 /mnt/hdb1
```
And also use the technique you previously used to mount hdb5 on /mnt/hdb5. Then proceed with:
```
sudo cp -ax /mnt/hdb5/* /mnt/hda5
sudo cp -ax /mnt/hdb1/* /mnt/hda1
```
Once all the copying is done, also do:
```
sudo tune2fs -U "787eae0b-b4cd-4330-8ba0-6bf898df2180" /dev/hda1
```
That will make your new hda1 partition have the same UUID as your old hdb1 partition. But unfortunately it will be a little more complicated about your main hda5 partition, because we can't simply transfer the hdb5 LVM UUID to your new hda5 ext3 partition, because your LVM UUID uses non-hexadecimal characters. So please post the output of the following:
```
sudo blkid -c /dev/null
```
And then I can help you take care of the rest of the details.

---

### Post by lildoggie on 2009-01-02
Grrrr....

I rebooted using the liveCD (all the other tests and repartitioning were done while logged in booted from the HD), and was able to create and mount everything except the Logical volume.  Initially lvm2 wasn't installed, so I grabbed it using apt-get, and then when I ran lvdisplay, I got the following output:
```
ubuntu@ubuntu:~$ sudo lvdisplay
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
  --- Logical volume ---
  LV Name                /dev/Ubuntu/root
  VG Name                Ubuntu
  LV UUID                e5MMbF-1E8p-7F6D-DcHD-or4X-jJ7V-LSi5nz
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                109.33 GB
  Current LE             27988
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto
   
  --- Logical volume ---
  LV Name                /dev/Ubuntu/swap_1
  VG Name                Ubuntu
  LV UUID                cwz5t2-zyLy-BC3O-LA5t-ohQO-aJWH-HqhNBB
  LV Write Access        read/write
  LV Status              NOT available
  LV Size                2.22 GB
  Current LE             568
  Segments               1
  Allocation             inherit
  Read ahead sectors     auto

```
Even though it says the LV Name is /dev/Ubuntu/root, /dev/Ubuntu doesn't exist.  The error messages made me think that something was missing, so I did apt-cache search device-mapper, and saw that libdevmapper1.02.1 was available, so I tried to install it, and got the message that I'm already running the latest version...

Any more ideas?   It definitely behaves differently running from the Live CD than from the booted installation!

---

### Post by caljohnsmith on 2009-01-02
So there's nothing under /dev/Ubuntu? Do you know what you did differently last time that you were able to mount hdb5? I mean can you follow the same steps again? What do those other lvm2 commands return from post #36?

---

### Post by lildoggie on 2009-01-02
> **caljohnsmith said:**
> So there's nothing under /dev/Ubuntu? Do you know what you did differently last time that you were able to mount hdb5? I mean can you follow the same steps again? What do those other lvm2 commands return from post #36?
Nope, nothing under /dev/Ubuntu (in fact, /dev/Ubuntu doesn't exist).

When I mounted it before, it was from my HD-booted installation, not from the live CD (but it's my understanding that when doing the copy process, I should not do that when booted from the HD, right?)

So I've never been able to mount hdb5 from the Live CD.
Other command outputs:
```
ubuntu@ubuntu:~$ sudo vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "Ubuntu" using metadata type lvm2
ubuntu@ubuntu:~$ sudo pvscan
  PV /dev/sdb5   VG Ubuntu   lvm2 [111.55 GB / 0    free]
  Total: 1 [111.55 GB] / in use: 1 [111.55 GB] / in no VG: 0 [0   ]
ubuntu@ubuntu:~$ sudo lvscan
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  /proc/misc: No entry for device-mapper found
  Is device-mapper driver missing from kernel?
  Failure to communicate with kernel device-mapper driver.
  Incompatible libdevmapper 1.02.27 (2008-06-25)(compat) and kernel driver 
  inactive          '/dev/Ubuntu/root' [109.33 GB] inherit
  inactive          '/dev/Ubuntu/swap_1' [2.22 GB] inherit

```

This is getting really strange...

---

### Post by caljohnsmith on 2009-01-02
OK, let's take a slightly different approach then; how about going ahead and booting into your hdb5 partition, and then do:
```
sudo mkdir /mnt/hda5
sudo mount /dev/hda5 /mnt/hda5
sudo rsync -avx --exclude=/proc/* --exclude=/boot/* --exclude=/dev/* --exclude=/sys/* --exclude=/tmp/* --exclude=/lost+found / /mnt/hda5
sudo mkdir /mnt/hda5/proc /mnt/hda5/boot /mnt/hda5/dev /mnt/hda5/sys /mnt/hda5/tmp
```
So in other words, since it is inconvenient to do it from your Live CD, we can still copy over hdb5 while you are booted in it, but we just exclude certain "virtual" file system directories like /proc, /dev, /sys, etc. during the copying. And then to copy over your boot partition:
```
sudo mkdir /mnt/hda1
sudo mount /dev/hda1 /mnt/hda1
sudo cp -ax /boot/* /mnt/hda1
```
And then please post the output of:
```
sudo blkid -c /dev/null
```
And we can go from there.

---

### Post by lildoggie on 2009-01-02
> sudo mkdir /mnt/hda5
sudo mount /dev/hda5 /mnt/hda5
sudo rsync -avx --exclude=/proc/* --exclude=/boot/* --exclude=/dev/* --exclude=/sys/* --exclude=/tmp/* --exclude=/lost+found / /mnt/hda5
sudo mkdir /mnt/hda5/proc /mnt/hda5/boot /mnt/hda5/dev /mnt/hda5/sys /mnt/hda5/tmp
Should I use the above mount command for hda5 or mount /dev/Ubuntu/root /mnt/hda5?  I was thinking that I needed to get to the LVM to make this work...  is that right?

EDIT:  Oops, I see -- I was thinking of hdb5, not hda5...

So, the rsync will sync /mnt/hda5 with what?

EDIT AGAIN:  sorry, I missed the "/" in front of the last "/mnt/hda5"  (idiot! -- I've got it now)

---

### Post by caljohnsmith on 2009-01-02
> **lildoggie said:**
> Should I use the above mount command for hda5 or mount /dev/Ubuntu/root /mnt/hda5?  I was thinking that I needed to get to the LVM to make this work...  is that right?
Just use the mount command for /dev/hda5; since you will be booted into hdb5, you don't have to mount hdb5 anywhere or mess with any LVM stuff. Also, "rsync" is just a copy program with more features than "cp", so it's not really "syncing" hda5 (but maybe you could think of it that way). :)

---

### Post by lildoggie on 2009-01-02
Cool...  it's building the file list as we speak....  I'll post back when I've got something to report...

Thanks again for your patience!

andy

---

### Post by lildoggie on 2009-01-03
> **caljohnsmith said:**
> OK, let's take a slightly different approach then; how about going ahead and booting into your hdb5 partition, and then do:
```
sudo mkdir /mnt/hda5
sudo mount /dev/hda5 /mnt/hda5
sudo rsync -avx --exclude=/proc/* --exclude=/boot/* --exclude=/dev/* --exclude=/sys/* --exclude=/tmp/* --exclude=/lost+found / /mnt/hda5
sudo mkdir /mnt/hda5/proc /mnt/hda5/boot /mnt/hda5/dev /mnt/hda5/sys /mnt/hda5/tmp
```
So in other words, since it is inconvenient to do it from your Live CD, we can still copy over hdb5 while you are booted in it, but we just exclude certain "virtual" file system directories like /proc, /dev, /sys, etc. during the copying. And then to copy over your boot partition:
```
sudo mkdir /mnt/hda1
sudo mount /dev/hda1 /mnt/hda1
sudo cp -ax /boot/* /mnt/hda1
```
And then please post the output of:
```
sudo blkid -c /dev/null
```
And we can go from there.
OK, the rsync is *finally* complete!

It was really strange, though....  When it had been going for quite a while, I opened a remote terminal so I could monitor progress, and when I did a "ps aux |grep rsync" I noticed that there were 2 rsync processes going.  Then, quite a bit later, I noticed there were 3 rsync processes.

The other thing that I thought was strange was the output of df (which I used to get an idea of how much had been copied).  The final result was:```
$ df /dev/hda5 /dev/mapper/Ubuntu-root
Filesystem              1K-blocks      Used Available Use% Mounted on
/dev/hda5                76723716  17370380  55455972  24% /mnt/hda5
/dev/mapper/Ubuntu-root 112839368   8662756  98444672   9% /mnt/hdb5
```What I found strange about this is that /dev/hda5 (the destination) is about twice as big as the source!  Any idea why that might be (or where the extra data came from or where it's located? the root directories appear to be identical). 

In any case, the output of sudo blkid -c /dev/null is as follows:```
andy@huey:~$ sudo blkid -c /dev/null
Password:
/dev/hda1: UUID="55798ab8-6cdd-4303-981b-e983ab31bd59" SEC_TYPE="ext2" TYPE="ext3"
/dev/hda5: UUID="2ea16c7a-0fe5-472f-a89b-979f896673fe" SEC_TYPE="ext2" TYPE="ext3"
/dev/hdb1: LABEL="/boot" UUID="787eae0b-b4cd-4330-8ba0-6bf898df2180" SEC_TYPE="ext2" TYPE="ext3"
/dev/dm: LABEL="/" UUID="fa5e5be2-f5a1-47e7-ab96-35aa593ad980" SEC_TYPE="ext2" TYPE="ext3"
/dev/mapper/Ubuntu-swap_1: TYPE="swap"
/dev/evms/hda1: UUID="55798ab8-6cdd-4303-981b-e983ab31bd59" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hda5: UUID="2ea16c7a-0fe5-472f-a89b-979f896673fe" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/hdb1: LABEL="/boot" UUID="787eae0b-b4cd-4330-8ba0-6bf898df2180" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/lvm2/Ubuntu/root: LABEL="/" UUID="fa5e5be2-f5a1-47e7-ab96-35aa593ad980" SEC_TYPE="ext2" TYPE="ext3"
/dev/evms/lvm2/Ubuntu/swap_1: TYPE="swap"
```
Thanks again!

andy

---

### Post by caljohnsmith on 2009-01-03
I think I know what might have happened: I forgot to exclude copying the "/mnt" directory that you had hda5 mounted on, so rsync might have recursively copied hdb5 into the /mnt/hda5/mnt/hda5 directory. If that's what happened, I'm really sorry I missed that #-o, but at least it should be easily fixable. While you have hda5 still mounted on /mnt, how about doing:
```
ls -l /mnt/hda5/mnt /mnt/hda5/mnt/hda5
```
If that shows anything under /mnt/hda5, you should go ahead and delete what was accidentally copied there:
```
sudo rm -fr /mnt/hda5/mnt/*
```
But be really careful with the rm command that you get the directory above just right without any typos. Let me know how that goes, and sorry again for the goof.

---

### Post by lildoggie on 2009-01-03
Thanks for the reply -- that makes perfect sense that the duplication could occur.  (and I'm glad to see you available today -- I wasn't sure!)

Well, there is no data in /mnt/hda5/mnt/hda5.  So I thought that wasn't it...

HOWEVER: (!)  as I checked into this, I saw that I had a directory /mnt/hdb5, I thought "AHA!" and sure enough, that was an additional mount of the root directory....  so the duplicated data is on /mnt/hda5/mnt/hdb5  (at least it was -- it's in process of being deleted now).

So I think we're about ready to proceed...  What other information can I provide?

---

### Post by caljohnsmith on 2009-01-03
OK, great, glad you found the problem; how about making sure by doing:
```
df -h
```
And check that /dev/hda5 is no larger than /dev/mapper/Ubuntu-root (it might be a little smaller since we deliberately excluded copying some of the virtual file system directories). If it looks OK, how about doing the following, and please post the output of all the commands:
```
sudo grub
grub> root (hd0,0)
grub> setup (hd0)
grub> quit
```
Next open your menu.lst:
```
sudo mkdir /mnt/hda1 && sudo mount /dev/hda1 /mnt/hda1
gksudo gedit /mnt/hda1/grub/menu.lst
```
And change all your Ubuntu boot stanzas to look similar to:
```
title		Ubuntu, kernel 2.6.15-53-386
root		[COLOR="Blue"](hd0,0)[/COLOR]
kernel		/vmlinuz-2.6.15-53-386 [COLOR="Blue"]root=UUID=2ea16c7a-0fe5-472f-a89b-979f896673fe[/COLOR] ro quiet splash
initrd		/initrd.img-2.6.15-53-386
savedefault
boot
```
Also change the "# kopt=...." line to:
```
# kopt=root=UUID=2ea16c7a-0fe5-472f-a89b-979f896673fe ro
```
And your "# groot=(hd1,0)" line change to:
```
# groot=(hd0,0)
```
Next open your fstab:
```
gksudo gedit /mnt/hda5/etc/fstab
```
And change the line that mounts hda5 on "/" uses the new UUID, similar to:
```
UUID=[COLOR="Blue"]2ea16c7a-0fe5-472f-a89b-979f896673fe /[/COLOR]  ext3  relatime,errors=remount-ro 0 1
```
Don't worry if your mount options after the ext3 are different, you can keep them as they are. After you've made all the above changes, reboot, set your BIOS to boot the hda drive, and let me know how far you get. Hopefully I didn't forget anything, but let me know how it goes. :)

---

### Post by lildoggie on 2009-01-03
> **caljohnsmith said:**
> OK, great, glad you found the problem; how about making sure by doing:
```
df -h
```
And check that /dev/hda5 is no larger than /dev/mapper/Ubuntu-root (it might be a little smaller since we deliberately excluded copying some of the virtual file system directories). 
I didn't proceed with the rest, because /mnt/hda5 is slightly larger:
```
$ df -h
Filesystem               Size  Used Avail Use% Mounted on
/dev/mapper/Ubuntu-root  108G  7.9G   95G   8% /
varrun                   189M  152K  189M   1% /var/run
varlock                  189M  4.0K  189M   1% /var/lock
udev                     189M  108K  189M   1% /dev
devshm                   189M     0  189M   0% /dev/shm
lrm                      189M   19M  170M  10% /lib/modules/2.6.15-53-386/volatile 
/dev/hdb1                228M   47M  170M  22% /boot
/dev/hdc                 699M  699M     0 100% /media/cdrom0
/dev/mapper/Ubuntu-root  108G  7.9G   95G   8% /mnt/hdb5
/dev/hda1                190M  4.1M  177M   3% /mnt/hda1
/dev/hda5                 74G  8.4G   62G  13% /mnt/hda5
/dev/hdb1                228M   47M  170M  22% /mnt/hdb1
```
Is this anything to be concerned about?

---

### Post by caljohnsmith on 2009-01-03
How about posting the output of:
```
ls -l /mnt/hda5/proc /mnt/hda5/sys /mnt/hda5/mnt /mnt/hda5/dev /mnt/hda5
sudo du -sh /mnt/hda5/*
sudo du -sh --exclude=mnt --exclude=media /*
```
The du commands will take awhile unfortunately, so we'll have to be patient. Also, I notice that /dev/hda1 is only 4.1 MB, whereas /dev/hdb1 is 47 MB. Did you copy everything over from hdb1 to hda1? How about checking that too and let me know what you find.

---

### Post by lildoggie on 2009-01-03
```
$ ls -l /mnt/hda5/proc /mnt/hda5/sys /mnt/hda5/dev /mnt/hda5
/mnt/hda5:
total 108
drwxr-xr-x   2 root root  4096 2008-12-30 18:54 bin
drwxr-xr-x   2 root root  4096 2009-01-01 14:35 boot
lrwxrwxrwx   1 root root    11 2009-01-02 15:26 cdrom -> media/cdrom
drwxr-xr-x   2 root root  4096 2005-12-29 07:35 debootstrap
drwxr-xr-x   2 root root  4096 2009-01-02 14:51 dev
drwxr-xr-x 118 root root  8192 2009-01-02 15:01 etc
drwxr-xr-x  11 root root  4096 2009-01-02 12:14 home
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 initrd
lrwxrwxrwx   1 root root    29 2009-01-02 15:26 initrd.img -> boot/initrd.img-2.6.15-53-386
lrwxrwxrwx   1 root root    29 2009-01-02 15:26 initrd.img.old -> boot/initrd.img-2.6.15-28-386
drwxr-xr-x  20 root root  4096 2008-12-30 18:54 lib
drwx------   2 root root 16384 2009-01-02 12:40 lost+found
drwxr-xr-x   5 root root  4096 2005-12-29 07:32 media
-rw-r--r--   1 root root  5310 2009-01-01 13:06 menu.lst
drwxr-xr-x   8 root root  4096 2009-01-02 13:40 mnt
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 opt
dr-xr-xr-x   2 root root  4096 2009-01-02 07:50 proc
drwxr-xr-x   9 root root  4096 2007-05-20 14:35 root
drwxr-xr-x   2 root root  8192 2009-01-01 20:01 sbin
drwxr-xr-x   2 root root  4096 2005-12-29 07:33 srv
drwxr-xr-x   2 root root  4096 2009-01-02 07:50 sys
drwxrwxrwt   2 root root  4096 2009-01-02 15:08 tmp
prw-r-----   1 root root     0 2007-01-31 20:55 usplash_fifo
drwxr-xr-x  12 root root  4096 2007-01-31 18:55 usr
drwxr-xr-x  15 root root  4096 2006-06-20 13:24 var
lrwxrwxrwx   1 root root    26 2009-01-02 15:26 vmlinuz -> boot/vmlinuz-2.6.15-53-386
lrwxrwxrwx   1 root root    26 2009-01-02 15:26 vmlinuz.old -> boot/vmlinuz-2.6.15-28-386

/mnt/hda5/dev:
total 0

/mnt/hda5/proc:
total 0

/mnt/hda5/sys:
total 0
```

```

Also, good catch on copying /boot -- it appears that I didn't complete that step!

Now for the du output:
[code]$ sudo du -sh /mnt/hda5/*
4.5M    /mnt/hda5/bin
4.0K    /mnt/hda5/boot
0       /mnt/hda5/cdrom
4.0K    /mnt/hda5/debootstrap
4.0K    /mnt/hda5/dev
66M     /mnt/hda5/etc
4.1G    /mnt/hda5/home
4.0K    /mnt/hda5/initrd
0       /mnt/hda5/initrd.img
0       /mnt/hda5/initrd.img.old
370M    /mnt/hda5/lib
16K     /mnt/hda5/lost+found
16K     /mnt/hda5/media
8.0K    /mnt/hda5/menu.lst
28K     /mnt/hda5/mnt
4.0K    /mnt/hda5/opt
4.0K    /mnt/hda5/proc
224K    /mnt/hda5/root
11M     /mnt/hda5/sbin
4.0K    /mnt/hda5/srv
4.0K    /mnt/hda5/sys
4.0K    /mnt/hda5/tmp
0       /mnt/hda5/usplash_fifo
1.8G    /mnt/hda5/usr
2.1G    /mnt/hda5/var
0       /mnt/hda5/vmlinuz
0       /mnt/hda5/vmlinuz.old
```and
```
$ sudo du -sh /*
4.3M    /bin
43M     /boot
0       /cdrom
4.0K    /debootstrap
228K    /dev
62M     /etc
4.1G    /home
4.0K    /initrd
0       /initrd.img
0       /initrd.img.old
388M    /lib
48K     /lost+found
699M    /media
8.0K    /menu.lst
43M     /mnt
4.0K    /opt
du: `/proc/5970/task': No such file or directory
du: `/proc/5970/fd': No such file or directory
388M    /proc
224K    /root
8.7M    /sbin
4.0K    /srv
0       /sys
60K     /tmp
0       /usplash_fifo
1.8G    /usr
1.6G    /var
0       /vmlinuz
0       /vmlinuz.old
```So it looks like the big difference is in /var...   so here are the outputs from those two dirs:
```
$ sudo du -sh /mnt/hda5/var/*
3.6M    /mnt/hda5/var/backups
255M    /mnt/hda5/var/cache
4.0K    /mnt/hda5/var/games
131M    /mnt/hda5/var/lib
4.0K    /mnt/hda5/var/local
4.0K    /mnt/hda5/var/lock
1.4G    /mnt/hda5/var/log
232K    /mnt/hda5/var/mail
24K     /mnt/hda5/var/named
4.0K    /mnt/hda5/var/opt
4.0K    /mnt/hda5/var/run
272M    /mnt/hda5/var/spool
4.0K    /mnt/hda5/var/tmp

$ sudo du -sh /var/*
3.6M    /var/backups
255M    /var/cache
4.0K    /var/games
141M    /var/lib
4.0K    /var/local
4.0K    /var/lock
830M    /var/log
232K    /var/mail
24K     /var/named
4.0K    /var/opt
152K    /var/run
327M    /var/spool
4.0K    /var/tmp
```So the big difference is in the log dir, and some differences in the spool dir as well (and some smaller changes, of course)...

---

### Post by caljohnsmith on 2009-01-03
That is really strange, because it looks like most of your root directories on hda5 are slightly larger than the hdb5 directories that you copied from, like /var, /bin, /sbin, /lib, etc. Maybe that has something to do with the fact that your hdb5 partition is LVM, while the hda5 partition is straight ext3. I don't think we need to be too concerned about it (at least not yet), so how about going ahead and completing the rest of the steps in post #55 (after you've copied hdb1 to hda1) and let me know how that goes.

---

### Post by zika on 2009-01-03
all this made me generate RESULTS.TXT for my machine. the result gave me a worry about the lines marked with <--------

```
============================= Boot Info Summary: ==============================

 => Drive sdb does not have a valid partition table.
 => Drive sdc does not have a valid partition table.
 => Drive sdd does not have a valid partition table.
 => Drive sde does not have a valid partition table.
 => Grub is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #2 for its boot files.

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  According to the info in the boot sector, sda1 has 
                       293080064 sectors, but according to the info from             <------------------------------------------------
                       fdisk, it has 293080078 sectors.                              <------------------------------------------------
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot

sda2: _________________________________________________________________________

    File system:       ext3
    Boot sector type:  No Boot Loader
    Boot sector info:  
    Operating System:  Ubuntu 8.10
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab /boot /boot/grub

sda3: _________________________________________________________________________

    File system:       swap

=========================== Drive/Partition Info: =============================

Drive sda: _____________________________________________________________________

fdisk -lu /dev/sda:

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x9434e9d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   293082126   146540039+   7  HPFS/NTFS
/dev/sda2       293089860   478624544    92767342+  83  Linux
/dev/sda3       478624545   488392064     4883760   82  Linux swap / Solaris

sfdisk -V /dev/sda:

Warning: partition 1 does not end at a cylinder boundary                             <------------------------------------------------

Drive sdb: _____________________________________________________________________

fdisk -lu /dev/sdb:

sfdisk -V /dev/sdb:

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading

Drive sdc: _____________________________________________________________________

fdisk -lu /dev/sdc:

sfdisk -V /dev/sdc:

/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading

Drive sdd: _____________________________________________________________________

fdisk -lu /dev/sdd:

sfdisk -V /dev/sdd:

/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading

Drive sde: _____________________________________________________________________

fdisk -lu /dev/sde:

sfdisk -V /dev/sde:

/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

blkid -c /dev/null: ____________________________________________________________

/dev/sda1: UUID="BECC3BE3CC3B951D" TYPE="ntfs" 
/dev/sda2: UUID="7e8ce743-2191-42ed-bfa1-ebb8298be377" TYPE="ext3" 
/dev/sda3: UUID="b1fde2cc-6961-4b94-8799-c981f6d3346d" TYPE="swap" 

=============================== "mount" output: ===============================

/dev/sda2 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.27-9-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/viktor/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=********)

================================== sda1/Boot: ==================================

total 544
drwxrwxrwx 1 root root   4096 2008-10-05 23:42 .
drwxrwxrwx 1 root root  24576 2008-12-24 18:17 ..
-rwxrwxrwx 1 root root  24576 2008-12-24 18:17 BCD
-rwxrwxrwx 1 root root  21504 2008-12-24 18:17 BCD.LOG
-rwxrwxrwx 2 root root      0 2008-10-06 04:41 BCD.LOG1
-rwxrwxrwx 2 root root      0 2008-10-06 04:41 BCD.LOG2
-rwxrwxrwx 1 root root  65536 2008-10-06 04:41 bootstat.dat
drwxrwxrwx 1 root root      0 2008-10-05 23:42 cs-CZ
drwxrwxrwx 1 root root      0 2008-10-05 23:42 da-DK
drwxrwxrwx 1 root root      0 2008-10-05 23:42 de-DE
drwxrwxrwx 1 root root      0 2008-10-05 23:42 el-GR
drwxrwxrwx 1 root root      0 2008-10-05 23:42 en-US
drwxrwxrwx 1 root root      0 2008-10-05 23:42 es-ES
drwxrwxrwx 1 root root      0 2008-10-05 23:42 fi-FI
drwxrwxrwx 1 root root   4096 2008-10-05 23:42 Fonts
drwxrwxrwx 1 root root      0 2008-10-05 23:42 fr-FR
drwxrwxrwx 1 root root      0 2008-10-05 23:42 hu-HU
drwxrwxrwx 1 root root      0 2008-10-05 23:42 it-IT
drwxrwxrwx 1 root root      0 2008-10-05 23:42 ja-JP
drwxrwxrwx 1 root root      0 2008-10-05 23:42 ko-KR
-rwxrwxrwx 1 root root 406584 2008-01-19 08:43 memtest.exe
drwxrwxrwx 1 root root      0 2008-10-05 23:42 nb-NO
drwxrwxrwx 1 root root      0 2008-10-05 23:42 nl-NL
drwxrwxrwx 1 root root      0 2008-10-05 23:42 pl-PL
drwxrwxrwx 1 root root      0 2008-10-05 23:42 pt-BR
drwxrwxrwx 1 root root      0 2008-10-05 23:42 pt-PT
drwxrwxrwx 1 root root      0 2008-10-05 23:42 ru-RU
drwxrwxrwx 1 root root      0 2008-10-05 23:42 sv-SE
drwxrwxrwx 1 root root      0 2008-10-05 23:42 tr-TR
drwxrwxrwx 1 root root      0 2008-10-05 23:42 zh-CN
drwxrwxrwx 1 root root      0 2008-10-05 23:42 zh-HK
drwxrwxrwx 1 root root      0 2008-10-05 23:42 zh-TW

=========================== sda2/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default        0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        2

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

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
# kopt=root=UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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
# defoptions=vga=788 splash

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

title        Ubuntu 8.10, kernel 2.6.27-9-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 ro vga=788 splash 
initrd        /boot/initrd.img-2.6.27-9-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-9-generic root=UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 ro  single
initrd        /boot/initrd.img-2.6.27-9-generic

title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 ro vga=788 splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

title        Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 ro  single
initrd        /boot/initrd.img-2.6.27-7-generic

title        Ubuntu 8.10, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
savedefault
makeactive
chainloader    +1


=============================== sda2/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7e8ce743-2191-42ed-bfa1-ebb8298be377 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda3
UUID=b1fde2cc-6961-4b94-8799-c981f6d3346d none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

================================== sda2/boot: ==================================

total 25380
drwxr-xr-x  3 root root    4096 2008-12-16 10:29 .
drwxr-xr-x 24 root root    4096 2008-12-24 18:17 ..
-rw-r--r--  1 root root  503560 2008-11-04 21:53 abi-2.6.27-7-generic
-rw-r--r--  1 root root  503560 2008-11-21 00:30 abi-2.6.27-9-generic
-rw-r--r--  1 root root   85316 2008-11-04 21:53 config-2.6.27-7-generic
-rw-r--r--  1 root root   85316 2008-11-21 00:30 config-2.6.27-9-generic
drwxr-xr-x  3 root root    4096 2008-12-24 14:20 grub
-rw-r--r--  1 root root 8596648 2008-11-26 11:46 initrd.img-2.6.27-7-generic
-rw-r--r--  1 root root 8596637 2008-12-16 10:29 initrd.img-2.6.27-9-generic
-rw-r--r--  1 root root  124152 2008-09-11 22:11 memtest86+.bin
-rw-r--r--  1 root root 1352144 2008-11-04 21:53 System.map-2.6.27-7-generic
-rw-r--r--  1 root root 1352144 2008-11-21 00:30 System.map-2.6.27-9-generic
-rw-r--r--  1 root root    1130 2008-11-04 21:57 vmcoreinfo-2.6.27-7-generic
-rw-r--r--  1 root root    1130 2008-11-21 00:32 vmcoreinfo-2.6.27-9-generic
-rw-r--r--  1 root root 2339552 2008-11-04 21:53 vmlinuz-2.6.27-7-generic
-rw-r--r--  1 root root 2339712 2008-11-21 00:30 vmlinuz-2.6.27-9-generic

=============================== sda2/boot/grub: ===============================

total 224
drwxr-xr-x 3 root root   4096 2008-12-24 14:20 .
drwxr-xr-x 3 root root   4096 2008-12-16 10:29 ..
-rw-r--r-- 1 root root    197 2008-10-10 15:04 default
-rw-r--r-- 1 root root     15 2008-10-10 15:04 device.map
-rw-r--r-- 1 root root   8056 2008-10-10 15:04 e2fs_stage1_5
-rw-r--r-- 1 root root   7904 2008-10-10 15:04 fat_stage1_5
-rw-r--r-- 1 root root     16 2008-10-10 15:04 installed-version
-rw-r--r-- 1 root root   8608 2008-10-10 15:04 jfs_stage1_5
-rw-r--r-- 1 root root   4927 2008-12-24 14:20 menu.lst
-rw-r--r-- 1 root root   5027 2008-12-24 14:20 menu.lst~
-rw-r--r-- 1 root root   5012 2008-10-20 09:43 menu.lst.backup
-rw-r--r-- 1 root root   7324 2008-10-10 15:04 minix_stage1_5
-rw-r--r-- 1 root root   9632 2008-10-10 15:04 reiserfs_stage1_5
drwxr-xr-x 2 root root   4096 2008-10-20 09:43 splashimages
-rw-r--r-- 1 root root    512 2008-10-10 15:04 stage1
-rw-r--r-- 1 root root 108356 2008-10-10 15:04 stage2
-rw-r--r-- 1 root root   9276 2008-10-10 15:04 xfs_stage1_5

/dev/sdb: No medium found

sfdisk: cannot open /dev/sdb for reading
/dev/sdc: No medium found

sfdisk: cannot open /dev/sdc for reading
/dev/sdd: No medium found

sfdisk: cannot open /dev/sdd for reading
/dev/sde: No medium found

sfdisk: cannot open /dev/sde for reading

```should I be worried ...? if so, what am I to do?

---

### Post by lildoggie on 2009-01-03
The grub setup appeared to have no problems.

I'll capture the output of the other commands first in this message, then try the reboot and follow up...

Editing the menu.lst file was fine -- no issues there.

However, on the fstab, the one on my current install looks like:
```
proc /proc proc defaults 0 0
/dev/mapper/Ubuntu-root / ext3 defaults,errors=remount-ro 0 1
/dev/hdb1 /boot ext3 defaults 0 2
/dev/hda1 /mnt/80gig ntfs-3g defaults,locale=en_US.UTF-8 0 2
/dev/mapper/Ubuntu-swap_1 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sda /media/usb0 auto rw,user,noauto 0 0
```
It seems that I need to change some of the other lines, but I don't want to mess it up...  Obviously the /dev/hda1 line won't work any more, but I'm wondering about swap, etc...   

(I figure this is better to ask before rebooting!)

Thanks!

---

### Post by caljohnsmith on 2009-01-03
Zika, it would be better to start your own thread rather than posting your own results of the boot_info_script.txt in this thread, because your results have nothing to do with this thread. To answer your question though, that section in the results file that gives info about the Windows boot sector is still experimental, so if you can boot into Vista OK, you shouldn't need to worry about it.

---

### Post by caljohnsmith on 2009-01-03
Andy, I was hoping that your fstab used the UUID for your boot partition rather than /dev/hdb1, but I see I was wrong; so how about making the following changes to it:
```
proc /proc proc defaults 0 0
[COLOR="Blue"]UUID=2ea16c7a-0fe5-472f-a89b-979f896673fe[/COLOR] / ext3 defaults,errors=remount-ro 0 1
[COLOR="Blue"]UUID=55798ab8-6cdd-4303-981b-e983ab31bd59[/COLOR] /boot ext3 defaults 0 2
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,noauto 0 0
/dev/sda /media/usb0 auto rw,user,noauto 0 0
```
Then I think you should be OK.

---

### Post by lildoggie on 2009-01-03
OK, I've made those changes, but I just wanted to check before I reboot -- do I need to have anything in there for swap?  I know I haven't configured any swap space, and I'm wondering if that's an issue at this point...

Thanks!

andy

---

### Post by caljohnsmith on 2009-01-03
> **lildoggie said:**
> OK, I've made those changes, but I just wanted to check before I reboot -- do I need to have anything in there for swap?  I know I haven't configured any swap space, and I'm wondering if that's an issue at this point...

Thanks!

andy
I think it would be better to just go ahead and try booting into your new installation, and then we can set up a swap file for you if it works. It would be good if you can disconnect the hdb drive though, because otherwise Ubuntu might mount the hdb1 boot partition rather than hda1 when you get into Ubuntu since their UUIDs are currently the same. Let me know how it goes. :)

---

### Post by zika on 2009-01-03
> **caljohnsmith said:**
> Zika, it would be better to start your own thread rather than posting your own results of the boot_info_script.txt in this thread, because your results have nothing to do with this thread. To answer your question though, that section in the results file that gives info about the Windows boot sector is still experimental, so if you can boot into Vista OK, you shouldn't need to worry about it.

I'm sorry, it won't happen again, nevertheless thank You for Your answer.

---

### Post by lildoggie on 2009-01-03
> **caljohnsmith said:**
> I think it would be better to just go ahead and try booting into your new installation, and then we can set up a swap file for you if it works. It would be good if you can disconnect the hdb drive though, because otherwise Ubuntu might mount the hdb1 boot partition rather than hda1 when you get into Ubuntu since their UUIDs are currently the same. Let me know how it goes. :)
Unfortunately, when I tried to boot, I just got the black screen with the blinking cursor in the upper left corner...  :(

---

### Post by lildoggie on 2009-01-03
Well, SuperGrubDisk just saved me -- it took care of everything (makes me wonder if this whole exercise could have been avoided by using it when I got the black screen after trying to install grub on the bigger disk).

Now it'll boot directly from the disk, so that's good.

Now, do we need to do anything to worry about the other directories that we excluded?  Also, what about swap?

---

### Post by caljohnsmith on 2009-01-03
Glad to hear that you can boot now after using Super Grub. So you're in your new hda5 Ubuntu now? If so, how about doing:
```
sudo dd if=/dev/zero of=/swapfile bs=10M [COLOR="Blue"]count=200[/COLOR]
sudo mkswap /swapfile
sudo swapon /swapfile
free

```
Note the above "dd" command will create a 2 GB swap file, so if you want it larger or smaller, just modify the "count" number above (total swap size = 10M X count). Also, please post the output of all the above commands. Next open your fstab:
```
gksudo gedit /etc/fstab
```
And add the following line at the bottom:
```
/swapfile none swap sw 0 0
```
Lastly open up your resume file (if you have one):
```
gksudo gedit /etc/initramfs-tools/conf.d/resume
```
And change the contents of the resume file to:
```
RESUME=/swapfile
```
Next run:
```
sudo update-initramfs -u -k all
```
And then I think you should be all set. I would try rebooting and run the "free" command when you get back into Ubuntu to make sure your swap file is being used and working OK.

---

### Post by lildoggie on 2009-01-03
Excellent!  I'll give it a shot and post back if there are any issues.

Thanks so much for your help!

andy

---

