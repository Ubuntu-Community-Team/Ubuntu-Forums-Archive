---
title: "Can't login: file permissions help!"
date: 2008-11-23
forum: General Help
---

### Post by clintonthegeek on 2008-11-23
Hey everyone,

I went and did a stupid thing on my new Ubuntu installation.

I have a bunch of old files backed up on a secondary ext3 hard drive, and didn't have write-access to any of it. It's mounted on /media/disk, so I just went ahead and recursively changed the permissions to belong to me in username, group, and to be readable by other users. Suddenly, my whole desktop distorts and crashes, and X won't load. When I try to login at TTY1 I get and error saying that it can't cd to "/home/clinton", and then returns to the login prompt!

It looks like thanks to .wine config folder I had backed up, there were symlinks such as* .wine/dosdevices/z: -> / *, or* .wine/dosdevices/h: -> /home/clinton* which may have just recursed into my whole root directory? Does that make sense?

When I do 'ls -la /', it looks like all my folders have the correct permissions: everything belongs to root, and they all have different permissions set (most folders have drwxr-xr-x, . and .. have drw-rw-rw, tmp, lost+found, and some other special stuff have their own).

My home folder belongs to me (clinton:clinton), with drw-rw-rw-.

There are some things on startup that say [failed] instead of [OK] now, but they go to fast to see what they are. Looks like one can't write a log file, and maybe the other is cups?

If I have to just reinstall everything I will because I only started this morning. It'll just be a huge setback. :p

---

### Post by clintonthegeek on 2008-11-23
Update: I ran

find -perm 777

and it looks like so far everything in my /usr/ folder, /sys, /etc, /var, and a few more show up. :P

So I did change the permissions on every file to rwxrwxrwx!

I'm screwed, aren't I?

---

### Post by clintonthegeek on 2008-11-25
Well no one responded.

That's okay, because I just formatted and reinstalled from scratch.


Thanks... anyways? :p

---

### Post by vwvr9 on 2008-11-25
hahaha, looks like you found the simplest solution. As long as your /home is on a seperate partition you should be able to format/install wothout loosing your files

---

