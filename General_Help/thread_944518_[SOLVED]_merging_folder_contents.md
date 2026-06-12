---
title: "[SOLVED] merging folder contents"
date: 2008-10-11
forum: General Help
---

### Post by cheics on 2008-10-11
I have folders on two different storage devices on my computer fulll of movies.
I am trying to merge the contents of the folders together using symbolic links so that the contents of the two folders will be displayed as one folder.
I can manually make links to all files in the 2 folders in my 'new' folder, but then if i update the contents of one of the folders, the contents of the 'new' folder will not change

I was thinking of setting up a cron job to recreate the links every hour or so; but I believe there must be a way to do it easier, such as:

a) have a job that will occur every time the folder is updated (a watcher??)
b) actually mere the foders with the link command

thanks for the help in advance.
-and i did read the ln man page... but no dice

---

### Post by koenn on 2008-10-11
read the man pages for 'watch' and 'dnotify', they can be set up to watch a directory and execute a command when a file is added. That command could be a script that checks for the newest files, or compares the two directories for missing links, and creates the required links

I can't think of a way that ln, mount, ...,  can make 2 directories look as one

---

### Post by cheics on 2008-10-11
so, i will "dnotify myscript.sh" to do the operation...

where would i put this command to have it run on startup?

---

### Post by koenn on 2008-10-12
/etc/rc.local

---

### Post by cheics on 2008-10-14
for anyone having a similar issue, I ended up using 'mhddfs'

[http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/]("http://debaday.debian.net/2008/05/25/mhddfs-join-several-real-filesystems-together-to-form-a-single-larger-one/")

works in ubuntu 8.04 32 bit

---

