---
title: "creating a standardised install"
date: 2005-12-18
forum: Installation &amp; Upgrades
---

### Post by HainjeDAF on 2005-12-18
Hello,

I'm not exactly newbie but I can't come to terms with the following:

I would like to create standardised installation.

Problem
At home I run an Ubuntu server and several clients.
All clients mount the /home directory from the server via NFS so a user will have his personal data present at every client he logs into.

Since the bsic needs on clients are similar, I'd like to standardise installation.
I'm thinking of creating a "MyIdealClient" deb-package which, when installed, will be depending on the desired packages I want to be installed.

First of all:
How do I get the apt tools to generate a list of installed packages?
I think I need this list to generate the dependency list for my
"MyIdealClient".deb package

Second:
could I use such a list to generate instllation template for custom machines?
I have several friends/relatives, whose machines I maintain. THey all
use Debian or Ubuntu. I plan to move everyone to (K)ubuntu but I would like to be capable of reïnstalling their machines in case of hardware failure.

Regards,
marout

---

### Post by greenway on 2005-12-18
No offense, but wouldn't it a lot more easier to just perform a normal install on a client (since this is already a pretty basic install) and then use simple script to set up and configure your NFS client to your specific wishes? This is the way I set up my clients and it works quite ok. Just a suggestion... Not quite sure about your apt question though. Best of luck anyway!

---

### Post by greenway on 2005-12-18
Offtopic:

Al ingesneeuwd...???

---

### Post by mlomker on 2005-12-18
[QUOTE=HainjeDAF]How do I get the apt tools to generate a list of installed packages?[/QUOTE]

Take a [look here.]("http://ubuntuforums.org/showthread.php?p=402461#post402461")

---

