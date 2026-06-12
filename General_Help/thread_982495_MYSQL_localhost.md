---
title: "MYSQL localhost?"
date: 2008-11-14
forum: General Help
---

### Post by quikone8 on 2008-11-14
I am trying to setup mysql.  It doesn't seem to like localhost.  I am running a Citadel mail server that is using 127.0.0.1  When I set up mysql can I set it to use something other than 127.0.0.1 and localhost and if so how do I change the conf file to reflect that?

---

### Post by GepettoBR on 2008-11-14
You need to use 127.0.0.1 or localhost if you plan on storing the database locally. What exactly is going wrong?

---

### Post by quikone8 on 2008-11-14
> **GepettoBR said:**
> You need to use 127.0.0.1 or localhost if you plan on storing the database locally. What exactly is going wrong?

I am probably doing something wrong, but it won't let me do anything, I can't build a new database or change password.  I am not in front of the server right now but when I am there again I will paste what it says.  I have even tried to do something in webmin, but it won't let me do anything in localhost, could it be that it is not properly configured?

---

### Post by quikone8 on 2008-11-15
Is it possible to run mysql and citadel along side eachother?  The reason I ask is; don't both of them wnat to use localhost and 127.0.0.1?  If thats the case how do I get around that problem or is it okay?  I noticed if I want to get into 127.0.0.1 it goes to citadel and if I try localhost I get the following browser error;

 

Failed to Connect

       
       

         

Firefox can't establish a connection to the server at [www.localhost.com](www.localhost.com).
 


       
       

Though the site seems valid, the browser was unable to establish a connection.

    * Could the site be temporarily unavailable? Try again later.
    * Are you unable to browse other sites?  Check the computer's network connection.
    * Is your computer or network protected by a firewall or proxy? Incorrect settings can interfere with Web browsing.

---

### Post by GepettoBR on 2008-11-15
"localhost" is to "127.0.0.1" like "www.google.com" is to Google's server's IP, whatever it is. They are the exact same thing. Localhost is your computer, and many services run web interfaces that you can access via localhost. Unless both services are running on the same port, they shouldn't interfere with each other.

For example, directing your browser to [http://127.0.0.1:631/](http://127.0.0.1:631/) or to [http://localhost:631/](http://localhost:631/) should both take you to the CUPS web interface. That means you're accessing an internal service at port 631.

---

### Post by quikone8 on 2008-11-15
Okay, that makes sense.  When I try to create a database I get the following, any ideas?
DBI connect failed : Access denied for user ''@'localhost' to database 'mysql'

---

### Post by GepettoBR on 2008-11-16
Try specifying the user you want to use by appending -u USERNAME to your command.

---

