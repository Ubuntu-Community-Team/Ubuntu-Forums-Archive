---
title: "Map Network Drives &amp; Printers script"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by MaindotC on 2009-09-11
On my college campus, they only support Windoze.  Typically, when users need to locate a printer, they can open a Run command and type:
```

\\printer

```
and they get a list of all the printers on campus.  Same thing with network drives.  Our campus gives us personal storage space that we can access by typing:
```

\\myfiles

```
The name of the server is myfiles.csntprod.morrisville.edu so obviously they have some sort of DNS setting that allows us to just type "myfiles".  I made a wiki to show other Ubuntu Gnome users how to connect to network drives and printers on [http://morrisville-linux.pbwiki.com](http://morrisville-linux.pbwiki.com).

Once I know all the printers and network drives I want a machine to have, how do I do that automatically on another machine?  Is there an installation script or can I just transfer a configuration file(s) to the other machine?  Thanks!

---

### Post by MaindotC on 2009-09-12
Bump - I don't see what is so harmful about this topic, no one ever answers.  Either it's insanely difficult or insanely easy and users feel I'll just find the answer eventually.

---

### Post by MaindotC on 2009-09-12
bump - must be a difficult subject

---

### Post by falconindy on 2009-09-12
Make sure the "smbfs" package is installed and you can use the 'smbmount' to mount network drives from the command line. Something similar to:
```
sudo smbmount //server/share /localdir -o username=user,password=pass,uid=500,gid=500
```
Of course, the issue here is that it's based on sudo, which means manual password input... there's gotta be a way to do it in /etc/fstab.

Honestly, I'm not sure how to mount a samba printer from the command line.

---

### Post by falconindy on 2009-09-13
And thanks to Google, here it is:
```
//server/share /localdir smbfs username=user,password=pass,uid=500,gi d=100,dmask=770,fmask=770 0 0
```

---

### Post by MaindotC on 2009-09-13
I know how to mount network shares.  Please read my first post as you must have missed the question I was asking.

---

### Post by MaindotC on 2009-09-21
Bump it up!

---

