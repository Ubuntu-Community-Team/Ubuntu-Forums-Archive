---
title: "Ubuntu virgin needs a little guidance"
date: 2008-09-20
forum: General Help
---

### Post by bootneck on 2008-09-20
:confused:Well I have just downloaded Ubuntu onto a hard drive and feeling a little excited as I have only used Microsoft OS before and have this PC dual boot with XP Pro. What do I need to do now what is recommended for internet security, what about drivers, I noticed on install that the download searched the PC so will all drivers be downloaded for this OS? ):P All help greatfully received

---

### Post by Monotoko on 2008-09-20
Ubuntu cannot get viruses, thats the beuty of it.

Just dont play with the network management side unless you know what your doing, if you do you will probably end up leaving your OS wide-open to malicious hackers who can then take over your box.

Not too sure about the drivers, i think most hardware is supported by ubuntu, as mine was perfect from the first time i loaded it, didnt need any extra drivers.

---

### Post by Vivaldi Gloria on 2008-09-20
> **bootneck said:**
> internet security,

Just use the noscript extension of firefox. Nothing else is needed.

>  what about drivers,

Drivers are installed automatically (most of the time).

---

### Post by zvacet on 2008-09-20
Ubuntu comes with installed firewall.There is no linux viruses in wild so you don´t have to worry about that.If some of your device need driver and you don´t know how to instll it just ask here.What you can do right now is to go to the **applications>accessories>terminal** and type

```
sudo apt-get install ubuntu-restricted-extras
```

With this command you will install flash,java and other things you need.

---

### Post by Vivaldi Gloria on 2008-09-20
For installing programs use

system menu > admin > synaptic

Also enable restricted and multiverse repositories from the repository settings to get a more complete list. Then click refresh. 

Now you can search and install whatever you want in synaptic. For example search and install

```
ubuntu-restricted-extras
```

which contains java, codecs, and other goodies.

---

### Post by bootneck on 2008-09-20
Thanks every one for being so helpful, n:grin:ice to meet you all):P

---

### Post by Sef on 2008-09-20
Besides Synaptic and the Terminal, you can use Add/Remove to install software, it is usually the easiest way.

Applications > Add/Remove > Show: change to "All Available Applications" > Search: type in extras > check the desktop version you are using > apply changes > apply > close.

>  		Thanks every one for being so helpful, n:grin:ice to meet you all):P 	

If someone is not nice to you, please click on the report button on the bottom left.

---

### Post by mb_webguy on 2008-09-20
For more information about security, check the link in my signature.

As far as drivers, everything for your current setup should have been installed for you.  If you add or change some hardware later on, post to the forum and we can help you with whatever action (if any) needs to be done to get the new hardware working.

---

### Post by bootneck on 2008-09-21
:popcorn:Thanks every one for your input and help to me it is very much appreciated and I am enjoying the site, once again thanks for everything:lolflag:

---

### Post by Zyphrexi on 2008-09-21
btw, in linux drivers are called modules. Granted some hardware manufacturers refer to them as drivers, but if you're looking around in synaptic and see it, that's what it is.

have you tried wine yet? It allows you to run (some) windows programs (and games) under linux.

also if you go to System -> Help and support, it opens up a nice guide for newbies. 

the more you play with linux, the more you'll love it. enjoy.

---

