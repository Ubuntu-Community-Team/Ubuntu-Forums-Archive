---
title: "Add second harddrive to existing install?"
date: 2005-06-02
forum: Hardware &amp; Laptops
---

### Post by October on 2005-06-02
Hey all,

My 120GB drive in my family file/multimedia server is almost full!!!!

I've always used special /home directories for file storage (made sense at the time!) like /home/pictures, /home/videos, etc.

I want to add a second 120GB drive to the machine and am wondering what is the best way to do this task and end up with at least the majority of the new drive being devoted to file storage as well.  In other words, can a /home tree span multiple drives and if so how do I do this from an exisiting install?  If not, what are my best options, barring backing everything up on CD?

Suggestions?

Thanks in advance,

Jon Hoskins

---

### Post by Kamping_Kaiser on 2005-06-03
[QUOTE=October]Hey all,

My 120GB drive in my family file/multimedia server is almost full!!!!

I've always used special /home directories for file storage (made sense at the time!) like /home/pictures, /home/videos, etc.

I want to add a second 120GB drive to the machine and am wondering what is the best way to do this task and end up with at least the majority of the new drive being devoted to file storage as well.  In other words, can a /home tree span multiple drives and if so how do I do this from an exisiting install?  If not, what are my best options, barring backing everything up on CD?
/QUOTE]


Yes you can add a second disc to the machine, as long as you have free power plugs and a spare place on your ide ribbon(s).

*NOTE* this should be done with sudo for all commands
To make the new hard drive /home, you would 
plug in the drive and note where it is - is it primary slave, or slave\master on the secondary cable?
boot up.
You could use "cat /proc/partitions" to check the new disc is detected. Asuming you are using secondary master as the drive, it will apear as a line similar to:
   3     1    ******   hdc1
If your sure you have the right drive (and our drive is still secondary master), 
mkfs.ext3 /dev/hdc
Then mount it somewhere - /mnt is good.
mount -t ext3 /dev/hdc /mnt
And copy all the data in your existing home over 
cp -a /home /mnt
Then unmount the new hd from /mnt
umount /mnt
And add the change to fstab 
echo "/dev/hdc    /home    ext3      defaults     0         0" >> /etc/fstab
And reboot,
All going well, you will now have home on the second hard drive....

---

### Post by October on 2005-06-03
Thank you for your prompt and informative reply.  Unfortunately that does not really answer the question at hand which might be partially my fault for not posting clear enough...

> In other words, can a /home tree span multiple drives and if so how do I do this from an exisiting install?

More precisely what I want to do is just add a second drive to the machine and have it carry the overflow from the first drive.  As in the quote this would require that *both* drives act as "/home" or perhaps even more clearly yet, I want to increase my /home partition by adding an additional drive and wonder if it makes any difference to the OS if the partition is contained solely on a single drive or not?

Perhaps even moving one segment of my /home collection to the new drive, like "/home/videos".  Could "/home", "/home/music", "/home/files", etc. remain on the first drive and is there a way to make this work transparently?

---

### Post by Xanthous on 2005-06-30
[QUOTE=Kamping_Kaiser]

*NOTE* this should be done with sudo for all commands
To make the new hard drive /home, you would 
plug in the drive and note where it is - is it primary slave, or slave\master on the secondary cable?
boot up.
You could use "cat /proc/partitions" to check the new disc is detected. Asuming you are using secondary master as the drive, it will apear as a line similar to:
   3     1    ******   hdc1
If your sure you have the right drive (and our drive is still secondary master), 
> **mkfs.ext3 /dev/hdc**
Then mount it somewhere - /mnt is good.
mount -t ext3 /dev/hdc /mnt
And copy all the data in your existing home over 
cp -a /home /mnt
Then unmount the new hd from /mnt
umount /mnt
And add the change to fstab 
echo "/dev/hdc    /home    ext3      defaults     0         0" >> /etc/fstab
And reboot,
All going well, you will now have home on the second hard drive....[/QUOTE]

I was trying to mount a second HD, that was already formated ext3 and had data on it, by following your instructions, but I didn't know that mkfs would wipe out my data.
Any ideas on how to recover my data?   [-o<

---

### Post by calebsdaddy on 2007-11-27
What you are looking for is LVM.  It will aide you in doing what you are trying to do.

Visit [http://ubuntuforums.org/showthread.php?t=584473]("http://ubuntuforums.org/showthread.php?t=584473")

---

