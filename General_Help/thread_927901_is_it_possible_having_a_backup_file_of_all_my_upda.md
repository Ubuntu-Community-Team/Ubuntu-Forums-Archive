---
title: "is it possible having a backup file of all my updates?"
date: 2008-09-23
forum: General Help
---

### Post by ieBrazil on 2008-09-23
I mean, last Sunday I spent more than 6 hours on the Internet just for downloading some repositories... or updates, I don't know the correct word for that.

Anyway, I'd like to know if I can keep them as a back up on a cd, because I may need them in future...

Is it possible?

tnx.




ieBrazil

---

### Post by IanW on 2008-09-23
Take a look at "aptoncd" - it's in Synaptic. I believe it may be exactly what you're looking for.

Here's Synaptic's writeup for it...
```

Installation disc creator for packages downloaded via APT
APT removable repository creator and package backup tool for Debian based
systems.

This tool will allow you to create a media (CD or DVD) to use to install
software via APT in a non-connected machine, as well upgrade and install
the same set of softwares in several machines with no need to re-download
the packages again.

For more information, visit http://aptoncd.sourceforge.net
```

---

### Post by hyper_ch on 2008-09-23
the downloaded .deb files through synaptic, apt-get, aptitude, adept, .... are stored in /var/cache/apt/archives

---

### Post by kokkus on 2008-09-23
You can also install Remastersys.
This will let you create a live installation CD of everything on your PC or a distro version without private stuff (home folder) so you can share with your friends. 
This program will create both ISO file and copy everything so cd image you can create an archive file if you either want that.
[http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb](http://scumbox.com/ubuntu/remastersys_2.0-5_all.deb)

Note: A private backup will also take backup of your temp files in i.e firefox, so remember to remove the private data, log files, temp etc. 

Keep in mind that a normal cd is 700mb, and DVD is 4GB.

---

### Post by LowSky on 2008-09-23
Remastersys is awesome. I recommend it.

---

