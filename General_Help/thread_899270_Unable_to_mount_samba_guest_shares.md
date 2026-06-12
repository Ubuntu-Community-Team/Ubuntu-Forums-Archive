---
title: "Unable to mount samba guest shares"
date: 2008-08-24
forum: General Help
---

### Post by mb_webguy on 2008-08-24
I've been building up a lot of good karma on the boards recently, and I think it's time for me to reap some of the rewards...  So, here's my problem.

I've set up some samba shares on two different Ubuntu Hardy systems.  Except for these shares, I'm using the default smb.conf file.  Here are the entries on the machine I'm currently using:```
[Downloads]
	comment = Downloads
	path = /media/Big/Downloads
	read only = No
	guest ok = Yes
	browseable = Yes

[Music]
	comment = Downloads
	path = /media/Big/Music
	guest ok = Yes
	browseable = Yes


```

I'll post the entire contents of the smb.conf files if someone requests it, but I assure you that other than the above entries, they're about as vanilla as they can get. The entries on the other machine are identical, except for the paths.  

When I run testparm, everything looks good.  And I *am* remembering to reload/restart samba, so that's not contributing to the problem.

No matter how I try to access these shares, I get messages saying the share failed to mount or something similar.  I've attached screenshots of the specific error messages in Nautilus and pyNeighborhood.  I can see the machines on the network and can see the shares, but simply can't open them.  On occasion, when I try to access the second machine from the one I'm using now, Nautilus throws a "Couldn't display smb://...  There is no application installed for this file type" message, as shown in the third screenshot.

I can access the local shares using smbclient from the command line, but attempting to access shares on the other computer gives the following output:```
matt@the-tardis:~$ smbclient //ACCESS-MUNDI/Music
Password: 
session setup failed: NT_STATUS_LOGON_FAILURE

```

I can access shares on an XP machine from either Ubuntu machine with no problem, so it's doesn't seem to be any problem with the samba client...  The only differences as far as I can tell is that the shares I can't access are on Ubuntu machines, and shouldn't require a password (whereas the shares on the XP machine required authentication).

Unlike most of the Linux-speaking world, I've never really had many problems with samba, so I'm pretty much stumped at this point.

Any ideas?


EDIT:  I just realized, however, that if I don't enter a password, the above smbclient command works!!!  Frak... this is a bug with samba authentication in Hardy, isn't it?
...
:frown:

---

### Post by mb_webguy on 2008-08-25
Bibbidi-Bobbidi-Bump

---

### Post by kevin79 on 2008-10-29
Did you ever figure this out? I'm having the same issue.

---

### Post by Nepherte on 2008-10-29
Try using the ipaddress of the computer instead of the hostname.

---

