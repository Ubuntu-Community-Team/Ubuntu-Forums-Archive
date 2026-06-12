---
title: "amarok mysql problems"
date: 2008-10-07
forum: General Help
---

### Post by cong06 on 2008-10-07
A while ago I realized the beauty of mysql so I installed it, and have been toying with mysql in Amarok.

It worked flawlessly at home on my home network where the connection was local: 192.168.1.x

Then I moved my desktop server and my laptop (both using mysql to maintain my library across two computers) to the university.
My desktop was able to connect to the server (localhost, so it didn't change, my desktop is the server) and my laptop can connect as well.

The problem is, now that I've moved my computer to the university, my laptop can't "load" the database, or more accurately, the library isn't available to browse.

Whenever mysql fails in amarok it throws an error. Now it's not throwing an error, and so I'm convinced I have permissions set correctly.

A few things that support this:
1) I ran the command:
```
GRANT ALL ON amarok.* TO amarok@<wireless address here> IDENTIFIED BY '<password>'
```
2) I attempted to connect to the host:
```
mysql -h <computername> -u amarok -p
```
and it worked, so I copied that into amarok. Again, no error, simply no connection/viewable library.

Other facts:
1) I switched stuff around on my desktop so that I could figure out how to duplicate things. My desktop was connecting to *localhost*, and my laptop to *[I]computer.university.edu*[/I]. I switched the address on my server to this also, and it failed. However it worked when I switched it to just *computer*. Doing this on my laptop didn't fix the problem, however.
2) I attempted to grant "Super_priv" among other things to the user that was connecting...but then I noticed that that was probably only needed to manually edit mysql.

I think that's everything, I'm sure I forgot something that I tried...

---

### Post by geirha on 2008-10-07
I think it's maybe amarok that doesn't want to share the database. Just to try, create a new database on the same mysql-server, and have the laptop use and populate that one. Does that work?

---

### Post by cong06 on 2008-10-07
> **geirha said:**
> I think it's maybe amarok that doesn't want to share the database. Just to try, create a new database on the same mysql-server, and have the laptop use and populate that one. Does that work?

Oh, like they won't be usable at the same time... (I do remember having it running only on one machine at a time until I got to the university)

I'm trying now.

---

### Post by cong06 on 2008-10-07
Yeah, it seems like that took care of it. I guess there's no work around?

If no one comes up with anything I guess I'll just deal with it (and I could see it being a problem in amarok)

It seems silly that amarok is using a tool that allows multiple connections, but only lets one use it at a time. Maybe I'll make a complaint on the amarok forums also.

---

