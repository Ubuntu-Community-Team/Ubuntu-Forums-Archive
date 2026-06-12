---
title: "I ejected my hd while using ubunto livecd"
date: 2015-04-10
forum: Hardware
---

### Post by crissy2 on 2015-04-10
Hello, i had a problem with my windows 7 so I used a ubuntu livecd to save all my files from my hd to a flash drive but instead of eject my flash drive i ejected my hd, what can i do now to have my hd working again?

---

### Post by Frogs Hair on 2015-04-10
Hello and Welcome

If you are still in Ubuntu , the listed drives in the file manager(left Pane) can be mounted and I'm guessing your referring to dismounting a drive rather than ejecting it. Right clicking the drive in the file manager will display a mount option. If this doesn't apply please provide more information.

---

### Post by crissy2 on 2015-04-10
Thanks for the help.
No i cant see it in the file manager only if i go to Search and clickin Disks the hd appear and says unknow for all  the partitions .

---

### Post by crissy2 on 2015-04-10
says 640 gb block device
partition type. unknow
contents unknow.

---

### Post by Frogs Hair on 2015-04-10
Run the following command in the terminal and copy and paste the output here. 

```
df -h
```

---

### Post by crissy2 on 2015-04-10
I did and nothing appear

 :confused:

---

### Post by crissy2 on 2015-04-10
ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow            2.9G  115M  2.8G   4% /
udev            2.9G  4.0K  2.9G   1% /dev
tmpfs           588M  1.3M  587M   1% /run
/dev/sr0       1003M 1003M     0 100% /cdrom
/dev/loop0      968M  968M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs           2.9G  1.1M  2.9G   1% /tmp
none            5.0M  4.0K  5.0M   1% /run/lock
none            2.9G  428K  2.9G   1% /run/shm
none            100M   56K  100M   1% /run/user
ubuntu@ubuntu:~$

---

### Post by Frogs Hair on 2015-04-10
I don't boot from live disk except for installations so I have to defer to another user with more experience in repair from live disk. Bump the thread as needed 

> says 640 gb block device
partition type. unknow
contents unknow.         

This might be useful: [http://askubuntu.com/questions/186791/how-to-access-files-in-windows-partition-from-ubuntu-live-usb](http://askubuntu.com/questions/186791/how-to-access-files-in-windows-partition-from-ubuntu-live-usb)

---

### Post by user_of_gnomes on 2015-04-11
What's the problem, though? Unless you made alterations to the file system before dismounting it, this operation shouldn't have any effect on the hard drive. 

Did you simply try restarting your computer to see if Windows will boot? Or if it'll automatically re-mount when you load the LiveCD again?

---

