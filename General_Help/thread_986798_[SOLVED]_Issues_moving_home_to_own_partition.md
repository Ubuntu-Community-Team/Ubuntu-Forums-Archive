---
title: "[SOLVED] Issues moving /home to own partition"
date: 2008-11-18
forum: General Help
---

### Post by dazzlindonna on 2008-11-18
Ok, I followed the instructions from psychocats, and failed miserably.  After much runaround, I have my system back to the way it was, except that now I have a new separate partition just waiting to be used.

Basically the initial problem was that when I did this:
```
sudo find . -depth -print0 | cpio --null --sparse -pvd /new/
```

it spit out a bunch of lines that said it failed because I didn't have permission.  still...it looked like it was just a small portion of files, so I carried on with the rest of the instructions.  

In any case, before I ever attempt to do this again, I thought I'd show you my partitions, making sure they look ok and they aren't the issue.

```
sudo fdisk -l

Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11629    93409911    7  HPFS/NTFS
/dev/sda2           47495       48641     9213277+   7  HPFS/NTFS
/dev/sda3           11630       47494   288085612+   5  Extended
/dev/sda5           11630       37687   209310853+  83  Linux
/dev/sda6           47229       47494     2136613+  82  Linux swap / Solaris
/dev/sda7           37688       47228    76638051   83  Linux

Partition table entries are not in disk order

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8d399bc0

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       60800   488375968+   c  W95 FAT32 (LBA)  
```

/dev/sda5 was the original partition (where /home lives) and /dev/sda7 is the new one that I attempted to move /home to.

Do those look ok?  Does sda7 look ready to take on the moved /home folder?

Sorry if those are stupid questions, but I don't know enough to ask intelligent ones I guess.  :)

---

### Post by dcstar on 2008-11-19
> **dazzlindonna said:**
> Ok, I followed the instructions from psychocats, and failed miserably.  After much runaround, I have my system back to the way it was, except that now I have a new separate partition just waiting to be used.
.......
/dev/sda5 was the original partition (where /home lives) and /dev/sda7 is the new one that I attempted to move /home to.

Do those look ok?  Does sda7 look ready to take on the moved /home folder?

Sorry if those are stupid questions, but I don't know enough to ask intelligent ones I guess.  :)

Boot off a live CD, mount your old / partition and your new /home partition and simply copy the contents of your old /home into the new partition.

Once that is done all you need is the correct entry in your /etc/fstab and you should be up and running.

---

### Post by dazzlindonna on 2008-11-19
Well i think it was the copy part of it where it all started going wrong.  I assume that find code I posted above was the bit that copies over the data.  Would a straight copy work better?

---

### Post by caljohnsmith on 2008-11-19
I think that might be a mistake in the tuturial, because after you do the step:
```
sudo mount -t ext3 /dev/sda3 /new
```
Then you can't write to /new unless you are the root user, since /new is owned by root. When you prefaced your "find" command with sudo:
```
[COLOR="Blue"]sudo[/COLOR] find . -depth -print0 | cpio --null --sparse -pvd /new/
```
Then "find" is run as root, but the second "cpio" command is run under your user name, not as root. So I think the tutorial means to say:
```
find . -depth -print0 | [COLOR="Blue"]sudo[/COLOR] cpio --null --sparse -pvd /new/
```
In other words, it's not necessary to run the "find" command as root since "find" should have access to all your files and directories in your home directory, but the cpio command should be run as root since it needs to copy everything to the new /home folder, which is owned by root.

Just as a side note, I think a simpler way than the tutorial's method is:
```
sudo mkdir /old /new
sudo mount /dev/sda1 /old
sudo mount /dev/sda3 /new
sudo cp -ax /old/home/* /new
```
The above steps accomplish the same thing so that all permissions/users/groups etc are all preserved on all the files/directories that you copy over, and I've used it myself with success. Either method should work though. Let me know how it goes. :)

---

### Post by dazzlindonna on 2008-11-19
caljohnsmith - you rock!  that worked perfectly.  i now have /home on its own partition.  woot!

---

### Post by caljohnsmith on 2008-11-20
Really glad to hear you successfully moved your /home. Cheers and have fun with Ubuntu. :)

---

### Post by hawkhock on 2008-12-28
This is a solved thread -- I should not be posting to it.

---

