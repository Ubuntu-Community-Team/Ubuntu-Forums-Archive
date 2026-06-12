---
title: "[SOLVED] /home on separate partition isn't being /home"
date: 2008-11-13
forum: General Help
---

### Post by Mark_in_Hollywood on 2008-11-13
Some weeks ago, I set /home on a separate partition per Psychocats page:

Create a separate home partition in Ubuntu
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I thought that at the end of that tutorial, the /home that was in with root and all the other OS directories would be deleted and that all of /home would be on another partition.

That's what my sudo fdisk -l shows. 

sda1 is the /
sda3 is /home

but inexplicably /home is still in / partition, and now I have 2 /home partitions. One in root (so to speak) and one in it's own partiton. Yikes this is way way beyond my computer skills. Because the original install had only 3 partitons, root, home and swap, when the new partition was created for home it is quite large. BUT, the /home in the sda1 is still in use by the OS. I deleted it and lost my config files, etc. It was easy enough to restore with putting what had been deleted back where it came from.

But how can I fix this? I made a separate /home and all the stuff from that how-to went OK. So why is the OS "looking" at sda1 instead of sda3?

---

### Post by taurus on 2008-11-13
Can you post the outputs of these commands again?  

```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  Here we go again...

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> Can you post the outputs of these commands again?  

```
sudo fdisk -l
cat /etc/fstab
df -h
```

p.s.  Here we go again...

I've been ill and quit late last night. I'm sorry if you were expecting this sooner:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000080

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9711    78003576   83  Linux
/dev/sda2           38537       38913     3028252+   5  Extended
/dev/sda3            9712       38536   231536812+  83  Linux
/dev/sda5           38537       38913     3028221   82  Linux swap / Solaris

mark@Lexington-19:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=62e29314-59b3-4ead-95d0-92763420a111 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=755a36f6-c291-4ba2-b502-9304af3be671 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0

mark@Lexington-19:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
varrun                505M  136K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  452K  505M   1% /dev/shm
rootfs                 74G   74G     0 100% /
tmpfs                 505M     0  505M   0% /lib/init/rw
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             220G   30G  179G  15% /home
overflow              1.0M   32K  992K   4% /tmp
/dev/sdb1             246M   42M  205M  17% /media/UDISK 28X_

Also, this morn, when I powered up, I got a disk full error. Then I tried LiveCD and booted into a hard drive normally. I think.

---

### Post by taurus on 2008-11-14
Boot your machine with the LiveCD and from a terminal, mount the partition where / is, /dev/sda1.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
Now, post the outputs of these commands.

```
df -h
ls -la /media/ubuntu
ls -la /media/ubuntu/home
```
I just want to see if you still have the old /home laying out, eating up disk space.

---

### Post by cdtech on 2008-11-14
Your "fstab" file is incorrect:
```

/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 **UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0**

```
Whats up with the bold inserted after your sda3 partition?

---

### Post by Mark_in_Hollywood on 2008-11-14
> **cdtech said:**
> Your "fstab" file is incorrect:
```

/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 **UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0**

```
Whats up with the bold inserted after your sda3 partition?

When I could not get the 80 gig ext. usb drive to unmount (mtab says so) I repartitioned the 80 gig, still the same device, and ext3.

I'm going for LiveCD boot and will return in a moment with the command cut & paste

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> Boot your machine with the LiveCD and from a terminal, mount the partition where / is, /dev/sda1.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
```
Now, post the outputs of these commands.

```
df -h
ls -la /media/ubuntu
ls -la /media/ubuntu/home
```
I just want to see if you still have the old /home laying out, eating up disk space.

Here 'tis:

