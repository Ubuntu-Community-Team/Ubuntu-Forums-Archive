---
title: "Update results in no downloads"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by feeno49 on 2009-09-28
I just went through a typical update and part way through, it hung.  After a while I noticed that everything requiring a download was hung.  I can ping, look up host names and so on, so the network is functional, but some setting has caused all downloading to the system to be stopped.  It will connect to the Web, but hangs bringing down a page and more importantly, it will tell me that the package I need is available and say it is fectching it, but it won't download it, which makes it darn hard to get what I need to diagnose the problem.  Has anyone else seen this?

Its fairly unprofessional to treat things as updates that will render a system useless.  This is the second time the Ubuntu folks have done it.

Thanks in advance

---

### Post by tommcd on 2009-09-29
What happens if you run:
```

sudo apt-get update
sudo apt-get dist-upgrade

```
Are you able to browse web pages in firefox and download stuff from websites in firefox? Or is it just the downloading of updates for ubuntu that is not working?
If an update hung and failed half way through, and you still can't get updates, try running:
```
sudo dpkg --configure -a
```
Then try again to get the updates.

And welcome to the Ubuntu forums!

---

### Post by feeno49 on 2009-09-29
If I attempt an apt-get, it can tell me what it needs to do based on the local cache, but as soon as it tries to download anything from the repository, it hangs. 

Same with Firefox, it says connecting, and then hangs.  Since I can't download wireshark, burp or any other tools, its a bit of a pain.  Since this happened suddenly, during an update, I'm thinking that it is probably a security change - like apparmor or a firewall.

---

