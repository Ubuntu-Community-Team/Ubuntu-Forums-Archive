---
title: "Server packages"
date: 2009-01-28
forum: Installation &amp; Upgrades
---

### Post by mut80r on 2009-01-28
I installed Ubuntu Server on my VIA EPIA-M home server. I then proceeded to install linux-image-generic and remove the server kernel (because the VIA C3 does not support PAE and thus wouldn't boot). However, when I attempted an apt-get upgrade today, it wanted to install the server kernel again. Is there a file somewhere containing what distribution this is or something? I already checked /etc/apt/sources.list but that just showed the repositories.

TL,DR: How do I remove -server packages from future upgrades?

EDIT: [http://pastebin.com/f3c861334](http://pastebin.com/f3c861334)
EDIT 2: Manual thread solving.

---

### Post by icheyne on 2009-01-29
Maybe try:
```
sudo aptitude keep linux-image-generic
```
?

---

### Post by mut80r on 2009-01-29
> **icheyne said:**
> Maybe try:
```
sudo aptitude keep linux-image-generic
```
?

It's not that it wants to get rid of the generic kernel, it just wants to install the server kernel too! and that's bad because it'll edit GRUB's menu and then a reboot would probably try and boot the server kernel and well, it's 100 miles away with no keyboard, mouse or monitor.

How would I tell it that I never want to install any server kernel, ever?

TIA.

EDIT: [http://pastebin.com/f6511f767](http://pastebin.com/f6511f767)

---

### Post by icheyne on 2009-01-29
I should have read the pastebin. Try:

```
sudo aptitude why linux-image-2.6.24-23-server
```This will tell you which package is asking for the server kernel.

Then you could either uninstall that program or try:

```
sudo aptitude forbid-version linux-image-2.6.24-23-server
```I'm pretty sure that ```
sudo aptitude safe-upgrade
``` avoid installations and reboots.

---

### Post by mut80r on 2009-01-29
> **icheyne said:**
> Try:
```
sudo aptitude why linux-image-2.6.24-23-server
```This will tell you which package is asking for the server kernel.



Thanks, forgot to remove the modules for -server.
Problem resolved.

EDIT: Can a moderator/admin mark this thread as resolved? It is not in the "thread tools" menu at the top of the page. Thanks.

---

### Post by icheyne on 2009-01-29
My pleasure. :)

(The thanking/solving functionality has been temporarily removed. - [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481))

---

### Post by mut80r on 2009-01-29
> **icheyne said:**
> My pleasure. :)

(The thanking/solving functionality has been temporarily removed. - [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481))

I see. I wondered why it was down. Anyway, edited for manually solved.

---

