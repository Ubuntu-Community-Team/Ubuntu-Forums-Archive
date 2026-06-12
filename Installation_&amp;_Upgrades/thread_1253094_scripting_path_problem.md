---
title: "scripting path problem?"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by gingoblin on 2009-08-29
Hi I'm having trouble running scripts from a new partition created on a second hard drive. The permissions for the mounted partition are all mine (my single user). When I try to execute a script from a directory in said partition I get:
as user
   bash: ./test.sh: /bin/bash: bad interpreter: Permission denied
as root
   sudo: unable to execute ./test.sh: Permission denied

but if I run the same script out of my user directory. It works fine!
I have no problems running utilities out of /bin in that directory so it can't be pathing

I've tried changing the path and home environment variables to include the directory I'm working in but to no avail. I changed fstab to use the UUID of the partition in mounting no dice.
I've mounted the partition under the filesystem root and as a subdirectory of my user account, no help there. 
                                         stumped gingoblin:confused:

---

### Post by tal007 on 2009-08-29
Check the read, write and execute privilege of your test.sh script. It is probably owned by root. You may have to change its access right to run it in your directory.

rwx rwx rwx   owner etc...

chmod 777 test.sh

Giving permission every one to run it. You can change it to yours later.

./test.sh   in your home directory

---

### Post by gingoblin on 2009-08-29
The permissions for the mount point, directory in which the script resides and the script all belong to me. The script is executable.

---

### Post by tal007 on 2009-08-29
I have done a while ago, can vaguely remember. When you mount a file system on a directory and try to execute a script you also have specify the path in your home directory.

/root
/mnt
/tmp


Let say you have mounted it on /tmp

sudo mount /dev/sda1  /tmp


Then if you want to execute it from /tmp/dev/sda1  you have to ensure that the path is set correctly in your logon profile file. 

PATH:/tmp/dev/sda1/test.sh something like that in you profile file.  

Find out the path where your test.sh script resides. Then set this path in your logon profile file.

---

### Post by tal007 on 2009-08-29
Forgot to mention, you also have to execute the logon profile file
in your home directory for changes to take effect using a command like

./profile

But I don't know exactly what they call this file in Linux.


PATH=/your shell script's path

./profle 

Then try to execute your file.

---

### Post by gingoblin on 2009-08-31
I think I have a workaround for this problem. It seems to work but i can't explain why. If I execute the script via "./"  I get the error. If I execute the script by explicitly invoking bash, as in "bash test.sh" it works! Thanks to all those who assisted me in arriving at a solution.

---

### Post by gingoblin on 2009-09-03
DOH!  When you mount the partition in fstab be sure to mount it "exec"

---

