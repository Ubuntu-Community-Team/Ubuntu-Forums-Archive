---
title: "Problem with Updating"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by tigerking615 on 2009-09-30
I've been having a problem updating Ubuntu. When I go to System > Administration > Update Manager, and click "Check," it gives me an error (see screenshot). 

I have tried googling the error, but I did not find anything that helped. I'm using Jaunty, and am kind of a Ubuntu noob. 

Thanks!

---

### Post by drs305 on 2009-09-30
tigerking,

Welcome to Ubuntu and the Ubuntu forums.

As the message says, you have an expired key for Opera. To allow yourself to get non-Opera updates, open Synaptic to the Repository pages:  
System, Administration, Synaptic Package Manager: Settings > Repositories. 
Opera is probably located in the Third Party/Other Software tab. Untick it and hit Reload on the main menu bar.

This should allow you to update your other packages.

You can go to the Opera web site, where there should be instructions on how to add the repository and get the public key for linux package managers such as Synaptic. You may need to go to the Synaptic Repository Authentication tab and remove any existing reference to the expired Opera key.

Here is some general information from the Ubuntu wiki on how Repositories work and are added in Ubuntu:
[https://help.ubuntu.com/community/Repositories/Ubuntu]("https://help.ubuntu.com/community/Repositories/Ubuntu")

---

### Post by tigerking615 on 2009-09-30
I unticked the 3 Opera entries, clicked Reload, and it worked! Thanks!

To get the Opera update working, you just have to type this into Terminal:
```
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
```

---

