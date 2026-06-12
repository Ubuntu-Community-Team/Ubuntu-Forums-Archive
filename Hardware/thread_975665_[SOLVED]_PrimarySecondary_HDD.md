---
title: "[SOLVED] Primary/Secondary HDD"
date: 2008-11-08
forum: Hardware
---

### Post by Zohso on 2008-11-08
I have 2 HDD: Primary is 80gb, and Secondary is 250gb. I have Ubuntu installed on the primary. I would like to have Music, Videos, Pictures, Documents, etc. folders for my account (along with all the other user accounts) located on the Secondary.

How do I do this?

---

### Post by caljohnsmith on 2008-11-08
So are you asking how to move your /home directory to the other drive? If so, that's relatively simple. First open a terminal (applications > accessories> terminal), and post the output of:
```
sudo fdisk -lu
```
And we can go from there if you want.

---

### Post by Zohso on 2008-11-08
Okay, here is what you requested...
> Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000b40a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   149838254    74919096   83  Linux
/dev/sda2       149838255   156296384     3229065    5  Extended
/dev/sda5       149838318   156296384     3229033+  82  Linux swap / Solaris

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x3b5c3b5b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   488392064   244196001   83  Linux


---

### Post by caljohnsmith on 2008-11-08
OK, how about doing this while you are in your sda1 Ubuntu install:
```
sudo mount /dev/sdb1 /mnt
sudo cp -ax /home/* /mnt/.
sudo mv /home /home.backup
sudo mkdir /home
sudo cp /etc/fstab /etc/fstab.11-08-08
sudo blkid | grep sdb1
gksudo gedit /etc/fstab
```
And add the following line in your fstab:
```
# /dev/sdb1
UUID=[COLOR="Blue"]d0b10c15-66ed-4d1c-b7f6-c1fc131636f7[/COLOR] /home  ext3 relatime,errors=remount-ro 0 0
```
And replace the UUID above with whatever the blkid command says your sdb1 UUID is. Reboot, and check to see that your /home directory is mounted OK after you get into Ubuntu. Once you are sure everything is OK, you can delete the /home.backup folder if you want. Let me know how it goes.

---

### Post by Zohso on 2008-11-08
Okay, we have a problem.  I THOUGHT I followed your directions completely, but I have apparently missed a step or something else terribly wrong.  

Now, when I log in I get all kinds of errors telling me, "/home/zohso can be found but does not exist."  I go through a series of window-warnings explaining basicly the same thing. and I now cannot login or interact with it at all.

Is there a way to restore what I have done.  maybe go back to the way it was originally, when I first installed Ubuntu?  

I think i'm going to wait til i'm a little more comfortable with Linux before I go screwing around with things.  lol

HELP!!

Ps. I installed another copy of ubuntu on the 250gb.  That is how I'm talking to you now.

---

### Post by caljohnsmith on 2008-11-08
I guess I should have asked you to post the output of the commands so I could see if anything went wrong. From you other Ubuntu install, how about doing:```

sudo mkdir /mnt/sdb1 /mnt/sda1
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sdb1 /mnt/sdb1
ls -l /mnt/sdb1 /mnt/zohso
ls -l /mnt/sda1 /mnt/sda1/home
```
And post the output of all those commands so I can try and see what happened.

---

