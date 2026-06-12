---
title: "Automatic backup"
date: 2009-05-07
forum: Hardware
---

### Post by mihaicj on 2009-05-07
I'm looking to start a script that does an automatic backup to my external hard disk by using rsync. I have the backup script, it works. I can get it called by udev when I plug in the hard drive but it gets called before gnome mounts the disk. Any ideas?

---

### Post by mihaicj on 2009-05-07
Anybody at all?

---

### Post by applefox on 2009-05-07
Here try this. It is not a script but it is a good program. Simple Backup (sbackup)

---

### Post by mihaicj on 2009-05-07
Thanks, but I need what I said.

---

### Post by applefox on 2009-05-07
Well you need to install a program first. If you want it to be comand line then install rsync.
The most basic way to use rsync is like this (command goes into the terminal): 
rsync -av /path/to/source/directory /path/to/target/directory
For example, let's say your username is alice and you wanted to back up your home directory to your external hard drive that mounts at /media/usbdrive, you would use the command
rsync -av /home/alice /media/usbdrive
If rsync doesn't seem sophisticated enough for you, you can type 
man rsync
to find more options than just -av. You can also explore rdiff-backup, which allows you to store (and restore) different date-stamped versions of the same file without taking up too much extra space.

---

### Post by mihaicj on 2009-05-07
OK, thanks. Very interesting. But that's not what I asked.

---

### Post by applefox on 2009-05-07
This may be so but my hint to you is that you can't do it with terminal without first installing a program.

---

### Post by mihaicj on 2009-05-07
I have rsync. I think it's installed by default. Thanks again.

---

### Post by applefox on 2009-05-07
Can you not use it? I am not sure of your reasoning behind using a terminal command.

---

### Post by mihaicj on 2009-05-07
applefox, please read what I asked.

---

### Post by applefox on 2009-05-07
I did. I am not sure what is wrong. I am just trying other things. Do you have an error output?

---

### Post by leandromartinez98 on 2009-05-07
> **mihaicj said:**
> I'm looking to start a script that does an automatic backup to my external hard disk by using rsync. I have the backup script, it works. I can get it called by udev when I plug in the hard drive but it gets called before gnome mounts the disk. Any ideas?

What about doing a loop that checks if the drives is mounted? I'm not sure about the details on how to do this in bash, but surely it can be done:

mountpoint=/media/disk
while ( not exist $mountpoint )
   sleep 3  (this waits 3 seconds)
done
rsync...

the exact scripting in bash I don't know, but the idea should work.

---

