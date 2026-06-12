---
title: "Backup updates and software?"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by lotster on 2009-05-28
I'm fairly new to Ubuntu; fairly inexperienced with the command line and such...  Now I have a rather complicated question.

Let me explain first: I live in a small farming community with very poor internet access, and in South Africa bandwidth is extremely expensive (and slow); yet I am so impressed with Ubuntu that I started promoting it everywhere I go, and I have to install it for friends and family quite often.  However, I still have Intrepid Ibex (I already ordered my Jaunty CD), and every time I install it there are over 300 updates to download and install, as well as other software, such as web development tools, media codecs, etc.  I simply don't have the bandwidth to download all of this every time I reinstall.

What I need to know is this:  Is there some way to backup the updates that I already downloaded on my PC, to install some or all of them on another PC at a later time?  (Yes, I know that different hardware and software will require different updates, but it will help if I don't have to download everything every time...)  For example, is there some sort of cache somewhere on my PC where Synaptic stores the data it downloads and installs?  I found some of the software I regularly install in deb packages, which helps, but I can't get all of it.

Any tips, advice, or help regarding this will be extremely welcome...

Thanks!

---

### Post by kpkeerthi on 2009-05-28
The downloaded deb files are stored in /var/cache/apt/archives. Just backup the stuff from this folder to an external media and restore the contents back to the same place if you happen to reinstall.

On your newly installed Ubuntu, open nautilus with super-user privilege
```
gksudo nautilus /var/cache/apt/archives
``` and then simply COPY/PASTE (Ctrl-C, Ctrl-V) the contents from the backup media to this folder.

---

### Post by lotster on 2009-05-28
That is awesome! Thank you very much! :)

---

### Post by iiiears on 2009-05-28
Information on creating a list of installed applications and a quick way to reinstall them.

[http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

dpkg, aptitude, in addition to synaptic are helpful.

 It is sometimes helpful to install applications and copy the deb packages from /var/cache/apt/archives after each install series to separate directories for backup. Name each folder by function  installed. 
Example: 
  display-adapter, 
  build-essential, 
  codecs, 
  icons-themes. 
  
 Because package names don't easily describe their functions and it is much easier later to reinstall only what you liked.

 If some problem has you using the command line.
apt, w3m, wget, vi, apropos,

---

### Post by glotz on 2009-05-28
You might also want to check out [Debian](http://debian.org/) stable. Minimal amount of updates, maximum stability and security.

Good luck!

---

### Post by New00Folder on 2010-12-29
> **kpkeerthi said:**
> The downloaded deb files are stored in /var/cache/apt/archives. Just backup the stuff from this folder to an external media and restore the contents back to the same place if you happen to reinstall.

On your newly installed Ubuntu, open nautilus with super-user privilege
```
gksudo nautilus /var/cache/apt/archives
``` and then simply COPY/PASTE (Ctrl-C, Ctrl-V) the contents from the backup media to this folder.
@KP Keerthi: Absolutely stupid thing to do. I tried that once. All the packages will get deleted from the archives folder after some time; probably after first real package update. Some of the packages won't even install.

---

