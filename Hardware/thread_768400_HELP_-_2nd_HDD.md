---
title: "HELP - 2nd HDD"
date: 2008-04-26
forum: Hardware
---

### Post by Y^2om&amp;#7sgP on 2008-04-26
I have a PC with two ATA HDD.  Before upgrading to Hardy, I backed data onto the second HDD.  Now when I boot up with Hardy installed on the 1st HDD, I can't see the 2nd HDD.  Results of fdisk -l are:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c0f83

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60045   482311431   83  Linux
/dev/sda2           60046       60801     6072570    5  Extended
/dev/sda5           60046       60801     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12121212

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14334   115137823+  83  Linux
/dev/sdb2           14335       14946     4915890    5  Extended
/dev/sdb5           14335       14946     4915858+  82  Linux swap / Solaris

I've tried seaching on the forums and tried most of the ideas being give, but I can't see the drive or (naturally) get the data back from it.  I have installed gkparted and that will see the drive and let me format it. But of course having data, I don't want to do that yet.

Sorry if this question has been asked a thousand times, but as a noob to Linux I don't know what else to try now.

Can someone help.... PLEASE !!

Cheers

---

### Post by RudolfMDLT on 2008-04-26
Hi,

Please open the terminal, make it full screen and then enter this command:
[B]
 cat /etc/fstab[/B]

And paste the output.

Thanks,

Rudolf

---

### Post by Y^2om&amp;#7sgP on 2008-04-26
phatton@phatton-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=545b6521-0303-44bf-a381-9475018f1d7a /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=16302078-def0-4957-bb94-3adb07388ccc none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
phatton@phatton-desktop:~$ 


Thanks

---

### Post by RudolfMDLT on 2008-04-26
Cool,

fstab is the file that controls what devices are mounted where and their respective properties.

From your first post I can see that this drive is mounted and probably the drive that Ubuntu installed by default:

> Device Boot Start End Blocks Id System
**/dev/sda1** * 1 60045 482311431 83 Linux
/dev/sda2 60046 60801 6072570 5 Extended
**/dev/sda5** 60046 60801 6072538+ 82 Linux swap / Solaris

So I take it that this was a previous installation's drive:

> Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12121212

Device Boot Start End Blocks Id System
/dev/sdb1 1 14334 115137823+ 83 Linux
/dev/sdb2 14335 14946 4915890 5 Extended
/dev/sdb5 14335 14946 4915858+ 82 Linux swap / Solaris

Feel free to format sdb5 as Ubuntu has already allocated Linux Swap space on the sda drive.

I'll give you instructions below to just mount the drives mentioned above so that you can get the data off them. Hopefully after that you will know enough to remount them to places where you actually want them.

So, to business:

In the terminal please execute the following commands:

Creating folders for mounting, using chmod 777 so that we can read/write freely.
> 
sudo mkdir /backupfolder
sudo chmod 777 /backupfolder


make a backup of the old fstab file:

> sudo cp /etc/fstab /etc/fstab~


Now we need to edit the fstab file to tell Ubuntu which drives to mount where. It will be easier using gedit. If you are using KDE, replace 'gedit" below with "kate".

Press [ALT]+[F2] to open the run dialog and paste the following and press enter:
> 
gksu gedit /etc/fstab

Give your root password.

For completeness I will quote your entire fstab file - but please copy and paste the **bold** lines below and append them to your fstab file:

> # /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=545b6521-0303-44bf-a381-9475018f1d7a / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=16302078-def0-4957-bb94-3adb07388ccc none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0

[B]#Extra Stuff Goes Here:
/dev/sdb1 /backupfolder ext3 defaults 0 [/B]2

Now save the file and restart your computer. The drive should now be available under /backupfolder.

JUST IN CASE: If the system does not boot due to this change, restart the machine, and at the GRUB boor menu select recovery mode. Enter your root password and type the following command(remember to write it down):

> mv /etc/fstab~ /etc/fstab
shutdown -r now

The system should then boot normally. Post back if this happens! :)

---

### Post by Y^2om&amp;#7sgP on 2008-04-26
System boots OK.  but the backupfolder is empty.....  Now I know that the 2nd HDD has around 20Gb of data....  

I tried to enter the command

sudo mount /dev/sdb1 /backupfolder

and all that does is show a lost+found folder under the backupfolder.

Have I done something wrong (again) or do I take it I've lost the data (and learn from that and remember to back the darn thing up) ?

Thanks

---

### Post by RudolfMDLT on 2008-04-26
Well, unless you ticked the drive to be formatted during the install there should be no good reason for the data to have disappeared. Usually a crashed drive won't mount or give you errors etc...

please open the terminal and type in **mount** and paste the output. You could have look at it yourself.

here is small copy of mine:

> 
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)


**/dev/sdb2 on /stuff type ext3 (rw)**

sshfs#root@192.168.10.250:/backupdrive1/Rudolf/incremential/DocsSync/ on /backupfolders/Documents type fuse (rw,nosuid,nodev,max_read=65536,user=rudolf)

