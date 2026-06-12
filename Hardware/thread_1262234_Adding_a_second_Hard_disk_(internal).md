---
title: "Adding a second Hard disk (internal)"
date: 2009-09-09
forum: Hardware
---

### Post by David Beard on 2009-09-09
Hi, 

I'm something of a newbie to Ubuntu (but a very happy one) and would appreciate a little guidance:-

I want to add a second internal sata HDD to my PC - I have no problem with the physical installation but I'm not too confident about the steps I need to take thereafter, I think I'll need to mount the new drive or will this happen automatically at start up ?

I guess I'll then need to create a partition (or several) on the drive - can this be done from the GUI or am I heading for some command line fun?

I am tempted to just install the drive & start playing but would really prefer not to risk trashing the existing system.

Any help greatly appreciated,

Thanks
DB

---

### Post by lindsay7 on 2009-09-09
First thing to remember is to make sure that the power is off. Shut down your system and take the power cord out of the back of the machine.  Install the new drive and restart the computer.  Your system may or may not see the new drive at first.  If the system does not see the drive open Gparted and look for the drive there.  It may show up as unallocated space. Format the drive any way you want.  I have found that formatting as a fat32 file system is fast and will get you started and your system will see the new drive.  You can the use Gparted to partition and format the file systems as you want later on.

---

### Post by theozzlives on 2009-09-09
> **lindsay7 said:**
> First thing to remember is to make sure that the power is off. Shut down your system and take the power cord out of the back of the machine.  Install the new drive and restart the computer.  Your system may or may not see the new drive at first.  If the system does not see the drive open Gparted and look for the drive there.  It may show up as unallocated space. Format the drive any way you want.  I have found that formatting as a fat32 file system is fast and will get you started and your system will see the new drive.  You can the use Gparted to partition and format the file systems as you want later on.

