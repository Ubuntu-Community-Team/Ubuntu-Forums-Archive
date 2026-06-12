---
title: "Update Errors"
date: 2009-06-11
forum: Installation &amp; Upgrades
---

### Post by chpage07 on 2009-06-11
I've have had been getting this error code for a few days now and I'm not sure what to do. Obviously it has something to do with Screenlets because it is in the error code. The application works fine I'm thinking it doesn't know where to get the packages from. I am new to this so I could be completely wrong. 

I searched the forum but I only saw things relevant to other version.  

GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 665F9AEFE1098513Failed to fetch [http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages](http://hendrik.kaju.pri.ee/ubuntu/dists/gutsy/screenlets/binary-i386/Packages)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

opfor@OpFor-laptop:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 9.04
Release:    9.04
Codename:    jaunty


I think this is all the information that I need to supply. 

Thank you all in advance.

---

### Post by Partyboi2 on 2009-06-11
Hi, looks like you have a old gutsy ppa in your sources.list. Open a terminal (Applications>Accessories>Terminal) and open your sources.list
```
gksu gedit /etc/apt/sources.list
```then find the gutsy ppa entry and remove it or put a # infront of that line.
Then save the  changes and close gedit,  back in the terminal
```
sudo apt-get update
```If you are not sure how to do it, open a terminal and post the output to
```
cat /etc/apt/sources.list
```

---

### Post by _Purple_ on 2009-06-11
Looks like you have an entry for Gutsy in your sources list where as you are using jaunty. You can remove the Gutsy entry and update.

Edit: Partyboi2 was faster than me :P

---

### Post by chpage07 on 2009-06-11
Thank you so much!!! Your help is greatly appreciated. 

I am still kind of new and learning all of this but I am trying my best. lol

---

