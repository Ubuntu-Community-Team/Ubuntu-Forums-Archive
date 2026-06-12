---
title: "SSD Drive Not Automatically Mounting Arghhhh!"
date: 2016-02-15
forum: Hardware
---

### Post by markackerman8@gmail.com on 2016-02-15
Ok,

Another headache, and simple to describe.  I have a new 480 GB SSD HD, which I have a "Data" folder with Folders form my Home folder in them (and links to them of course in the main Home Folder).  Good idea right, actually awesomely easy BUT .... BUT ....

when I restart the laptop it (the SSD Drive) does NOT Mount.  It is easy to overcome by simply trying to open it up using Nemo - which subsequently and immediately crashes, but does the trick (ei.) mounts the SSD Drive.  This however is not ideal as many programs (Like Dropbox) need immediate access to their "Home" Folder Files.

So simply - how do I get this SSD to automatically Mount during Login??  Easy right???  Hmmmm? Thanks ion advance.

Cheers, Mark

---

### Post by TheFu on 2016-02-15
This is the way that Unix systems work. Mounting storage has real security implications, so automatic mounting is a bad idea - IMHO.  But if the system admin sets up the mounts, that is fine.
[https://help.ubuntu.com/community/AutomaticallyMountPartitions](https://help.ubuntu.com/community/AutomaticallyMountPartitions) explains. You want the "systemwide" mounting, not per-user.

This is easy stuff.

---

