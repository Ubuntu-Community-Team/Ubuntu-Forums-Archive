---
title: "[SOLVED] apt incomplete install removal"
date: 2008-11-30
forum: General Help
---

### Post by MaddMatt on 2008-11-30
Hi All, 

I've got some dependency problems because I was tinkering and installed some Intrepid packages on Hardy (I needed it for a script, and it had been removed from a hardy repo, but I digress...) 
In any case, Aptitude is now stuck halfway through the installation / removal of these two completely-superfluous packages due to a broken install script.
Here is what I mean:

```

..
Setting up usbhid-dkms (0.11.1) ...
Loading new usbhid-0.11.1 DKMS files...

Error! Cannot locate /usr/src/usbhid-0.11.1.dkms.tar.gz.
File does not exist.
dpkg: error processing usbhid-dkms (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of bcm5974-dkms:
 bcm5974-dkms depends on usbhid-dkms; however:
  Package usbhid-dkms is not configured yet.
dpkg: error processing bcm5974-dkms (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 usbhid-dkms
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I already tried finding the required source, which proved unsuccessful, and eventually in a month or so I plan on installing Intrepid, so I'm not really interested in solving this as much as making it go away.
For the life of me, I cannot figure out where apt keeps it's list of things-to-do. I'd really just like to comment out these two packages from it's 'to-do-list' so that I can stop being bothered by these errors until I do a fresh install in a month. Does anyone know how to make apt just 'forget' about these two for a while? 

Thanks!
M

---

### Post by CatKiller on 2008-11-30
I don't know how to answer your actual question, but you could try creating the file that it can't find with ```
sudo touch /usr/src/usbhid-0.11.1.dkms.tar.gz
``` Hopefully the script just needs to delete it.

Where did you get the packages from, anyway? I'd imagine that the package maintainers would find this useful information.

---

### Post by MaddMatt on 2008-11-30
> **CatKiller said:**
> I don't know how to answer your actual question, but you could try creating the file that it can't find with ```
sudo touch /usr/src/usbhid-0.11.1.dkms.tar.gz
``` Hopefully the script just needs to delete it.

Where did you get the packages from, anyway? I'd imagine that the package maintainers would find this useful information.

Ha! Such as simple solution, I don't know why I didn't think of that. Thanks!

I got it from the mactel ppa - for whatever reason they seem to have stopped supporting hardy and the only way to get applesmc was to use the intrepid repo, which caused these dependency problems.. I doubt that many other people are doing this, however, so I'm not planning on reporting it. 

Thanks again. 
M

---

