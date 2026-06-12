---
title: "Ubuntu netbook remix 10.04 issues on toshiba nb205"
date: 2010-07-13
forum: Hardware
---

### Post by sorbic on 2010-07-13
Hey guys,

Had a problem today getting remix to work on my new toshiba nb205.

Basically it was booting into a terminal. startx got me into the ordinary ubuntu interface, but networking didn't work.

if I tried running **gdm **it gave me an error like 

```
** (gdm-binary:11778): WARNING **:  Couldn't connect to system 
        bus: Failed to connect  to 
        socket /tmp/gdm-testing/var/run/dbus/system_bus_socket:  No such 
        file or directory 
```

Here's the fix, explanation to follow:

run **dbus-uuidgen --ensure**
if that gives you something like 
```
"/var/lib/dbus/machine-id should consist of 32 hex characters and not 0"
```
then run **dbus-uuidgen **
and copy the resulting string into the file where it says it should be.
Then restart and everything should be hunky dory.

What I think the problem was:

dbus-uuidgen is supposed to be run after install and give you a unique bus ID or something. obviously it wasn't running, and so the stuff that needs to use your bus (graphics, networking, etc.) didn't know where to find it so everything asploded.

I'm not sure if the forum was the right place to post this but could this possibly be looked into? 

Anyway hopefully that solves some people's problems :)

---

### Post by pajarraco on 2010-08-12
Hi, I have a problem with my mini too. but in my case my mini take like 20 min to start. I have installed Ubuntu Lucid Netbook on Toshiba nb205. Any ideas

I fix it

[http://www.uluga.ubuntuforums.org/showthread.php?t=1491379](http://www.uluga.ubuntuforums.org/showthread.php?t=1491379)

---

