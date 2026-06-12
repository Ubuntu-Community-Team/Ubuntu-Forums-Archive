---
title: "problem installing extra HD"
date: 2008-09-14
forum: Hardware
---

### Post by 748Snowman on 2008-09-14
I installed an extra 320gig hd into my Xubuntu system, for some reason after I formatted it to a fat32 partition I got an error

"malloc: cannot allocate memory" 

I used Gparted to format it. 

In Gparted there is a little sign next to the format (fat32) of the hd.

Can anyone offer me any advise on this. I'm really stumped and new to Linux.

---

### Post by 748Snowman on 2008-09-15
Can anyone help me? I'm really stumped here.

---

### Post by knattlhuber on 2008-09-15
Don't bump your thread in less than 24hrs.. the Forum Police will come and get you (and rightfully so)..

Is it possible that your filesystem is corrupted?

You could check the filesystem on the disc by running

```
sudo fsck.vfat /dev/devicename
```

where devicename is the name of the HD in question (e.g. sdb1)

---

### Post by 748Snowman on 2008-09-15
Sorry for bumping my post so soon, I was just freaking out. Thought I some how bricked my new hd. 

In the end I think you were correct about the file system being corrupted, I reinstalled xubuntu and it saw the drive right away as fat32.

I guess my next question would be:
I know that if I type in "\\(my servers ip)\homes", takes me to my home dir on the server is there any way I can go directly to the new hd on the server?

Thanks a bunch for your help!

---

### Post by knattlhuber on 2008-09-15
Ha ha, I actually thought that your FAT drive is corrupted... well, in the end my advice worked for you even though not quite as intended :)
The hard drive is mounted in a subdirectory of /media, so you could point your file browser there maybe (\\my.server.ip.address\media\mountdir). I'm not on Xubuntu or a server installation so I have no way to see if that works.

---

### Post by 748Snowman on 2008-09-15
"(\\my.server.ip.address\media\mountdir)"

So the mountdir would be just any old file on the new drive? Not really sure how to set a mount point on the drive.

Thanks again

---

### Post by knattlhuber on 2008-09-15
Do

```
sudo fdisk -l
```

to find the device address (*/dev/sd...*) of the FAT32 drive.

Create a directory in /media as the mountpoint

```
sudo mkdir /media/FATdrive
sudo chmod 755 /media/FATdrive

```
Add the drive to /etc/fstab

```
gksudo gedit /etc/fstab
```

Add this line

```
/dev/sd...    /media/FATdrive    vfat    defaults    0    0
```

Save the file and the drive should mount automatically to /media/FATdrive next time you boot.

Instead of FATdrive you can call it any old name.

There's a great HOWTO on mounting drives: [http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by 748Snowman on 2008-09-23
Finally got around to doing what you instructed but I got errors on boot up, to sum it up the errors were unable to mount. or something like that. I was only able to catch the end of it when I was finally able to get a monitor plugged in. Also when I ran sudo fdisk -l it would show the drive in the list, now it doesn't.
Also when I run "sudo fsck.vfat /dev/hba"

I got an "Read 512 bytes at 0:Input/output error"

Thanks a bunch for your help!

---

### Post by 748Snowman on 2008-09-25
So today I loaded up vnc to move some files to the backup drive. Now the drive isn't even showing up, haha this thing is driving me nuts. I'm wondering if, when I partitioned it to fat32 that gparted did something wrong? Is that even possible, should I just reformat it. If so what would be the best way to do that?

Hope someone can help me :D

---

### Post by knattlhuber on 2008-09-25
Can you please post the output of

```
cat /etc/fstab
```

---

### Post by 748Snowman on 2008-09-25
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>     <dump> <pass>
proc             /proc            proc   defaults      0     0
# /dev/hda2

UUID=46c90374-4562-4999-82cc-95730cc735f2 /            ext3defaults
s=remount-ro 0       1
# /dev/hda5
UUID=98b74514-c004-40d3-a90b-e86e77ac7446 none         swap sw
0      0
/dev/hdc     /media/cdrom0 udf,iso9660 user, no auto  0   0
/dev/fd0     /media/floppy0  auto  rw,user,noauto  0    0