ubuntu@ubuntu:~$ sudo mkdir /media/ubuntu
ubuntu@ubuntu:~$ sudo mount -t ext3 /dev/sda1 /media/ubuntu
ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
tmpfs                 506M   16M  490M   4% /lib/modules/2.6.24-16-generic/volatile
varrun                506M  100K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
udev                  506M   60K  506M   1% /dev
devshm                506M   52K  506M   1% /dev/shm
tmpfs                 506M   16K  506M   1% /tmp
gvfs-fuse-daemon      506M   17M  490M   4% /home/ubuntu/.gvfs
/dev/sdb1             246M   42M  205M  17% /media/UDISK 28X
/dev/sda1              74G   74G     0 100% /media/ubuntu
ubuntu@ubuntu:~$ ls -la /media/ubuntu
total 116
drwxrwxrwx  21 root root  4096 2008-11-03 21:52 .
drwxr-xr-x   4 root root   120 2008-11-14 22:10 ..
drwxr-xr-x   2 root root  4096 2008-10-30 16:06 bin
drwxr-xr-x   3 root root  4096 2008-11-10 17:12 boot
lrwxrwxrwx   1 root root    11 2008-05-17 13:48 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-24 18:53 dev
drwxr-xr-x 148 root root 12288 2008-11-14 22:05 etc
drwxr-xr-x   3 root root  4096 2008-05-17 13:55 home
drwxr-xr-x   2 root root  4096 2008-04-22 17:48 initrd
lrwxrwxrwx   1 root root    32 2008-10-24 18:57 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2008-11-13 16:17 lib
drwx------   2 root root 16384 2008-05-17 13:48 lost+found
drwxr-xr-x  11 root root  4096 2008-11-14 22:04 media
drwxr-xr-x   2 root root  4096 2008-04-15 05:53 mnt
drwxr-xr-x   6 root root  4096 2008-10-30 15:54 opt
drwxr-xr-x   2 root root  4096 2008-04-15 05:53 proc
drwxr-xr-x  23 root root  4096 2008-11-13 21:03 root
drwxr-xr-x   2 root root  4096 2008-11-13 16:17 sbin
drwxr-xr-x   2 root root  4096 2008-04-22 17:48 srv
drwxr-xr-x   2 root root  4096 2008-04-19 05:05 sys
drwxrwxrwt   2 root root 12288 2008-11-14 22:04 tmp
drwxr-xr-x  14 root root  4096 2008-10-24 18:32 usr
drwxr-xr-x  15 root root  4096 2008-04-22 18:07 var
lrwxrwxrwx   1 root root    29 2008-10-24 18:57 vmlinuz -> boot/vmlinuz-2.6.27-7-generic
ubuntu@ubuntu:~$ ls -la /media/ubuntu/home
total 20
drwxr-xr-x   3 root root  4096 2008-05-17 13:55 .
drwxrwxrwx  21 root root  4096 2008-11-03 21:52 ..
drwx------ 139 1000 1000 12288 2008-10-27 23:05 mark

---

### Post by unutbu on 2008-11-14
Boot from the live CD.
```

sudo mkdir /media/sda1
sudo mkdir /media/sda3
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda3 /media/sda3
gksu nautilus

```
Navigate to /media/sda1/home/mark. This should be your old home account.
And in another window navigate to /media/sda3/mark. This should be your new home account.

Verify that /media/sda3/mark is the one you want to keep, and that you are willing to get rid of /media/sda1/home/mark.

If that is the case, then go ahead and delete /media/sda1/home/mark.
This should give you some space in your root partition and eliminate the duplication.

---

### Post by taurus on 2008-11-14
Or you can rename the "old" home to something else so that the new home on /dev/sda3 will be mounted to /home.  And if everything is working fine with the new home and you don't need to move any more stuff off the "old" home, you can just remove it, reclaiming the space on /dev/sda1.

```
cd /media/ubuntu
sudo mv home old_home
ls -la
```
Reboot and remove the LiveCD.

---

### Post by unutbu on 2008-11-14
As cdtech pointed out, there appears to be a syntax error in your fstab.

So, while booted from the LiveCD, open /media/sda1/etc/fstab
```

gksu gedit /media/sda1/etc/fstab
```

and make sure this shows up on two separate lines:
```
/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 
UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0
```

Otherwise, you may not have been mounting your new home at all. 

fstab expects each line to have exactly 6 space-separated fields. If it doesn't then fstab will fail to parse the line properly. If you find that the above was all run into one line, then it is likely that you've been using your old home on the /dev/sda1 partition all this time, and the home on /dev/sda3 has not been used since its creation. The bottom line is: be careful before you erase either one.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> Or you can rename the "old" home to something else so that the new home on /dev/sda3 will be mounted to /home.  And if everything is working fine with the new home and you don't need to move any more stuff off the "old" home, you can just remove it, reclaiming the space on /dev/sda1.

