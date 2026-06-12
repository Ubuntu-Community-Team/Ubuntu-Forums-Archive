---
title: "Last name Apache, first name Pamela"
date: 2008-08-04
forum: General Help
---

### Post by karrister on 2008-08-04
Hello all of you guys! I have a problem, maybe some of you guys already understood from the title of the thread. Well I got some newer hardware (finally!) and I decided to install Linux on it to have it as a server/general use computer. After a while of using it I wanted to test with Apache and dyndns to create my own server. It had been up for a few weeks and I was already happy that yay, I did it all by myself, with no problems! Until I noticed on one of my mounted NTFS-partitions is a folder called pamela...

Ok so here's how it is. I have 2 harddrives, one 40GB and one 500GB SATA. On the 40 I first installed XP, used it for a while and bought a half-tera HD. I made two partitions, called SATA and SATA-MEDIA. And then I decided to install as a second operating system Linux and didnt change any of the NTFS partitions I had. Then I started using Apache, and I used to log onto this Linux computer from my laptop with SSH to use irssi etc. I also used to every once in a while check my access log of apache. From the start already every now and then someone was trying to access on my page folder /SATA-MEDIA and it was a little weird to me, tried it myself on a browser and since it didnt work for me I didnt focus much on it.
But then one day I opened this mounted partition SATA-MEDIA and noticed in the root of the partition a file called I think XXX.folder (opened it in a text editor and during the first lines aleste was mentioned). Then I also noticed a folder called pamela. Now I started being really curious. It deffinately wasnt my creation!!!! Here's a list of the folder that I made:

yhteensä 1157 
-rwxrwxrwx 1 root root 197867 2004-07-29 02:31 _aleste.exe 
-rwxrwxrwx 1 root root 299 2008-06-19 23:06 Desktop.ini
-rwxrwxrwx 1 root root 5652 2008-06-19 23:08 Folder.htt
-rwxrwxrwx 1 root root 847920 2002-10-14 17:02 python22.dll
-rwxrwxrwx 1 root root 45103 2002-10-14 17:02 _socket.pyd
-rwxrwxrwx 1 root root 53292 2002-10-14 17:03 _sre.pyd
-rwxrwxrwx 1 root root 16384 2002-10-14 17:03 w9xpopen.exe

I panicked at first a little, I just tried to umount both of the SATA and SATA-MEDIA (cause the other SATA partition had some personal information, the XP partition wasnt so crucial but I dont have it mounted either anymore) and at first it didnt seem to work, I was still able access it. Then after a few tries I wasnt able to mount it back anymore. Booted to XP and it didnt show them either, only I was able access SATA and there were only a few files left.

So here's the main problem I have a question about: am I still able to recover both of the partitions entirely, or should I just forget about it and start from the scratch?


That was the most important thing I needed answer about, but also if you have tips about security with apache and this not happening again, you could let me know. Instantly afterwards I changed su so that it doesnt ask for the password of the user but password of root. So that like for instance if someone got my pass when I was logging to my ftp server, they could use it for su. But how did this happen?? And what is this thing that someone is all the time trying to access /SATA-MEDIA? How was anyone even able to know I have such a partition? What's going on?


Thanks guys for all the help! For sure if someone's gonna be able to help me with this it's worth at least one beer/coffee/whatever, if we just hopefully ever happened to meet somewhere! And that's a promise!


With warm greetings, from (now) a little cold finnish summer,

Karri

---

### Post by karrister on 2008-08-06
Anyone?

---

### Post by geirha on 2008-08-06
Sounds like you have a security hole in your web application(s). What are you running on your web server? Do you use php? Do you have any symbolic links that point to /SATA-MEDIA in your webroot?

As for the NTFS partitions. What error messages do you get when you try to mount them? 

If you get finnish messages, do the command again, but prepend it with "LANG=C ", which should show messages in english. I.e. ```
LANG=C sudo mount ...
```

---

### Post by karrister on 2008-08-06
Yeah, I use php. I also have mySQL installed, even though I'm not using it. And no, there are no symbolic links to /SATA-MEDIA in my webroot.

I am able to mount the /SATA but there are only a few of the files left there for me to see. /SATA-MEDIA I am not able to mount at all, and when I'm trying to mount it in console it says this:

> 
:/media$ sudo mount /dev/sdb1 /media/
Failed to open ntfs attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory


There are sdb, sdb1 and sdb2. Sdb2 is the /SATA so I tried sdb now:

> 
:/media$ LANG=C sudo mount /dev/sdb /media/
mount: you must specify the filesystem type



Thanks for any help!

---

### Post by geirha on 2008-08-06
Hm. Could you post the output of ```
sudo fdisk -l
```?

---

### Post by karrister on 2008-08-06
Here's sudo fdisk -l:

> Disk /dev/sda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb061b061

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551        4009    11719417+  83  Linux
/dev/sda3            4010        4133      996030   82  Linux swap / Solaris
/dev/sda4            4134        4998     6948112+   b  W95 FAT32

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000142c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       52641   422838801    7  HPFS/NTFS
/dev/sdb2           52642       60801    65545200    7  HPFS/NTFS


---

### Post by karrister on 2008-08-07
Could the security hole be in Samba? Cause now I tried to share something between this computer and my laptop and I opened up the samba configuration tool and the folder that was being shared was /SATA-MEDIA. Could there be something wrong with my Samba settings (even though I didnt change the default ones)? What about my hard drive, do I have to clear all my data or am I somehow able to get it all back still?

---

### Post by karrister on 2008-08-08
Would anyone happen to know how to solve this?

---

### Post by karrister on 2008-08-09
Is there any way to recover the data from my harddrive?

---

### Post by karrister on 2008-08-19
Could anyone try to help me? I'd be very thankful!

---