---

### Post by 748Snowman on 2008-09-28
Anyone have an incite on this one? I'm really stumped and have no idea where to even start. 

Thanks a bunch to everyone who has helped.

---

### Post by knattlhuber on 2008-09-28
I think there's something wrong with your FAT formatted drive given that you get all these error messages.

I would try to run

```
sudo fsck.vfat /dev/hdb1
```

again.

You mentioned that you tried that before but I think you had a typo in your syntax. I am assuming that your drive/partition is /dev/hdb1 as it is your second IDE drive and there's only the FAT32 partition on it.

Also, your drive isn't listed yet in fstab, but we can deal with that later.

---

### Post by 748Snowman on 2008-09-28
Ok ran sudo fsck.vfat /dev/hdb1
open /dev/hdb1: No such file or directory

then I tried sudo fsck.vfat /dev/hdb
and got Read 512 Bytes at 0: Input/output error

---

### Post by knattlhuber on 2008-09-28
OK, so it was probably the wrong device name. Can you please try

```
sudo fdisk -l
```

again and post the output?

---

### Post by 748Snowman on 2008-09-28
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

    Device Boot       Start    End   Blocks    Id   System
/dev/hda1              1       2335   18755865  83   Linus
/dev/hda2    *         2336    4772   19575202+ 83   Linus
/dev/hda3              4773    4865     747022+  5   Extended
/dev/hda5              4773    4865     746991  82   Linus swap / solaris

Thanks so much for your help knattlhuber

---

### Post by knattlhuber on 2008-09-28
There appears to be only one hard drive, namely 'hda'. The second drive should show up as 'hdb' (internal, IDE) or 'sda' (external, USB), respectively.
Just to make sure: Is your second hard drive plugged in?

---

### Post by 748Snowman on 2008-09-28
It is plugged in, I wonder if I some how screwed up the format or file system, while trying to set a mount point. So now it has no where to mount from? Is that possible? Should I just pull the hd and format it with a diff computer and start from there?

---

### Post by knattlhuber on 2008-09-28
Not sure why it doesn't show then. You could try if it shows up in GParted (and then re-format it from there) but I doubt it.
Either way, if there's no valuable data on it, I'd reformat the drive and try again.
BTW, is it an internal or external (USB) drive?

---

### Post by 748Snowman on 2008-09-28
I used gparted to format it to fat32 in the first place, should I try a diff program to format it? It is an internal drive. If it doesn't show up in gparted what would be the next step formating it with a diff os? ie: windows, osx?

---

### Post by knattlhuber on 2008-09-28
Could you please do

```
sudo lshw -C disk
```

and post the output?

---

### Post by 748Snowman on 2008-09-29
Output of 
> sudo lshw -C disk

> Hardware Lister (lshw) - B.02.08.01
usage: lshw [-format] [-options ...]
       lshw -version

        -version         print program version (B.02.08.01)

format can be
        -html            output hardware tree as HTML
        -xml             output hardware tree as XML
        -short           output hardware paths
        -businfo         output bus information

options can be
        -class CLASS     only show a certain class of hardware
        -C CLASS         same as '-class CLASS'
        -disable TEST    desable a test
        -enable TEST     enable a test


---

### Post by knattlhuber on 2008-09-29
'sudo lshw -C disk' should give a listing of the drives on your system, at least it does so on mine... and then fdisk -l not showing your partioned drive. Not sure if that's a Xubuntu thing or what's going on. I'm totally lost here. Maybe one of the valued senior forum members can help?

---

### Post by knattlhuber on 2008-09-29
Oh.. now I got it. Your version of 'lshw' is older than mine.. Would

```
lshw -short -C disk
```

produce more meaningful output on your system?

---

### Post by 748Snowman on 2008-09-29
I'll try and reformat the drive with a different comp. I just hope I didn't brick it. Thank you so much again for your help. I'll try the reformat if someone else would like to throw some more ideas into the hat that would be great.

