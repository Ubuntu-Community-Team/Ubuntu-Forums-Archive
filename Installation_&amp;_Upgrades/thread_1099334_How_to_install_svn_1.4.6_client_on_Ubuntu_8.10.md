---
title: "How to install svn 1.4.6 client on Ubuntu 8.10"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by eyeced on 2009-03-18
Hi,

I have an Ubuntu 8.10 , the default subversion version synaptic manager installs is 1.5.1 but in my office svn version 1.4.6 is being used , 
hence i am unable to authenticate in it.

Can any one help me in showing the steps to install subversion 1.4.6 on my laptop.

Thanks

---

### Post by Partyboi2 on 2009-03-18
You will probably need to remove your current version of subversion and  the  libsvn1 package as well. You can either search through synaptic and remove them or from the terminal (Applications>Accessories>Terminal)
```
sudo apt-get remove subversion libsvn1
``` then go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/hardy/subversion") and download subversion 1.4.6. Then go [[COLOR=Blue]here[/COLOR]]("http://packages.ubuntu.com/hardy/libsvn1") and download a older version of libsvn1. Then double click on the libsvn1 package you downloaded and install. Then do the same for the downloaded subversion package. 
You then will need to search for 'subversion' and 'libsvn1' in synaptic and lock the version by going to "Package>Lock Version" this will prevent then getting upgraded when you update your machine.

---

### Post by ekidmose on 2011-03-30
Thanks a bunch! 
Just got it working on 10.04 with eclipse 3.5.2 and subclipse 1.0.0
Though I couldn't get it to work before I installed(and locked) this package as well:
[http://packages.ubuntu.com/hardy/libsvn-java](http://packages.ubuntu.com/hardy/libsvn-java)

Still having some issues connection to an svn+ssh:// address but i got i working with a file:/// type of address, and the repository is on AFS so that works OK. 

Sorry for waking up such an old thread, just wanted to confirm that it works on my set-up, and say thanks :-)

---

