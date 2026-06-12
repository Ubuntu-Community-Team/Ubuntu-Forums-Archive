---
title: "external hard drive, problems at boot, autorun message"
date: 2009-01-02
forum: Hardware
---

### Post by PierreRussellStraddler on 2009-01-02
Hello!

I have a western digital mybook premium edition es hard drive.  It is an external USB hardrive.  

On it is 3 partitions: 1 partition has my files generated during my years as a windows user.  the other two partitions are failed attempts at installing ubuntu on the external hard drive.

Now that Ubuntu is installed on my internal hard drive, I would like to turn the 2 ubuntu-installation partitions on my external hard drive (the WD mybook premium edition es hard drive) into one gigantic empty space where I can put my files and projects from ubuntu.

The funny thing about this hard drive is that if it is plugged in when I turn on the computer, the computer doesn't boot.  Does not make it to grub.  This, obviously, is a drag.

When I plug it in while the computer is running, two screens pop up: /media/disk 1 and /media/disk 2 (again, both of which contain a ubuntu download).

When I go to Places>Removable Media> and I choose the 3rd partition (the one with the files from windows), there is a band at the top that says "the media contains software" and to the far right, there is a button that says "open auto run prompt."

When I look at the files in this 3rd partition, I see a file called "auto run."  In it are four files:

autorun.bat
autorun.inf
autorun.run
wdlogo.ico

wdlogo.ico has a western digital icon.  because it is in the same folder as everything else, I assume they're all from western digital.

How do I make my Western Digital external USB hard drive this passive thing where I store a bunch of files? Can the autorun file be removed, or is that too easy?

Any help would be greatly appreciated.

thanks!

Pierre Russell Straddler

---

### Post by logos34 on 2009-01-03
Here's what I'd do:

unmount the partitions on the usb drive. 

In a terminal:

[B]sudo apt-get install gparted

gksudo gparted[/B]

Delete the two linux partitions.  Create a new primary partition in their place, formatted** ext3**. More info [here]("https://help.ubuntu.com/community/InstallingANewHardDrive#Partitioning%20Using%20GParted").

Give it a [volume label]("https://help.ubuntu.com/community/RenameUSBDrive#ext2%20and%20ext3").


Try to fix windows:

[B]sudo apt-get install ntfs-config

gksudo ntfs-config[/B]

enable write support for external drive (ntfs partition).  Enter a mountpoint (like **/media/windows**). 

post back if you have any questions

make sure the Bios device boot order is set for:

cdrom first, then hard disk

in the separate hard disk boot priority, the internal hard disk should be first/top of list

---

### Post by PierreRussellStraddler on 2009-01-04
Hi Logos34

Thanks for your help!


sudo apt-get gparted worked great.

according to gparted, I erased the two ubuntu partitions and indeed made one gigantic partition on the external hard drive, formatted in ex3.

I tried to give it a volum label.  When I do, I get the message

pierre@pierre-desktop:~$ sudo e2label /dev/sdb
e2label: Bad magic number in super-block while trying to open /dev/sdb
Couldn't find valid filesystem superblock.


That said, the new partition appears on the desk top, along with the name I gave it, as well as the windows partition.

Did I succeed in giving the partition a volume label?  Is that "LinuxHD"

The only folder in the new partition is one that says "lost and found" and above it to the right, is a small orange circle with a rectangle that has an x through it.



later in your message you wrote this.

enable write support for external drive (ntfs partition). Enter a mountpoint (like /media/windows). 

