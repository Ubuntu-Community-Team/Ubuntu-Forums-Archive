---
title: "can I upgrade from an old version?"
date: 2009-03-18
forum: Installation &amp; Upgrades
---

### Post by rebeltaz on 2009-03-18
First of all, I's would like to say that I love Ubuntu. I had never used Linux before, but I grew up programming in DOS, so I was no stranger to the command line. My first foray into Linux was Ubuntu Server that I installed sans-GUI to run my web server - which has been going strong for over a year now! 

Then I purchased a new laptop on Woot that had some stripped down command-line Linux on it. I installed the latest 8.10 Ubuntu on her and i have been converting all of my computers to Linux ever since!

Here's my problem... I have an old Fujitsu Stylistic 3400 touchscreen notebook that I want to put Ubuntu on. The problem is that I do not have a CD drive or a floppy drive for it. I have both in USB versions, but this thing will not boot from a USB device. What I did was I pulled the hard drive out and put it in an old laptop with a CD drive. Then I ran the Ubuntu CD and let it install the everything to the hard drive. When it ejected the CD and wanted to reboot, I shut the computer down, took the hard drive out of the laptop and put it back in the notebook. Then when I turned the notebook on, the installation completed on that - no hardware issues at all ;) (well, except for the stylus, but that is a later problem). 

The problem with that is that, for some reason, 8.10 kept hanging on install on the laptop. The only other disc I had was an old 5.10 I had gotten a while back. That is the disc that I had to use to install it. I figured I could always upgrade later over the internet - the notebook has both a PCMCIA wireless card and a LAN connection. Following the directions on [https://help.ubuntu.com/community/UpgradeNotes]("https://help.ubuntu.com/community/UpgradeNotes"), I modified the repository list so that 5.10 could update itself. After that, I tried to upgrade to the 6.06 distro. That keeps giving me 404 File Not Found errors. 

Is it still possible for me to upgrade the 5.10 to... well, anything higher?

I plan on using this as a large screen GPS navigation unit in a vehicle, so I need to make sure the software I've chosen will work on it. 

Thanks...

---

### Post by karimone on 2009-03-18
try with the command

do-release-upgrade 


Usage: do-release-upgrade [options]

Options:
  -h, --help            show this help message and exit
  -d, --devel-release   Check if upgrading to the latest devel release is
                        possible
  -p, --proposed        Try upgrading to the latest release using the upgrader
                        from $distro-proposed
  -m MODE, --mode=MODE  Run in a special upgrade mode. Currently 'desktop' for
                        regular upgrades of a desktop system and 'server' for
                        server systems are supported.
  -f FRONTEND, --frontend=FRONTEND
                        Run the specified frontend

---

### Post by rebeltaz on 2009-03-18
> **karimone said:**
> try with the command

do-release-upgrade 


I tried that, but I get a "Command Not Found" error. I did an apt-cache search (after updating it) for it, but it didn't return anything. I did a search on Google, thinking I might could find a repository to add to get it from, but again, no luck...

???
 

Thanks...

---

### Post by karimone on 2009-03-18
Try with

apt-get install update-manager-core

---

### Post by rebeltaz on 2009-03-18
> **karimone said:**
> Try with

apt-get install update-manager-core

Responded with "Couldn't Find Package" error.

---

### Post by karimone on 2009-03-18
the is a source.list problem. Have you made a apt-get updta and apt-get upgrade?

Maybe the 5.10 have another system to make the upgrade

---

### Post by rebeltaz on 2009-03-18
> **karimone said:**
> the is a source.list problem. Have you made a apt-get updta and apt-get upgrade?

Maybe the 5.10 have another system to make the upgrade

I did... for the reference, the only line not commented out in the sources list are:

```

deb http://old-releases.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb http://old-releases.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse 

```

---

### Post by markbuntu on 2009-03-18
5.10 is no longer maintained. You need something newer.

---

### Post by rebeltaz on 2009-03-18
> **markbuntu said:**
> 5.10 is no longer maintained. You need something newer.

ummm... no kidding. That's I am trying to upgrade....

---

### Post by ugm6hr on 2009-03-18
```
sudo apt-get update && sudo apt-get dist-upgrade
```

I think update-manager-core is not available on 5.10.

---

### Post by Partyboi2 on 2009-03-18
Looking at the system specs for the Fujitsu Stylistic 3400 I see that it can have a max of 192mb ram. Hardy and Intrepid requires more then 192mb to run. So even if you manage to upgrade it to hardy or intrepid you will have performance problems. I would suggest trying to install a lighter distro on it like[COLOR=Blue][ darn small linux (dsl)]("http://damnsmalllinux.org/")[/COLOR]

---

### Post by markbuntu on 2009-03-18
Considering that 5.10 support was dropped over 2 years ago....

Upgrading is likely not possible since the repositories are no longer officially available. If you can find a mirror that still has the 5.10 repository it may be possible to upgrade to 6.06 which will be supported until June. An upgrade path from 6.06 is still available until June.

You may really just have to just install a newer distro, like 8.04 xubuntu which will support your hardware and which will be supported until 04/2011.

---

### Post by rebeltaz on 2009-03-18
> **Partyboi2 said:**
> Looking at the system specs for the Fujitsu Stylistic 3400 I see that it can have a max of 192mb ram. Hardy and Intrepid requires more then 192mb to run. So even if you manage to upgrade it to hardy or intrepid you will have performance problems. I would suggest trying to install a lighter distro on it like[COLOR=Blue][ darn small linux (dsl)]("http://damnsmalllinux.org/")[/COLOR]

I noticed that 5.10 is running a little slow. I'm trying to upgrade to 6.06 now using an ISO image, but if tat doesn't work, I may try the DSL....

Thanks.

---

