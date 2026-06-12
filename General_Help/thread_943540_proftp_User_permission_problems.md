---
title: "proftp User permission problems"
date: 2008-10-10
forum: General Help
---

### Post by wizardofshadynook on 2008-10-10
Hello,

My problem is this:  I have installed proftpd and configured it using GPROFTPD.  I created logins in the program (which created system accounts).  I can connect via ftp with any of the accounts but when ever one of these accounts uploads a file the persions to that file have that user set as the owner, the accounts group set to read only and others set to read only.  I would like this to work so that when ever an account uploads to the ftp server the files is read,write,delete for my other users.  Any help with this is badly needed.  I'm not sure what I'm missing.

Help.

Ubuntu 7.10 Server

---

### Post by abhilashm86 on 2008-10-10
try using relative permissions................for user permission do 
sudo chmod u+x filename
else
u can use absolute permissions also,give octal equivalents................

---

