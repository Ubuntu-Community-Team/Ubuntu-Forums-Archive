---
title: "updating to new distro, fresh install, how do you do it"
date: 2009-10-29
forum: Installation &amp; Upgrades
---

### Post by renebs on 2009-10-29
Hi,

I am running 8.10 for while now. I have installed and configured some applications to make my 8.10 fell like home (like gnome-do and other applications).

I keep a file for all the applications I have installed so that, in case of fresh-install, I can use apt-get in a breeze (more info in this post [http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)).

I also keep /home on different partition. In my /home I keep a $HOME/usr folder and other $HOME/bin for some scripts and other applications (like unetbootin). 

So, what I would like to ask here is the following. What kind of procedure (advice) would you recommend to make such type of transition bug-free, and with as taking as little time as possible?

---

### Post by jrrader on 2009-10-29
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

more specifically:
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)

---

### Post by renebs on 2009-10-29
> **jrrader said:**
> [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

more specifically:
[https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04](https://help.ubuntu.com/community/KarmicUpgrades/Kubuntu/8.04)

Did you upgrade? 
I will not upgrade. Reason, the 8.10 I have sits in it's own partition, works very well. And for my situation (I have an extra partition to install a different distro) I think it's much easier to keep my 8.10 running in case something goes wrong. After all, it's just a matter of reboot and pick the right entry on grub and I am on a productive environment back again. 

However, to make 9.10 (or whichever other OS you plan to install) my new productive environment of choice, I will need to use my time to change the configuration of this and that application. The discussion I would like to have is, how to minimize this time of configuration? Which trick/approach you use in order to do that? For instance, would I gain by having a separate partition for /usr that would be used by BOTH distros (I imagine that this would be asking for a headache, however keeping a $HOME/usr would be fine...)

---

