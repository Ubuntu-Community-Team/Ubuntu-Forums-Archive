---
title: "How to automatically mount a partition at a particular point"
date: 2009-07-07
forum: Hardware
---

### Post by codingfreak on 2009-07-07
Hi

I am a newbie in terms of knowledge in Linux. I had some problem regarding mounting the partitions when the system is restarted.

```
# df -hT
Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/sda8     ext3     26G   11G   14G  46% /
/dev/sda6     ext3     99M   12M   83M  13% /boot
tmpfs        tmpfs    506M   48K  506M   1% /dev/shm
gvfs-fuse-daemon
fuse.gvfs-fuse-daemon     26G   11G   14G  46% /root/.gvfs
/dev/sda1  fuseblk     40G   15G   25G  37% /media/disk
/dev/sda5     ext3    9.7G  2.7G  7.0G  28% /media/disk-1
```Actually the partition /dev/sda5 was a NTFS. Because of space constraints I have formatted and made it as EXT3. The path for this partition according to above information is "**/media/disk-1**".

Sometimes when I restart the server the path gets changed into "**/media/disk**" as a result I am facing some problems. I came to know that we have to change it in "**/etc/fstab**"

But I really dont know how to do that ... 

Can anyone help me in "**How to automatically mount a partition at a particular location everytime when the server gets restarted**".

```
$ cat /etc/fstab
UUID=870366ad-d6fb-4b95-9e38-ccf884ba94fc /                       ext3    defaults        1 1
UUID=4ce91995-8ff7-45f4-8d4f-d6fe28d4f9bc /boot                   ext3    defaults        1 2
tmpfs                   /dev/shm                tmpfs   defaults        0 0
devpts                  /dev/pts                devpts  gid=5,mode=620  0 0
sysfs                   /sys                    sysfs   defaults        0 0
proc                    /proc                   proc    defaults        0 0
UUID=ca924ce7-db9d-492e-bc78-b46d928b0d2d swap                    swap    defaults        0 0

```

---

### Post by bernied on 2009-07-08
You need to:
- choose (and possibly create) a mountpoint, something like this:
```
sudo mkdir /media/mypartition
```(change the 'mypartition' to something sensible)

- add an entry in /etc/fstab, something like this:
```
/dev/sda5 /media/mypartition ext3 defaults 1 2
```(change the 'mypartition' to what you used as the mountpoint above)

To test it, try this:
```
sudo umount /dev/sda5
sudo mount -a
```

See the man pages for details:
```
man fstab
man mount
```

Hope this helps
Bernie

---

### Post by codingfreak on 2009-07-09
That really worked without any problems ...... Thank you

---

### Post by theozzlives on 2009-07-09
> **codingfreak said:**
> That really worked without any problems ...... Thank you

You don't have to make your mount point in /media. if you want it just for your eyes you can do /home/user/mypartition. Just a little FYI.

---

### Post by codingfreak on 2009-07-09
Thanks for the reply

---