### Post by Zohso on 2008-11-08
Okay, starting with your first command to the last, here is the output within my terminal window.
> brandon@raistlin:~$ sudo mkdir /mnt/sdb1 /mnt/sda1
[sudo] password for brandon: 
brandon@raistlin:~$ sudo mount /dev/sda1 /mnt/sda1
brandon@raistlin:~$ sudo mount /dev/sdb1 /mnt/sdb1
brandon@raistlin:~$ ls -l /mnt/sdb1 /mnt/brandon
ls: cannot access /mnt/brandon: No such file or directory
/mnt/sdb1:
total 92
drwxr-xr-x   2 root root  4096 2008-11-08 21:20 bin
drwxr-xr-x   3 root root  4096 2008-11-08 21:22 boot
lrwxrwxrwx   1 root root    11 2008-11-08 20:45 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 19:04 dev
drwxr-xr-x 123 root root 12288 2008-11-08 21:29 etc
drwxr-xr-x   3 root root  4096 2008-11-08 20:51 home
lrwxrwxrwx   1 root root    32 2008-11-08 20:53 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-11-08 21:20 lib
drwx------   2 root root 16384 2008-11-08 20:45 lost+found
drwxr-xr-x   4 root root  4096 2008-11-08 21:04 media
drwxr-xr-x   4 root root  4096 2008-11-08 21:29 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 opt
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 proc
drwxr-xr-x  10 root root  4096 2008-11-08 21:19 root
drwxr-xr-x   2 root root  4096 2008-11-08 21:20 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
drwxr-xr-x   2 root root  4096 2008-10-14 09:02 sys
drwxrwxrwt  14 root root  4096 2008-11-08 21:25 tmp
drwxr-xr-x  13 root root  4096 2008-11-08 21:01 usr
drwxr-xr-x  15 root root  4096 2008-10-29 19:12 var
lrwxrwxrwx   1 root root    29 2008-11-08 20:53 vmlinuz -> boot/vmlinuz-2.6.27-7-generic
brandon@raistlin:~$ ls -l /mnt/sda1 /mnt/sda1/home
/mnt/sda1:
total 96
drwxr-xr-x   2 root root  4096 2008-10-30 16:27 bin
drwxr-xr-x   3 root root  4096 2008-11-05 16:37 boot
lrwxrwxrwx   1 root root    11 2008-10-30 16:00 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 19:04 dev
drwxr-xr-x 140 root root 12288 2008-11-08 20:22 etc
drwxr-xr-x   2 root root  4096 2008-11-08 20:06 home
drwxr-xr-x   4 root root  4096 2008-10-30 16:46 home.backup
lrwxrwxrwx   1 root root    32 2008-10-30 16:13 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-11-05 18:39 lib
drwx------   2 root root 16384 2008-10-30 16:00 lost+found
drwxr-xr-x   5 root root  4096 2008-11-08 20:22 media
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 mnt
drwxr-xr-x   3 root root  4096 2008-10-30 16:52 opt
drwxr-xr-x   2 root root  4096 2008-10-20 08:27 proc
drwxr-xr-x  18 root root  4096 2008-11-08 20:00 root
drwxr-xr-x   2 root root  4096 2008-11-05 18:39 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 18:53 srv
drwxr-xr-x   2 root root  4096 2008-10-14 09:02 sys
drwxrwxrwt   9 root root  4096 2008-11-08 20:32 tmp
drwxr-xr-x  13 root root  4096 2008-10-30 16:18 usr
drwxr-xr-x  15 root root  4096 2008-10-29 19:12 var
lrwxrwxrwx   1 root root    29 2008-10-30 16:13 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

/mnt/sda1/home:
total 0
brandon@raistlin:~$ 


---

### Post by Zohso on 2008-11-08
I think the problem began with the secondary drive not auto-mounting upon boot.  i should have asked you about that first.

Well, at any rate, how do I restore what I've done.  I really don't want to put my home on the secondary now.  atleast not yet.  any suggestions?

---

### Post by caljohnsmith on 2008-11-08
OK, to restore your original home folder, first do:
```
sudo mount /dev/sda1 /mnt/sda1
nautilus &
```
Then use Nautilus to navigate to /mnt/sda1/home.backup. Make sure your user directory is there with all your files, otherwise do not proceed. If your files are all there, do:
```
sudo rmdir /mnt/sda1/home
```
That above command should not return an error, so proceed only if it doesn't return an error:
```
sudo mv /mnt/sda1/home.backup /mnt/sda1/home
```
And then you should be done, assuming you removed the line in your fstab for mounting sdb1. Let me know how it goes.

---

### Post by Zohso on 2008-11-09
Okay, success!  Whew, that felt like I was driving down a winding mountain and the breaks have given way - only right before I go off the cliff they start working again.  lol   Okay, maybe a little dramatic for this situation, but I'm happy none the less.

Thank you for getting me back to square one.

Where did I go wrong?  Was it the auto-mounting of sdb1?

---

### Post by caljohnsmith on 2008-11-09
What was originally on sdb1? Was that partition empty? Because from your post #7, it looks like you have a complete linux install in sdb1. If you didn't install linux to sdb1, then when you tried to copy over the home partition to sdb1, maybe you accidentally copied the entire file system instead?

---

### Post by Zohso on 2008-11-09
I'm assuming it was empty.  i used gEdit and formatted it to ext3.  that, and when i mounted the drive, opened it up, the only thing in nautilus was a "lost+found" folder with an "x" on the icon.  I couldn't create folders or anything.  that, and I'd have to manually mount the drive everytime i'd startup.

---

