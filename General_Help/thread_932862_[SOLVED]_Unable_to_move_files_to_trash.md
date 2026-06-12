---
title: "[SOLVED] Unable to move files to trash"
date: 2008-09-28
forum: General Help
---

### Post by Gotterdammerung on 2008-09-28
Hi, there,

I have 5 ext3 filesystems mounted as follows:

```
/dev/sdb1 on /home type ext3 (rw,noatime,nodiratime)
/dev/sdb2 on /mnt/sdb2 type ext3 (rw,noatime,nodiratime)
/dev/sdc1 on /mnt/sdc1 type ext3 (rw,noatime,nodiratime)
/dev/sdc2 on /mnt/sdc2 type ext3 (rw,noatime,nodiratime)
/dev/sdc3 on /mnt/sdc3 type ext3 (rw,noatime,nodiratime)
```

If I try to delete any file from anywherelse other than /home, the system says it's unable to move to the trash can, and asks if I want to erase it definetely. What am I doing wrong? What should I do to make it possible to move the files to the trash can?

Here's the lines of my fstab related to these FSs:

```
/dev/sdb1 /home ext3    defaults,noatime,nodiratime		1 2
/dev/sdb2 /mnt/sdb2 ext3    defaults,noatime,nodiratime		1 2
/dev/sdc1 /mnt/sdc1 ext3    defaults,noatime,nodiratime		1 2 
/dev/sdc2 /mnt/sdc2 ext3    defaults,noatime,nodiratime		1 2 
/dev/sdc3 /mnt/sdc3 ext3    defaults,noatime,nodiratime		1 2 
```

This is how they were formatted:

```
mkfs.ext3 -I 128 -L HDn /dev/sdxy
```

---

### Post by iaculallad on 2008-09-28
There's a probability that you don't own your Trash folder. In your terminal, try:


```
sudo chmod 666 /home/your_username/.local/share/Trash
```

or

```
sudo chmod 666 ~/.local/share/Trash
```

---

### Post by Gotterdammerung on 2008-09-29
> **iaculallad said:**
> There's a probability that you don't own your Trash folder. In your terminal, try:


```
sudo chmod 666 /home/your_username/.local/share/Trash
```

or

```
sudo chmod 666 ~/.local/share/Trash
```

If I delete something from /home I'm able to send it to the Trash. The problem is with files outside /home.

---

### Post by mc4man on 2008-09-29
As a point of comparison 
If you don't mount your other volumes in fstab and instead chown them and mount from places, ect.  then when you choose 'move to trash' a .trash-1000 is created and moving is allowed.

---

### Post by Gotterdammerung on 2008-10-01
> **mc4man said:**
> As a point of comparison 
If you don't mount your other volumes in fstab and instead chown them and mount from places, ect.  then when you choose 'move to trash' a .trash-1000 is created and moving is allowed.

I've tried

```
sudo umount /mnt/sdc3
sudo chown myuser:myuser /mnt/sdc3
sudo mount /mnt/sdc3

```
than moving the file to trash, but the result is the same: the system only allows me to move files from my home folder to trash.

I don't understand what you mean. :confused: Would you mind typing the steps to this test?

Thanks

---

### Post by drs305 on 2008-10-01
I am not sure what your problem is, but you ran the commands:
```

sudo umount /mnt/sdc3
sudo chown myuser:myuser /mnt/sdc3
sudo mount /mnt/sdc3

```

Those chown command acted only on the sdc3 folder, not any subfolders. If the problem is with ownership, you may need to change the ownership of the subfolders, including the trash bins.

If everything on sdc3 partition can be owned by you, run the following command. Adding the "-R" switch will change all subfolders as well as sdc3.
```
sudo chown -R myuser:myuser /mnt/sdc3
```

---

### Post by Gotterdammerung on 2008-10-02
> **drs305 said:**
> I am not sure what your problem is, but you ran the commands:
```

sudo umount /mnt/sdc3
sudo chown myuser:myuser /mnt/sdc3
sudo mount /mnt/sdc3

```

Those chown command acted only on the sdc3 folder, not any subfolders. If the problem is with ownership, you may need to change the ownership of the subfolders, including the trash bins.

If everything on sdc3 partition can be owned by you, run the following command. Adding the "-R" switch will change all subfolders as well as sdc3.
```
sudo chown -R myuser:myuser /mnt/sdc3
```

The problem remains. :(

---

### Post by drs305 on 2008-10-02
> **Gotterdammerung said:**
> The problem remains. :(

I was able to duplicate your problem and will investigate it further. I believe I solved it by deleting the existing .Trash-1000 folder (1000 is my uid) in that mountpoint (/media/testfolder/.Trash-1000). When I subsequently deleted a file, I was no longer informed it couldn't be moved to Trash and the deleted file went directly into the automatically-created new .Trash-1000 bin. 

So if you have an existing .Trash-1000 folder, try deleting it.

---

### Post by Gotterdammerung on 2008-10-03
> **drs305 said:**
> I was able to duplicate your problem and will investigate it further. I believe I solved it by deleting the existing .Trash-1000 folder (1000 is my uid) in that mountpoint (/media/testfolder/.Trash-1000). When I subsequently deleted a file, I was no longer informed it couldn't be moved to Trash and the deleted file went directly into the automatically-created new .Trash-1000 bin. 

So if you have an existing .Trash-1000 folder, try deleting it.

hooray! it worked! thanks!

:D :D :D :D :D

---

### Post by ItalOz on 2008-11-12
I could not resolve the same issue in this way.
The reason was that, after installing the latest version of Ubuntu the disk was not mounted at the boot with the correct permissions.
When, after boot, I clikked on the icon and the disk was mounted (NTFS disk) the permissiones where set to root and I could not delete a file as user but it was eliminated as only option.
Thus I had to change the fstab to allow the disk to be mounted at boot time.
I followed the guide:
[[COLOR="Blue"]how to fstab[/COLOR]]("http://ubuntuforums.org/showthread.php?&t=283131")

and I added the line
```

/dev/sda4       /mnt/DiskOne     auto    rw,auto,nosuid,uid=1000,fmask=0111,dmask=0000,utf8 0       0
```

to my /etc/fstab

Hope it helps

---

### Post by ItalOz on 2009-01-28
> **ItalOz said:**
> 
I followed the guide:
[[COLOR="Blue"]how to fstab[/COLOR]]("http://ubuntuforums.org/showthread.php?&t=283131")

and I added the line
```

/dev/sda4       /mnt/DiskOne     auto    rw,auto,nosuid,uid=1000,fmask=0111,dmask=0000,utf8 0       0
```

to my /etc/fstab

Hope it helps

that's the way I have actually done it, if you have a NTFS partition it works (worked for me twice on different computers)

edit: I am so sorry I did not realize that it was my post... too much work I reckon! sorry again

---

### Post by claudiohfg on 2009-02-02
> **ItalOz said:**
> that's the way I have actually done it, if you have a NTFS partition it works (worked for me twice on different computers)

edit: I am so sorry I did not realize that it was my post... too much work I reckon! sorry again

yeah, dude, you're working too much. the problem was already solved when you sent your first post. :lolflag:

---