### Post by caljohnsmith on 2008-12-28
> **hawkhock said:**
> [/COLOR]
--Resize /ext3 to 41G  -- resize from right handle? at the end of the partition?
--Unallocated is now 30G -- format as /ext3
--Leave /extended and swap alone

2) Close out GPartEd and Live CD. Reboot from hard drive.

Yes, I would resize the "right-handle" so that you shrink your current Ubuntu partition from the end. But when you resize your sda1 Ubuntu partition, its UUID will change, and then you won't be able to immediately boot back into your Ubuntu install. I would recommend before doing the resizing, open a terminal and do:
```
sudo blkid | grep sda1
```
That will show the current UUID of sda1; then go ahead and resize sda1, and after you are done, do:
```
sudo tune2fs -U "[COLOR="Blue"]<original UUID>[/COLOR]" /dev/sda1
```
So copy/paste the original UUID of sda1 into the command above. Then you should be able to reboot into Ubuntu OK. 
> **hawkhock said:**
> 
3) Open terminal. This is where I get confused.  
Do I just type the commands you recommend (red text above) as is? 

OR do I need to log in as root? Am noobie but thought that using "sudo" = "root user".

The commands will depend on the partition number of your new home partition, which most likely will be sda2. Also, if you boot into Ubuntu, you won't have to mount your original Ubuntu sda1 partition. Instead you could do:
```
sudo mount /dev/[COLOR="Blue"]sda2[/COLOR] /mnt
sudo cp -ax /home/* /mnt
sudo mv /home /home_backup
sudo mkdir /home

```
So change "sda2" above if your home partition ends up with a different number; you can check your partitions by doing:
```
sudo fdisk -l
```
> **hawkhock said:**
> 
I found instructions on how to log on as root in another tutorial. Are they correct?

regarding to "login as root" just do like this example

hannah@pysen:~$ sudo passwd root
Enter new UNIX password: [passwd of your choice]
Retype new UNIX password:
passwd: password updated successfully

then su as root

hannah@pysen:~$ su -
Password:
root@pysen:~#
done!

4)  If root log in required, then after "root@name:~#" is where I would put your command lines?

It's not recommended to enable the root user account as you would with the above commands. Instead, whenever you need to run commands as root, just stick the "sudo" in front of it and in general you should be fine. The "sudo" command allows a common user to run commands as root. Or if you want to effectively login as root, you could use "sudo -i". 
> **hawkhock said:**
> 
5)  After executing your commands, do I then go back to the psychocats tutorial to "specify to use the new home partition as /home:" where the /etc/stab file is opened and a line is added to the end of the file?

OR does your command block take care of everything at the same time?

Any help would be appreciated.
Georgi in UT
Yes, you would need to add the new home partition to your /etc/fstab as the tutorial shows; the commands from my previous post are only to copy the existing /home directory over to the new home partition. Good luck and let me know how it goes. :)

---

### Post by hawkhock on 2008-12-28
> **caljohnsmith said:**
> Yes, I would resize the "right-handle" so that you shrink your current Ubuntu partition from the end. But when you resize your sda1 Ubuntu partition, its UUID will change, and then you won't be able to immediately boot back into your Ubuntu install. I would recommend before doing the resizing, open a terminal and do:
```
sudo blkid | grep sda1
```
That will show the current UUID of sda1; then go ahead and resize sda1, and after you are done, do:
```
sudo tune2fs -U "[COLOR="Blue"]<original UUID>[/COLOR]" /dev/sda1
```
So copy/paste the original UUID of sda1 into the command above. Then you should be able to reboot into Ubuntu OK. 

The commands will depend on the partition number of your new home partition, which most likely will be sda2. Also, if you boot into Ubuntu, you won't have to mount your original Ubuntu sda1 partition. Instead you could do:
```
sudo mount /dev/[COLOR="Blue"]sda2[/COLOR] /mnt
sudo cp -ax /home/* /mnt
sudo mv /home /home_backup
sudo mkdir /home

```
So change "sda2" above if your home partition ends up with a different number; you can check your partitions by doing:
```
sudo fdisk -l
```

It's not recommended to enable the root user account as you would with the above commands. Instead, whenever you need to run commands as root, just stick the "sudo" in front of it and in general you should be fine. The "sudo" command allows a common user to run commands as root. Or if you want to effectively login as root, you could use "sudo -i". 

Yes, you would need to add the new home partition to your /etc/fstab as the tutorial shows; the commands from my previous post are only to copy the existing /home directory over to the new home partition. Good luck and let me know how it goes. :)