I'm not entirely sure what that means...I think I can enable write support for external drive, but I'm not sure I understand what you mean by "enter a mount point"--are you saying give the prompt (i'm assuming) a new name (in your instance "windows") or are you saying I should know the name of the disk/partition/something else?

ok, thanks again for your help.  Talk soon,

Pierre Russell Straddler

---

### Post by logos34 on 2009-01-04
> **PierreRussellStraddler said:**
> 
enable write support for external drive (ntfs partition). Enter a mountpoint (like /media/windows). 

I'm not entirely sure what that means...I think I can enable write support for external drive, but I'm not sure I understand what you mean by "enter a mount point"--are you saying give the prompt (i'm assuming) a new name (in your instance "windows") or are you saying I should know the name of the disk/partition/something else?


ie. enter '/media/windows' or whatever (without '') and it will use that as the mointpoint.  It edits /etc/fstab for your--if you check afterward, you'll  see the entry with that mount


As for the label you should have entered the partition # and the label something like this:
> 
sudo e2label /dev/sdb2 LinuxHD

or sdb1, whatever the linux partition is you created.

But if it's showing up on the desktop as LinuxHD then you must have done it right

---

### Post by PierreRussellStraddler on 2009-01-04
Hi

when I do  

gksudo ntfs-config

a screen pops up and gives me a choice between

+ Enable write support for internal device
 or
+ Enable write support for external device

I chose Enable write support for external device (as you suggested) and when I press "OK" the little screen disappears, and nothing else happens.

Is something else supposed to happen?  Am I supposed to type something into the terminal window after I choose enable write support for external device?


also...


When I plug in the USB hard drive, the first screen that pops up is "LinuxHD" or /media/LinuxHD.  For some reason, I am not permitted to create a new folder on the external hard drive.  In addition, I still get the message that says "This medium contains software intended to be automatically started.  Would you like to run it?."  This is coming from the windows partition, and my guess is that it's trying to run the western digital factory installed software.

Thanks for your continued help,

Pierre Russell Straddler

---

### Post by theozzlives on 2009-01-04
delete the factory software and go to the terminal and type:
```
sudo chown username /media/LinuxHD
```
username would be your username, then set your permissions.

---

### Post by logos34 on 2009-01-04
ok, I guess it's automounting using the label.  Just what you want, so leave it.

With the drive mounted, what does 

mount

or

cat /etc/mtab

show?

If it's mounted as fuse filesystem, then you have ntfs-3g (write) support and everything is fine

---

### Post by PierreRussellStraddler on 2009-01-04
Hello Friends!

Logos34:

mount produces

/dev/sda5 on / type ext3 (rw,relatime,errors=remount-ro)
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
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/pierre/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=pierre)
gvfs-fuse-daemon on /home/misskaka/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=misskaka)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)
/dev/sdb7 on /media/LinuxHD type ext3 (rw,nosuid,nodev,uhelper=hal)

cat etc/mtab:

 /dev/sda5 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
/proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.27-9-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/pierre/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=pierre 0 0
gvfs-fuse-daemon /home/misskaka/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=misskaka 0 0
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush 0 0
/dev/sdb7 /media/LinuxHD ext3 rw,nosuid,nodev,uhelper=hal 0 0

logos34, theozzlives--

is there consensus on what the terminal code should be?

is it:

sudo chown pierre /media/LinuxHD

or is it:

sudo chown -R pierre:pierre /media/LinuxHD

I just read "Linux is not Windows" and so I want to extra thank you both so much for your help.

Pierre Russell Straddler.

---

### Post by PierreRussellStraddler on 2009-01-04
And there is this too, if this helps any.

thanks again,

Pierre Russell Straddler

pierre@pierre-desktop:~$ ls -al /media
total 56
drwxr-xr-x  6 root   root  4096 2009-01-04 14:58 .
drwxr-xr-x 20 root   root  4096 2008-12-08 00:11 ..
lrwxrwxrwx  1 root   root     6 2008-12-07 14:20 cdrom -> cdrom0
drwxr-xr-x  2 root   root  4096 2008-12-07 14:20 cdrom0
drwxr-xr-x  2 root   root  4096 2008-12-07 14:20 cdrom1
drwx------ 28 pierre root 32768 1969-12-31 16:00 disk
-rw-r--r--  1 root   root   172 2009-01-04 14:58 .hal-mtab
-rw-------  1 root   root     0 2009-01-04 14:58 .hal-mtab-lock
drwxr-xr-x  3 root   root  4096 2009-01-04 00:03 LinuxHD

---

### Post by PierreRussellStraddler on 2009-01-04
ah--

one more thing--

Is it possible all users on the computer (all two of us) to have permission to write to the external HD?

ok thanks.

prs

---

### Post by logos34 on 2009-01-04
oh, so the windows partition is fat32!  No wonder the problem--I should have asked for your **sudo fdisk -l**...I just assumed it was NTFS formatted
> 
/dev/sdb1 /media/disk [COLOR="Red"]vfat[/COLOR] rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=10 00,utf8,umask=077,flush 0 0
/dev/sdb7 /media/LinuxHD ext3 rw,nosuid,nodev,uhelper=hal 0 0

Ntfs-config not needed in that case.  Linux natively supports read write to fat32.

Use 

> sudo chown -R pierre:pierre /media/LinuxHD

You want to own folders inside /media/LinuxHD and everything below.  More info bottom of [this page]("http://www.psychocats.net/ubuntu/mountlinux").

sudo chmod -R 777 /media/LinuxHD

-rwx access to all users

---

### Post by PierreRussellStraddler on 2009-01-04
Hello!

Some victories.  Yaaay!

I can now save files to /media/LinuxHD.  That is a VICTORY!