USE STATIC PRECAUTIONS! Use an ESD strap or touch the metal of the case while in there. I recommend NTFS as a file system unless you want the whole thing to be /home. After you create your partition with gparted, you'll need to add a line in your /etc/fstab:
```
mkdir /home/drive2
gksudo gedit /etc/fstab
```
Add a line like:
```
dev/sdb1 /home/drive2 ntfs relatime 0 1
```
is just an example, see this thread [http://ubuntuforums.org/showthread.php?t=1244185]("http://ubuntuforums.org/showthread.php?t=1244185")

---

### Post by David Beard on 2009-09-10
Thanks guys,

I'm fine with the actual physical installation - done it hundreds of times in windoze / dos but just needed a little confidence boost for the formatting / mounting aspects - I'll do the job later today.

Cheers
Dave

---

### Post by ukreech on 2009-09-10
i'm doing the format using NTFS everytime.. what's the difference between NTFS and FAT32 anyway?:confused:

---

### Post by rob-ward on 2009-09-10
> **lindsay7 said:**
> First thing to remember is to make sure that the power is off. Shut down your system and take the power cord out of the back of the machine.  Install the new drive and restart the computer.  Your system may or may not see the new drive at first.  If the system does not see the drive open Gparted and look for the drive there.  It may show up as unallocated space. Format the drive any way you want.  I have found that formatting as a fat32 file system is fast and will get you started and your system will see the new drive.  You can the use Gparted to partition and format the file systems as you want later on.

Not to be picky but you shouldn't take the power cable out you should just turn the power of at the switch on the PSU or the wall, the reason for this is that the case is then kept grounded meaning that the likelyhood of static build up and damage to equipment is reduced to nearly zero.

[quote=ukreech]i'm doing the format using NTFS everytime.. what's the difference between NTFS and FAT32 anyway?:confused:[/quote]
The difference is quite significant, in fat32 for example you can't have files larger than 4gb. NTFS is however slower on linux than fat32, I would just stick to ext3.

---

### Post by lindsay7 on 2009-09-10
Rob-Ward,  if you do not disconncect the power cord, there is still power going to the case and one would be making an assumption that there are no shorts or ground faults in the system (a bad idea). You are correct that keeping the power cord attached does provide a ground to the case and I the person working on the computer has a anti-static strap attached to them and it is grounded to the same ground point as the power cord, then there is little possibility of damaging the compnents.  The safest way  to work on computers is to remove the power cord and ground the case to a good system ground point and to use the anti-stactic strap grounded to the same system ground point.  For safty sake it is better to risk a computer component because of static then to shock a person if the power cord is attached.

---

### Post by rob-ward on 2009-09-11
If it is turned off at the wall there should be no power going to the case, this can be determined with a multimeter on the powercord if you are not an an indicated socket. Once there is no power it is better to leave it in for grounding. Safety isn't really an issue as the ouput from the PSU does not have the ability to do anything but give a mild shock, so unless you are taking the PSU apart then then it is OK, if you are taking the PSU apart then the capacitors hurt like hell when they zap you(i have a tendancy to ignore the labels that say only qualified personel should take them apart). 

I know the litriture and what people are tought is to disconnect the power cord but there is really no danger and it is the cheap way of protecting your computer components. Of cause you could always make one of my power grounding plugs and connect it to the case(it has no other wires except ground)

---

### Post by trundlenut on 2009-09-11
I think because of the difference in electrical sockets between the UK and US that in the US most sockets don't have switches on them and so they are live if plugged in.

---

### Post by rob-ward on 2009-09-11
ah, yes very true, ye people in US may want to disconnect the computer from the mains then. Good point

---

### Post by Mostly.Harmless on 2009-09-11
Hey guys,

Having the same problem.


Ive read around as much as I can.  I think this is the most related case.

I have a 500gb internal sata drive which is my boot hd. I use it for all the normal stuff. Ive put in a samsung 1TB internal sata hd. I have created 1 primary partition (ext3 format) I called it MediaDump or something like that

If it means anything, I would like the drive to remain as one uncomplicated drive with no partitions, just a simple mass dump for media files.

Ive fiddled around for ages, I can usually get it to see the drive but like the creator of this thread, I cant write to it.

So How do I fix this?

---

### Post by rob-ward on 2009-09-11
Can you load a terminal and then run the following commands and paste the output in here:

```
sudo fdisk -l
```

```
df
```

```
mount
```

```
cat /etc/fstab
```

---

### Post by Mostly.Harmless on 2009-09-11
Sure,

In order of request.

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000db44a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1      121601   976760001   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0003758a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       60050   482351593+  83  Linux
/dev/sdb2           60051       60801     6032407+   5  Extended
/dev/sdb5           60051       60801     6032376   82  Linux swap / Solaris
chris@chris-desktop:~$ 


chris@chris-desktop:~$ df
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb1            474781296 229999480 220664240  52% /
tmpfs                  1030716         0   1030716   0% /lib/init/rw
varrun                 1030716       220   1030496   1% /var/run
varlock                1030716         0   1030716   0% /var/lock
udev                   1030716       148   1030568   1% /dev
tmpfs                  1030716       284   1030432   1% /dev/shm
lrm                    1030716      2192   1028524   1% /lib/modules/2.6.28-15-generic/volatile
chris@chris-desktop:~$ 

chris@chris-desktop:~$ mount
/dev/sdb1 on / type ext3 (rw,relatime,errors=remount-ro)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/chris/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=chris)
chris@chris-desktop:~$ 


chris@chris-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=614e793e-4089-438f-b0a1-2f58d2aea0a9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=76b3ad15-2249-426f-af70-668be3aefa42 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
chris@chris-desktop:~$ 


Thanks,

---

### Post by rob-ward on 2009-09-11
OK, firstly the 1TB drive you have inserted has taken priority over your other so it is now /dev/sda for the 1TB drive and /dev/sdb for you 500gb boot drive.

According to mount the sda(1TB) drive isn't mounted, to test that it can mount you will have to run the following commands:

```
sudo mkdir /mnt/storage
```

```
sudo mount /dev/sda1 /mnt/storage
```

Once you have run them commands you should have your 1 terabyte drive mounted in /mnt/storage.

This means that if you cd to that directory you should be able to create files and directories.

If that works we can work on making it mount automatically on startup.

Give that a go and let us know how it goes.

---

### Post by Mostly.Harmless on 2009-09-11
Hey mate,

Well, It certainly did something, I did those commands with no visible improvement, however, I then restarted the computer and it appeared, looking like it should.

