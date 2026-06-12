---
title: "Scanning only works with the default user"
date: 2009-08-26
forum: Hardware
---

### Post by Kapli on 2009-08-26
Got a multifunctional Canon PIXMA MP160 and I'm running ubuntu 09.04.
Scanning works perfectly with the user I created when I installed ubuntu, however on any other user it does not work. When I try to scan with XSane nothing happens after I click Scan.

Thanks in advance for any help :)

---

### Post by drs305 on 2009-08-26
Take a look at the groups that the first user belongs to by typing "groups" in terminal. Then do the same thing with the other user(s). You can also check in System, Administration, Users & Groups. You may find that the other users don't belong to the necessary group - such as "scanner".

You can add the user to a group with the following command:
```

sudo adduser *username groupname* 
Example:  sudo adduser john scanner

```

---

### Post by Kapli on 2009-08-26
Hm... I can't find any group for scanning..
I have 2 users, kim which is me, the default user, and laila which is my mom.
Here is the output og "groups":
kim adm dialout cdrom plugdev lpadmin admin sambashare
Here is the output of "groups laila":
laila adm dialout fax cdrom floppy tape audio dip video plugdev fuse lpadmin netdev admin sambashare

---

### Post by drs305 on 2009-08-26
*Scanner* was just an example. Since your second user appears to be in the same groups as you this doesn't appear to be the path that will lead to a solution.

You might look to see if you have any scanner configuration files in your /home/kim folders which do not appear in the other user's /home folders.

---

### Post by Kapli on 2009-08-26
Couldn't find anything like that, but I created a new test user and tried to scan, it worked, so I'll just delete my moms user (since its newly created anyway), and recreate it and see if it works then. Thanks for the help btw.

Edit: Yep, works now :D

---

