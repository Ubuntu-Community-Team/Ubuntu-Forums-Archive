---
title: "Installing packages without apt-get"
date: 2009-04-22
forum: Installation &amp; Upgrades
---

### Post by su_list on 2009-04-22
Hi:

I have got intrepid on one of my lab PC. I can connect to net from my browser. But somehow, my synaptic or apt-get is not able to connect to the repositories. I dont know how to verify this though. When I run apt-get install telnetd, I get, "E: Couldn't find package telnetd".

I quickly need to install vsftpd and telnetd, manually. Can you please suggest me how can I install a package with all the dependencies without the apt-get. I downloaded the vsftpd debian installer, and when I tried to install, it failed for absence of libc6, whereas thats already installed in my system.

Thanks
Su

---

### Post by oldos2er on 2009-04-22
If you're using Gnome, check System, Administration, Software Sources to be sure the repositories are enabled. Then in a terminal, run
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by su_list on 2009-04-22
Yes, its enabled and I have gone and appended the apt file for all the repositories. 

I think its more of a connection problem.

From synaptic, I get errors like this:

Failed to fetch [http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg](http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/Release.gpg)  
Failed to fetch [http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  
Failed to fetch [http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2](http://ge.archive.ubuntu.com/ubuntu/dists/intrepid/universe/i18n/Translation-en_GB.bz2)  

I can connect to the net through browser but synaptic fails. Unfortunately I dont know the HTTP proxy and so its failing possibly.

Is there any way around to install the packages with all its dependencies manually without synaptic or apt-get.

Thanks

---

### Post by drs305 on 2009-04-22
You can try another server via Synaptic, Settings, Repositories, Download From. Select Other, then Best Server. Let it run it's test and then select the recommended Server. 

This technique also works well if you are planning a large upgrade,  Run it just before you run the update, as server speed can vary considerably due to demand volume.

---

### Post by su_list on 2009-04-22
I did the same by pointing to some other server. I see the same issue - "Failed to fetch <repository url>". Is there any way around to installing packages other than synaptic or apt-get.

---

### Post by drs305 on 2009-04-22
Have you checked Synaptic's Settings, Preferences, Network tab. Ticking "Direct connection to the internet".

---

### Post by su_list on 2009-04-22
Ya, I have done that, but still I get the, "failed to fetch" error. The problem is I am not sure of the HTTP proxy we use. 

So there is no way to install the packages minus this synaptic and apt.

---

