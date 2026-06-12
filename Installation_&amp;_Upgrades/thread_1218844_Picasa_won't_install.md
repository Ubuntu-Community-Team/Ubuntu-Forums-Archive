---
title: "Picasa won't install"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by Ichinenjuu on 2009-07-21
I downloaded the deb file for Picasa and clicked on it and it begins to install once I press "Install Package" and then it stops and I get a box pop up and say "Only one software management tool is allowed to run at the same time." Only problem is, there isn't anything else running. What is going on?

---

### Post by balaknair on 2009-07-21
It might have been running in the background(checking for updates perhaps)

In any case, it's probably better to use the Google repositories to install Picasa rather than with just the .deb file. Using the package manager+ repositories keeps your installed application up-to-date with the latest bugfixes and security patches.


To install Picasa 2.7 for Linux(the stable version)
[http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)

To install Picasa 3 for Linux(beta)
[http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html)

---

### Post by Ichinenjuu on 2009-07-21
Alright, thanks.

Just out of curiosity, is there any way to stop it from running in the background?

---

### Post by balaknair on 2009-07-21
> **Ichinenjuu said:**
> Alright, thanks.

Just out of curiosity, is there any way to stop it from running in the background?

Update manager?
I'm pretty sure there is. 
But it only runs in the background for a few minutes a day as it checks the repositories for updates. All you should have to do is try again after a few minutes.

---

### Post by crunchfighter on 2009-09-07
> **balaknair said:**
> It might have been running in the background(checking for updates perhaps)

In any case, it's probably better to use the Google repositories to install Picasa rather than with just the .deb file. Using the package manager+ repositories keeps your installed application up-to-date with the latest bugfixes and security patches.


To install Picasa 2.7 for Linux(the stable version)
[http://www.google.com/linuxrepositories/](http://www.google.com/linuxrepositories/)

To install Picasa 3 for Linux(beta)
[http://www.google.com/linuxrepositories/testrepo.html](http://www.google.com/linuxrepositories/testrepo.html)

I successfully added the 2.7 repository, but it won't show up in add/remove programs or synaptic when I do a search for "google" or "picasa".  Is there anything I need to do after adding a 3rd-party repository?

Thanks.

Update 3 minutes later: did "sudo apt-get install picasa" in a command window and did it that way.  Still not sure why it's not showing on the GUI tools though...

---

