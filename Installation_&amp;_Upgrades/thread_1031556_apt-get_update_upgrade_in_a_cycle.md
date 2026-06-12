---
title: "apt-get update upgrade in a cycle"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by jackyu on 2009-01-05
Normally, when I notice the orange square icon which indicates that updates are avalilable, come up, I do the following in a shell,

sudo apt-get update

sudo apt-get upgrade

But recently, I have started to notice that when I do this, I get the following error after I have done the 'upgrade' command:

"
The following packages have been kept back:
  amarok amarok-xine gnucash gnucash-common libdvdcss2 mplayer w32codecs
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded.
"

While the icon disappears, it comes back after a couple minutes.  Not surprisingly, when I use the same commands I get the same error again.  

What can I get out of this endless loop?  


cheers

---

### Post by maybeway36 on 2009-01-05
Try:
```
sudo apt-get dist-upgrade
```
dist-upgrade is the new upgrade; I started using it after reading the apt-get manpage.

---

