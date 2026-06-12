---
title: "Cant drag and drop folders onto new 500g hard drive"
date: 2008-08-16
forum: General Help
---

### Post by PsychedelicWonders on 2008-08-16
It wont allow me to drag and drop a file into my new 500g hard drive.

I'm pretty sure it is mounted and formated, but if you guys want me to run a code, just give it to me.

I get the following error...

The folder "old hard drives" cannot be copied because you do not have permissions to create it in the destination.

---

### Post by drs305 on 2008-08-16
What type of formatting does it have? If it's ext3 and you want to own it:
```

sudo chown -R username: /media/*mountpoint*
chmod -R 750 /media/mountpoint

```

Or open nautilus with the following and then move the files:
```

gksu nautilus

```

How is this partition/drive getting mounted?

---

### Post by PsychedelicWonders on 2008-08-16
> **drs305 said:**
> What type of formatting does it have? If it's ext3 and you want to own it:
```

sudo chown -R username: /media/*mountpoint*
chmod -R 750 /media/mountpoint

```

How is this partition/drive getting mounted?

it is ext3, so yeah i did format it.

I believe it is already mounted because I can access it, just cant modify it it seems.

Do you want me to run those two codes?

---

### Post by drs305 on 2008-08-16
Running those two commands will change the mount point ownership to you and will allow you to move the files into the partition. Just change the username and mountpoint to reflect your data.

---

### Post by PsychedelicWonders on 2008-08-16
hmm.  I opened nautilus via the terminal (i dont know where else to find it by the way if you can tell me really quick)

But when i opened the 500g and dragged and dropped the folder that I want to, it seems to be copying the files to that drive.

The way I was trying to do it before was....

There was a 500g icon on my desktop that I tried to drag and drop and that wasnt working.

I also tried to go through places>computer and then drag and drop them to the left and it would not let me.

What was I doing wrong before that now through nautilus I am able to do so?

---

### Post by PsychedelicWonders on 2008-08-16
what is the lost+found folder on my new 500g?

Can I just delete this?

---

### Post by drs305 on 2008-08-16
> **PsychedelicWonders said:**
> hmm.  I opened nautilus via the terminal (i dont know where else to find it by the way if you can tell me really quick)


Places, Home will open nautilus. You can also go to Places, click and drag Home to the panel and release to create a nautilus shortcut there.

The 'lost+found' folder is a system folder where fsck puts fragments when it discovers errors. If you delete it, it will reappear. If it really bugs you, make a text file in the same folder named '.hidden'. Open it with a text editor and add a line: lost+found   Now save and close the file. If you have the hidden option enabled in nautilus, any file or folder listed in hidden will not show up.

As far as why nautilus now works, if you ran the commands I gave you it changed the ownership of the partition/mountpoint from root to you. Before, root owned it and the system will not let you copy anything into anyone else's or root's partition without making changes. You now own the partition/mountpoint, so you can do with it what you want.

---

### Post by PsychedelicWonders on 2008-08-16
> **drs305 said:**
> Running those two commands will change the mount point ownership to you and will allow you to move the files into the partition. Just change the username and mountpoint to reflect your data.

I dont know what part of that code is considered the mount point for me to change the code successfully.

I belive it is mounted, what code can I run for you to show you the mount?

---

### Post by PsychedelicWonders on 2008-08-16
alright so when i try to access the 500g and open some of the files, they all seem to have a red X at the top right and give me this error message when I try to open them...

---

### Post by drs305 on 2008-08-16
I'm a bit confused as to where we are. I thought you were now able to copy everything over after running the commands. 

The mount point is where the partition is showing up in your new drive. It is probably in /media  (for example, /media/disk).

If it is mounted, you can run "mount" and it will show something like the following. The area in bold is the mount point:  
/dev/sda8 on **/media/data** type ext3 (rw,noexec,nosuid,nodev)

