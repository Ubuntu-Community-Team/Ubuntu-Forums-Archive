---
title: "No write access to /home/user/.ICEauthority"
date: 2009-08-29
forum: Installation &amp; Upgrades
---

### Post by Linux Lover on 2009-08-29
I am using Kubuntu 9.04.

While I am going to log into my machine I am getting an error after giving my log in name and password,

[B]
The following installation problem was detected while trying to start KDE:

No write access to '/home/user/.ICEauthority'
KDE unable to start
[/B]

I logged in to console and used the following command,

$ ls -al /home/user/.ICEauthority
-rw------- 1 root root 0 2009-08-28 12:18 /home/user/.ICEauthority

What is the problem? How do I log into my desktop? Please help. I am a newbie.

---

### Post by ptn107 on 2009-08-29
The problem is that it is owned by root instead of the user of the home directory where it resides.  You can fix it this way:
```
sudo chown $USER.$USER /home/user/.ICEauthority
```

For example, mine is:
```
-rw-------  1 phil phil       2736 2009-08-28 23:22 .ICEauthority
```

---

### Post by tal007 on 2009-08-29
See, if you can bring up the system using the Live CD. You may have some supper user administrative tools to manipulate user account. You probably will be able to reset the user password from the administrative tool bar. But, one caution - do  not try to edit or try to change anything without logging on to the system as root(Super User). If you do, it will make the system inoperable. You may have to mount your drive too. I use Unix. Not so familiar with Linux. As a matter of fact, I started using Linux not long ago. 

Also, make sure to check the user read/write privileges. 

rwx  rwx  rwx    user ---------------------------------

---

### Post by Linux Lover on 2009-08-29
> **ptn107 said:**
> The problem is that it is owned by root instead of the user of the home directory where it resides.  You can fix it this way:
```
sudo chown $USER.$USER /home/user/.ICEauthority
```

For example, mine is:
```
-rw-------  1 phil phil       2736 2009-08-28 23:22 .ICEauthority
```

Thank you for your response. I tried and used the following command,

```
sudo chown $user.$user /home/user/.ICEauthority
```

after that I restarted the machine. But again I am facing the same problem. Hope I am missing something. Please help me.

---

### Post by Linux Lover on 2009-08-29
I used ls -al command again, and for your information, it failed to transfer ownership of .ICEauthority from root to user. I don't know why that happened. I can only confirm you that I did not miss sudo in this case. :confused:

---

### Post by Soley on 2009-08-29
> **Linux Lover said:**
> Thank you for your response. I tried and used the following command,

```
sudo chown $user.$user /home/user/.ICEauthority
```

after that I restarted the machine. But again I am facing the same problem. Hope I am missing something. Please help me.

I'm probably wrong on this, but shouldn't it be:

```
sudo chown $user:$user /home/user/.ICEauthority
```

Where the "user" (in /home/user/...) is your username and there's a colon between the two "$user".

So, for example, mine would be:

```
sudo chown $user:$user /home/soley/.ICEauthority
```

I think that's right. I hope. :)

---

### Post by Soley on 2009-08-29
Also, if you can't login to your main account & have to use a livecd, I believe you can also set the name manually.

```
sudo chown soley:soley /home/soley/.ICEauthority
```

I've used that before & it's worked fine.

---

### Post by Linux Lover on 2009-08-29
Hello Soley,


Great feedback............ it worked :):):)

There is no requirement for the $ symbol. So, at last this code worked for me,

```
sudo chown user:user /home/user/.ICEauthority
```

Thank you friend. :)

---

### Post by Linux Lover on 2009-08-29
Thanks all

---

### Post by Soley on 2009-08-29
> **Linux Lover said:**
> Hello Soley,


Great feedback............ it worked :):):)

There is no requirement for the $ symbol. So, at last this code worked for me,

```
sudo chown user:user /home/user/.ICEauthority
```

Thank you friend. :)

I wasn't entirely sure that first one would work, but I was pretty sure the second one would.

Glad to hear you got it working! :D

---

### Post by cblanquer on 2011-02-24
Thanks guys, 
I had the same issue after I disconected my box for a physical reinstallation (just changing USB devices and wires).
Now I am in!:)

Kubuntu 10.10 on Shuttle XS36GT & OCZ-Vertex 2 SSD

---

### Post by billbr on 2012-03-10
I ran into the same problem and, once I figured out that I needed to do a console login, everything worked fine.

I'm am pretty sure that on the day the owner of the .ICEauthority got switched, the only sudo I did was KMyFirewall.  It complained about a compatibility problem, so I exited before doing any updates.  I had some trouble getting the program started and did an "su -" somewhere along the way.  That may have done the deed.

Anyway, Kubuntu is up and running now.

---

### Post by oldos2er on 2012-03-10
Closed, necromancy.

---

