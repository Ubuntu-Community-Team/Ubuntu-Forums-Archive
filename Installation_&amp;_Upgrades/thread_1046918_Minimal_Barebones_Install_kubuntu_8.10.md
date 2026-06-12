---
title: "Minimal Barebones Install kubuntu 8.10"
date: 2009-01-21
forum: Installation &amp; Upgrades
---

### Post by enigmakv on 2009-01-21
Hi all,

I am an experienced windows and mac user and am fairly new to Ubuntu.  I have tried a couple installs over the last few years but was always overwhelmed at the number of packages and the amount of stuff installed by default that I would never use.  This is just a hobby and I don't plan to have Ubuntu as a main system so no need for common computer stuff like mp3 players, etc.  I am installing to a VMware Fusion 64-bit virtual machine.

I want a barebones minimal install.  I want a BASIC KDE (KUbuntu) environment that I can add bells and whistles to manually as I find a need.

So I started with the instructions at:
[http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

Downloaded the minimal install CD from:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And installed the command-line interface following the instructions up to the first login.

Then I went to:
[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

and followed the following steps...

* after installation you may want to blacklist some restricted modules in:
  /etc/default/linux-restricted-modules-common

  The text on the site suggested:
  DISABLED_MODULES="ath_hal fc fglrx fwlanusb ltm nv"

  but the documentation in the actual file suggested:
  DISABLED_MODULES="madwifi ltm wl"
  so I went with that.

* if you do not use hibernation, comment or delete (I chose to delete)...
  /etc/initramfs-tools/conf.d/resume
  then execute...
  sudo update-initramfs -u

* if you do not have a laptop, you may consider removing acpi and acpid by executing
  sudo aptitude remove acpi acpid

It also suggested editing the /etc/apt/sources.list file, but I decided to leave it at the default so as not to get any more or less than what is necessary. (comments???)

Next I Updated and Upgraded the system with...
sudo aptitude update  and
sudo aptitude upgrade

Then I installed X.org with the command...
sudo aptitude install xorg

So now I'm not sure what I have as far as command line usability, but what I have is only consuming 853MB of disk space (per df -h).

I know the next steps are a Login Manager and the Window Manager System.

I am not sure however which packages to install to get the MOST BASIC KDE environment up and running.  Please Help!

Also, any comments or criticisms on my progress so far would be greatly appreciated.

-k-

---

### Post by Bucky Ball on 2009-01-21
Why don't you install the smallest version from here:

[http://www.kde.org/download/](http://www.kde.org/download/)

... and then 'sudo apt-get remove/purge' what you don't want? It might take awhile though, I guess.

If you're up to working with the source code or can get the help of someone who is, you might be able to do it that way and come up with something we can all share! \\:D/

Nice job, by the way. I'm aiming to give the minimal a go when I have the time. The burnt disc has been sitting there awhile now.

---

### Post by logos34 on 2009-01-21
> **enigmakv said:**
> 
I know the next steps are a Login Manager and the Window Manager System.

I am not sure however which packages to install to get the MOST BASIC KDE environment up and running.  Please Help!

Also, any comments or criticisms on my progress so far would be greatly appreciated.

I think what you want is **kde-core**:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)
[http://ubuntuforums.org/showthread.php?t=548340](http://ubuntuforums.org/showthread.php?t=548340)
[http://ubuntuforums.org/showthread.php?t=277090](http://ubuntuforums.org/showthread.php?t=277090)

hope that helps

---

### Post by enigmakv on 2009-01-21
Hi Bucky Ball,

Thanks for the reply.  My goal is to work from the ground up, rather than top down.  All my years of installing operating systems I have learned that when you start with a full install, you never get rid of ALL the stuff that is not used.  Starting from the bottom lets me keep more control of the system.  I will try to document and share my experiences as I go.

---

### Post by enigmakv on 2009-01-21
> **logos34 said:**
> I think what you want is **kde-core**:

[https://help.ubuntu.com/community/InstallingKDE](https://help.ubuntu.com/community/InstallingKDE)
[http://ubuntuforums.org/showthread.php?t=548340](http://ubuntuforums.org/showthread.php?t=548340)
[http://ubuntuforums.org/showthread.php?t=277090](http://ubuntuforums.org/showthread.php?t=277090)

hope that helps

Logos,

Thanks for your reply.  In one short post, you answered the majority of my questions.  The InstallingKDE page is perfect, I searched and searched today and never came across it.  The other two links are filled with tons of info and links to even more so thank you thank you thank you.

I apologize to all if my post is a duplicate, but I spent a good part of the day searching various terms and only found very old posts.  That is why I put so many terms in the subject (including 8.10), to help others searching the same thing.

-k-

---

### Post by Bucky Ball on 2009-01-22
> **enigmakv said:**
> Hi Bucky Ball,

Thanks for the reply.  My goal is to work from the ground up, rather than top down.  All my years of installing operating systems I have learned that when you start with a full install, you never get rid of ALL the stuff that is not used.  Starting from the bottom lets me keep more control of the system.  I will try to document and share my experiences as I go.

After years of experience with *Windoze* myself, I know what you are saying. Linux is different and you will successfully get rid of everything and all dependencies, but doing it top down would be time consuming. kde-core sounds like a good idea.

---

### Post by enigmakv on 2009-01-22
Progress Report!

I installed kde-core and got a base system.  KDM was installed with it, but NO (zero) applications were included.  From links on previous posts, I expected to have Konsole and Konqueror but got nothing.

I have since installed kdebase in order to get those apps.  It appears that since the time of those previous posts (2006-2007) that kde-core has been made even more basic.

My next mission is to get VMware Tools installed and running.

---

