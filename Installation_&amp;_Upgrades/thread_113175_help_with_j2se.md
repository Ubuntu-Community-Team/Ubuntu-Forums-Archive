---
title: "help with j2se"
date: 2006-01-05
forum: Installation &amp; Upgrades
---

### Post by jubuntu on 2006-01-05
im trying to install js2e and usung this command

sudo apt-get install sun-j2re1.5
java -version

its coming back to me with a soure error stat - can anyome tell me what this means or suggest where im going wrong?

(ive updated the capacity to add extra repositories)

thanks

---

### Post by Turtle.net on 2006-01-05
Can you give us the exact errors you have ?

---

### Post by justafish on 2006-01-06
I can't seem to install j2se either. I've tried adding the free and non-free repositories and apt-get installing, but I've noticed that there's no Packages.gz in the binary-amd64 folder on any of the mirrors. So obviously that's not going to work...
:(

---

### Post by Turtle.net on 2006-01-06
You could use this [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")
to be sure to use the proper repo...

---

### Post by jubuntu on 2006-01-06
[QUOTE=Turtle.net]Can you give us the exact errors you have ?[/QUOTE]

thanks for your interest, any help is greatly appreciated.

here is what i get after i attempt an install.

------------------------------------------------------------------------------------------------

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package sun-j2re1.5
-------------------------------------------------------------------------------------------

---

### Post by Turtle.net on 2006-01-07
Follow the instructions here [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
to change you repository list.
after that ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-j2re1.5
```
That should work...

---

### Post by Ailis on 2006-01-07
I'm having the exact same problem. I've tried following the tip above, but it doesn't change anything. I also get the same error when I try to install the w32codecs, libdivx4linux and libdvdss2 packages.

---

### Post by jubuntu on 2006-01-07
[QUOTE=Turtle.net]Follow the instructions here [http://www.psychocats.net/linux/sources.php]("http://www.psychocats.net/linux/sources.php")
to change you repository list.
after that ```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install sun-j2re1.5
```
That should work...[/QUOTE]


umm i followed those instructions and my system died.  ive just done a complete reinstall.

---

### Post by jubuntu on 2006-01-07
[QUOTE=Ailis]I'm having the exact same problem. I've tried following the tip above, but it doesn't change anything. I also get the same error when I try to install the w32codecs, libdivx4linux and libdvdss2 packages.[/QUOTE]
 same here.

---

### Post by Turtle.net on 2006-01-08
I do not understand...
that's exactly the way I used to add repositories under Hoary and Breezy and everything works perfectly....

---

### Post by matthew413 on 2006-01-09
I'm having problems installing Java too.

Following the guide above I get the message

[http://www.ubuntuforums.org/showthread.php?t=113175&highlight=java+install](http://www.ubuntuforums.org/showthread.php?t=113175&highlight=java+install)

Fetched 756B in 16s (46B/s)
Reading package lists... Done
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: Unknown error executing gpgv
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release: Unknown error executing gpgvW: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release: Unknown error executing gpgv
W: You may want to run apt-get update to correct these problems

then

matthew@ubuntu:~$ sudo apt-get install sun-j2re1.5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package sun-j2re1.5

I've followed the part about clearing the repositary too.

Anyone got any ideas?  I only need it to install Azureus :(

---

### Post by jubuntu on 2006-01-10
i get much the same crap.  i get the feeling that hoary reps are not updated or supported like the breezy ones.

---

