---
title: "[SOLVED] Valid password is denied from locked screen"
date: 2008-10-01
forum: General Help
---

### Post by michaelkahl on 2008-10-01
I've had a couple of strange issues lately.  My .dmrc file (that lists my default session) was corrupted.  It had no owner/group set.  I removed the file, and recreated and everything works fine with that.  Here's the second issue and I wonder if it's related.
Anytime I lock the screen I can't resume my session.  It tells me I'm typing an invalid password.  There is only one problem with this, I'm not typing in the wrong password.  I can ctrl-alt-f2 and login there, or I can hit switch user and can log in there.  I only installed one keyboard, so that shouldn't be an issue.  
I tried activating the root account with sudo passwd, The response told me it was successful, but anytime I try to su over it won't accept the password.  I can do a sudo -i -u root and it works just fine.  
I'm just wondering if any of this points to a central issue.  Any help would be appreciated.

---

### Post by michaelkahl on 2008-10-01
Nothing?

---

### Post by michaelkahl on 2008-10-01
So I'm reading and googling, and this is the only thing I've found.  My /sbin/unix_chkpwd seems to have improper permissions.  Apparently I should get -rwxr-sr-x, but instead I get the following:

shawn@shawn-laptop:~$ ls -l /sbin/unix_chkpwd 
-rwxr-xr-x 1 root shadow 19584 2008-08-22 16:03 /sbin/unix_chkpwd

**SOLVED EDIT:  I figured it out.**

chown root:shadow /sbin/unix_chkpwd
 chmod 2755 /sbin/unix_chkpwd

This has been an all me posting, but I know its kinda difficult and in a fast moving forum.  Hopefully this information helps someone out there.

---

