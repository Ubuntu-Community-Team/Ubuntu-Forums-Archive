---
title: "TV Card / Mythtv"
date: 2005-06-21
forum: Hardware &amp; Laptops
---

### Post by Dave_is_sexy on 2005-06-21
```
dave@D5:~$ mythtv
2005-06-21 22:24:33.759 Switching to square mode ()
2005-06-21 22:24:33.766 Unable to connect to database!
2005-06-21 22:24:33.766 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-21 22:24:33.767 Switching to square mode (blue)
Segmentation fault
dave@D5:~$
```

This leads me to believe my TV card doesn't work? This is going to be hard isn't it?

---

### Post by mad_alfred on 2005-06-21
[QUOTE=Dave_is_sexy]```
dave@D5:~$ mythtv
2005-06-21 22:24:33.759 Switching to square mode ()
2005-06-21 22:24:33.766 Unable to connect to database!
2005-06-21 22:24:33.766 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-21 22:24:33.767 Switching to square mode (blue)
Segmentation fault
dave@D5:~$
```

This leads me to believe my TV card doesn't work? This is going to be hard isn't it?[/QUOTE]
 i got the same message...i'm using a skystar2 DVB card :(

---

### Post by Dave_is_sexy on 2005-06-21
I'm using a Medion TV card that no-one will have heard of, but it's a standard Philips chipset

---

### Post by Drain on 2005-06-22
[QUOTE=Dave_is_sexy]```
dave@D5:~$ mythtv
2005-06-21 22:24:33.759 Switching to square mode ()
2005-06-21 22:24:33.766 Unable to connect to database!
2005-06-21 22:24:33.766 Driver error was [1/1045]:
QMYSQL3: Unable to connect
Database error was:
Access denied for user: 'mythtv@localhost' (Using password: YES)

couldn't open db
2005-06-21 22:24:33.767 Switching to square mode (blue)
Segmentation fault
dave@D5:~$
```

This leads me to believe my TV card doesn't work? This is going to be hard isn't it?[/QUOTE]

Mythtv is going to be hard a lot of the time. When it gets to be a .7 release instead of a .17 release (or even a 1.0 release! what a dream!) , maybe then the install gets easy. ;-)

First, let me make a suggestion - download and try tvtime first ("sudo apt-get install tvtime" should work, I believe), and perhaps that will give you a better idea of whether or not the tv-card is auto-detected and working. And just having some tv at all makes the process a little less frustrating. :-) (By the way, what kind of card is it?) 

Second, let's look at the error message again. It says in 4 places that it is unable to connect to the MySQL database, with the "unable to connect", "Database error", and "couldn't open database" lines. So it doesn't look like it's a problem with the tv-card (a good thing), but it means that there is some other troubleshooting you need to work on (not a good thing). These are problems that can be solved by going through the documentation and searching on the web. [www.mythtv.org](www.mythtv.org) and [http://www.cs.rit.edu/~css8044/?q=mythtv](http://www.cs.rit.edu/~css8044/?q=mythtv) should be able to help you further and get you closer to where you want to be.

---

### Post by Dave_is_sexy on 2005-06-23
Good plan! WOW I have tv on linux already!

..this is so good. OK, so my tv card is fine!  :smile: 

```
root@D5:/home/dave #  sudo mysql -u root mysql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
root@D5:/home/dave #

```

---

### Post by desdinova on 2005-06-23
[QUOTE=Dave_is_sexy]Good plan! WOW I have tv on linux already!

..this is so good. OK, so my tv card is fine!  :smile: 

```
root@D5:/home/dave #  sudo mysql -u root mysql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
root@D5:/home/dave #

```[/QUOTE]

Did you setup the mysql root passwd?

[http://www.netadmintools.com/art90.html](http://www.netadmintools.com/art90.html)

---

### Post by Dave_is_sexy on 2005-06-23
Yeah I did. It's the same as the root password

---

### Post by desdinova on 2005-06-23
How did you do it - did you use mysqlcc the mysql control centre?

---

### Post by Dave_is_sexy on 2005-06-23
No, as far as i'm concerned i don't have my SQL> it must've come as a dependancy for mythtv. I typed a command line for it, but i've forgotton what cos i've been locked out for 2 days (fight to the death thread)

Can i install some kind of presence so i get a control panel?

---

### Post by desdinova on 2005-06-23
IIRC you will have mysqlcc as a gui tool for configuring it - though if you didn't set explicity a root password for MYSqyl its "" by default (blank) - try putting in a blank password with that line you just did

---

### Post by Drain on 2005-06-23
```
root@D5:/home/dave #  sudo mysql -u root mysql
ERROR 1045: Access denied for user: 'root@localhost' (Using password: NO)
root@D5:/home/dave #
```

Shouldn't that be # mysql -u root **-p** mysql ? 
(then it prompts you for a password) 

It's all about the little details. ;-)

You can drop the "sudo" from that line, I think. When your command line prompt ends in "#" it means you're the root user anyway. When it ends in "$", then you're a regular user and will have to use "sudo" in front of some commands. And at least on my setup, mysql doesn't require sudo. 

Once you can log into mysql, type \s to see the status, and then you can go back to the documentation and find out how to list databases, create databases, and give the mythtv user access to those databases.

---

### Post by Dave_is_sexy on 2005-06-23
It doesn't bother asking for the pasword, it just assumes it's wrong  [-X  lol

YAY. ok, adding a p asks for a password and i accepted it ^_^ ...on to level 2

---

