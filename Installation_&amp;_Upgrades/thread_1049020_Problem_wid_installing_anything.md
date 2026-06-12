---
title: "Problem wid installing anything"
date: 2009-01-24
forum: Installation &amp; Upgrades
---

### Post by Yathi on 2009-01-24
This is a problem for  one of my friends.. Thing is she is not able to install anything.. when u run sudo apt-get install gparted or any such thing.. we get this response...

 Could not resolve 'in.archive.ubuntu.com'
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.5-1ubuntu3_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/main/g/gparted/gparted_0.3.5-1ubuntu3_i386.deb)  Could not resolve 'in.archive.ubuntu.com'
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

when trying to run apt-get update the resonse is 

E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
linux@linux-laptop:~$ 

wat could be the problem..???

---

### Post by x33a on 2009-01-24
resolve problems are usually linked to dns servers.

most likely it's a problem with her internet connection and/or dns settings.

post the output of /etc/resolv.conf

Edit: i just noticed, she is downloading from indian servers.

ask her to switch to international/main server and see if it works.

---

### Post by Yathi on 2009-01-24
no the thing is synaptic is working now after changing proxy settings.. but still not apt..

---

### Post by taurus on 2009-01-24
If you want to run apt-get from a terminal, you **must** close synaptic or add/remove first.  Otherwise, you would get that error message in your OP.

---

### Post by KIAaze on 2009-01-24
> **Yathi said:**
> no the thing is synaptic is working now after changing proxy settings.. but still not apt..

Just some google results:
[http://ubuntuforums.org/showthread.php?t=136065](http://ubuntuforums.org/showthread.php?t=136065)
[http://www.linuxquestions.org/questions/fedora-35/how-to-set-up-proxy-in-apt-gets-apt.conf-265793/](http://www.linuxquestions.org/questions/fedora-35/how-to-set-up-proxy-in-apt-gets-apt.conf-265793/)
[http://www.linuxforums.org/forum/ubuntu-help/66480-how-do-i-use-apt-get-behind-proxy.html](http://www.linuxforums.org/forum/ubuntu-help/66480-how-do-i-use-apt-get-behind-proxy.html)

I hope it helps.

---

