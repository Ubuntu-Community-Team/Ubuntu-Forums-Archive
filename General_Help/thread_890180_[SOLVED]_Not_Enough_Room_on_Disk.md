---
title: "[SOLVED] Not Enough Room on Disk"
date: 2008-08-14
forum: General Help
---

### Post by greenco on 2008-08-14
I am having problems trying to open some movie (wmv) files. I am running Ubuntu 8.04 and I am getting this error message when I try and open one.


There is not enough room on the disk to save /tmp/funny.wmv.part.
Remove unnecessary files from the disk and try again, or try saving in a different location.


What part of the disk do I need to goto, to remove the unnecessary files from?
How do I change the location for saving the files?

thanks

---

### Post by gobbles414 on 2008-08-14
Are you trying to open WMV files from a website, or from your hard drive? What program are you using to open the WMV files? Thanks...

---

### Post by jerome1232 on 2008-08-14
Sounds like your trying to stream them? It's saying your /tmp is full more than likly you just need to delete some stuff from /tmp, can you post the output of df -h?

---

### Post by greenco on 2008-08-15
Here is the results of the df -h command.

coleman@coleman-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G   19G     0 100% /
varrun               1013M   92K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   64K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  974M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             207G   48G  150G  25% /home
overflow              1.0M   40K  984K   4% /tmp
gvfs-fuse-daemon       19G   19G     0 100% /home/coleman/.gvfs
coleman@coleman-desktop:~$ 

If I need to remove files from the /tmp, which ones should I keep?

Thanks

---

### Post by greenco on 2008-08-15
The .wmv files are attachments to emails, that I received. I am using the default MPlayer to view them and it has worked great up until I started getting these messages. This all started after I tried to run the "Simple Backup" module and it failed to make a backup.

---

### Post by plucky on 2008-08-15
> **greenco said:**
> Here is the results of the df -h command.

coleman@coleman-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
[color=red]/dev/sda1              19G   19G     0 100% /[/color]
varrun               1013M   92K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M   64K 1013M   1% /dev
devshm               1013M   12K 1013M   1% /dev/shm
lrm                  1013M   39M  974M   4% /lib/modules/2.6.24-19-generic/volatile
/dev/sda2             207G   48G  150G  25% /home
overflow              1.0M   40K  984K   4% /tmp
gvfs-fuse-daemon       19G   19G     0 100% /home/coleman/.gvfs
coleman@coleman-desktop:~$ 

If I need to remove files from the /tmp, which ones should I keep?

Thanks


Your / partition is full,is the reason you are getting the messages.You need to find what is filling up that partition,possibly the simple backup process is still running.

To clear out some space quickly ```
sudo apt-get clean
```will remove all the downloaded packages you have installed from the archives.

Try this command to look for very large files ```
sudo find / -type f -size +100000k
``` and see what is taking up your disk space.If it find nothing,reduce the 100000 to 75000 and try again.

You could also check the **/var/backup** for the simple backup files,which might be using up the disk space.

Good Luck

---

### Post by greenco on 2008-08-15
plucky, I did not find any large files on my " / " folder. 

I checked the /var folder and I have a "Backup" folder that has 7 items in it and it is using 15.9 GiB. I also have a "Backups" folder that has 12 items in it and it is using 3.0 MB. 

I looked at the system monitor screen and it does not show Simple Backup as running. Is there another way to find what is running?

Thanks

---

### Post by plucky on 2008-08-15
> **greenco said:**
> plucky, I did not find any large files on my " / " folder. 

I checked the /var folder and I have a "Backup" folder that has 7 items in it and it is using 15.9 GiB. I also have a "Backups" folder that has 12 items in it and it is using 3.0 MB. 

I looked at the system monitor screen and it does not show Simple Backup as running. Is there another way to find what is running?

Thanks

I think you will find that simple backup saves its files in "/var/backup",so that 15.9 GB file is your backup and is your problem.

The other folder "/var/backups" should be there so don't delete any files from there.

I haven't used simple backup for a long time,but it did a similar thing when I used it.If you look in "system-monitor" and select view > All processes,it think you might find simple backup is probably still running.

You will need to kill the process before it will allow you the delete the files in /var/backup and you will need to do it with sudo privilege.

Good Luck

---

### Post by greenco on 2008-08-15
When I checked the system monitor (all) it shows everything as sleeping. there is one process that is named "SystemToolsBack" and it is sleeping. It is the only item that looks like a backup program.


The "Backup" folder has one folder in it and it is named :

2008-08-14_14.12.45.816170.coleman-desktop.ful

That folder has 5 files and a folder named :

files.tgz

This folder is the one using all of the space. Can I safely delete it?

---

### Post by greenco on 2008-08-15
I got "BRAVE" and removed the " files.tgz " file and now everything seems to be back to normal!!!

Thanks for everyone's help!

---

