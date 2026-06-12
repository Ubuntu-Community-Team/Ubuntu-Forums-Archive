---
title: "Access denide for root@localhost"
date: 2008-09-28
forum: General Help
---

### Post by dreambox on 2008-09-28
This is my first post to this community so be nice to me:D
I dont know where to post but i have 3 questions.

1.I get access denide on phpmyadmin saying #1045 - Access denied for user 'root'@'localhost' (using password: YES) all the users gets the same.
2.I get access denide also when in use putty for the root account.
3.We have a backupscript which makes backups for all the databases and was working when we was using debian but we get access denide there too.Thats for the root account by the way

---

### Post by jigsaws on 2008-09-28
Please, be more specific. 

Have you had a MySQL migration from Debian to Ubuntu? How? 
Do you know root password for the database?
What does it mean "when in use putty"? What are you doing?
Do you have any content in the database? 
Have you set root password for MySQL?

---

### Post by ju2wheels on 2008-09-28
Try using your machine name instead of localhost for the domain and see if that helps, also try 127.0.0.1 and your regular IP on the current network if it is Static, and the domain name of the Static IP if it is tied to one. 

If you are sure you have the correct password for the root account then the issue is the domain you are using to log in because MySQL sets permissions based on the domain you use to login.

---

### Post by dreambox on 2008-09-28
> **jigsaws said:**
> Please, be more specific. 

Have you had a MySQL migration from Debian to Ubuntu? How? 
Do you know root password for the database?
What does it mean "when in use putty"? What are you doing?
Do you have any content in the database? 
Have you set root password for MySQL?


Yes we have an migration from debian to ubuntu, but the root password is the same no changes there.We are going to try to change localhost to ip or machinename wich is xeon.Will be back later to post

---

### Post by p_quarles on 2008-09-28
Okay, first of all, the error message you are getting is about the MySQL root account, not the system's root account. These are two entirely separate things. You may know that, but it's not clear from what you have written.

Second, the error messages with no context are not helpful. Please describe (cut and paste text, or post screenshots, preferably) exactly what you were attempting to do when you get these errors. That way people will be able to identify the cause of those errors and possibly a solution.

---

