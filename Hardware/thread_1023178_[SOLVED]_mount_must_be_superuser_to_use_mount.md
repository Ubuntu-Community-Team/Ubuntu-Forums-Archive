---
title: "[SOLVED] mount must be superuser to use mount"
date: 2008-12-27
forum: Hardware
---

### Post by protean.star on 2008-12-27
Hi,

I have posted about this problem before but no one responded.

I still have not solved it. I think it is a simple problem to solve. It's just that I am a beginner at command line in linux. I appreciate knowledgeable, accurate help. 
Thank you.

I have a Eee PC 1000, with Ubuntu eee 8.4.0.1 (Hardy Heron) installed.

I am unable to mount the DVD/CD external drive. It is an LG Super Multi DVD Rewriter, model GE20LU10. In the command line, I don't know what the description of the device should be. I also don't know how to write a SUDO command to mount the volume.

When I try to view a DVD, I get a message: Mount: Unable to mount volume. Must be superuser to mount volume.


Here is what I get when I type this into the terminal and  hit enter:~$ gedit /etc/fstab



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44e7edce-bb53-431a-b0d5-12ccdb25b34c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b1927876-0e25-416e-bb06-3de636982271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by jrusso2 on 2008-12-27
Try gksu gedit command and enter your password.  This will give you sudo rights to gedit.

---

### Post by taurus on 2008-12-27
> **protean.star said:**
> 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44e7edce-bb53-431a-b0d5-12ccdb25b34c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b1927876-0e25-416e-bb06-3de636982271 none            swap    sw              0       0
**[COLOR="Blue"]/dev/scd0       /media/cdrom0[/COLOR]**   udf,iso9660 user,noauto,exec,utf8 0       0
**[COLOR="Blue"]/dev/scd0       /media/floppy0[/COLOR]**  auto    rw,user,noauto,exec,utf8 0       0

Did you ever edit your /etc/fstab?

---

### Post by protean.star on 2008-12-27
Hi, thanks. OK, I did that, entered my password. Now what to do?

---

### Post by protean.star on 2008-12-27
Hi Taurus,
No, I have not. I am a rank beginner. Thanks

---

### Post by jrusso2 on 2008-12-27
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

Just use this example and plug in the user and the partition you want to auto mount and use gedit instead of kate or kedit.

Bookmark this website its very good for new users and was done by one of this forums moderators.

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

He also talks about mounting partitions which you might want to read to help
you understand how Linux numbers partitions instead of using C:\, D:\, etc.

---

### Post by protean.star on 2008-12-27
Jrusso,
OK, I am reading through the first link.

Do I just use the command:
sudo mount -a

---

### Post by protean.star on 2008-12-27
Hello Jrusso2 and taurus,

OK. I am a bit confused. Before I do anything in superuser mode, I want to make sure I am doing it correctly. It looks like I can do this in [COLOR="RoyalBlue"]user[/COLOR] mode, based on what is displayed.



This is copied from the Linux man page (mount)

The file /etc/fstab (see fstab(5)), may contain lines describing what devices are usually mounted where, using which options. This file is used in three ways:


    mount -a [-t type] [-O optlist]

(usually given in a bootscript) causes all file systems mentioned in fstab (of the proper type and/or having or not having the proper options) to be mounted as indicated, except for those whose line contains the noauto keyword. Adding the -F option will make mount fork, so that the filesystems are mounted simultaneously.

(ii) When mounting a file system mentioned in fstab, it suffices to give only the device, or only the mount point.

(iii) Normally, only the superuser can mount file systems. However, when fstab contains the user option on a line, anybody can mount the corresponding system.

---

### Post by protean.star on 2008-12-27
Hello jrusso and taurus,

I have been reading through the man pages of mount, and I am thinking the following way about how to solve the problem. Should I edit out the words 'noauto' in fstab using superuser status,  then run the command in user status,  mount -a?

From the mount man pages:

[COLOR="RoyalBlue"]noauto
    Can only be mounted explicitly (i.e., the -a option will not cause the file system to be mounted). [/COLOR]

---

### Post by protean.star on 2008-12-27
see next  post

---

### Post by protean.star on 2008-12-27
CORRECTED!

Hello jrusso2 and taurus,

Well, I believe that I have solved my problem.

Here is what I did.

Edited out the '[COLOR="RoyalBlue"]no[/COLOR]' in 'noauto', both places where it occurred.
Tried to use mount -a command as user. Permission denied, so I did that command as superuser. 

Now, everything appears to work fine. 

I was able to open a data CD with photos, then I listened to an audio CD, then I watched a DVD, then I burned an audio CD, no problem.

One of the DVDs I have does not open, but I am not sure the LG unit is to blame or not. 

Thanks to both of you for your help. 

Here is the new /etc/fstab. I have indicated with blue where I made the only changes.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44e7edce-bb53-431a-b0d5-12ccdb25b34c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b1927876-0e25-416e-bb06-3de636982271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR="RoyalBlue"]auto[/COLOR],exec,utf8 0       0
/dev/scd0       /media/floppy0 auto    rw,user,[COLOR="RoyalBlue"]auto[/COLOR],exec,utf8 0       0

---

### Post by pguedes on 2009-11-21
> **protean.star said:**
> CORRECTED!

Hello jrusso2 and taurus,

Well, I believe that I have solved my problem.

Here is what I did.

Edited out the '[COLOR="RoyalBlue"]no[/COLOR]' in 'noauto', both places where it occurred.
Tried to use mount -a command as user. Permission denied, so I did that command as superuser. 

Now, everything appears to work fine. 

I was able to open a data CD with photos, then I listened to an audio CD, then I watched a DVD, then I burned an audio CD, no problem.

One of the DVDs I have does not open, but I am not sure the LG unit is to blame or not. 

Thanks to both of you for your help. 

Here is the new /etc/fstab. I have indicated with blue where I made the only changes.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=44e7edce-bb53-431a-b0d5-12ccdb25b34c /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=b1927876-0e25-416e-bb06-3de636982271 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,[COLOR="RoyalBlue"]auto[/COLOR],exec,utf8 0       0
/dev/scd0       /media/floppy0 auto    rw,user,[COLOR="RoyalBlue"]auto[/COLOR],exec,utf8 0       0

After one week of desperate searching....and thinking about quitting ubuntu after som good 4 years experience...finally I solved the USB problem!!! Thank you all for your precious hints. I did exactly as you did and now its working!

---

