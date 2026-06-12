---
title: "mounting my slave HD"
date: 2005-08-28
forum: Hardware &amp; Laptops
---

### Post by rivervalleyprinting on 2005-08-28
Ok Ive finally got my hdb formatted to ext3 (I think) then I went to mount it and nothing seems to work. After searching the forums I tried "/etc/fstab"  and then I tried "sudo mount /mnt/mynewdrive" and no dice. Honestly I have no idea what either one of these commands mean either. So after the first command the message I got was " Permission denied", then after the second command I tried it said "can't find /mnt/mynewdrive in /etc/fstab or /etc/mtab". Anybody here got a clue what I'm doing wrong? Also FYI this drive is only a month old, I took it out of a working windows machine. No worries about losing data there was nothing important on it.
Thank You 
Tony ](*,)

---

### Post by invalid on 2005-08-28
I am making the following assumptions:
Your drive is /dev/hdb and you have a linux partition /dev/hdb1

do:
sudo mkdir /media/hdb

sudo nano /etc/fstab
and add the following line:
/dev/hdb1    /media/hdb    ext3    defaults    0    0

sudo mount /dev/hdb1 /media/hdb

Now you can access your drive in the folder /media/hdb
It will me owned by root by default - so if you plan to use it as your user, you should create a folder within and chown/chgrp it to yourself.

Cheers,
Cb

---

### Post by jasmuz on 2005-08-28
Taken from the wiki and modified:


Step 1. Create a mount point.

$ sudo mkdir /mnt/whatevername

Step 2. Determine the device name assigned to the disk partition

:~ $ sudo fdisk -l

Note: the '-l above is the letter 'l' (pronounced 'el') NOT the numeral 1.

The output should be something like this:

Device Boot     Start      End      Blocks      ID      System
/dev/hda1       1          638      5124703     b         Linux
/dev/hda2       639        4525     31222327    83      Linux
/dev/hda3       4526       4635     497980      82      Linux swap

Step 3. Launch gedit (a text editor) and open the fstab file

$ sudo gedit /etc/fstab

Step 4. Add the following line at the end of the fstab file

<file system>    <mount point>     <type>     <options>                      <dump>     <pass> 
/dev/hda1        /mnt/whatevername    ext3       defaults,auto,uid=1000,gid=1000 0 0

Step 5. Save the fstab file and close the gedit window.

Click the save button in the toolbar menu of the gedit program and close out the edit window (File | Close)

Step 6. Mount the new partition.

To access your  partition use the following command:

$ sudo mount /dev/hda1 /mnt/whatevername

---

### Post by rivervalleyprinting on 2005-08-28
[QUOTE=invalid]I am making the following assumptions:
Your drive is /dev/hdb and you have a linux partition /dev/hdb1

do:
sudo mkdir /media/hdb

sudo nano /etc/fstab
and add the following line:
/dev/hdb1    /media/hdb    ext3    defaults    0    0

sudo mount /dev/hdb1 /media/hdb

Now you can access your drive in the folder /media/hdb
It will me owned by root by default - so if you plan to use it as your user, you should create a folder within and chown/chgrp it to yourself.

Cheers,
Cb[/QUOTE]
 Thanks I see it now. Now if I could just figure out how to set the sudo password so I can access it. I dont remember it asking me to set up a super user account and now I cant figure out how to do it. GRRRR!  My mind is clouded from years of Windows Use.

---

### Post by invalid on 2005-08-29
Your sudo password is your default users password.

Example: If your default user is Bob and your password is foobar - then your sudo password is foobar as well.

Cheers,
Cb

---

### Post by invalid on 2005-08-29
<!-- extra post by mistake -->

---

