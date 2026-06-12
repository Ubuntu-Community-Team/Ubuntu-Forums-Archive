---
title: "/home/user does not appear"
date: 2008-08-22
forum: General Help
---

### Post by scottbrank on 2008-08-22
Hi there, 

I trying to configure Jdeveloper on my ubuntu and it has to HAVE an user called oracle...
well, i create the user with the command: /usr/sbin/useradd -g oinstall -G dba,oper oracle
while having added the groups with the commands:
/usr/sbin/groupadd oinstall
/usr/sbin/groupadd dba
/usr/sbin/groupadd oper 

well, then, I got to open the .bash_properties to edit some properties, but the folder /home/oracle isn't there.

Does anybody knows whats going on?!

thanks in advance

---

### Post by aloshbennett on 2008-08-22
Can you see how things look from under System -> Administration -> Users and Groups?

Btw, you dont need oracle user to use JDeveloper. Unless, you have an Oracle Application Server or db installed.

---

### Post by koenn on 2008-08-22
with useradd, you have to give the -m option to create a homedirectory.

with adduser, this is done automatically (it's a userfirendly wrap around useradd)

type useradd in a shell to see the options


you can manually create the home dirs (mkdir); you have to make sure that the are owned by the user (chown user:group ... ) and that the user has rwx
(chmod 750)

---

