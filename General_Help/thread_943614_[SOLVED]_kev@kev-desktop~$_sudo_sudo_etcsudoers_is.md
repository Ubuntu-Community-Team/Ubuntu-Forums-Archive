---
title: "[SOLVED] kev@kev-desktop:~$ sudo sudo: /etc/sudoers is owned by gid 1005, should be 0"
date: 2008-10-10
forum: General Help
---

### Post by kabooz on 2008-10-10
Hello All,

Since my last reboot i have no access to synaptic and any sudo command as well.

Any command result in: 
kev@kev-desktop:~$ sudo
sudo: /etc/sudoers is owned by gid 1005, should be 0


root as no password, and therefore i can't log in as root to run any commands detailed in previous posts.

Appreciate the effort.

---

### Post by cariboo on 2008-10-10
If you boot up in recovery mode, and select drop to root at the menu you will be running as root. You should be able to repair your problem.

Jim

---

### Post by Titan8990 on 2008-10-10
From the recover console you will want to do the following:


chown root:root /etc/sudoers

---

### Post by kabooz on 2008-10-10
Thnaks titan.
After this command, the message is now:
sudo: /etc/sudoers is owned by gid 1006, should be 0

Smthg i don't get so far

---

### Post by Titan8990 on 2008-10-10
Can you verify that after running the command given that the /etc/sudoers file is in fact owned by root?


And just to make sure, what format is your filesystem in?

---

### Post by kabooz on 2008-10-10
Hey back,
ls - lrt /etc/sudoers
shows root as owner of the file.
permissions are on r only. 
BTW, can i dump or recall commands form recovery mode in normal mode for me to explicitely c&p them?
I'm not sure what you asking about format....
It's hardy heron with a core: 2.6.24-19.

---

### Post by Titan8990 on 2008-10-10
I am talking about the filesystem format (XFS, EXT3, NTFS). 

You can dump commands using the ">" symbol. What this does and redirects standard output (feedback that commands give you) to a file.

For example:

ls -l /etc/sudoers > list.txt

This will put the results of ls -l into the file list.txt in your current directory.

---

### Post by kabooz on 2008-10-10
it's EXT3 on dev/sda1.

---

### Post by Titan8990 on 2008-10-10
Once you have gone back in to normal mode can you verfiy ownership as still being root?

---

### Post by kabooz on 2008-10-10
negative, root has no password. as it can log into recovery mode, i'am unable to connect with this account in normal mode. I have tried to set a pw to root using the appropriate commands ( graphical user interface) but still doesn't work.

Any thought?

---

### Post by kabooz on 2008-10-10
kev@kev-desktop:~$ ls -lrt /etc/sudoers
-r--r----- 1 root root 470 2008-05-28 00:03 /etc/sudoers

sory misunderstanding.

this is the ls output in normal mode

---

### Post by kabooz on 2008-10-10
Did i miss something here? Is there anybody that can give me a hand?
Thx

---

### Post by geirha on 2008-10-10
It's a bit of a mystery why sudo would say that /etc/sudoers is not owned by the root group, when it clearly is. So I'm thinking that there's either a bug in sudo that makes it give incorrect error messages in certain cases, which I doubt, or that the root group does not have gid 0.

Could you give us the output of these commands:
```

grep root /etc/passwd /etc/group
ls -ld /etc $(which sudo)

```

---

### Post by kabooz on 2008-10-10
dear Savior,

Please find enclose.

Note that UID replied from sudo is UID 1006.



kev@kev-desktop:~$ grep root /etc/passwd /etc/group
/etc/passwd:root:x:0:115:root:/root:/bin/bash
/etc/group:root:x:1006:
/etc/group:admin:x:115:kev,root
kev@kev-desktop:~$ ls -ld /etc $(which sudo)
drwxr-xr-x 139 root    0  12288 2008-10-10 20:55 /etc
-rwsr-xr-x   2 root 1005 107872 2008-09-10 20:05 /usr/bin/sudo

---

### Post by geirha on 2008-10-10
Seems we've found the root of your problem. Boot into recovery mode and edit /etc/group and change 1006 to 0 on the line that starts with "root:". Just in case you're unfamiliar with editing files from the console, use nano ```
nano /etc/group
``` Close the editor with ^X (meaning Ctrl+x) then Y when it asks if you want to save, and hit enter when it asks where the file should be saved (which should allready be filled out with /etc/group)

After editing /etc/group, change group-ownership again: ```
chgrp root /etc/sudoers
```
Double check that it now has gid 0 with: ```
ls -ln /etc/sudoers
``` which should show "0 0" where ls -l shows "root root"

---

### Post by kabooz on 2008-10-10
RESOLVED. I will adress a thank you as per my first post resolved within even a greater SLA than i have ever known.

Do you know what happened?
I didn't relally messed with groups and permissions lately.
Anyway a million THX

---

### Post by geirha on 2008-10-10
Glad you got it sorted :)

Hard to say why this happened. It would be prudent to try to figure out what did it. If you did it somehow, then it's just a lesson not to do it again ;), but if you didn't do it, then it's a serious security issue. I'm hoping you did it somehow :). It could've been through the users and groups GUI, and it could've been with adduser, addgroup, groupmod or similar commands. 

See if you've used any such commands lately by looking at your bash history: ```
less ~/.bash_history
``` And possibly also look at /root/.bash_history. Read the man-pages of the commands, e.g. ```
man addgroup
``` and try to figure out what the commands actually did (if you ran any such commands).

As for the users and groups GUI, it does allow you to change the gid of the root group. It would probably be a good idea for that GUI to issue a warning when trying to do that (if it doesn't allready), because changing the uid of the root user or the gid of the root group is a bad idea. Lots of programs will have problems with that.

---

