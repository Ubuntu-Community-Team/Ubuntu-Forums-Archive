---
title: "ftp directories and permissions"
date: 2008-08-18
forum: General Help
---

### Post by philosophia on 2008-08-18
I have proftpd + MySQL + TLS/SSL set up, I create virtual users in MySQL and create their home directories in /home/proftpd/username.

I would like ftp users on my system to upload everything to the firewire hard drive attached to my server.  This volume is mounted at /media/My Book.  I've created a directory on this server /media/MyBook/mp3.

Inside of /home/proftpd/username/ I've created a symlink to /media/MyBook/mp3.  When the user connects via their ftp client, they are able to see this symlink, but it is a text file, the user is not able to click the directory to view the files and folders inside /media/MyBook/mp3 .

Any suggestions on how to fix?  Permissions for these directories look like
```

root@bigly:/home/proftp/username# ls -l
total 0
lrwxrwxrwx 1 root root 18 2008-08-18 15:06 mp3 -> /media/MyBook/mp3
root@bigly:/home/proftp/username# ls -l /media
total 168
drwx------ 7 rjm  root 163840 2008-08-18 14:42 MyBook
root@bigly:/var/proftp/username# ls -l /media/MyBook/
total 160
drwx------ 825 rjm root 163840 2008-08-01 12:09 mp3
```

---