```
cd /media/ubuntu
sudo mv home old_home
ls -la
```
Reboot and remove the LiveCD.

ls -la shows:

ubuntu@ubuntu:/media/ubuntu$ ls -la
total 116
drwxrwxrwx  21 root root  4096 2008-11-14 15:01 .
drwxr-xr-x   5 root root   140 2008-11-14 14:21 ..
drwxr-xr-x   2 root root  4096 2008-10-30 09:06 bin
drwxr-xr-x   3 root root  4096 2008-11-10 09:12 boot
lrwxrwxrwx   1 root root    11 2008-05-17 06:48 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-24 11:53 dev
drwxr-xr-x 148 root root 12288 2008-11-14 14:05 etc
drwxr-xr-x   2 root root  4096 2008-04-22 10:48 initrd
lrwxrwxrwx   1 root root    32 2008-10-24 11:57 initrd.img -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root 12288 2008-11-13 08:17 lib
drwx------   2 root root 16384 2008-05-17 06:48 lost+found
drwxr-xr-x  11 root root  4096 2008-11-14 14:04 media
drwxr-xr-x   2 root root  4096 2008-04-14 22:53 mnt
drwxr-xr-x   3 root root  4096 2008-05-17 06:55 old_home
drwxr-xr-x   6 root root  4096 2008-10-30 08:54 opt
drwxr-xr-x   2 root root  4096 2008-04-14 22:53 proc
drwxr-xr-x  23 root root  4096 2008-11-13 13:03 root
drwxr-xr-x   2 root root  4096 2008-11-13 08:17 sbin
drwxr-xr-x   2 root root  4096 2008-04-22 10:48 srv
drwxr-xr-x   2 root root  4096 2008-04-18 22:05 sys
drwxrwxrwt   2 root root 12288 2008-11-14 14:04 tmp
drwxr-xr-x  14 root root  4096 2008-10-24 11:32 usr
drwxr-xr-x  15 root root  4096 2008-04-22 11:07 var
lrwxrwxrwx   1 root root    29 2008-10-24 11:57 vmlinuz -> boot/vmlinuz-2.6.27-7-generic

But you lost me. Sorry. If I still have an old_home, isn't it taking up space, too? I know for certain that my sda3 'home' has all my /home files on it. My question is: how do I get the OS to know to use /sda3 for the 'directory' named: /home and how what directory or directories do I remove to reclaim the space. I'm still not well understanding this.

---

### Post by taurus on 2008-11-14
If you are certain that all your files are in /home (/dev/sda3), you can remove the old_home.  And since you tell the system in /etc/fstab to mount /dev/sda3 to /home, you are using a separate partition for /home now.  Therefore, you don't need the old_home anymore, /old_home.  Just delete it with, assuming you are still in a LiveCD.

```
cd /media/ubuntu
rm -rf old_home
df -h
```
Now, see how much space on /dev/sda1 you have recovered after removing the old_home.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> If you are certain that all your files are in /home (/dev/sda3), you can remove the old_home.  And since you tell the system in /etc/fstab to mount /dev/sda3 to /home, you are using a separate partition for /home now.  Therefore, you don't need the old_home anymore, /old_home.  Just delete it with, assuming you are still in a LiveCD.

```
cd /media/ubuntu
rm -rf old_home
df -h
```
Now, see how much space on /dev/sda1 you have recovered after removing the old_home.

No, I had tried the reboot, before reading the above. First I got a blue scrren with 

GDM has no write authorization
No space left on device

then, on another reboot attempt:

Problem with config server
/usr/lib/libgonf2-4/gconfig-sanity-check2 exited with status 256

clearing that message brought up

/home does not exist. Do you want to log in using / (root) as your /home? Yes/no -- I said yes

Then I got the usual .dmrc user's is being ingnored
dismissing that, the kb locks and I can't Alt-SysRq R E I S U B K
for a warm boot and I'm back here in LiveCD (Hardy - as I did an Syn Pkg Mgr. distribution upgrade and haven't burned a Ibex cd as yet)

I hope this helps.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **unutbu said:**
> As cdtech pointed out, there appears to be a syntax error in your fstab.

So, while booted from the LiveCD, open /media/sda1/etc/fstab
```

gksu gedit /media/sda1/etc/fstab
```

