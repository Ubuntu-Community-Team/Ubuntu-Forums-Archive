---
title: "How to properly mount additional NTFS hard drive?"
date: 2011-04-20
forum: Hardware
---

### Post by qkzoo on 2011-04-20
I have an extra 120 gig hard drive on my system here.  I can mount the hard drive just fine under my login, but if I try to mount it under my wife's login I get told I'm not authorized to do that.  What steps do I need to take to have it show up on hers as well?

Thank you for any advice,

Q

---

### Post by mynameisnotbob on 2011-04-20
you need to mount it under yours. Then you can switch user and use it from her account. She isn't an admin, so she can't do that.

---

### Post by Jimmy9pints on 2011-04-20
> **qkzoo said:**
> I have an extra 120 gig hard drive on my system here.  I can mount the hard drive just fine under my login, but if I try to mount it under my wife's login I get told I'm not authorized to do that.  What steps do I need to take to have it show up on hers as well?

Thank you for any advice,

Q


Let me understand the problem a bit better. 

What steps are you taking to mount it under your account?

What error does it report under your wife's account?

---

### Post by mynameisnotbob on 2011-04-20
If you log out, I think it automatically unmounts the drive.

---

### Post by Morbius1 on 2011-04-20
Have it automount on boot the way Ubuntu would do it had you asked it to so during the initial install.

**First**, if you currently have the partition mounted - unmount it. Then:

**[1] Run the following command to see how the system sees your partitions:**
```
sudo blkid -c /dev/null
```You'll get something like this - [COLOR=Blue]as an example[/COLOR]:
> /dev/sda2:  UUID="1EF42FA9F42F81DF" TYPE="ntfs"**[2] Make a permanent mount point for the partition:**
```
sudo mkdir /media/Data
```**[3] Add the following line to the end of /etc/fstab:**
```
UUID=1EF42FA9F42F81DF /media/Data ntfs  defaults,nls=utf8,umask=007,gid=46 0       0
```[B][4] Then run the following command to test for errors ( and post them if you get any ) and mount the new partition:
[/B]```
sudo mount -a
```umask=007 will allow read /write access to owner ( root ) and group and no one else.
gid=46 will make the group plugdev ( 46 ) - all local users are members of the plugdev group in Ubuntu.

So all local login users will have read / write access to the the partition at /media/Data.

---

### Post by mynameisnotbob on 2011-04-20
Yeah...that's probably a little less clunky than my method.

---

### Post by qkzoo on 2011-04-21
Hey there, thanks for the assistance!  I thought this drive was ntfs but it isn't, whoops, it's vfat:

```

/dev/sda1: UUID="04e5cc73-6d48-45cb-a8da-27a1e4385ada" TYPE="ext4" 
/dev/sda5: UUID="93e35061-9ffd-4d37-8e3d-f98265f2a1a9" TYPE="swap" 
/dev/sdb1: LABEL="New Volume" UUID="9C6F-1D04" TYPE="vfat" 

```

Do I follow the above instructions anyhow, substituting ntfs for vfat?

---

### Post by Morbius1 on 2011-04-21
```
sudo mkdir /media/Data
```The fstab line would become:
```
UUID=9C6F-1D04 /media/Data vfat utf8,umask=007,gid=46 0       1
```Then run the following to test for errors and mount the new partition:
```
sudo mount -a
```

---

### Post by qkzoo on 2011-04-21
Ok, I confess, I took a stab at it on my own before you replied.  Whatever I did here seems to be working just fine, the drive auto-mounts in whichever login I use, and both users can read and write files to the drive (thank God Quicken 2004 runs in Wine).  I did notice some differences, though, between what I did, and what you told me to do (I know, I should have waited...).  First, here's the commands I typed in:


sudo mkdir /media/shared_drive
UUID=9C6F-1D04 /media/shared_drive vfat umask=007,gid=46 0       0
sudo mount -a

Notice I didn't put the "utf8" command in, and I also used the "0     0" from your previous instructs, instead of "0     1".  Should I unmount it and re-edit the fstab file, or just leave it alone?

Also, the drive has a label of "New Volume" is there a way I can rename it to something more appealing?  

Thanks for your help!

---

### Post by Morbius1 on 2011-04-21
>  UUID=9C6F-1D04 /media/shared_drive vfat umask=007,gid=46 0       0That line is fine. 

The utf8 is so that it's mounted in such a way that it recognizes all the characters in the unicode standard. To tell you the truth it's probably in the defaults for vfat, I just got used to adding it out of habit. If you ever end up saving something with an odd character and it gives you an error you can just add it back. 

The last digit of the fstab line determines the relative frequency of when at boot the system checks for file errors. In the case of ntfs you don't want Linux to check for and possibly correct errors. Fat32 is a more understood filesystem so it usually has either a "1" or a "2". You have a "0" meaning it won't check for errors.

The only problem is your last sentence:
>  Also, the drive has a label of "New Volume" is there a way I can rename it to something more appealing?  With your line in fstab it should be mounting to /media/shared_drive. If it's mounting to /media/New Volume then your line is being ignored in fstab. If you mean that you just don't like the Label itself then you can use gparted to change the lablel.

---

### Post by qkzoo on 2011-04-21
Ok, I went ahead and made the changes, adding the vfat and changing the 0 at the end to a 1.  I ran "sudo mount -a" to check how it mounted and it gave me this:

```

andrew@andrew-Dimension-2400:~$ sudo mount -a
[mntent]: line 12 in /etc/fstab is bad
andrew@andrew-Dimension-2400:~$ 

```

SO, here's my /etc/fstab file:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=93e35061-9ffd-4d37-8e3d-f98265f2a1a9 none            swap    sw              0       0
UUID=9C6F-1D04 /media/shared_drive vfat utf8, defaults,umask=007,gid=46 0       1

```

The drive is still mounting as "New Volume" which confuses me, because it's mounting under all logins now, so something must be working?

When I navigate to /media/shared_drive in Nautilus and click on it, it shows the contents of the drive.  Likewise, when I click on the "New Volume" icon that's on the desktop, it shows the contents of the drive just fine.  I click the "Places" menu, and it shows "New Volume" - no where, that I can see right now, is it appearing as "shared_drive" - confused! :o

UPDATE EDIT:

After removing the "utf8" from the fstab file and re-running the "sudo mount -a" command, I don't get an error anymore, but it does still appear as "New Volume" everywhere.

I included a screenshot so you can see how it looks under /media/, if that helps at all :)

---

