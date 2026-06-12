---
title: "Laptop hanged half way through upgrading"
date: 2006-01-17
forum: Installation &amp; Upgrades
---

### Post by swong1 on 2006-01-17
I was upgrading from Hoary to Breezy using Synaptic. All the packages have been downloaded and installation was 95% completed when my laptop hanged! I had no choice but to switch off the computer. Upon rebooting, Breezy is added to the list of OS. However, I have lost gnome desktop, it only login to text mode. Login to Hoary redirects me to Breezy as well. What should I do? Can I continue where I left off? Please help.

---

### Post by Sef on 2006-01-17
Have you tried installing Gnome desktop yourself?

From the terminal:

sudo apt-get update

sudo apt-get install ubuntu-desktop

The bottom one will install the Gnome Desktop, but update first before you do.

---

### Post by swong1 on 2006-01-18
I tried 

```
sudo apt-get update
```

and got the following error messages:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-updates Release.gpg
Temporary failure resolving 'archive.ubuntut.com'
...
Failed to fetch ...
Err dpkg was interrupted, you must manually run 'dpkg -- configure -a' to correct the problem

running
```
ifconfig
```

shows the internet connection is not on. But I tried

```
sudo pon dsl-provider
``` to no avial.:(

---

### Post by Sef on 2006-01-18
I got this from pyschocats.net.  I hope it works for you.  You may just be able to work with it from the bottom part, where it says "Apparently, some people....."

Link:  [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")

> If you're using Ubuntu (Gnome):
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

Or copy and paste the following over your existing sources.list if you're using Breezy (5.10): 
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted 

## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy main restricted 

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-updates main restricted 

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted 

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse 
Save your file and close either kwrite or gedit. Lastly, and most importantly, type this into the terminal
sudo apt-get update 

Apparently, some people have been experiencing errors even after following this tutorial. There's some weird glitch where residual info hangs out and gives you a GPG signature error. If that's the case, do this: 

Back up the sources.list you got from this tutorial with this command: sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup 

Then edit the sources.list by typing sudo gedit /etc/apt/sources.list and delete everything. 

sudo apt-get update with your empty repositories list. 

Finally, sudo cp /etc/apt/sources.list_backup /etc/apt/sources.list sudo apt-get update

---

### Post by swong1 on 2006-01-18
I suspect the GPG error was due to the disconnected dsl. But I will try your suggestion anyway. Since I can't get into gnome desktop, I will have to use vi to edit the source.list file. Thanks for doing all the leg work. I really appreciate it.

---

### Post by swong1 on 2006-01-20
Hi,

I followed the instructions from pyschocats.net. The computer does not complain about failing to fetch all those files anymore, but it still advises me to do

```
dpkg --configure -a
```

So I did. It proceeds to install the downloaded packages. I presume it is finishing what I started a couple of days ago. At the end, it complains of encountering errors while processing

cupsys
hplip-base
bluez-cups
ubuntu-desktop
cupsys-driver-gimpprint

I don't know about the others, but I am a little concern that ubuntu-desktop is not installed properly. Anyway, I login again, and this time, I have gnome desktop, and I am able to connect to the internet via

```
sudo pon dsl-provider
```

So, I'm happpy:smile: . But I'm still concerned with the other lingering problems. 

Also, my track pad does not respond to double-tap. Does anyone know how to fix that? Does Breezy support vertical and horizontal scolling on the track pad?

---

### Post by swong1 on 2006-01-20
I execute again

```
sudo apt-get update
sudo dpkg --configure -a
```

cupsys
hplip-base
bluez-cups
ubuntu-desktop
cupsys-driver-gimpprint

are now set up properly.

---

