---
title: "Webserver Password database"
date: 2008-10-16
forum: General Help
---

### Post by luke213 on 2008-10-16
So I've been looking around for a little while for a webserver based application that will store passwords for my users. Here is my situation.

In my office(15 users) everyone has a long list of websites they are required to keep logins and passwords for. These are for other companies many of which are a real pain to get a password reset so they used to keep their passwords in an excel spreadsheet(with a password). Which isn't very secure so since I've been doing some of the tech work I've been running an excel sheet in a truecrypt volume so I'm fairly sure it's secure but right now the problem is the way I've been getting the passwords.

 At the moment I modified a simple guestbook php script to be a password manager so they can goto the intranet page(internal only) and enter their username and password when they change it and then I manually go in and move those passwords over to the encrypted file. 

So what I'm looking for is an application thats simple that a user can goto a page on the webserver enter their new information for a website and have the application encrypt the information into a mysql database or something of the sort. That way I can use the database through https rather than having to jump through these other hoops. 

Any help would be much appreciated. And I hope this is the correct location in the forums for this type of question. 

Oh and I've been a long time lurker of these forums and just want to thank you all for the help I've derived from all the posts I've read over the last couple years.

Thanks.

Luke

Should mention I'm running 8.04 on my server but I can go as far as dedicating another machine or a VM to a solution if it requires a different OS/distro.

---

### Post by ju2wheels on 2008-10-16
Im not sure about finding a custom application but if you know php its simple enough to write yourself....

All you need to install is Apache, MySQL and PHP. Create one database to store the website, user name, and password. Use php to pull information from the database to display and when storing it, php has an array of encryption functions you can use...

[http://www.php.net/manual/en/refs.crypto.php](http://www.php.net/manual/en/refs.crypto.php) [Cryptography PHP Extensions]
[http://us3.php.net/manual/en/book.mysql.php](http://us3.php.net/manual/en/book.mysql.php)  [MySQL PHP API]

---

### Post by luke213 on 2008-10-16
I'll have to take a look at those tomorrow, I would say my understanding of php is limited at best;) I do appreciate the links though.

I was hoping for a prefab solution if anyone has any other suggestions.

Thanks again

Luke

---

### Post by firefly2442 on 2008-10-17
I don't know if this is possible or not but another idea might be to use the built in features in Firefox of remembering passwords.  Maybe it would be possible to save this file someplace?  I imagine it's probably locked in some way to prevent people from reading all your website passwords straight away.

---