Just tried what you wrote:
> lshw -short -C disk
> H/W path                  Device      Class           Description
=================================================================================
/0/f8000000/7.1/0/0              /dev/hda     disk           37GB ST340823A
/0/f8000000/7.1/0/0/1            /dev/hda1    disk           Linux filesystem partition
/0/f8000000/7.1/0/0/2            /dev/hda2    disk           Linux filesystem partition
/0/f8000000/7.1/0/0/3            /dev/hda3    disk           729 Extended partition
/0/f8000000/7.1/0/0/3/5          /dev/hda5    disk           Linus swap / Solaris partition
/0/f8000000/7.1/0/1              /dev/hdb     disk           298GB WDC WD3200AAJB-00WGAO
/0/f8000000/7.1/1/0              /dev/hdc     disk           ARTEC WRR-52Z  1.25 20030606
/0/f8000000/7.1/1/0/0            /dev/hdc     disk 



You can see the drive right there! YAY

---

### Post by knattlhuber on 2008-09-29
YAY! So it is not partitioned yet. Here goes:

Start fdisk

```
sudo fdisk /dev/hdb
```

Press
"n" to create a new partition on the drive.
"p" to choose 'primary partition'.
"1" as this will be the only partition on the drive.
"w" to write the partition table to the disk

Format the new partition

```
sudo mkfs -t vfat -v /dev/hdb1
```

Create a mount point

```
sudo mkdir /media/FAT320
```

Add drive to /etc/fstab

```
gksudo gedit /etc/fstab
```

Add the following line at the end

```
/dev/hdb1    /media/FAT320    vfat    defaults    0    2
```

Save it. Then do

```
sudo mount -a
```

which should now mount your drive. The drive should also be automatically mounted (and the filesystem checked) on boot.

Hope that works smoothly. If not, let me know.

---

### Post by 748Snowman on 2008-09-29
Got this error when I ran
> sudo fdisk /dev/hdb

> Unable to read /dev/hdb

---

### Post by knattlhuber on 2008-09-29
That seems to be a hardware problem. Maybe something's wrong with your IDE controller or the IDE cable. Is there another IDE cable that you could try on that drive? Did you maybe use the IDE channel/cable for the CD/DVD drive?

---

### Post by 748Snowman on 2008-09-29
Shouldn't be the IDE cable, both /dev/hda1 and /dev/hdb are on the same string. The IDE is even labeled master slave. I don't think I have any extra IDE cables lying around. Could prob buy one.

---

