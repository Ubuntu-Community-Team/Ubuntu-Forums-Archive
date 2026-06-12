---
title: "Installing Alien"
date: 2009-10-09
forum: Installation &amp; Upgrades
---

### Post by Beavis111 on 2009-10-09
Hello,

I'm trying to to install Alien .. I use the command:

sudo aptitude install alien

But I get :

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

debhelper libbeecrypt6 librpm4 dpkg-dev rpm alien

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": Yes
Writing extended state information... Done
Err http: //archive.ubuntu.com edgy/main dpkg-dev 1.13.22ubuntu7
404 Not Found
Err http: //archive.ubuntu.com edgy/main debhelper 5.0.37.3ubuntu4
404 Not Found
Err http: //archive.ubuntu.com edgy/main libbeecrypt6 4.1.2-5
404 Not Found
Err http: //archive.ubuntu.com edgy/main librpm4 4.4.1-9.1build1
404 Not Found
Err http: //archive.ubuntu.com edgy/main rpm 4.4.1-9.1build1
404 Not Found

Does this mean the servers are currently down or do I have something misconfigured? Its not the internet connection as I'm sure I'm connected (posting this)..

I also had similar errors when trying to install other applications from "Add/Remove.." and "Synaptic"..

I am using a bit old Ubuntu 6.10 live CD. Thanks in advance..

---

### Post by mac9416 on 2009-10-09
Edgy (6.10) has reached end-of-life, as you can see here: [https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You'll want to upgrade to something more recent.

---

### Post by Beavis111 on 2009-10-15
I got Jaunty and its working fine.. Thanks a lot!

---