### Post by caljohnsmith on 2008-11-09
OK, so if sdb1 was supposed to be empty, and it now has your entire sda1 file system, that must be what went wrong. :) How about doing:
```

sudo umount /mnt
sudo mount /dev/sdb1 /mnt
ls -l /mnt
```
Don't worry if the first command gives you an error about not being mounted, it is only a precaution. If that listing shows your sdb1 partition directories as you gave in post #7, then you can delete everything in sdb1 with:
```
sudo rm -fr /mnt/*
```
Be extremely careful with the above command, as that will erase everything in the /mnt folder, which will be your sdb1 partition if the previous commands showed it correctly. After that, you could try and copy over your /home folder again with:
```
sudo cp -ax /home/* /mnt/.
ls -l /mnt
```
And post the output of the above commands. Let me know how it goes. :)

---

### Post by Zohso on 2008-11-09
let me ask you this.  one of the major reasons for putting my personal stuff on a second hdd is because of the old windows mentality:  i'm probably going to have to reformat my HDD every so often (due to whatever) so I should protect that data and put it on another location.

will i be able to link my old "personal" data to a fresh install if need be?

---

### Post by caljohnsmith on 2008-11-09
> **Zohso said:**
> let me ask you this.  one of the major reasons for putting my personal stuff on a second hdd is because of the old windows mentality:  i'm probably going to have to reformat my HDD every so often (due to whatever) so I should protect that data and put it on another location.

will i be able to link my old "personal" data to a fresh install if need be?
There could be some issues with simply linking your old /home directory to a new install, because all your hidden .files and .directories will be configured for the old install; most likely you would be just fine though. Maybe a better solution for you would be to just copy all your personal data over to sdb1 (Music, Videos, Pictures, Documents, etc) and not your entire home directory, and then you could mount all those sdb1 files in a folder called "My Documents" in your home folder for example. That way all the hidden files/directories in your home directory will stay on the main sda1 partition. 

Does that sound better? If so, after you've deleted the file system from sdb1, and while sdb1 is still mounted on /mnt, you could do:
```
sudo chown <user>:<user> /mnt
nautilus &
```
And replace <user> with your username. Then use Nautilus to copy/paste your Music, Videos, etc to the /mnt directory, which is sdb1. See if you can get that far and we can work from there.

---

### Post by j.smith on 2008-11-09
Keep ON , Thanks (._.)

---

### Post by Zohso on 2008-11-10
> **caljohnsmith said:**
> There could be some issues with simply linking your old /home directory to a new install, because all your hidden .files and .directories will be configured for the old install; most likely you would be just fine though. Maybe a better solution for you would be to just copy all your personal data over to sdb1 (Music, Videos, Pictures, Documents, etc) and not your entire home directory, and then you could mount all those sdb1 files in a folder called "My Documents" in your home folder for example. That way all the hidden files/directories in your home directory will stay on the main sda1 partition. 

Does that sound better? If so, after you've deleted the file system from sdb1, and while sdb1 is still mounted on /mnt, you could do:
```
sudo chown <user>:<user> /mnt
nautilus &
```
And replace <user> with your username. Then use Nautilus to copy/paste your Music, Videos, etc to the /mnt directory, which is sdb1. See if you can get that far and we can work from there.

That sounds a lot better.  The only thing I'm experiencing is I can't use my second drive.  I can see it, I can mount it, but I can't write to it.  It's telling me I don't have priviledges to do that.

I've looked and tried a lot of these forums.  People are doing similarly to what you've described, but I can't get over this hump.  dunno:confused:

---