### Post by knattlhuber on 2008-09-29
I googled that error message that you get when you run fdisk ("Unable to read /dev/"). Quite a few people had a similar problem but there's no single one solution.
One person here on the forums reported the same prob and it was due to a faulty IDE controller:
[http://ubuntuforums.org/showthread.php?t=470396]("http://ubuntuforums.org/showthread.php?t=470396")

And there's always the possibility that your drive's completely borked up.

I would probably try the drive on a different computer (Win, Linux, doesn't matter) and see what happens. Or, hook up a drive that's know to be working to the same IDE cable thereby testing your IDE controller.

I don't know much about hardware so I can't really help you beyond this point, sorry. :(

Cheers,
Stefan

---

### Post by 748Snowman on 2008-09-29
One thing I don't get is, why after I set up a file and set up a new mount point wrote it in the fstab, then after all that it wouldn't load or mount the drive. Before that it would show up just fine. 

I'll try it on a diff channel and a diff cable. Then post my findings. 

Also I recall you saying something was wrong with my fstab, could that be the cause of my problems?

On another topic when I connect to my system via puddy, why does it always tell me I have "new mail"

---

### Post by knattlhuber on 2008-09-29
Your fstab did not have an entry for you FAT drive, other than that it looks fine. Could it be that you edit fstab without sudoeing? But that doesn't really matter for your problem. The strange thing is that 'lshw' lists your drive but 'fdisk' can't access it. So your BIOS and kernel see the drive, but you are not able to do anything with it (as indicated by all the error messages you got when you tried to mount/access the drive). To me that sounds like a hardware problem.

BTW, what version of Xubuntu are you using?

---

### Post by 748Snowman on 2008-09-29
I'm running Feisty 7.04. I'm gonna try and format the disk with a diff os, I wonder if I didn't change something software related to the HD. I did the things  you told me to do (set up file, set mount point.) Restarted the computer got the error, then the HD was gone from that point on. Maybe its as simple as restarting the computer. Since I only restarted it twice only after I edited the fsab.

Also is there anyway I can look up all the mount points, like add remove them?

---

### Post by knattlhuber on 2008-09-29
Creating a mountpoint wouldn't cause these problems as it is nothing more than creating a directory in the /media folder. You can remove the mountpoint by doing

```
sudo rm -r /media/yourmountpoint
```

but really there is no need to do so. Drives under Ubuntu are commonly mounted in a subdirectory of /media.

```
cat /etc/fstab
```

will show you the current mountpoints for your drive. You can also use GParted to see to which directory your drives are mounted.

As I said earlier, your changes to /etc/fstab weren't saved as can be seen by the 'cat /etc/fstab' command. Restarting doesn't really matter in this case. Once you have added a drive to fstab, you can mount it by doing

```
sudo mount -a
```

without restarting.

---

### Post by 748Snowman on 2008-09-29
The reason that wasn't in the fstab, was beacuse I removed it duo to the errors on start up. Is it possible I put the command in the wrong place in fstab?

Once I get home from work I'll mess around with it some more.

---

### Post by knattlhuber on 2008-09-29
You said that initially you were able to see and mount the drive and copy files to it, right? Maybe maybe maybe something messed up your partition table which now prevents fdisk from reading from your drive. You could try testdisk to repair the partition table:

```
sudo apt-get update
sudo apt-get install testdisk
sudo testdisk
```

When you run testdisk, choose "C" to create a logfile and then check if on the next screen your drive (/dev/hdb) shows up. If not, do *NOT* mess with /dev/hda or any other drive you see, just press "Q" to quit.
If /dev/hdb shows up, select it with the arrow keys, press ENTER and follow the instructions on the screen.

---

### Post by 748Snowman on 2008-09-30
Running it right now, It failed right off the bat on the partition test, now its checking cylinders. Showing me alot of read errors. Man I must of mucked something up pretty bad. 

One of the up shots to this is the fact that we have this huge post going, so that if anyone else runs into this. Bam pretty much all the info they are gonna need.

---

### Post by 748Snowman on 2008-10-01
Well putty timed out or something, I can restart it but it was gonna take a few days to get thru all the tests. Should I just restart it and let it go? Or just format it and start over there wasn't any important files on it. So I wouldn't be at a loss

---

### Post by knattlhuber on 2008-10-01
Well, see if you can now format and partition the drive using the instructions in post #26. Then check it for physical defects using

```
sudo badblocks -v /dev/hdb1
```

and for logical errors using

```
sudo fsck.vfat /dev/hdb1
```

The drive must not be mounted while you do above commands.

---

### Post by 748Snowman on 2008-10-01
Well I have major issues, I hooked up a screen to the box and tried to run Gparted. Gparted just sat there and scanned. On top of that another one of my drives is now missing. I should say not another drive missing but a partition on the same drive as the OS. It is also still giving me tons of errors on bootup. 

I am just gonna have to start fresh, I think something must be very mucked up with the OS. Unless it is as you believe a hard ware issue.

---

### Post by knattlhuber on 2008-10-01
Oh man... :)

Do

```
fdisk -l
```

and see what you get.

---

### Post by 748Snowman on 2008-10-01
The results were the same as before.

I'm to the point of just starting fresh. Not sure what dmg has been done to the system. Unless its hardware, also even after cleaning the backup drive. Its still not showing up in fdisk.

---

### Post by 748Snowman on 2008-10-16
So one of the things I think I was over looking was editing the config for samba. That might of just been the start of the problem.

well live and learn.

> nano smb.conf

---