Look for a line that looks like the bold bit, except in your case it would have the relevant info - sdb1 etc.

Also, in Nautilus(the default file manager), navigate to root and right click on "backupfolder" and click properties. Under the "Volume" header, does it say "/" or "/backupfolder"? if it says "/" then **mount** didn't mount it, if it says "/backupfolder" with the **contents**  = about 5 files then I'm sorry but I believe the data is gone.

Try copy and pasting a large folder into /backupfolder and see whether the free space drive on which "/" is mounted

Goodluck and postback,

Rudolf

---

### Post by Y^2om&amp;#7sgP on 2008-04-26
output of mount

/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-16-generic/volatile type tmpfs (rw)
securityfs on /sys/kernel/security type securityfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/phatton/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=phatton)
/dev/sdb1 on /backupfolder type ext2 (rw)


In properties for backupfolder is unknown, and location /

I tried copying  a folder and the freesapce/usedspace changed

?????

Thanks

---

### Post by RudolfMDLT on 2008-04-27
Weird!

Mount says that the drive is mounted but nautilus picks up that nothing is in the folder.

Something is definitely wrong with the drive, though whether it has crashed I don't know.

You can try one of two things - take the drive and plug it in another PC and see whether that pc's OS can see the drive and actually see your files. If on the other machine you also see blank drive, then you can conclude it is a lost case. OR you can try testdisk. you can install it straight form the command line.

I once had a power failure at the start of a partition resizing procedure. Both partitions involved disapeared. testdisk was able to rescue the partition table and I was able to use the drive again.

You are going to have to do some googleing on testdisk as I've only used it once!

Good luck,

Rudolf

---

### Post by Y^2om&amp;#7sgP on 2008-04-27
I'll give those two options a try.

Guess this is nature's way of telling me to backup !!:lolflag:

Thanks for all your help.

---

### Post by RudolfMDLT on 2008-04-27
> rsync -vrup --delete /backupdrive1/ /backupdrive2/


That's a  little script that I use to backup 1 drive onto another. It can just as well be any two folders on your pc. Backing up is a pain in the neck so I put the script in cron. Now once an hour Drive1 updates Drive2. Works like a charm.

If you're interested in something similar post back and we'll work something out.

Cheers,

Rudolf

---

### Post by Y^2om&amp;#7sgP on 2008-04-27
that's be really great.  I work in I.T. (all M$ though) so of course never practise what I preach and use backups.....  a script to do it automatically would be a real help

Thanks

---

### Post by RudolfMDLT on 2008-04-27
Well, basically all you have to do is decide what you want to backup and how you want to do it.

For example, I wanted to create a really pedantic system that backs up my "Documents" folder every 15 minutes. That way, no matter what happens, I'll always have a 15 minute up to date backup copy of my data available.

The best thing for backing stuff up over a network is rsync. It's a really awesome tool and you'll have to do some reading  about what it can specifically do for you. The reason I use it is that it supports compressing data before network transmission and updating only files that have changed. So in my 2 gig documents folder, it only ever backs up the 200kb or so of data when needed. 

At my house I have a PC that I use as a file server. That PC and my PC both run Ubuntu. So what I did was use ssh and sshfs, to map a network drive to my computer. I then use rsync to sync the "Documents" folder with the back up folder. Rsync supports syncing over ssh by itself, but I preferred being able to actually browse to the specified folders when ever I wanted.

The final trick is to use cron. i don't know why people don't advocate cron more because it really is a useful tool. You now tell cron to run your script every day of the week or every 15th minute of every hour or etc...

And that's it. I recommend you create a folder where you save all your scripts, but for the rest, once cron knows what to do and when, you can really just forget about it.

The script:
> 
#!/bin/bash
fusermount -u /backupfolders/Documents/
sshfs root@192.168.10.250:/backupdrive1/Rudolf/incremential/DocsSync/ /backupfolders/Documents/ -p 2233
rsync -ruve ssh --delete /home/rudolf/Documents/ /backupfolders/Documents/


The above script basically unmounts anything that might be mounted in /backupfolder/Documents/ and then remounts it using sshfs. I use RSA keys for passwordless logins via ssh. It then calls rsync to recursively update the target folder and also to delete any files in the backup folder that aren't in the source folder any more.

When working with cron, I reccomend using Kcron to edit the cron config file, but if you don't want to download any KDE app's, gcrontab works as well - it's just damn ugly.

Some stuff that I needed to know:
[Scipting]("http://tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html")
[Cron]("http://www.unixgeeks.org/security/newbie/unix/cron-1.html")
[Something]("http://www.mikerubel.org/computers/rsync_snapshots/") I just found now that I wish I knew before! :)

Best of luck! Sorry about the hard drive!

Cheers,

Rudolf

---

### Post by Y^2om&amp;#7sgP on 2008-04-27
Hey, the HDD, such is life I guess.

Thanks again for the help and even more for the script and suggestions, really appreciated.

---