However, I tried putting a file in it and I got this

"The folder "Jap" cannot be copied because you do not have permissions to create it in the destination"

Which is a new error.

Thanks again for all the help

---

### Post by rob-ward on 2009-09-11
Oh that is a standard permission error, in order to fix that you need to run this command:

```
sudo chmod 777 /mnt/storage
```

Substitute /mnt/storage to the location the drive is mounting if you have it different.

You should then be able to copy files.

If that works we will make it mount automatically each boot either there or wherever you want.

---

### Post by Mostly.Harmless on 2009-09-11
I tried that command, it did not work. 

How do I know what location the drive is mounting?

Error:
Error opening file '/media/MediaDump/Alliance Execution code sample.odt': Permission denied

---

### Post by Mostly.Harmless on 2009-09-11
Ah I see,

I looked in the properties, it was located in /media/mediadump

I ran the command again and I can now place files in the Hard drive. Many thanks, this is the furthest I have ever gotten.  You mentioned a final step, I think im ready for that if you are.

---

### Post by rob-ward on 2009-09-11
What you need to do is place an entry in fstab

so what you need to to is launch a terminal and run this command:

```
sudo gedit /etc/fstab &
```

At the moment the line contains the following text at the bottom:

[CODE# / was on /dev/sda1 during installation
UUID=614e793e-4089-438f-b0a1-2f58d2aea0a9 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=76b3ad15-2249-426f-af70-668be3aefa42 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0][/CODE]

You need to add a line similar to this but you need the correct UUID, to find the UUIS you need to run this command in the terminal

```
sudo vol_id --uuid /dev/sda

```

this will print a line like this:
```
76b3ad15-2249-426f-af70-668be3aefa42
```

Copy that number,

now in the fstab you want to start a new line and enter this:
```
UUID=INSERT-THE-ONE-YOU-COPIED /media/mediadump               ext3    relatime,errors=remount-ro 0       1
```

Then save the file, now whenever you reboot the computer the HDD will be mounted into /media/mediadump

Hope that helps you.

---

### Post by ahbart on 2009-09-11
Why for god sake are you (first page) recommending the topic starter to format as fat32 or NTFS! Under linux there much better filesystems! What about ext2, 3 or better ext4!

---

### Post by Mostly.Harmless on 2009-09-11
Thanks so much Rob

I have fstab open

But when I attempt to run the second command in the terminal I get this

chris@chris-desktop:~$ sudo vol_id --uuid /dev/sda
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
chris@chris-desktop:~$

---

### Post by rob-ward on 2009-09-11
> **ahbart said:**
> Why for god sake are you (first page) recommending the topic starter to format as fat32 or NTFS! Under linux there much better filesystems! What about ext2, 3 or better ext4!

Not sure who that comment is aimed at hopefully it wasn't me cos I don't use either partitions, ibeileve what I said was

[QUOTE=rob-ward]The difference is quite significant, in fat32 for example you can't have files larger than 4gb. NTFS is however slower on linux than fat32, I would just stick to ext3.[/QUOTE]

Like I said there I would stick with ext3, never ntfs, I was just responding to the question what is the difference. ext4 is slightly maybe, problem with ext4 is it isn't 100% proved yet and there have being some reports of minor dataloss, also it can't be read under windows at the moment, however I would take ext4 over ntfs every time and am considering changing to ext4 at karmic.

---

### Post by rob-ward on 2009-09-11
> **Mostly.Harmless said:**
> Thanks so much Rob

I have fstab open

But when I attempt to run the second command in the terminal I get this

chris@chris-desktop:~$ sudo vol_id --uuid /dev/sda
unknown or non-unique volume type (--probe-all lists possibly conflicting types)
chris@chris-desktop:~$

K, my bad try:

```
sudo vol_id --uuid /dev/sda1
```

---

### Post by Mostly.Harmless on 2009-09-11
Just to confirm,

I copied your code directly from the box but placed my uuid in, It looked like this

UUID=5be5e5db-0e1c-4f5d-9dc2-18cfca030807 /media/mediadump               ext3    relatime,errors=remount-ro 0       1

I then Saved.

Is this correct?

---