For the above example, the commands would be (with your *username*):
sudo chown -R *username*: /media/**data**
chmod -R 750 /media/**data**

---

### Post by PsychedelicWonders on 2008-08-16
So am I.  I see the file, I was able to access all of them until I closed out and tried to reopen.

Now they all have red X's and wont show me the data.

here are my results after running "mount"

psychedelicwonders@JohnnyScience:~$ mount
/dev/sda3 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-19-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/storage type ext3 (rw)
securityfs on /sys/kernel/security type securityfs (rw)
gvfs-fuse-daemon on /home/psychedelicwonders/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=psychedelicwonders)
/dev/sdc2 on /media/Psychedelic Wonders' Data type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
psychedelicwonders@JohnnyScience:~$

---

### Post by PsychedelicWonders on 2008-08-16
> **drs305 said:**
> I'm a bit confused as to where we are. I thought you were now able to copy everything over after running the commands. 

The mount point is where the partition is showing up in your new drive. It is probably in /media  (for example, /media/disk).

If it is mounted, you can run "mount" and it will show something like the following. The area in bold is the mount point:  
/dev/sda8 on **/media/data** type ext3 (rw,noexec,nosuid,nodev)

For the above example, the commands would be (with your *username*):
sudo chown -R *username*: /media/**data**
chmod -R 750 /media/**data**

my results:

psychedelicwonders@JohnnyScience:~$ sudo chown -R psychedelicwonders: /media/data
[sudo] password for psychedelicwonders: 
chown: cannot access `/media/data': No such file or directory
psychedelicwonders@JohnnyScience:~$

---

### Post by drs305 on 2008-08-16
data was just an example. You have to use the *actual* mountpoint.

It appears the new partition is mounted on /media/storage. These commands will make you (psychedelicwonders) the owner of that mountpoint:

```
sudo chown -R psychedelicwonders: /media/storage
chmod -R 750 /media/storage
```

---

### Post by PsychedelicWonders on 2008-08-16
alright thanks, seems to be working properly now.

Why wasnt I the owner to begin with?

What do I do with this lost+found button?

---

### Post by drs305 on 2008-08-16
> **PsychedelicWonders said:**
> alright thanks, seems to be working properly now.

Why wasnt I the owner to begin with?

What do I do with this lost+found button?


New partitions/drives are initially created by the system, so 'root' is the owner since it doesn't know which of possibly many users will be using it.

For the lost+found issue, I assume you mean the 'folder'. Please refer to post #7 about why it is there and how you can hide it.

If you think this issue is resolved, please mark it Solved with the tread tools link at the top right of the original post. (You can mark it Unsolved if something should come back up).

---

### Post by PsychedelicWonders on 2008-08-16
Alright thanks.

One last thing, how do I rename the 500g to whatever I want?

---

### Post by PsychedelicWonders on 2008-08-16
i honestly dont know how to do that lost+found hidden folder thing you said.

What program do I make this initial text file in?  Open office word?

---

### Post by drs305 on 2008-08-16
> **PsychedelicWonders said:**
> Alright thanks.

One last thing, how do I rename the 500g to whatever I want?

```

tune2fs -L <label> /dev/sdb1
sudo blkid

```

Replace **<label>** with the label name you wish. I suggest no spaces. Running 'sudo blkid' should display the new label name.

---

### Post by PsychedelicWonders on 2008-08-16
psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1
[sudo] password for psychedelicwonders: 
umount: /media/storage: device is busy
umount: /media/storage: device is busy
psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1
umount: /media/storage: device is busy
umount: /media/storage: device is busy
psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1

how do I fix?

---

### Post by drs305 on 2008-08-17
> **PsychedelicWonders said:**
> psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1
[sudo] password for psychedelicwonders: 
umount: /media/storage: device is busy
umount: /media/storage: device is busy
psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1
umount: /media/storage: device is busy
umount: /media/storage: device is busy
psychedelicwonders@JohnnyScience:~$ sudo umount /dev/sdb1

how do I fix?

There is no need to 'fix' it in this case. It just means the device is in use - one or more of the files on the partition is being used. You can run the tune2fs command with the partition mounted.

---

