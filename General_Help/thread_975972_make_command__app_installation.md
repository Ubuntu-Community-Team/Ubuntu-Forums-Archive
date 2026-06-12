---
title: "make command / app installation"
date: 2008-11-08
forum: General Help
---

### Post by rothdavid on 2008-11-08
Hi:

I am new to linux but am reading about it regularly.  (I bought a 1,000 plus page book on Ubuntu 8.04 desktop/server). I have Ubuntu desktop 8.10 and its not clear about packages, installation etc...  

For example, I have a web cam and found a tar.bz2 file from a website with instructions on how to install the drivers. I'm not sure where these files are to be unpacked?  maybe in the /etc  directory?  I have these files inside my Documents folder and have unpacked them there but it its not clear where I should be installing them.  In reading I understand there may be dependencies with other apps/drivers and they need to be located in the same area??

Also, using the file browser, it doesn't just let me copy the package into the /etc drive..  I have to run it somehow using sudo so I have privs to move stuff there.  Any good rules of thumb I should use when working with apps.drivers I want to install?  I have a quickcam pro and want to install it but short of having a clean .deb file that the system can install itself, using linux isn't really solidifying for me yet.

Getting down to command line commands, while I understand its origins and purpose, its really kinda cryptic. Seems like there should be a command cheat sheet on a function key? (looking for a good summary of command line items?)

Having a professional background in Winx systems, servers, desktops, networks & databases and a life in dos before winx, I thought this would be a bit easier than it is...

I'd be greatful for assistance and links to sites, or books that perhaps I should be reading? 
 
Thanks
David in Florida

---

### Post by taurus on 2008-11-08
You can save it to wherever you want but usually it should be in your $HOME/Desktop.  Then, you need to unpack it and probably either run the setup to install it or have to build it from source.  Usually, there should be a README or INSTALL that tells you exactly what you need to do to install it.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvjf **filename**.tar.bz2
cd **filename**
more INSTALL
```

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by rothdavid on 2008-11-09
Thanks taurus... for the link and advice... David

---

