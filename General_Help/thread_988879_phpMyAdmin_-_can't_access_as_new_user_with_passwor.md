---
title: "phpMyAdmin - can't access as new user with password"
date: 2008-11-21
forum: General Help
---

### Post by 5circles on 2008-11-21
Apologies for posting here, but I can't find a phpMyAdmin forum, and I'm using standard 8.04 packages.

I installed phpMyAdmin.  Then set up a new user.  I can login to phpMyAdmin if the user doesn't have a password, but when I set the password and try to login I get:

```
#1045 - Access denied for user 'USER'@'localhost' (using password: YES)
```

I'm sure I'm just doing something very dumb.

Thanks
Mike

---

### Post by iaculallad on 2008-11-21
From what I know, both MySQL and phpMyadmin use a single user called root: You could try changing the password using the terminal:

```
$ mysql -u root
mysql> UPDATE mysql.user SET Password=PASSWORD('yourpassword') WHERE
User='root';
mysql> FLUSH PRIVILEGES;
mysql> quit
```

---

### Post by 5circles on 2008-11-21
Sorry - I guess I wasn't being clear.

The root MySQL user works fine through phpMyAdmin with a password.

But when I created a new regular user and tried to set the password, I couldn't log in as the new user through phpMyAdmin.  When I made the user 'no password' I was able to login.

Your post made me wonder, so I checked with the command line instead.  Its the same, so I guess the problem is with MySQL not phpMyAdmin.

---

### Post by iaculallad on 2008-11-21
Append **@localhost** with the user name that you had created and try setting the password. Retry logging on phpmyadmin if it works.

> username@localhost

---

### Post by 5circles on 2008-11-21
I don't understand.  

Are you suggesting logging on with mysql -u username@localhost?  

Or with phpMyAdmin doing the same?

I think localhost is a red herring.   The user is set up for host = %, and I get the same results when accessing phpMyadmin either locally or across the LAN.  I tried with mysql too.  The only difference from before is that the error message is now user 'user@localhost'@'localhost'

But thanks

---

### Post by JasonDFR on 2008-11-29
I am having the same or a very similar problem.

I installed LAMP on ubuntu 8.10 with no problems.

I installed phpmyadmin with no problems. root user has a password and can log in successfully to phpmyadmin with all privileges. This user was created during the mysql setup.

I used phpmyadmin while logged in as the root user to create a new user and assigned a password.

When logged into phpmyadmin as the root user, the new user shows up under privileges.

I cannot log into phpmyadmin with the new user I created.

I cannot log into mysql via the terminal with the new user I created.

Terminal Error:

ERROR 1045 (28000): Access denied for user 'jasondeb_jason'@'localhost' (using password: YES)

Any ideas?

Thanks a lot!

Jason

---

### Post by JasonDFR on 2008-11-29
More Info:

The user I created shows up in MySQL administrator, but I cannot log in to phpmyadmin or mysql with this user.

Also, in MySQL Administrator I cannot stop the server with user root. When I enter the root user's password to stop the server, an "Invalid Password" error message is displayed.

Thanks again!

And if there is a better place to post questions such as these, please let me know.

Cheers,

Jason

---

### Post by JasonDFR on 2008-11-29
I found a solution.

The user I had created had access on host: %

I created copied this user two times, each time changing host to "localhost" and "127.0.0.1" respectively.

Now everything is working as I would expect it to.

Is this the normal and most appropriate way to create users?

Thanks a lot!

Jason

---

### Post by 5circles on 2008-11-29
Jason, thanks for working through this issue.  I thought that I'd replied earlier, but apparently not.  I found the same thing - that having localhost set as the host worked when setting up users.  I don't quite get it, but I'm far from an expert at phpMyAdmin or mysql.

mike

---

### Post by vanyrow on 2009-03-16
i don't understand,what can i do???????

---