Golly--didn't think I'd get a reply to a solved post-- even tried to delete my post. And then posted same question as a new thread! 

Thank you for your prompt response.  I want to be sure I understand what you are saying.

1) I can open terminal & find the sda1 UUID using the Live CD.  It recognizes the current hard drive partitions.

2) Resize partition - follow psychocats tutorial

3) Use Live CD to open terminal and type the second command which changes the UUID.  

4) Close Live CD -boot into Ubuntu original installation.  Substitute your commands above for the first block of commands in the tutorial under "Using new partition" -- making sure sda# is correct.  If I understand correctly your commands combine both the first and second block of commands in the tutorial -- yes or no?

5) Resume tutorial for /etc/stab.

6) If everything is working okay, do I also follow the tutorial to remove the /home_backup?

Again, thanks for your help.

BTW -- how does one delete a posted message from the forum? Haven't been able to figure it out!

Georgi in UT

---

### Post by caljohnsmith on 2008-12-28
> **hawkhock said:**
> Golly--didn't think I'd get a reply to a solved post-- even tried to delete my post. And then posted same question as a new thread! 

Thank you for your prompt response.  I want to be sure I understand what you are saying.

1) I can open terminal & find the sda1 UUID using the Live CD.  It recognizes the current hard drive partitions.

2) Resize partition - follow psychocats tutorial

3) Use Live CD to open terminal and type the second command which changes the UUID.  

4) Close Live CD -boot into Ubuntu original installation.  Substitute your commands above for the first block of commands in the tutorial under "Using new partition" -- making sure sda# is correct.  If I understand correctly your commands combine both the first and second block of commands in the tutorial -- yes or no?

5) Resume tutorial for /etc/stab.

6) If everything is working okay, do I also follow the tutorial to remove the /home_backup?

Again, thanks for your help.

BTW -- how does one delete a posted message from the forum? Haven't been able to figure it out!

