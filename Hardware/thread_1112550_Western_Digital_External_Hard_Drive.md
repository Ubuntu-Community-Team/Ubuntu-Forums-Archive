---
title: "Western Digital External Hard Drive"
date: 2009-03-31
forum: Hardware
---

### Post by mysteriousdarren on 2009-03-31
I recently changed used gparted to change the format to ext3 to store larger files than 4gbs on it, and it tells me that I can not change anything since I am not the owner. I was wondering if I could do anything to change this. Its a big problem since I put all the info back on my computer and the hard drive is almost full. I would appreciate any help this this. thanks

---

### Post by drs305 on 2009-03-31
Change ownership of the mount point of the drive to yourself. Make sure you type the command correctly, an extra space with a sudo command can ruin your day!

```

sudo chown -R yourusername: /media/the.mountpoint

```
Example: sudo chown -R john: /media/mydata

Since it's an external, you shouldn't have to do anything to mount it. Just find the correct mount point/folder, probably in /media.

---

### Post by mysteriousdarren on 2009-04-01
I put in sudo chown -R kevin: /media/disk which is correct. I went in to put somethings in the folder, and it did not change anything. I was wondering what else I could do?

---

### Post by drs305 on 2009-04-01
Would you post the results of these commands with the drive mounted (on *[COLOR="Navy"]disk[/COLOR]* or change to current mount point):
```

ls -la /media/disk
df -Th | grep 'disk'
cd ~/Desktop
cp ~/Desktop/anyfile /media/disk  # choose any file and report the error message

```

---

### Post by mysteriousdarren on 2009-04-02
Here are the results.

kevin@Wizard:~$ ls -la /media/disk
total 24
drwxr-xr-x 3 kevin kevin  4096 2009-03-26 11:02 .
drwxr-xr-x 5 root  root   4096 2009-04-02 03:13 ..
drwx------ 2 kevin kevin 16384 2009-03-26 11:02 lost+found
kevin@Wizard:~$ df -Th | grep 'disk'
/dev/sdb1     ext3    463G  199M  439G   1% /media/disk
kevin@Wizard:~$ cd ~/Desktop
kevin@Wizard:~/Desktop$ cp ~/Desktop/anyfile /media/disk  # choose any file and report the error message

---

