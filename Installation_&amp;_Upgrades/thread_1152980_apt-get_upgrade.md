---
title: "apt-get upgrade ?"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by Duckslammer on 2009-05-08
I just did a re-install of jaunty.  Once it was up, first thing I did was apt-get upgrade.  Unfortunately, due to ignorance, I was already running some other upgrade from the gui, and the apt-get process didn't complete (complaints about not being able to acquire a dpkg lock).  I ran it again, and it downloaded some headers but that's all it did, nothing got installed.

Before when I've done this, after it was done, the list of device drivers showed the proper device driver for my video so I can enable it and get high res on my screen.  But now, no new drivers are shown.  Obviously the upgrade did not complete. I don't know what else didn't install and should have. Running it again only downloads headers.  How can I force it to re-run as if it hasn't been run yet?

Post Script, using Xubuntu, used "add/remove" and selected device drivers.  It's downloading 67 files just to get the one nvidia driver I need, most of them for kde (which I'm not using) and has been crunching on it for 20 mins.  This is insane.

---

### Post by snowpine on 2009-05-08
Did you use 'sudo apt-get update' first? (and if so, were there any errors?)

---

### Post by Duckslammer on 2009-05-08
> **snowpine said:**
> Did you use 'sudo apt-get update' first? (and if so, were there any errors?)

I believe I've already answered both of those questions.  Maybe I don't understand what you're asking.

---

### Post by geraldvillorente on 2009-05-08
kindly post the output here so that we can help you better.

run this command...always use sudo if you're not root...
> 
sudo apt-get upgrade


running apt-get and synaptic simultaneously will create conflict...

---

### Post by Kareeser on 2009-05-08
"apt-get upgrade" is recommended to be run in conjunction with "apt-get update".

Update retrieves the list of packages from the repositories, so your computer can tell which packages are out of date.
Upgrade handles the actual upgrading of packages.

---

### Post by Duckslammer on 2009-05-09
> **geraldvillorente said:**
> kindly post the output here so that we can help you better.

run this command...always use sudo if you're not root...


running apt-get and synaptic simultaneously will create conflict...

Hi Gerald, and thanks for your help.

Synaptic and apt-get should acquire the lock *before* they start processing files; that is, after all, the point of locking. I totally didn't expect that.

Per your request:
  
/home/david # apt-get update
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security Release
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release.gpg
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Translation-en_US
Ign [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Translation-en_US
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Packages        
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) jaunty-security/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty/multiverse Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/main Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/restricted Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/universe Sources
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Packages
Hit [http://mx.archive.ubuntu.com](http://mx.archive.ubuntu.com) jaunty-updates/multiverse Sources
Reading package lists... Done
/home/david # apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
/home/david #

---

