---
title: "Telnet ** please ** Ubuntu 8.10 Server"
date: 2009-04-09
forum: Installation &amp; Upgrades
---

### Post by gbxfan on 2009-04-09
Hello,

I an new to Ubuntu and loaded 8.10 server and have spent a wonderful day trying to get telnet to work and it doesn't. I don't want to hear about SSH, I know its better and its included - I need Telnet, because our clients don't have SSH.

The following package:
sudo apt-get install telnetd

isn't there and there doesn't appear to be any package that has telnetd. what can I do??????? I found a command apt-cache search and I looked for telnet and openbsd and even took out a remarked line so it could look elsewhere (some source file). Can ANYBODY help me and make something as small as Telnet work? I can telnet out of the server which is nice and know for a fact netstat -na | grep :23 that telnet is not loaded (listening for me).

THANKS!!!!! Dale

---

### Post by croto on 2009-04-09
Hi, welcome! I don't have ubuntu, but from experience, it is likely that you need to refresh the repositories database on a fresh install in order to see all available packages. 
I'm sure it is just a couple clicks away. I'd suggest you run Synaptic Package Manager (it's in one of the menus). Also have a look at:
[https://help.ubuntu.com/community/SynapticHowto]("https://help.ubuntu.com/community/SynapticHowto").

My guess is that after you reload the packages list you'll be able to do the apt-get install telnetd. You can also use Synaptic Package Manager for the same task - it is a nice gui to apt-get.

Post your progress! Good luck.

---

### Post by lemuriaX on 2009-04-09
I don't know anything about the telnet server but assuming you don't have a GUI on your server and your connecting to it via SSH -- you can use aptitude to look for packages available -- and it has a search function.

---

### Post by albinootje on 2009-04-09
> **gbxfan said:**
> The following package:
sudo apt-get install telnetd
isn't there and there doesn't appear to be any package that has telnetd.

telnetd is included :
[http://packages.ubuntu.com/search?keywords=telnetd](http://packages.ubuntu.com/search?keywords=telnetd)

You probably didn't enable the Universe repository yet.
See here :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by gbxfan on 2009-04-10
Really appreciate your help. I am not running a GUI. Any ideas on which GUI I should run, how do I find it and start it? Thanks for your time. Dale

---

### Post by gbxfan on 2009-04-10
Mmm. I see your messages of the packages for universe and I have used by VI Editor and uncommented out the lines for universe and I still don't see the telnetd package. When I 'apt-cache search telnet' I get the following results:

TCPD - Wietse Venema TCP Wrapper Utilities
Python - twisted bin Event based framework
Telnet - Telnet client (don't I need server?)
Libss10.9.8 - SSL shared libraries
Python - twisted -core - event based framework
libwrap0 - Weitse Venema's TCP Wrapper library

Sorry, still need a little help. Maybe I should try it from a GUI. Any ideas on which GUI to run, where to get it and start it?

Thanks!!! Dale

---

### Post by kpatz on 2009-04-10
If you edited your /etc/apt/sources.list file to uncomment the universe repository, issue this command to refresh your package list:

```
sudo apt-get update
```

Then you should be able to:

```
sudo apt-get install telnetd
```

---

### Post by lemuriaX on 2009-04-10
> **gbxfan said:**
> Really appreciate your help. I am not running a GUI. Any ideas on which GUI I should run, how do I find it and start it? Thanks for your time. Dale

Most folks would recommend not using a GUI on a server. Aptitude can be nice in that regard because it provides a usable interface through the terminal if you wanted to browse packages available etc. Have you checked out the documentation here?

[https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

Sounds like you've covered this already but you do know telnet is inherently insecure right?

---