### Post by caljohnsmith on 2008-11-10
If you mount the sdb1 to /mnt and do that chown command I gave, it should work fine (I've tried it myself). How about posting the output of:
```

sudo mount /dev/sdb1 /mnt
sudo chown `whoami`:`whoami` /mnt
ls -ld /mnt
touch /mnt/testfile
ls -l /mnt
```

---

### Post by Zohso on 2008-11-10
Okay, I think i've got it.  I copied all my "documents" in the new /mnt folder.  Here is the output.
> mount: according to mtab, /dev/sdb1 is already mounted on /mnt
[1]+  Done                    nautilus
brandon@raistlin:~$ sudo chown `whoami`:`whoami` /mnt
brandon@raistlin:~$ ls -ld /mnt
drwxr-xr-x 9 brandon brandon 4096 2008-11-10 18:30 /mnt
brandon@raistlin:~$ touch /mnt/testfile
brandon@raistlin:~$ ls -l /mnt
total 24
drwxr-xr-x 11 brandon brandon 4096 2008-11-10 18:29 Documents
drwxr-xr-x  4 brandon brandon 4096 2008-11-10 18:29 Music
drwxr-xr-x  3 brandon brandon 4096 2008-11-10 18:30 Pictures
drwxr-xr-x  2 brandon brandon 4096 2008-11-10 18:30 Public
drwxr-xr-x  2 brandon brandon 4096 2008-11-10 18:30 Templates
-rw-r--r--  1 brandon brandon    0 2008-11-10 18:38 testfile
drwxr-xr-x  2 brandon brandon 4096 2008-11-10 18:30 Videos
brandon@raistlin:~$ 

Now, how do I get the "right-click" directories to point to these newly created folders?  Example:  I right click on an image in my web-browser and select "Save Image As", a dialogue box comes up asking me where to save it.  When I select the Pictures folder, I want that picture to go to the sdb1.  Currently, it's still going to the old sda1.

Ps. Sorry for being a pain man.  I'm new to setting up Linux.  I really appreciate your patience.

---

### Post by caljohnsmith on 2008-11-10
OK, first you'll need to have sdb1 automount on start up, so you'll have to add it to /etc/fstab. I don't think that will be a problem this time since you don't have your whole file system in sdb1 any more and aren't trying to mount that whole file system to your /home directory. :) So how about doing:
```

sudo blkid | grep sdb1
sudo mkdir /media/sdb1
gksudo gedit /etc/fstab &
```
And then add to your fstab:
```
# mount /dev/sdb1 on /media/sdb1:
UUID=d0b10c15-66ed-4d1c-b7f6-c1fc131636f7 /media/sdb1  ext3 relatime,errors=remount-ro 0 0
```
And again, change the above UUID to match the UUID from the blkid command above. Also check from the blkid command what file system sdb1 is, and change the ext3 above to whatever it should be if necessary. Save fstab and do:
```
sudo mount -a
mount | grep sdb1

```
And that second command should show sdb1 mounted on /media/sdb1. Next, if you are sure you have all your files safe on sdb1, then go ahead and delete the original folders in your /home directory: Documents, Music, Pictures, Public, Templates, and Videos. Once those folders are deleted, you can make symbolic links to the new folders on sdb1 (sdb1 needs to be mounted):
```
ln -s /media/sdb1/Documents ~/Documents
ln -s /media/sdb1/Music ~/Music
ln -s /media/sdb1/Pictures ~/Pictures
ln -s /media/sdb1/Public ~/Public
ln -s /media/sdb1/Videos ~/Videos
```
And then you should be done. Any time you try and access your Music folder through one of the "Save as" dialog boxes for example, you will actually be accessing it from sdb1, even though it will look like it is still in your home directory. 

Give that a shot and let me know how it goes. :)

---

### Post by Zohso on 2008-11-10
Okay, here is what I got from your ```
sudo mount -a
and mount | grep sdb1
```does this look okay to you?
> brandon@raistlin:~$ sudo mount -a
[mntent]: line 10 in /etc/fstab is bad
[mntent]: line 12 in /etc/fstab is bad
[2]+  Done                    gksudo gedit /etc/fstab
brandon@raistlin:~$ mount | grep sdb1
/dev/sdb1 on /mnt type ext3 (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw,relatime,errors=remount-ro)

Here is what's in my fstab:> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc          proc         defaults                    0  0  
# /dev/sda1
UUID=22dd5fdb-8228-4c0f-bbc8-2c76a696cf3b  /              ext3         relatime,errors=remount-ro  0  1  
# /dev/sda5
UUID=df7cb634-f3d3-40d9-9592-78e280670a66  none           swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0  udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/sdb1                                  /media/My Data  ext3         defaults                    0  0  
# /dev/sdb1
UUID=63 488392064 244196001 83 Linux /home  ext3 relatime,errors=remount-ro 0 0
/dev/sdb1                                  /mnt           ext3         defaults                    0  0  
# mount /dev/sdb1 on /media/sdb1:
UUID=3897082d-95cc-46f2-81fd-4a35059662cd /media/sdb1  ext3 relatime,errors=remount-ro 0 0

---

### Post by caljohnsmith on 2008-11-10
OK, hang on, I see you posted it...

---

### Post by Zohso on 2008-11-10
> **caljohnsmith said:**
> Line 10 and 12 in your fstab have errors, according to that output. If you're not sure why, then how about posting your entire fstab so I can try and help sort it out.

that's my entire fstab.  i just selected everything and copy/pasted it here.  does it appear incomplete?

---

