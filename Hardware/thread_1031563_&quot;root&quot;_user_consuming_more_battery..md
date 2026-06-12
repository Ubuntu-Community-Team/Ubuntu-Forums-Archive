---
title: "&quot;root&quot; user consuming more battery."
date: 2009-01-05
forum: Hardware
---

### Post by paragkalra on 2009-01-05
I have a Dell Inspiron 1525 with Ubuntu 8.10 installed on it.

With normal user logged in and battery fully charged, power backup lasts for 1 hour 45 minutes where as with "root" user it's only lasts 1 hour 35 minutes.

Could someone please tell why does "root" user provides less battery backup and where are the remaining 10 minutes going?

---

### Post by pdtpatrick on 2009-01-05
does that mean you are logging into the computer as root at login or are you using a terminal to become root?

---

### Post by paragkalra on 2009-01-05
I am logging into the computer as root at login.

---

### Post by pdtpatrick on 2009-01-05
do you have certain applications that launch when the root user logs in? some application will launch when the root user uses the computer whereas it wont run when you log into the computer because you dont have the rights for the application to run. 

type top in the terminal and do log in as you and do the same and compare the processes to see whats taking up so much processing power. And determine whether u need that process or to kill it :)

---