I cannot, however, create files in /media/LinuxHD in which to put these newly saved files.

Also,

There is still that persistent problem wherein if I turn the computer on with the hard drive plugged in, the computer won't boot--it doesn't go to grub, it freezes on the pre-grub screen.

I erased the western digital "autorun" folder and it's contents (moved them in to the trash and emptied trash) and that didn't seem to do very much.

anyhow, I can save to the hard drive, and that is a tremendous victory for the day.  Thank you for all your help.

Pierre Russell Straddler

---

### Post by logos34 on 2009-01-04
> **PierreRussellStraddler said:**
> 
I can now save files to /media/LinuxHD.  That is a VICTORY!

I cannot, however, create files in /media/LinuxHD in which to put these newly saved files.


so you're saying you cannot create new directories even after taking ownership?

mkdir /media/LinuxHD/newfolder

?

> 
still that persistent problem wherein if I turn the computer on with the hard drive plugged in, the computer won't boot--it doesn't go to grub, it freezes on the pre-grub screen.

I'm thinking that maybe the boot order in the Bios is changing--when the usb is connected, the machine tries to boot from it instead of internal disk.  Check device boot order and hard disk boot priority (separate section)

---

### Post by PierreRussellStraddler on 2009-01-04
hold on...now all of a sudden everyone can make a folder.  double victory today!

maybe it will all change once I turn the computer off and on again.  Hopefully not, though, as things seem to be 'fixed'

as for the other problem with the no boot up at start up, I've been round and round with that one for a while now.  I will pursue it in another section.

Thank you for all your help today logos34!  Yaaay!

Pierre Russell Straddler

---

### Post by logos34 on 2009-01-04
ok.  glad I could be of assistance.  

> **PierreRussellStraddler said:**
> hold on...now all of a sudden everyone can make a folder.  double victory today!

If by chance you want others to have only read+execute access (no write), do:

sudo chmod -R 755 /media/LinuxHD

['How to set file permissions -  numeric mode']("http://www.tuxfiles.org/linuxhelp/filepermissions.html")

good luck and enjoy

---

### Post by PierreRussellStraddler on 2009-01-05
Hi again.

I recently successfully created a folder and copied a number of files from my internal hard drive to my external hard drive, using both the GUI and the terminal command line.  VICTORY.

In order to make my .wav files readable, I need to use the sox command on the command line, i.e.

sox file_1.wav file_1a.wav

I tried to do that operation on files that reside on the hard drive, and I get an error message:

pierre@pierre-desktop:/media/LinuxHD/Electronica$ sox electronicsplitapart_first.wav electronicsplitapart_first-1.wav
sox soxio: Can't open output file `electronicsplitapart_first-1.wav': Permission denied

so in the end, I guess I really didn't solve the permission problem totally, nor did I totally understand the info at the bottom of [this page]("http://www.psychocats.net/ubuntu/mountlinux")...I'm still unclear on "mount points" and fstab and what not...

so how does one go about getting permission to run commands on files that exist on the external hard drive?

(and if you knew how to get Grip to export files to the external hard drive instead of the internal hard drive, I'd be doubly grateful!)

any help would be much appreciated.

Thanks so much!

Pierre Russell Straddler.

---

### Post by logos34 on 2009-01-05
> **PierreRussellStraddler said:**
> Hi again.

I recently successfully created a folder and copied a number of files from my internal hard drive to my external hard drive, using both the GUI and the terminal command line.  VICTORY.

In order to make my .wav files readable, I need to use the sox command on the command line, i.e.

sox file_1.wav file_1a.wav

I tried to do that operation on files that reside on the hard drive, and I get an error message:

pierre@pierre-desktop:/media/LinuxHD/Electronica$ sox electronicsplitapart_first.wav electronicsplitapart_first-1.wav
sox soxio: Can't open output file `electronicsplitapart_first-1.wav': Permission denied

Do the .wavs have a 'padlock' icon?  I have to chown my music files if, say I copy .wavs and .m4a tracks from my backup dvds to my home dir--they are always owned by root until I do this.  Only then can I convert them or whatever


> 
so in the end, I guess I really didn't solve the permission problem totally, nor did I totally understand the info at the bottom of [this page]("http://www.psychocats.net/ubuntu/mountlinux")...I'm still unclear on "mount points" and fstab and what not...

i was referring only to the chmod and chown part, since this is an external drive that's automounting based on vol label and the fstab doesn't apply 

> (and if you knew how to get Grip to export files to the external hard drive instead of the internal hard drive, I'd be doubly grateful!)

You need to edit the path to the output directory (rip and config tabs, iirc)

---