### Post by caljohnsmith on 2008-11-10
> **Zohso said:**
> ```
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
# /dev/sda1
UUID=22dd5fdb-8228-4c0f-bbc8-2c76a696cf3b / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=df7cb634-f3d3-40d9-9592-78e280670a66 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
[COLOR="Red"]/dev/sdb1 /media/My Data ext3 defaults 0 0
# /dev/sdb1
UUID=63 488392064 244196001 83 Linux /home ext3 relatime,errors=remount-ro 0 0
/dev/sdb1 /mnt ext3 defaults 0 0[/COLOR]
# mount /dev/sdb1 on /media/sdb1:
UUID=3897082d-95cc-46f2-81fd-4a35059662cd /media/sdb1 ext3 relatime,errors=remount-ro 0 0 
```
OK, please delete the lines I have highlighted above, and after saving your fstab do:
```
sudo umount /dev/sdb1
sudo mount -a
mount | grep sdb1
```
And the last command should show sdb1 mounted on /media/sdb1; if that's true, you can proceed with the other directions I gave in post #20.

---

### Post by Zohso on 2008-11-10
Okay, here is the output of your last "code"
> brandon@raistlin:~$ sudo umount /dev/sdb1
[sudo] password for brandon: 
brandon@raistlin:~$ sudo mount -a
brandon@raistlin:~$ mount | grep sdb1
/dev/sdb1 on /mnt type ext3 (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw,relatime,errors=remount-ro)

does the > (rw,relatime,errors=remount-ro)from above mean anything.

---

### Post by caljohnsmith on 2008-11-10
The "relatime" and stuff is just mounting options, so that's OK. You could go ahead and unmount sdb1 from /mnt since you have it mounted on /media/sdb1 now:
```
sudo umount /mnt
```
It looks like your all set to follow the rest of the commands from post #20. Let me know how it goes.

---

### Post by Zohso on 2008-11-10
Wow, I didn't realize how touchy it was.  I was doing the whole symbolic link thing and it wasn't working.  I then read on post20 you telling me that if i was certain everything was on sdb1 to go ahead and delete my other folders.  i couldn't get it to work.

I then decided to archive my info (as well as having it all on sdb1), and then reran the symbolic link commands - and all seams to be well.

thanks man, this is what i wanted to do.  this is just how i had it when i was running windows.

Thank you so much.  This has been a great learning experience for me.  I really like the Ubuntu community.  Everyone is extremely helpful.  

Thanks again, and take care.:)

---

### Post by caljohnsmith on 2008-11-10
That's great news, I'm glad you have it working finally. Cheers and have fun with Ubuntu. :)

---

### Post by deltagostar on 2010-04-10
[LEFT]Hello
I have a problem
Can someone solve for me s
my server have 2 HDD 2*500GiG  but install vmware only show 1 HDD 
how detected Secondary HDD
And information stored not lose sight of . can someone IF Do give to  you root password 

see pic

[IMG]http://img98.com/show.php/12378_hdd.jpg.html[/IMG]
[IMG]http://img98.com/show.php/12384_sys.jpg.html[/IMG]

root@95-168-183-208:~# sudo fdisk -lu

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000af3c0

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   937505204   468752571   83  Linux
/dev/sda2       937505205   976768064    19631430   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x0004ee9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   976768064   488384001   83  Linux
root@95-168-183-208:~# df -H
Filesystem             Size   Used  Avail Use% Mounted on
[COLOR=Blue]/dev/sda1              477G    29G   425G   7% /    [COLOR=YellowGreen] NOT OK [/COLOR][/COLOR]
udev                   4.2G   205k   4.2G   1% /dev
none                   4.2G      0   4.2G   0% /dev/shm
none                   4.2G    62k   4.2G   1% /var/run
none                   4.2G      0   4.2G   0% /var/lock
none                   4.2G      0   4.2G   0% /lib/init/rw
/dev/sdb1              493G   208M   468G   1% /mnt
root@95-168-183-208:~#

AND====================================================

root@95-168-183-208:~# fdisk /dev/sdb1
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0x7c070fa6.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 60800.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

Command (m for help): p

[COLOR=YellowGreen]Disk /dev/sdb1: 500.1 GB[/COLOR], 500105217024 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7c070fa6

    [COLOR=YellowGreen] Device Boot      Start         End      Blocks   Id  System[/COLOR]

Command (m for help):

===========================================
root@95-168-183-208:~# fdisk /dev/sdb

The number of cylinders for this disk is set to 60801.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004ee9d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001   83  Linux


[/LEFT]

---

