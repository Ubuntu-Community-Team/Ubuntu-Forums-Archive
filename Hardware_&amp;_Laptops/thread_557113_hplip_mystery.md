---
title: "hplip mystery"
date: 2007-09-22
forum: Hardware &amp; Laptops
---

### Post by radar.duse on 2007-09-22
Hi, 
I'm no linux buff and -being fed up with windoze- I installed FeistyFawn on my "oldish" Celeron III 800Mhz, 512 RAM machine. Everything went smooth as butter and I'm a really happy camper with ubuntu....except for the HP drivers installation (hplip). Every time time I try to install via Synaptic I get this cryptic: "**E: hplip: subprocess post-installation script returned error exit status 1**"
(please refer to attached screen shot)
Every time my machine updates the system on line I get the same message. 
Funny is that the print system eventually does work! 
I have two questions:
1. should I ignore this message and carry on as if nothing happens (since printer works alright)
2. should I try to uninstall hplip altogether? (i tried re-installing it but no joy)
anyone had similar problems? I'd be grateful for any info....
Radar

---

### Post by Maxtorm on 2007-09-22
Try:
```
sudo apt-get -f install
sudo dpkg --configure -a
```

---

### Post by radar.duse on 2007-09-22
Thanx for responding Maxtorm.
I tried. There must be something "funny" going with my hplip! 
Here's the Terminal printout:

[B]xxxx@xxxx-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing: hplip
E: Sub-process /usr/bin/dpkg returned an error code (1)

xxxx@xxxx-desktop:~$ sudo dpkg --configure -a
Setting up hplip (1.7.3-0ubuntu1) ...
Creating/updating hplip user account...
 * Starting HP Linux Printing and Imaging System                         [fail] 
invoke-rc.d: initscript hplip, action "start" failed.
dpkg: error processing hplip (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:  hplip

xxxx@xxxx-desktop:~$ 
[/B]

...any ideas are welcome.

---

### Post by Maxtorm on 2007-09-22
OK. I had a similar error when setting up samba. The problem was a rogue file that it was looking for, but couldn't find. Solution was to "touch" the file and the install went fine (see previous discussion here: [http://ubuntuforums.org/showthread.php?t=482671](http://ubuntuforums.org/showthread.php?t=482671)). So, if indeed this is the same kind of problem, perhaps doing this right before you run apt-get install:
```
sudo touch /etc/hplip.conf
```

---

### Post by radar.duse on 2007-09-22
:(
tried that
no joy
thanks anyway

---

### Post by wsfulton on 2007-09-29
I had this problem too. I don't know what has gone wrong with the hplip install but most of the apt-get commands error out, which means you can't even re-install hplip. So to solve it, I removed the /etc/init.d/hplip file:

sudo mv /etc/init.d/hplip /tmp

Then the following will work:

sudo apt-get -f install
sudo dpkg --configure -a

Now that apt-get is working again, you can then reinstall the hplip drivers from:

[http://hplip.sourceforge.net/install/install/index.html](http://hplip.sourceforge.net/install/install/index.html)

---

### Post by radar.duse on 2007-09-30
[I]wsfulton:
I had this problem too. I don't know what has gone wrong with the hplip install but most of the apt-get commands error out, which means you can't even re-install hplip. So to solve it, I removed the /etc/init.d/hplip file:

sudo mv /etc/init.d/hplip /tmp[/I]

Tks for trying, wsfulton, but my bug seems somehow different.  Here's a copy from the Terminal:

> [b]xxxx@xxxx-desktop:~$ sudo mv /etc/init.d/hplip /tmp
mv: cannot stat `/etc/init.d/hplip': No such file or directory
xxxx@xxxx-desktop:~$ [/b]

:confused:

---

