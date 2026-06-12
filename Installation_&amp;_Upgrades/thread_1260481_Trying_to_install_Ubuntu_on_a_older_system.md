---
title: "Trying to install Ubuntu on a older system"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by pbeezy on 2009-09-07
Hello I am trying to install Ubuntu on a older computer but am having some issue's. I have downloaded the "ubuntu-9.04-desktop-amd64" and "ubuntu-9.04-desktop-i386" but during restart I am getting the same problem with both of them. It say's:
 
"This kernal requires an x86-64 cpu, but only dectected a i686 CPU. Unable to boot - Please use a kernal appropriate for your CPU"
 
I looked but was unable to find one, maybe I am just missing it? Can somebody please link me to one that will work on a i686 CPU?
 
Thanks!!

---

### Post by norwoods on 2009-09-07
ubuntu-9.04-desktop-i386 is the 32 bit operating system that should run on your hardware.  someone along the line may have propagated a 64 bit os with the ubuntu-9.04-desktop-i386 file name, probably you.  you can try to make a new cd with the your ubuntu-9.04-desktop-i386 file or download and make a new cd.

---

### Post by oboedad55 on 2009-09-07
> **norwoods said:**
> ubuntu-9.04-desktop-i386 is the 32 bit operating system that should run on your hardware.  someone along the line may have propagated a 64 bit os with the ubuntu-9.04-desktop-i386 file name, probably you.  you can try to make a new cd with the your ubuntu-9.04-desktop-i386 file or download and make a new cd.

How old is your hardware, which CPU, how much RAM, etc.?

---

### Post by raymondh on 2009-09-07
> **oboedad55 said:**
> How old is your hardware, which CPU, how much RAM, etc.?

+1

Release notes for 9.04

[http://www.ubuntu.com/getubuntu/releasenotes/904](http://www.ubuntu.com/getubuntu/releasenotes/904)

---

### Post by pbeezy on 2009-09-08
Thank you for the replys, I am trying to install it on 3 computers and have burnt about 4 cd's of Ubuntu already :p lol.
 
I boot from CD, select "Install Ubuntu" and it goes to the POST screen and sits there with the _ symbol on the top left, should I let it sit there? I've let it sit there for about an hour keeping in mind this notebook is VERY VERY old but was running Windows XP so I dont see why it wouldnt work for Ubuntu I'm not sure how much Ram it has but as I mentioned it ran Windows XP so it should be able to run Ubunutu? Correct?
 
I also tried to install the text based but was unable because I cant connect to the internet... (It doesnt have a ethernet port)
 
*edit*
Took the CD out and it still sit's at the POST screen :( I have no idea what to do lol. I know the CD works because I'm installing it on the other computers as I type this
 
[http://pcworld.about.com/news/Jun082002id101702.htm](http://pcworld.about.com/news/Jun082002id101702.htm) - is the notebook.

---

### Post by oldos2er on 2009-09-08
> **pbeezy said:**
>  I've let it sit there for about an hour keeping in mind this notebook is VERY VERY old but was running Windows XP so I dont see why it wouldnt work for Ubuntu I'm not sure how much Ram it has but as I mentioned it ran Windows XP so it should be able to run Ubunutu? Correct?
 

 No, not necessarily. The LiveCD requires 384MB RAM. According to the link you provided, there's only 256MB in your notebook.

 You could try the alternate cd. [http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by raymondh on 2009-09-08
On initial boot, try to press F4 and select safe graphics mode .... if you insist on using that version on your system hardware.  Note that though you may have 256 mb RAM, some of it will be used by your graphics card thus lessening the useable RAM.  Ann (oldos2er) has a very valid point.

You could try a Ubuntu-based distro like [crunchbang]("http://crunchbanglinux.org/") linux which uses a lightweight windows manager (openbox).  I have found it more nimble for older systems.

Good luck.

---

