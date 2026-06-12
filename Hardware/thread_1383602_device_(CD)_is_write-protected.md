---
title: "device (CD) is write-protected??"
date: 2010-01-17
forum: Hardware
---

### Post by wlraider70 on 2010-01-17
I'm having an issue with my cd/dvd/blu-ray

luke@luke-dell:~$ sudo mount /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only

Any help?

---

### Post by lloyd_b on 2010-01-17
> **wlraider70 said:**
> I'm having an issue with my cd/dvd/blu-ray

luke@luke-dell:~$ sudo mount /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only

Any help?

Er - I don't see what the problem is.  CD's (DVD's, etc) *are* "read-only" discs, so mounting them read-only makes sense.

Are you trying to write to a CD-R?  If so, use the program "Brasero" to build and burn the image to the CD.

Lloyd B.

---

### Post by wlraider70 on 2010-01-17
lol that true.

I'm having an issue keeping the drive mounted.
perhaps that is not why, i was thinking that it was referring to an inability to properly use the drive. 

Regardless, i've gotten this error too, see screen shot

ans it currently is not showing up in the computer.


it seems to work best when i first boot, but it is NOT functioning properly.

---

### Post by wlraider70 on 2010-01-17
maybe some of this will help show the error

```


luke@luke-dell:~$ sudo mount /dev/sr0 /media/cdrom
[sudo] password for luke: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0
luke@luke-dell:~$ cd /
luke@luke-dell:/$ cd media
luke@luke-dell:/media$ cd cdrom0
bash: cd: cdrom0: Permission denied
luke@luke-dell:/media$ sudo cd cdrom0
sudo: cd: command not found
luke@luke-dell:/media$ cd cdrom0
bash: cd: cdrom0: Permission denied



```



or this


```


luke@luke-dell:/media$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              20G  3.6G   16G  19% /
udev                  2.0G  332K  2.0G   1% /dev
none                  2.0G  200K  2.0G   1% /dev/shm
none                  2.0G   88K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/sda6              75G  4.6G   66G   7% /home
/dev/sr0              2.1G  2.1G     0 100% /media/cdrom0
luke@luke-dell:/media$ 




```



another error i get from the GUI says

Unable to mount location

DBus error org.gtk.private.remotevolumemonitor.failed: An operation is already pending

---

### Post by lloyd_b on 2010-01-17
> maybe some of this will help show the error
```
luke@luke-dell:~$ sudo mount /dev/sr0 /media/cdrom
[sudo] password for luke: 
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: /dev/sr0 already mounted or /media/cdrom busy
mount: according to mtab, /dev/sr0 is already mounted on /media/cdrom0
luke@luke-dell:~$ cd /
luke@luke-dell:/$ cd media
luke@luke-dell:/media$ cd cdrom0
bash: cd: cdrom0: Permission denied
luke@luke-dell:/media$ sudo cd cdrom0
sudo: cd: command not found
luke@luke-dell:/media$ cd cdrom0
bash: cd: cdrom0: Permission denied
```

Okay - the mount is failing because "/dev/sr0" is *already* mounted at "/media/cdrom0", but there's a permissions issue that's preventing you from even reading that directory.

For your command line stuff, try this:```
sudo -i
cd /media/cdrom0
ls
```The "sudo -i" will give you a "root shell", making it look like you had logged in as root (your "sudo cd ..." command will not work - at best it would change to that directory, but then immediately exit, which would put you back where you started).

Could you post the output of your "/etc/fstab" file, please?  *Something* is telling it to mount the CD at /media/cdrom0, with very restrictive permissions, and that's the first place to look.

Lloyd B.

---

### Post by wlraider70 on 2010-01-19
here is fstab

```


# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=76c58240-4834-4499-b222-c53717a842a0 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda6 during installation
UUID=5b94d663-cf6a-4508-a145-ac1c7c013613 /home           ext3    defaults        0       2
# swap was on /dev/sda7 during installation
UUID=a6501fdb-6896-48d2-9aa1-b2b92fd8a399 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


```


After you gave me a starting point i started playing with the mount points and such. I have found that.

1. the ubuntu install disk can  Mount and open and copy.

2. A commercial DVD can mount and it allows me to open a video player, but it wont play.  I get error: "could not read from source".

3. my "home made" DVD appears to mount twice automatically, if use mount command i can get to the point of browsing it, but not file opening or transferring.

4. in /media is cdrom, cdrom0. everything seems to mount to cdrom0.

I tried chmod 777 on both cdrom and cdrom0, but i don't think it took.
when i did ls, the colors did not match. I'm assuming the folder color is an indicator of accessibility.



...still stuck



update:

If i run nautilus as root i can access and even view a bit of the files.

---

### Post by wlraider70 on 2010-01-20
bump

---

### Post by wlraider70 on 2010-01-22
i still need the helps...

---

### Post by wlraider70 on 2010-01-23
help me....

---

### Post by crcosmos on 2012-07-06
Basically, what you're talking about is true, and unfortunately I haven't had the success of trying it. But, I did find that if you install xfburner and run it through terminal, it works like a charm. Sometimes your disk might have data on it from a previous config. try - using another clean, blank disk !! !!  !!  !!   !!

Hope your image burning goes well **!>**

---

### Post by coffeecat on 2012-07-06
Old thread closed.

---