### Post by rob-ward on 2009-09-11
Yep, that should do it, now everytime you restart it should mount automatically

---

### Post by Mostly.Harmless on 2009-09-11
I bow in your general direction.

Domo arigatou & Muchos Gracias

---

### Post by rob-ward on 2009-09-11
lol, it's no problem, and if you have any more trouble with it let me know.

---

### Post by ahbart on 2009-09-11
> **rob-ward said:**
> Not sure who that comment is aimed at hopefully it wasn't me cos I don't use either partitions, ibeileve what I said was
..
Like I said there I would stick with ext3, never ntfs, I was just responding to the question what is the difference. ext4 is slightly maybe, problem with ext4 is it isn't 100% proved yet and there have being some reports of minor dataloss, also it can't be read under windows at the moment, however I would take ext4 over ntfs every time and am considering changing to ext4 at karmic.

It was a litlle emotional ;-) reaction against the second (#2 - fat32 lindsay7) and the third (#3 - ntfs theozzlives) 'posters'. 

Sorry no offence to anyone, but fat32 and ntfs are far more inferior on linux, than the native linux filesystems.

---

### Post by ahbart on 2009-09-11
If you are sure that only one person will use this media drive, you can mount it to /home/your-username/media. That's more easy to find. Or you can mount it to /home/media, like I did and make a symlink to /home/your-username/media.

My fstab line:
```
UUID=8723c99b-7911-4c0f-9418-3fbf6473617e /home/media     ext3    defaults        0       2
```

```
ln -s /home/media /home/your-username/media
```

---

### Post by rob-ward on 2009-09-11
> **ahbart said:**
> It was a litlle emotional ;-) reaction against the second (#2 - fat32 lindsay7) and the third (#3 - ntfs theozzlives) 'posters'. 

Sorry no offence to anyone, but fat32 and ntfs are far more inferior on linux, than the native linux filesystems.

No offence taken and I completly agree, I would take any linux filesystem(ext2, ext3, ext4, xfs, raiserfs) over fat32 and ntfs any day

> **ahbart said:**
> If you are sure that only one person will use this media drive, you can mount it to /home/your-username/media. That's more easy to find. Or you can mount it to /home/media, like I did and make a symlink to /home/your-username/media.

My fstab line:
```
UUID=8723c99b-7911-4c0f-9418-3fbf6473617e /home/media     ext3    defaults        0       2
``````
ln -s /home/media /home/your-username/media
```

This is a good point however it may be better to make a symbolic link in your home directory to the drive mounted in /mnt or /media rather than mounting it in you home directory(bad practice), that was if you or someone else were to log on as a guest you would still be able to access it, as would any other users that you create.

---

### Post by ahbart on 2009-09-11
> **rob-ward said:**
> This is a good point however it may be better to make a symbolic link in your home directory to the drive mounted in /mnt or /media rather than mounting it in you home directory(bad practice), that was if you or someone else were to log on as a guest you would still be able to access it, as would any other users that you create.

I agree with this. I will change it to /media/name-of-the-disk. Don't know why I choose /home/media for that in the past.

---

### Post by rob-ward on 2009-09-11
We all have bad habbits, i'm still using /mnt instead of /media

---

### Post by louieb on 2009-09-11
> **rob-ward said:**
> ...you should just turn the power of at the switch on the PSU or the wall, the reason for this is that the case is then kept grounded...

+1  When working in the house. Thats the way I do it too. 

Got my A+ certification back when the test covered windows 98 and the hot CPU was a P3. ESD and its prevention  has not changed much - don't walk across the carpet in your leather shoes and touch the CPU.

---

### Post by Mostly.Harmless on 2009-09-13
Its the next days, I have restarted my computer since then and I have a minor problem. It says im not privileged to mount the volume. 

The volume has appeared just fine and seems to be normal otherwise. 

Im new to Ubuntu and all this access control is starting to bug me. Is there some way I can turn this off? I am the administrator and I dont have permission to mount a sata drive in my own computer. 

I tried the commands given to me previously, Ot asked me for a password as normal, and appeared to do nothing.

I got this on subsequent attempts:

"chmod: cannot access `/media/MediaDump': No such file or directory"

---

### Post by rob-ward on 2009-09-13
The drive should have automatically mounted, can you provide the output of the command

mount

and

sudo fdisk -l

and 

cat /etc/fstab

Then we should be able to see why you can't access your drive.

There shouldn't be any permission problems with the drive as you have got it auto mounting into a directory where you have full permissions, hopefully we will be able to see what is wrong from the output of them commands.

---

### Post by Mostly.Harmless on 2009-09-13
Well, you see... The funny thing about that is, I attempted to fix the problem myself. I scoured the forums and found one possible way. I ran some code which installed a volume manager or something, a simple ubuntu program which listed what I think was my drives, had buttons like assistant and mount volume.

I went into assistant frustrated with all of this 'permission' garbage and clicked a few click boxes which read "allow user to mount volume' and simple stuff like that.

I rebooted, and now it appears I melted my computer, I get a whole lot of errors when ubuntu boots (in the ms-dos like blackscreen white writing bit) and It just stalls there, allowing me to go on and type in some wonder code which will make evberything better.

After an hour, Im here running what seems to be a bare bones ubuntu, off the boot disk option "try ubuntu without any change"

It appears I have failed, astronomically. 

Is this situation repairable? or should I make this computer a new water feature, as Ive been trying for days to make it work.

/Thanks

---

### Post by Mostly.Harmless on 2009-09-13
If it helps, here are the current outputs. 

ubuntu@ubuntu:~$ mount
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.28-11-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
rootfs on / type rootfs (rw)
/dev/sr0 on /cdrom type iso9660 (ro,noatime)
/dev/loop0 on /rofs type squashfs (ro,noatime)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
/dev/sda1 on /media/MediaDump type ext3 (rw,nosuid,nodev,uhelper=hal)
ubuntu@ubuntu:~$ 


Command 2:
ubuntu@ubuntu:~$ sudo fdisk 1

Unable to open 1

Command 3:

ubuntu@ubuntu:~$ cat /etc/fstab
aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0


In a truly ironic chain of events, As im now running a live session of the boot disk, I can now see, and access files on my 1TB internal. So It looks like I can have an operable OS, or an accessible HD.

---

### Post by rob-ward on 2009-09-13
You can probably fix the errors however it may take awhile do do so, do you have a lot of data on the drive/any thing important, if not it may be better for you to install ubuntu again and chalk this attempt up to experiance.

If you would prefer to try and fix the problem then we can have ago but it may not be easy as we will have to mount your other ubuntu install in the livecd and try to change it.

If you are able to see the 1TB drive in the live CD then it is likely if you reinstall then you will still be able to see it.

---

### Post by Mostly.Harmless on 2009-09-13
I dont want to waste anyone's time for my own epic failures. 

I will bow my head in shame then re-install ubuntu. I will report back here.

/thanks

---

### Post by rob-ward on 2009-09-13
It's no problem and if you run into any problem in or after the reinstall then let me know.

---

### Post by Mostly.Harmless on 2009-09-13
I have re- done everything. currently updating everything/trying to get everything back to how it was. The 1TB sata seems to be working normally. I pray it continues that way

Thanks.

---

### Post by louieb on 2009-09-13
> **Mostly.Harmless said:**
> ..I will bow my head in shame then re-install ubuntu. I will report back here.
:) Welcome to the club!  I've screwed it, reinstalled, more that once - just trying to do what I find simple now. seeing what works and how to do it.

---

### Post by rob-ward on 2009-09-13
> **Mostly.Harmless said:**
> I have re- done everything. currently updating everything/trying to get everything back to how it was. The 1TB sata seems to be working normally. I pray it continues that way

Thanks.

I'm sure it will be fine.

> **louieb said:**
> :) Welcome to the club!  I've screwed it, reinstalled, more that once - just trying to do what I find simple now. seeing what works and how to do it.

Don't worry I have installed Ubuntu countless times when I was learning it, the problem is that unless you are using it as a standard machine for web browsing and word processing you always tend to do more, install more and tweak things, then you tweak something you shouldn't have and you end up reinstalling. However this is the beauty of Ubuntu/Linux, it can be a stable and easy to use OS or it can be a customised monster that does things how you want them to be done... I love open source

---

