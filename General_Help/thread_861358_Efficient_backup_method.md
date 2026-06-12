---
title: "Efficient backup method"
date: 2008-07-16
forum: General Help
---

### Post by drmontero on 2008-07-16
I am trying to think of an efficient way to do a weekly backup of a directory tree (say, /docroot/) to a Buffalo Terastation. I have two questions:

1) I am currently using a script which calls upon ncftp to do an entire upload of the directory. However the directory is ~50G and is extremely inefficient as it moves all files regardless of whether they've been updated. My question: Is there a way to have ncftp only upload those files which have been modified? Somewhat like the -u flag for cp.

2) I've tried using fuseftp to mount the Terastation as a userspace filesystem. This allowed me to use the cp command with the u flag, however for some reason it does not allow me to create new directories. I get this error:

> 
root@ronin:~# fuseftp /mnt/SAN/ backup
fuseftp 0.8 - 2005 (c) by Marcus Thiesen <marcus@thiesen.org>
Successfully logged into backup
Backgrounding...
root@ronin:~# cd /mnt/SAN/array1/Backup/
root@ronin:/mnt/SAN/array1/Backup# mkdir test
mkdir: cannot create directory `test': No such file or directory


My question: Is there a way around this. I've searched for quite awhile and haven't found a work around for this bug, just others who have run into this problem....

I'd much rather use rsync to accomplish this job, however I do not believe the Terastation is running an ssh daemon as I am not able to connect to it via rsync. I get the following error:

> 
root@ronin:~# rsync -avz bin/backup.sh admin@backup:array1/Backup/tmp
ssh: connect to host backup port 22: Connection refused
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(434)


Any ideas?

Thanks in advance!
--Dan

---

### Post by drmontero on 2008-07-19
::bump::

---

### Post by drmontero on 2008-07-23
one more, one last -- ::bump::

---

### Post by Titan8990 on 2008-07-23
I don't think you will be able to do anything without being able to add applications such as an SSH server to the machine you are trying to back up to. 

Why can't you or someone else install SSH on the server you are trying to back up to?

---

### Post by drmontero on 2008-07-24
Because it is a NAS. It would seem that with its stock firmware it can only run an ftp server.

-Dan

---

### Post by timcredible on 2008-07-24
well, if you can use nautilus to connect to the nas, then you could use rsync, which can be set to only back up changed files.  or grsync if you need a gui front end for it.  Places->Connect to Server has an ftp option, could try that and see if it creates a mountpoint in /media for your nas so you could use rsync.

---

### Post by drmontero on 2008-07-24
Connecting to an FTP server through Nautilus does not create a mount point in /media, or any other place i've looked....though that would have been nice....

-Dan

---