and make sure this shows up on two separate lines:
```
/dev/sda3 /home ext3 nodev,nosuid,relatime 0 2 
UUID=b137b9c0-cdce-43a7-917a-3cd4ee90cf22 /media/marks80 ext3 defaults,user 0 0
```

Otherwise, you may not have been mounting your new home at all. 

fstab expects each line to have exactly 6 space-separated fields. If it doesn't then fstab will fail to parse the line properly. If you find that the above was all run into one line, then it is likely that you've been using your old home on the /dev/sda1 partition all this time, and the home on /dev/sda3 has not been used since its creation. The bottom line is: be careful before you erase either one.

Doing:

gksu gedit /media/sda1/etc/fstab [returns an open gedit with a blank screen - no text]

takes my to the LiveCD session fstab. I tried to find the sda1's fstab in etc, but I can't get gksudo gedit to "go there".

---

### Post by taurus on 2008-11-14
You mounted your Ubuntu's partition to /media/ubuntu, not /media/sda1.  Therefore, it should be

```
gksudo gedit /media/ubuntu/etc/fstab
```
if you want to edit it.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> You mounted your Ubuntu's partition to /media/ubuntu, not /media/sda1.  Therefore, it should be

```
gksudo gedit /media/ubuntu/etc/fstab
```
if you want to edit it.

I'm so sorry, when I enter the above command, gedit opens to a BLANK screen.

---

### Post by taurus on 2008-11-14
Are you still in LiveCD and did you unmount your /dev/sda1?

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```
_But_ if you run Ubuntu from your harddrive, then the command to edit your /etc/fstab is 

```
gksudo gedit /etc/fstab
```

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> Are you still in LiveCD and did you unmount your /dev/sda1?

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
gksudo gedit /media/ubuntu/etc/fstab
```


I'm running LiveCD. The lines were 'run-on' and now each has their own line.

---

### Post by dcstar on 2008-11-14
> **Mark_in_Hollywood said:**
> Some weeks ago, I set /home on a separate partition per Psychocats page:
........
That's what my sudo fdisk -l shows. 

sda1 is the /
sda3 is /home

but inexplicably /home is still in / partition, and now I have 2 /home partitions. One in root (so to speak) and one in it's own partiton. Yikes this is way way beyond my computer skills.
........

Just to give you some sort of explanation of what you are trying to achieve, Linux needs a place called "/home" for each user's files. This can just be a directory under the root directory "/" or a mount point or even a link (soft or hard - these thinks are pointers to other storage resources).

You are making a separate partition and having Linux mount that as /home" using your fstab file (as all the instructions as asking you to do).

The "/home" directory on your root filesystem is the "mountpoint" for the partition you want to use for your home data, and when you successfully set it up it will hide all the files originally under that directory.

If you wanted to keep that home old data, you could simply create a new directory (perhaps called "/home-old") and copy all of the contents from /home (before you mount it!) to it. Then you will have access to both after you have the partition mount working.

Hopefully this explanation will increase your Linux skills a bit.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **dcstar said:**
> Just to give you some sort of explanation of what you are trying to achieve, Linux needs a place called "/home" for each user's files. This can just be a directory under the root directory "/" or a mount point or even a link (soft or hard - these thinks are pointers to other storage resources).

You are making a separate partition and having Linux mount that as /home" using your fstab file (as all the instructions as asking you to do).

The "/home" directory on your root filesystem is the "mountpoint" for the partition you want to use for your home data, and when you successfully set it up it will hide all the files originally under that directory.

If you wanted to keep that home old data, you could simply create a new directory (perhaps called "/home-old") and copy all of the contents from /home (before you mount it!) to it. Then you will have access to both after you have the partition mount working.

Hopefully this explanation will increase your Linux skills a bit.

If you will kindly read my first post, you will have a better answer than if I try to retype the same here.

I tried to make a separate /home via the Psychocat's instructions. For some reason, the /home on sda1 and the /home on sda3 didn't get set up correctly. My /home (on both sda1 and sda3) are both about 30 gig. I want to remove the /home on sda1 and set the OS to know that /home is now in sda3. That is a simple an explanation as I can give you.

---

### Post by taurus on 2008-11-14
If you look at the /etc/fstab from the harddrive, you will see an entry for /dev/sda3 which will be mounted to /home.  That is what you are after, a separate /home partition.

