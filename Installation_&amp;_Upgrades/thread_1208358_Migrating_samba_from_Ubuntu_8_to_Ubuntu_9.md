---
title: "Migrating samba from Ubuntu 8 to Ubuntu 9"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by konichiwa13 on 2009-07-09
I wonder where shall I ask this. But, I think I'm gonna start here
Well, few days ago i set up a system with the Ubuntu 9.04 which I have downloaded and installed Samba to.
I actually tried to clone the Samba file server from Ubuntu 8.04 that has Samba 3.0.28 to the new platform here.
New Samba, New OS. 
Use Old Samba configurations
old, unix group, old unix users, old samba passwords
That was what I tried to accomplished
Can't really finish up everything smoothly..
Any guide for it already?
It seems like I "HAD" unix user but no unix password in my OLD system
The unix are stored in smbpasswd only
Any idea?Tools? SWAT?

---

### Post by konichiwa13 on 2009-07-09
I would like to know, what changes would have possibly affect my upgrade here.
What could have possible gone wrong
First try was to copy smbpasswd,smbusers(empty),smb.conf, passwd(in /etc),groups(in /etc) , performed pwcon and grpconv 
It works fine. But I can't change any password
And, it seems like I can't sync unix and samba users using Webmin
I'm using webmin 1.480
I tried to change using Webmin at "System>Change Passwords"
It results Password changed successfully but it never really did.
So that confuses me. 
Found that my Samba user list is shown as empty..
So I tried to convert Unix users to Samba users
Errors I get,
```
add_smbfilepwd_entry: entry with name nobody already exists
```
Something like that.
Sorry for the mess here :???:

---

### Post by konichiwa13 on 2009-07-09
Oh, I'm using Samba 3.4.0

---

### Post by konichiwa13 on 2009-07-09
any help?

---

### Post by konichiwa13 on 2009-07-10
it appears that the samba 3.4.0 caused my error here..
samba 3.4.0 uses tdbsam and has smbpasswd disabled somehow?
testing it again

---

