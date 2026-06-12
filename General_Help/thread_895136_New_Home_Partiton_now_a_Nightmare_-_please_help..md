---
title: "New Home Partiton now a Nightmare - please help."
date: 2008-08-19
forum: General Help
---

### Post by Wootyeah on 2008-08-19
I noticed a thread by Madeinbrazil who appears to be having the same problem as me, but I didn't want to hijack his/her post by complaining about my problem.

My problem is this:

I tried to make a new home partition on my 2nd hard drive (Dedicated to Linux only), following the psychocats tutorial.  

Everything *seemed* to be going okay until I rebooted, then the fun began:

Blah! Error! Something about permissions!

Man.

So somebody told me to edit my fstab file to fix that.

Here is my fstab file:

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0

My new home partition SHOULD be on sdb as sdb3.

Any help would be greatly appreciated.


I love you Ubuntu!

---

### Post by cariboo on 2008-08-19
Can you post the output of:

```
sudo fdisk -l
```

Your /etc/fstab makes no sense. If you could paste the whole thing in your next post.That would help also.

Jim

---

### Post by meanburrito920 on 2008-08-19
if you can access the other drive, go to it and sudo chown -R your home directory to your user

---

### Post by Wootyeah on 2008-08-19
Here is the output:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 74.3 GB, 74355769344 bytes
255 heads, 63 sectors/track, 9039 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4446a53f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9039    72605736    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3084991d

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14822   119057683+  83  Linux
/dev/sdb2           29646       30401     6072570    5  Extended
/dev/sdb3           14823       29645   119065747+  83  Linux
/dev/sdb5           29646       30401     6072538+  82  Linux swap / Solaris

Partition table entries are not in disk order
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ 


I am not sure how to chown -R my home directory to my user ( I think I know what it means, but I just don't have the command experience to do it without asking for some help).  I was smart enough to get into this mess, but I'm not sure I'm smart enough to get out ;)

If I have to reinstall, *sigh*, I have to reinstall.

Oh - yeah, umm...well, that was sort of all of my fstab.  *cries* - I really don't know what I did...

unionfs / unionfs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sdb5 swap swap defaults 0 0  

I won't be able to check this post again until tomorrow at about this time most likely.  Thank you both so much for the help.

---

### Post by meanburrito920 on 2008-08-19
you wont need to reinstall. run this:

```

$ sudo chown -R NEW_OWNER HOME_DIRECTORY

```
just replace new_owner with your user name, and home directory with your home directory.

---

### Post by Wootyeah on 2008-08-20
Well, I did try it a couple of different ways:

ubuntu@ubuntu:~$ sudo chown -R user /dev/sdb3/home
chown: invalid user: `user'
ubuntu@ubuntu:~$ sudo chown -r user /dev/sdb3/home
chown: invalid option -- r
Try `chown --help' for more information.
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ chown --help


My username should be user, and this should be the location of my new home partition.  Any ideas?

---

### Post by madeinbrazil on 2008-08-20
meanburrito920 gave me the same tip. Running from the live CD terminal it didn't work. But, I went inside the recovery mode for my Ubuntu installation then I typed it in and it worked :)

I had placed the /home back into the main partition though, following the recovery steps in the psychocats tutorial.

---

### Post by meanburrito920 on 2008-08-20
It should work on the other drive, just make sure you replace the USER name with your actual user name, otherwise it won't find the user. And, as madeinbrazil said, you need to run it from recovery mode.

---

### Post by Wootyeah on 2008-08-20
Well, 

I had taken recovery mode off the GRUB menu.  Is there any way to get it back?

Meanwhile, I'll research it.

---

### Post by meanburrito920 on 2008-08-20
boot up as normal, and when it crashes, press Ctrl-Alt-F1 to get to the command line. enter the commands from there.

---

### Post by Wootyeah on 2008-08-21
Okay, I did exactly as you said.  

I reboot, put in my username, password, error message pops up, I hit ctrl+alt+f1, put in my username and password again, then I type the command:

sudo chown -R user /dev/sdb3     

which should be my username and new home directory.

It looks like it did what I told it to, I reboot again, try to log back in and 

Doh! There is that same error message again.

Is there any hope?
...Any hope at all?

---

### Post by meanburrito920 on 2008-08-21
run it with  the -v option,

sudo chown -Rv USER /dev/sdb3/home/

if you look at the results and see your files, then everything should work fine, assuming that you are actually logging into your computer with username 'user'

---

### Post by Wootyeah on 2008-08-21
Okay, thanks I'll try it.

---

### Post by Wootyeah on 2008-08-21
Okay, Ubuntu has returned! But no home folder, and none of that partition appears to be showing up under "Places".  This is at least one step in the right direction...


Wait!!! *edit* It does appear I have the contents of Home, just in the home_backup - looks like I didn't move it

I'm going to ask first Is it safe to replace the contents of the "home" folder with the contents of home_backup?  And then should I repartition my hard disk back to all one partition?

---

### Post by meanburrito920 on 2008-08-21
> **Wootyeah said:**
> Okay, Ubuntu has returned! But no home folder, and none of that partition appears to be showing up under "Places".  This is at least one step in the right direction...

Do you mean as sdb3? because it is mounted as /home it should just appear as Home on the Places menu.

> 
Wait!!! *edit* It does appear I have the contents of Home, just in the home_backup - looks like I didn't move it


So you created the new home directory empty? if that is the case, then you should be able to move everything over to your new /home with no problems. It's always good to keep a backup though.

> 
I'm going to ask first Is it safe to replace the contents of the "home" folder with the contents of home_backup?  And then should I repartition my hard disk back to all one partition?

I would suggest keeping your /home on a seperate partition. Why would you want to repartition your disk at this point? Unless you have extra empty partitions or you want to shrink/grow certain partitions, don't bother.

---

### Post by Wootyeah on 2008-08-21
I don't think it is mounted as home - the "Home" under "Places" is basically empty.  It's the home_backup folder on the main partition that has all the contents of my old home folder.

I'll move it over, and also probably keep the backup.

I'm good with keeping Home's partition separate, as long as it's functional.  I think I just misunderstood you or didn't see something.  But yeah, it's there on sdb3 as far as I know :)



P.S.  I think the command you gave me before the one with the "-Rv" worked fine after a couple of attempts.  Either way, it helped.

---

### Post by Wootyeah on 2008-08-21
It works!!!

It works!

Yay!

Thank you

---