```
cat /media/ubuntu/etc/fstab
```
Meanwhile, there shouldn't be a directory of home in / now.  

```
ls -la /media/ubuntu
```
Just reboot and everything should be peachy now.

---

### Post by Mark_in_Hollywood on 2008-11-14
> **taurus said:**
> Just reboot and everything should be peachy now.

Did the reboot. Same problem as before, except no GDM and disk full messages are gone.

I got the there is no /home do you want to use root? Said yes.

Next I got the .dmrc is being ignored. Dismissed that. 

KB locks, ALT-SysRq unavailable.

Anybody know what I might try next? (short of suicide!)

---

### Post by taurus on 2008-11-14
Just create a new mount point, /home, for your /dev/sda3 then.

Just boot your machine into recovery mode from GRUB menu and run

```
mkdir /home
shutdown -r now
```

---

### Post by Mark_in_Hollywood on 2008-11-14
Reboot worked fine. The Desktop Drapes is flawed, but that must be another post with some other help. I've taken enough of the time of those who have helped me over this.

One last question before I can mark the thread 'solved'.

How can I know I'm using /sda3 and not /sda1 after doing mkdir /home?

---

### Post by cdtech on 2008-11-14
Just a word of advice, the /media directory is for auto mounts that HAL (hardware abstraction layer), using the device label mounts to. The /mnt directory is for created directories manually created by the user to mount partitions, internal drives or whatever is created to mount via /etc/fstab.

A USB drive will or should (if HAL is working properly) mount into the media directory once it's plugged in. When it's mounted the directory will be created for you using the device label.

Just my two cents. More of an organizational bug for me I guess.

---

### Post by cdtech on 2008-11-14
> **Mark_in_Hollywood said:**
> Reboot worked fine. The Desktop Drapes is flawed, but that must be another post with some other help. I've taken enough of the time of those who have helped me over this.

One last question before I can mark the thread 'solved'.

How can I know I'm using /sda3 and not /sda1 after doing mkdir /home?

Just issue the command:
```
df -h
```

---

### Post by Mark_in_Hollywood on 2008-11-14
> **cdtech said:**
> Just a word of advice, the /media directory is for auto mounts that HAL (hardware abstraction layer), using the device label mounts to. The /mnt directory is for created directories manually created by the user to mount partitions, internal drives or whatever is created to mount via /etc/fstab.

A USB drive will or should (if HAL is working properly) mount into the media directory once it's plugged in. When it's mounted the directory will be created for you using the device label.

Just my two cents. More of an organizational bug for me I guess.

Just so I understand as best I can:

mark@Lexington-19:/media$ umount marks80
umount: /media/marks80 is not mounted (according to mtab)

which doesn't matter because it's an automount and not a manually mounted device?

---

### Post by cdtech on 2008-11-14
Yes, if it's a USB drive which it looks like it is. If you plug it in and go to /media you'll see it mounts itself and creates a directory for you under /media.

---

### Post by Mark_in_Hollywood on 2008-11-14
I'm posting this in case others find it useful to see how /home is mounted when /home is it's own partiton.

mark@Lexington-19:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              74G   74G     0 100% /
tmpfs                 505M     0  505M   0% /lib/init/rw
varrun                505M  236K  505M   1% /var/run
varlock               505M     0  505M   0% /var/lock
udev                  505M  2.8M  502M   1% /dev
tmpfs                 505M  440K  505M   1% /dev/shm
lrm                   505M  2.0M  503M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda3             220G   30G  179G  15% /home
overflow              1.0M   32K  992K   4% /tmp
/dev/sdb1             246M   42M  205M  17% /media/UDISK 28X__


Again, thank, Ubuntu Community. You guys save my bacon.

---

### Post by cdtech on 2008-11-14
Good job!

Another satisfied Ubuntu user. :guitar:

---

### Post by dcstar on 2008-11-14
> **Mark_in_Hollywood said:**
> I'm posting this in case others find it useful to see how /home is mounted when /home is it's own partiton.

mark@Lexington-19:~$ df -h
Filesystem            Size  Used Avail **Use%** Mounted on
/dev/sda1              74G   74G     0 **100% /**
......

You have a major problem if your root partition is 100% full, lots of things will not work correctly!

---

