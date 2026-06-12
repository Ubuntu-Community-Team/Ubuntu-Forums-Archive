---
title: "gedit:6810 Error, Partition mounting problems."
date: 2008-11-09
forum: General Help
---

### Post by Happibun on 2008-11-09
Hi.

I am trying to mount a new partition on my laptop's hard drive for my home folder.

I have a fresh install of 8.10 (Intrepid) which has immediately been re-partitioned with gparted before even going online for updates.

> jo@Epsilon:~$ sudo blkid -c /dev/null  
 [sudo] password for jo: 
 /dev/sda1: LABEL="OSpartition" UUID="e3d90611-7b61-45c4-b34b-98b41e8de29f" TYPE="ext3" 
 /dev/sda3: LABEL="JoHome" UUID="7747ed8f-52fe-4fbc-908a-9b278c6e7e42" SEC_TYPE="ext2" TYPE="ext3"  
 /dev/sda5: UUID="858065d3-8834-4669-88fc-111d3b36d97e" TYPE="swap" 
The new partition is /dev/sda3. Obviously I now have to save the information in to the fstab file.

When I open and save fstab, I get this error message.

> jo@Epsilon:~$ sudo gedit /etc/fstab  
 [sudo] password for jo: 
 

 ** (gedit:6810): WARNING **: Could not write gedit state file: Failed to create file '/root/.gnome2/gedit-2.XWS7JU': No such file or directory 
 

 I/O error : No such file or directory  
 I/O error : No such file or directory  If have saved without modifying the file, because I would like to know what this error message means before I go any further.

This is just one aspect of the problems I am having and outlining in this thread - [http://ubuntuforums.org/showthread.php?t=970879](http://ubuntuforums.org/showthread.php?t=970879)

Could someone please tell me what is happening?

Thank you.

---

### Post by umlungu64 on 2009-01-10
Hi Happibun

Did you solve this problem with the error message when opening gedit? I've got the same here, after I fiddled with my partition-table!

Regards

---

### Post by Happibun on 2009-01-12
Hi [umlungu64]("http://ubuntuforums.org/member.php?u=55651"),

I kind of did, but only by wimping out and not using gedit on the fstab file. Someone showed me how to use gparted manually when installing Ubuntu, and what to enter, so I reinstalled and did it that way. The post is here - [http://ubuntuforums.org/showthread.php?p=6143326#poststop](http://ubuntuforums.org/showthread.php?p=6143326#poststop) , on this thread - [http://ubuntuforums.org/showthread.php?p=6105254#poststop](http://ubuntuforums.org/showthread.php?p=6105254#poststop) .

I decided to keep this thread open, just in case anyone wanted to come along and tell me where I might be going wrong, 'cause I didn't exactly solve it this way...

I hope that this, and the stuff I've highlighted for you is not too garbled, and of some use to you.

If you have success, please let me know. Good luck :-)

---

