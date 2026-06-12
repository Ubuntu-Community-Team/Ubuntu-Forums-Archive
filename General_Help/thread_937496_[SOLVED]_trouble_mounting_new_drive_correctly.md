---
title: "[SOLVED] trouble mounting new drive correctly"
date: 2008-10-03
forum: General Help
---

### Post by Nicks Spleen on 2008-10-03
I have recently installed ubuntu on my desktop computer. I have 3 hard drives and am using one as /, one as /home, and I am wanting to use the third as /home/nick/music.

I specified / and /home durring the ubuntu installation and was going to mount the third after installation. I want my music hard drive to be mounted like my /home partition and not mounted as a removable drive. I am hoping it is possible to have it be mounted without putting an icon on my desktop and in nautilus. Its an internal drive so I am never going to want to unmount it.

After reading the posts on the forums I have tried editing fstab manually and using pysdm. Everything I have tried still lands it being counted as a removable drive. I hope what I am trying to do is possible.

Thanks for the help and let me know if you need any other details.

Here is a copy of my fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                    0  0  
# /dev/sda4
UUID=ef6495cc-4be3-46f0-9250-eee580cbc13b  /                 ext3         relatime,errors=remount-ro  0  1  
# /dev/sdd1
UUID=d0fed617-9723-44ac-a609-155b860be2b4  /home             ext3         relatime                    0  2  
# /dev/sda3
UUID=3ab04670-5dc8-4c39-8491-859fac76eb6e  none              swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1     udf,iso9660  user,noauto,exec,utf8       0  0  
# /dev/sdc1
UUID=2e84e7b6-18e1-4fd1-a1ac-4d32dfe01d7b  /home/nick/music  ext3         relatime                    0  2  
```

---

### Post by drs305 on 2008-10-04
> **Nicks Spleen said:**
> I am hoping it is possible to have it be mounted without putting an icon on my desktop and in nautilus. 
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc             proc         defaults                    0  0  
# /dev/sda4
UUID=ef6495cc-4be3-46f0-9250-eee580cbc13b  /                 ext3         relatime,errors=remount-ro  0  1  
# /dev/sdd1
UUID=d0fed617-9723-44ac-a609-155b860be2b4  /home             ext3         relatime                    0  2  
# /dev/sda3
UUID=3ab04670-5dc8-4c39-8491-859fac76eb6e  none              swap         sw                          0  0  
/dev/scd0                                  /media/cdrom0     udf,iso9660  user,noauto,exec,utf8       0  0  
/dev/scd1                                  /media/cdrom1     udf,iso9660  user,noauto,exec,utf8       0  0  
[B]# /dev/sdc1
UUID=2e84e7b6-18e1-4fd1-a1ac-4d32dfe01d7b  /home/nick/music  ext3         relatime                    0  2  [/B]
```

Assuming you wanted the other partitions to be displayed, you could prevent the partition from being displayed on the Desktop and in Places but you would have to change the mountpoint to a subfolder of /mnt. It would no longer be in your home folder, so you have to decide which is most important to you. 

If you don't want to see it, make the appropriate mountpoint in /mnt, change the ownership, and set the permissions. Be sure to change it to your username:
```

sudo mkdir /mnt/music
sudo chown -R *yourusername*: /mnt/music
chmod -R 0750 /mnt/music

```

Change the last entry in fstab (bold in the quoted text) after backing it up:
```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```

Change this:
```
[B]# /dev/sdc1
UUID=2e84e7b6-18e1-4fd1-a1ac-4d32dfe01d7b  /home/nick/music  ext3         relatime                    0  2  [/B]
```

To this and save:
```
[B]# /dev/sdc1 (old)
# UUID=2e84e7b6-18e1-4fd1-a1ac-4d32dfe01d7b  /home/nick/music  ext3         relatime                    0  2  [/B]
# /dev/sdc1 
UUID=2e84e7b6-18e1-4fd1-a1ac-4d32dfe01d7b  /mnt/music  ext3    defaults,users   0  2  
```

If this doesn't work as expected or you change your mind, delete the last line and uncomment the old UUID line.

---

### Post by Nicks Spleen on 2008-10-04
Thank you for your help and quick response. I did what you suggested and it worked perfectly. Then I created a link in my home directory to my music folder. Its pretty much what I wanted, thanks again.

---

