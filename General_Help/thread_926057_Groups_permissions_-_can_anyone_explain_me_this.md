---
title: "Groups permissions - can anyone explain me this?"
date: 2008-09-21
forum: General Help
---

### Post by eti.que on 2008-09-21
Hello all,

I am a bit puzzled. I have a folder /raid5 the following subfolders:
> drwxrwxr-x  7 root     root   4096 2008-09-20 17:47 .
drwxr-xr-x 23 root     root   4096 2008-09-16 19:09 ..
drwxrwx---  2 root     users  4096 2008-09-16 22:07 Downloads
drwxrwx---  2 root     users 16384 2008-09-16 21:51 lost+found
drwxrwx---  5 root     users  4096 2008-09-20 19:39 Musique
drwxrwx---  3 mldonkey users  4096 2008-09-21 20:50 P2P
drwxrwx---  7 root     users  4096 2008-09-16 22:14 Vidéos


My main user, called etique, belongs to the "users" group, among others.
> etique@server:~$ groups etique
etique adm dialout cdrom floppy audio dip video plugdev fuse lpadmin admin sambashare users

Though, when I try to cd to any of the subfolders, I get this:
> etique@server:~$ cd /raid5/Vidéos
-bash: cd: /raid5/Vidéos: Permission denied


Am I missing something in the groups management?

Thanks a lot in advance!
Etique

---

### Post by cmnorton on 2008-09-21
What's the output of ls -ld /raid5?

You should have group execute on /raid5.

---

### Post by eti.que on 2008-09-21
Hi,

I do have them :(

> etique@server:~$ ls -ld /raid5
drwxrwxr-x 7 root root 4096 2008-09-20 17:47 /raid5


I know I can have access in other ways, I just want to know why it doesn't work in that case.

Thanks!

---

### Post by unutbu on 2008-09-21
I don't know the answer, but I'm curious:
```

etique@server:~$ cd /raid5/Vidéos
-bash: cd: /raid5/Vidéos: Permission denied
```

Is there really a dash at the beginning of the error message above?

Also, can you "cd /raid5/Musique" or do you get the same kind of error?

---

### Post by eti.que on 2008-09-21
There is one, indeed.

And yes, no luck with any of the other folders. I also thought it might be due to the accent, but... :(

> etique@server:~$ cd /raid5/Musique
-bash: cd: /raid5/Musique: Permission denied


---

### Post by The Cog on 2008-09-21
Just fishing, but a couple of questions:

Can you get there in steps? I.e.:
[B]cd \raid5
cd musique[/B]

That - in front of bash worries me. What is the output of
**ps -u etique**
? Is it running bash or -bash?

---

### Post by eti.que on 2008-09-22
Hello,

I can access /raid5

But then I cannot access Musique from raid5.

As of ps -u etique:
> etique@server:~$ ps -u etique
  PID TTY          TIME CMD
 7905 ?        00:00:00 imapd
 7908 ?        00:00:00 gam_server
 7913 ?        00:00:00 imapd
 7920 ?        00:00:00 imapd
 7923 ?        00:00:00 imapd
 7926 ?        00:00:00 imapd
 8015 ?        00:00:00 imapd
 8018 ?        00:00:00 imapd
 8025 ?        00:00:00 imapd
 8029 ?        00:00:00 sshd
 8030 pts/0    00:00:00 bash
 8046 pts/0    00:00:00 ps


so it's supposed to use bash rather than -bash.

you see anything there ?

Thanks !

---

### Post by The Cog on 2008-09-22
Nah, I don't see anything. I see he is runnng bash. 

Has etique logged out and in again recently? I believe the group membership is only refreshed on login, so his hurrent login might not be aware of his current group membership. The command "id" will list his current group membership.

Also, I wonder if his bash or cd commands are the normal ones. For me, **which bash** prints /bin/bash, and which cd prings nothing (cd is built into bash). 

Otherwise, I am out of ideas.

---

### Post by unutbu on 2008-09-22
eti.que, I still don't know the answer, but perhaps this will give us some more clues:

If you run
```

sudo chmod 777 /raid5/Musique

```
can you then cd /raid5/Musique as a normal user?

(After the test, you can run
sudo chmod 770 /raid5/Musique
to restore the permissions.)

Also, please post the output of 
```

mount
lsattr -d /raid5
lsattr -d /raid5/Musique
```

PS. I don't know much about RAID. Do you think that might have something to do with the problem? I've tested the permissions/ownership setup you have on an ext3 filesystem, and it works as expected -- a user can cd to /raid5/Musique as long as user is a member of the "users" group.

---

### Post by eti.que on 2008-09-22
Guys,

Thank you all for your interest. I kinda feel very bad now :s

But I'm authenticating against ldap. I've created the users group using the smbldap-groupadd tool, and I guess something went wrong (though I'm not sure what it is).

Using another group to which belongs etique, it worked as intended. I'll investigate in that way.

Sorry for bugging :/

Thanks again for your support guys.

---

### Post by koenn on 2008-09-22
to test :
change the **group** on one of those directories to 'etique" and see if the user etique has access then.

---

### Post by eti.que on 2008-09-22
Guys,

I actually made some progress. Not sure it is related to the ldap auth anymore.

Here is what I noticed:
the "users" group etique is in has a gid of 1001:
> etique@server:/raid5$ id
uid=1000(etique) gid=1000(etique) groups=4(adm),20(dialout),24(cdrom),25(floppy),29(audio),30(dip),44(video),46(plugdev),107(fuse),111(lpadmin),112(admin),117(sambashare),1000(etique),1001(users)


If I do this:
> 
etique@server:/raid5$ sudo chgrp users Vidéos
etique@server:/raid5$ cd Vidéos
-bash: cd: Vidéos: Permission denied


but if I do this:
> etique@server:/raid5$ sudo chgrp 1001 Vidéos
etique@server:/raid5$ cd Vidéos
etique@server:/raid5/Vidéos$ 


Do I miss something?

Thanks a lot !
Etique

---

### Post by eti.que on 2008-09-22
and now the funny thing:
> etique@server:/raid5$ sudo chgrp 1001 Vidéos
etique@server:/raid5$ ls -all
total 40
[...]
drwxrwx---  7 root     users  4096 2008-09-16 22:14 Vidéos


> etique@server:/raid5$ sudo chgrp users Vidéos
etique@server:/raid5$ ls -all
total 40
[...]
drwxrwx---  7 root     users  4096 2008-09-16 22:14 Vidéos


:confused:

---

### Post by unutbu on 2008-09-22
Look inside /etc/group.
On a default Ubuntu system, you should find
```

users:x:100:
```
So users normally has GID 100.
Could it be that you have "users" defined twice, once as GID 100 and once as GID 1001?
If so, perhaps you should edit /etc/group and /etc/gshadow and remove the second instance of users.

---

### Post by eti.que on 2008-09-22
Thanks !

Indeed. The group users was defined twice. Once in /etc/group, with gid 100 and one in my ldap database, which had the gid 1001...

Hence all the problems. I modified it with phpldapadmin. Thank you all guys for the support!

I guess I had some troubles with the smbldap-populate thing. I'll look at this.

Regards!

---

