---
title: "Installation without blocked packages"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by imnes on 2009-04-24
A few packages are blocked from being downloaded by our corporate proxy.  Can't access any URL containing the work "proxy" or "mail" so those packages aren't able to be downloaded.  Any way to run update-manager and have it ignore those packages or install without them?

Nick

---

### Post by Slim Odds on 2009-04-24
> **imnes said:**
> A few packages are blocked from being downloaded by our corporate proxy.  Can't access any URL containing the work "proxy" or "mail" so those packages aren't able to be downloaded.  Any way to run update-manager and have it ignore those packages or install without them?

If your corporation has no problem with you using Ubuntu, get them to fix the blockage.

---

### Post by imnes on 2009-04-24
No exceptions allowed around here.  I have the packages blacklisted from trying to be upgraded on my intrepid install but update-manager seems to ignore those, or when it tries to re-install the metapackage ubuntu-desktop it's trying to pull those files even though they are blacklisted.

---

### Post by Slim Odds on 2009-04-24
> **imnes said:**
> No exceptions allowed around here. 
So they let you use Ubuntu, but you can't use it?

---

### Post by imnes on 2009-04-24
Our local IT Support shop lets us run whatever we want on our development boxes but network ops guys will not grant us proxy exceptions on a per-user basis so I can't get the block lifted.  We also can't access sourceforge.net, and some of the tools we use are hosted there so it's kind of a pain.

Nick

---

### Post by imnes on 2009-04-24
The three files I can't get are:

libp/libproxy/libproxy0_0.2.3-0ubuntu5_i386.deb
libm/libmailtools-perl/libmailtools-perl_2.04-1_all.deb
b/bsd-mailx/bsd-mailx_8.1.2-0.20081101cvs-2ubuntu1_i386.deb

---

### Post by imnes on 2009-04-24
This is what I did which finally worked for me...

echo "libproxy0 hold" | sudo dpkg --set-selections
echo "libmailtools-perl hold" | sudo dpkg --set-selections
echo "bsd-mailx hold" | sudo dpkg --set-selections

Edited my /etc/sources.list to change all isntances of intrepid to jaunty.

sudo update
sudo dist-upgrade

Looks good so far.

---

