---
title: "upgrade"
date: 2009-05-31
forum: Installation &amp; Upgrades
---

### Post by k5495 on 2009-05-31
I would like to upgrade from 8.04 Hardy Heron to 9.04 

I have read a book that says I can do this when I do my weekly update, but that option is definitely not listed.

How can I do an Update.  Do I have to update to other versions between 8.04  and 9.04

I don't know if I have a firewall active.  How do I find out?

---

### Post by drs305 on 2009-05-31
You must upgrade to 8.10, then to 9.04 if you wish.

You probably don't see the option to upgrade to 8.10 since 8.04 is a Long Term Support and 8.10 is not. However, it can be easily done and is fully supported. Here are the instructions:
[https://help.ubuntu.com/community/IntrepidUpgrades]("https://help.ubuntu.com/community/IntrepidUpgrades")

In the current versions, you get to the firewall settings via System, Administration, Firewall confguration. I will check my Hardy VM to see if it is the same. ADDED: Hardy used the CLI ufw (uncomplicated firewall). A gui firewall was called firestarter. Later versions use gufw, a gui interface to ufw.

You can see if ufw is running with:
```

sudo ufw status

```

---

### Post by LepeKaname on 2009-05-31
> I don't know if I have a firewall active. How do I find out? 

By default Ubuntu uses ufw... type:
```
sudo ufw status
```
And you will know. 

About the upgrade, I usually just change, for example:

In File: /etc/apt/sources.lst

From:
```
deb http://archive.ubuntu.com/ubuntu/ hardy main
```

to: (9.04)
```
deb http://archive.ubuntu.com/ubuntu/ intrepid main         
```
or: (9.10)
```
deb http://archive.ubuntu.com/ubuntu/ jaunty main        
```

And use synaptic or aptitude, update and apply all changes... 

(It is not the conventional way, but I have done that a lot of times without any update problem)

---