Georgi in UT
Yes, the commands I gave can replace the ones in the tutorial up until the part in the tutorial where it continues with:
```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
Also, I would recommend keeping the old /home_backup folder for at least a week just to make sure everything is OK, and then delete it if you don't run into any problems. It's up to you though of course. Also, about deleting one of your posts, you can't actually do that yourself, you have to ask a moderator to do that; just click the "report post" little icon in the lower left hand corner of your own post, and then you can ask the moderators to delete the post. Anyway, good luck, and let me know if you run into any problems. :)

---

### Post by hawkhock on 2008-12-28
> **caljohnsmith said:**
> Yes, the commands I gave can replace the ones in the tutorial up until the part in the tutorial where it continues with:
```
sudo cp /old/etc/fstab /old/etc/fstab_backup
```
Also, I would recommend keeping the old /home_backup folder for at least a week just to make sure everything is OK, and then delete it if you don't run into any problems. It's up to you though of course. Also, about deleting one of your posts, you can't actually do that yourself, you have to ask a moderator to do that; just click the "report post" little icon in the lower left hand corner of your own post, and then you can ask the moderators to delete the post. Anyway, good luck, and let me know if you run into any problems. :)


OK  -- what did I do wrong.  I successfully completed the disk partition with results as follows:
/dev/sda1      41.14G
/dev/sda3      30.28G
/dev/sda2      3G
  /dev/sda5    3G

I closed out Live CD and rebooted in Ubuntu.  Everything was going fine until I copied and pasted your command block, then attempted to change sda2 to sda3 in the first command line.  Before I realized that I could not highlight and change the 2 to a 3 something happened and I think that is what screwed things up.

I closed terminal and started over, typing in the block of commands. After the cp command the error message is

<cp: cannot stat 'home/georgi/.gvgs' permission denied>

I can't access the terminal, menus, email or any package -- get message

<Failed to change to directory /home/georgi (No such file or directory>

I'm not out much as my data is backed up and I can start over with a clean install but I would like to know what I did wrong.  If I do need start over, I will create the partitions when I do the install.

Any suggestions?

---

### Post by caljohnsmith on 2008-12-28
OK, from your Live CD, how about posting the output of all the following commands (be sure to copy/paste each command one at a time and hit enter, it's not possible to copy/paste the whole block of commands into the terminal command line at once):
```
sudo fdisk -l
sudo blkid
sudo mkdir /media/sda1 /media/sda3
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda3 /media/sda3
cat /media/sda1/etc/fstab
ls -l /media/sda3 /media/sda3/* /media/sda1 /media/sda1/home
```
And we can work from there.

---

### Post by hawkhock on 2008-12-28
Will do -- will take me some time and will post when I do.
Georgi

---

### Post by hawkhock on 2008-12-28
> **caljohnsmith said:**
> OK, from your Live CD, how about posting the output of all the following commands (be sure to copy/paste each command one at a time and hit enter, it's not possible to copy/paste the whole block of commands into the terminal command line at once):
```
sudo fdisk -l
sudo blkid
sudo mkdir /media/sda1 /media/sda3
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda3 /media/sda3
cat /media/sda1/etc/fstab
ls -l /media/sda3 /media/sda3/* /media/sda1 /media/sda1/home
```
And we can work from there.

OUTPUT OF EACH OF THE REQUESTED COMMANDS IS AS FOLLOWS:

ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/sda: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9dc96e9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5371    43142526   83  Linux
/dev/sda2            9325        9726     3229065    5  Extended
/dev/sda3            5372        9324    31752472+  83  Linux
/dev/sda5            9325        9726     3229033+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="93e43211-51ed-4f8d-b2e9-5e9747eb3520" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="dcd13079-a1a9-40b9-bf31-3a3f4bc4ad05" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda5: UUID="150a529e-ce6e-4135-9ebe-f024506f5aa5" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo mkdir /media/sda1 /media/sda3
mkdir: cannot create directory `/media/sda1': File exists
mkdir: cannot create directory `/media/sda3': File exists
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /media/sda1
mount: /dev/sda1 already mounted or /media/sda1 busy
mount: according to mtab, /dev/sda1 is already mounted on /media/sda1
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /media/sda3
mount: /dev/sda3 already mounted or /media/sda3 busy
mount: according to mtab, /dev/sda3 is already mounted on /media/sda3
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ cat /media/sda1/etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=93e43211-51ed-4f8d-b2e9-5e9747eb3520 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=150a529e-ce6e-4135-9ebe-f024506f5aa5 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ ls -l /media/sda3 /media/sda3/* /media/sda1 /media/sda1/home
/media/sda1:
total 96
drwxr-xr-x   2 root root  4096 2008-12-20 22:22 bin
drwxr-xr-x   3 root root  4096 2008-12-20 22:29 boot
lrwxrwxrwx   1 root root    11 2008-12-20 21:34 cdrom -> media/cdrom
drwxr-xr-x   4 root root  4096 2008-10-29 23:04 dev
drwxr-xr-x 132 root root 12288 2008-12-29 00:08 etc
drwxr-xr-x   2 root root  4096 2008-12-28 22:39 home
drwxr-xr-x   3 root root  4096 2008-12-20 21:41 home_backup
lrwxrwxrwx   1 root root    32 2008-12-20 22:28 initrd.img -> boot/initrd.img-2.6.27-9-generic
lrwxrwxrwx   1 root root    32 2008-12-20 21:44 initrd.img.old -> boot/initrd.img-2.6.27-7-generic
drwxr-xr-x  16 root root  4096 2008-12-20 22:21 lib
drwx------   2 root root 16384 2008-12-20 21:34 lost+found
drwxr-xr-x   4 root root  4096 2008-12-28 22:32 media
drwxr-xr-x   3 root root  4096 2008-12-28 22:35 mnt
drwxr-xr-x   2 root root  4096 2008-10-29 22:53 opt
drwxr-xr-x   2 root root  4096 2008-10-20 12:27 proc
drwxr-xr-x  10 root root  4096 2008-12-20 22:20 root
drwxr-xr-x   2 root root  4096 2008-12-20 22:22 sbin
drwxr-xr-x   2 root root  4096 2008-10-29 22:53 srv
drwxr-xr-x   2 root root  4096 2008-10-14 13:02 sys
drwxrwxrwt  10 root root  4096 2008-12-29 00:08 tmp
drwxr-xr-x  11 root root  4096 2008-10-29 22:58 usr
drwxr-xr-x  15 root root  4096 2008-10-29 23:12 var
lrwxrwxrwx   1 root root    29 2008-12-20 22:28 vmlinuz -> boot/vmlinuz-2.6.27-9-generic
lrwxrwxrwx   1 root root    29 2008-12-20 21:44 vmlinuz.old -> boot/vmlinuz-2.6.27-7-generic

/media/sda1/home:
total 0

/media/sda3:
total 20
drwxr-xr-x 46 1000 1000  4096 2008-12-28 22:34 georgi
drwx------  2 root root 16384 2008-12-28 22:25 lost+found

/media/sda3/georgi:
total 36
drwxr-xr-x  2 1000 1000 4096 2008-12-23 18:15 Desktop
drwxr-xr-x 21 1000 1000 4096 2008-12-21 17:30 Documents
lrwxrwxrwx  1 1000 1000   26 2008-12-28 22:38 Examples -> /usr/share/example-content
drwxr-xr-x  2 1000 1000 4096 2008-12-20 21:47 Music
drwx------  3 1000 1000 4096 2008-12-21 18:03 MyPDA
drwxr-xr-x  3 1000 1000 4096 2008-12-27 21:05 Photos
drwxr-xr-x  6 1000 1000 4096 2008-12-27 23:01 Pictures
drwxr-xr-x  2 1000 1000 4096 2008-12-20 21:47 Public
drwxr-xr-x  2 1000 1000 4096 2008-12-20 21:47 Templates
drwxr-xr-x  2 1000 1000 4096 2008-12-20 21:47 Videos
ls: cannot open directory /media/sda3/lost+found: Permission denied
ubuntu@ubuntu:~$ 

Thanks in advance for your help.
Georgi

---

### Post by caljohnsmith on 2008-12-28
OK, I see at least part of the problem; it looks like you still need to add your home partition to your /etc/fstab. While you still have sda1 mounted on /media/sda1 as per the previous instructions, please do:
```
gksudo gedit /media/sda1/etc/fstab
```
And add the following lines:
```
#/dev/sda3 home partition
UUID=dcd13079-a1a9-40b9-bf31-3a3f4bc4ad05 /home  ext3 relatime,errors=remount-ro 0 2

```
And while sda3 is still mounted on /media/sda3 do:
```
sudo chown -R georgi:georgi /media/sda3/georgi
```
Then try rebooting, and let me know what happens. We can go from there.

---

### Post by hawkhock on 2008-12-28
> **caljohnsmith said:**
> OK, I see at least part of the problem; it looks like you still need to add your home partition to your /etc/fstab. While you still have sda1 mounted on /media/sda1 as per the previous instructions, please do:
```
gksudo gedit /media/sda1/etc/fstab
```
And add the following lines:
```
#/dev/sda3 home partition
UUID=dcd13079-a1a9-40b9-bf31-3a3f4bc4ad05 /home  ext3 relatime,errors=remount-ro 0 2

```
And while sda3 is still mounted on /media/sda3 do:
```
sudo chown -R georgi:georgi /media/sda3/georgi
```
Then try rebooting, and let me know what happens. We can go from there.

Since I cannot access terminal from my install, I accessed terminal from the Live CD and copy/pasted the gedit command.  Two things happened:

1) The output from the terminal is:
ubuntu@ubuntu:~$ gksudo gedit /media/sda1/etc/fstab

** (gedit:7560): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.1VJQMU': No such file or directory

I/O error : No such file or directory
I/O error : No such file or directory
ubuntu@ubuntu:~$ 

2) A blank screen opened with a screen header *fstab??? (didn't write it down). I didn't know if I should copy/paste the next two commands on this screen or not.

---

### Post by caljohnsmith on 2008-12-29
OK, how about trying again from your Live CD:
```
sudo mkdir /media/sda1 /media/sda3
sudo mount /dev/sda1 /media/sda1
sudo mount /dev/sda3 /media/sda3

```
And then continue with the commands from post #15. Let me know how that goes or if you run into problems again.

---

### Post by hawkhock on 2008-12-29
WOW, WOW and DOUBLE WOW -- much thanks for your patience. I know what you did but don't understand the logic of how it was done. My install works and everything appears to be working just fine.  I checked the partitions and /home is mounted on /dev/sda3.  Bless you!

Being a noobie, ess than a month, I didn't have much data invested in Ubuntu and would willingly have started over but I understand the theory that "starting over" every time there's a glitch doesn't teach a person anything.  So thank you for helping and I learned a few crucial points along the way.
Georgi in UT

---

### Post by caljohnsmith on 2008-12-29
Glad that worked OK, Georgi; cheers and enjoy your new Ubuntu install. :)

---

