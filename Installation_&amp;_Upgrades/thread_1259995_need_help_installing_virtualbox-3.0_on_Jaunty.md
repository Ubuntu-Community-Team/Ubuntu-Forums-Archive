---
title: "need help installing virtualbox-3.0* on Jaunty"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by tr4sh on 2009-09-07
I'm about to install virtalbox3.0* using 
virtualbox-3.0_3.0.4-50677_Ubuntu_jaunty_amd64.deb
but it comes to below result, any idea why? how's the correct way to install my vb?
[INDENT]me@NB:~/partition$ sudo dpkg -i virtualbox-.0_3.0.4-50677_Ubuntu_jaunty_amd64.deb
Selecting previously deselected package virtualbox-3.0.                   
(Reading database ... 160867 files and directories currently installed.)  
Unpacking virtualbox-3.0 (from virtualbox-3.0_3.0.4-50677_Ubuntu_jaunty_amd64.deb) ...                                                              
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend requires a screen at least 13 lines tall and 31columns wide.)
debconf: falling back to frontend: Readline
dpkg: dependency problems prevent configuration of virtualbox-3.0:
 virtualbox-3.0 depends on libcurl3 (>= 7.16.2-1); however:
  Package libcurl3 is not installed.
dpkg: error processing virtualbox-3.0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 virtualbox-3.0
[/INDENT]

---

### Post by crownedzero on 2009-09-07
Have you checked the installation guide for prereqs and dependencies?

[http://www.virtualbox.org/manual/UserManual.html#id2497131](http://www.virtualbox.org/manual/UserManual.html#id2497131)

---

### Post by king EZi on 2009-09-07
you need to install libcurl3

sudo apt-get install libcurl3


Try that. Good luck

---

### Post by hal10000 on 2009-09-07
Why don't add the virtualbox repository to your /etc/apt/sources.list?

```

deb http://download.virtualbox.org/virtualbox/debian jaunty non-free

```
Then,on a command line, do ```
wget -q [http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc](http://download.virtualbox.org/virtualbox/debian/sun_vbox.asc) -O- | sudo apt-key add -
```
and 
> sudo apt-get update
Then you are able to install virtualbox with all it's dependencies with your package manager.

---

