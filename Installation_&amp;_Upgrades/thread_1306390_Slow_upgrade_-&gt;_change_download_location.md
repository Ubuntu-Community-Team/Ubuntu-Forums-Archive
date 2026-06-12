---
title: "Slow upgrade -&gt; change download location"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by svenskmand on 2009-10-30
Hello everybody,

I am getting tired of slow download speeds when upgrading to 9.10, so I wanted to change the server I was downloading from, my current speed is only 15 kbps. But when I go to "System -> Administration -> Software sources -> Ubuntu Software" I change the "Download from" drop-down box to custom and select another server. But when I upgrade through "System -> Administration -> Update Manager" it is still slow as hell, that is still 15 kbps. I suspect that the Update Manager is still downloading from the same place as it did before.

Now my question is how can I change where the update is downloaded from? Can I use apt-get instead and do it there?

Best regards

---

### Post by svenskmand on 2009-10-30
So i found out that I could use the alternate iso, and mount in ubuntu and upgrade from this, [see this link]("http://www.ubuntu.com/getubuntu/upgrading#Upgrading%20Using%20the%20Alternate%20CD/DVD"), and then all should be good right? But no, when I upgrade the updater still wants to grab some extra packages, around 400 MB which takes 10 hours. Then I unplug the internet and all should be good, but again no, now the updater starts counting the 1440 packages to be installed and when it reaches 1116 it starts over, this continues indefinely :(, so no Ubuntu 9.10 for me until the servers is less strained :(

---

### Post by aswik on 2009-11-02
I'm also facing the same problem while upgrading speed is not crossing 15KBps, seems like either there is some problem with the server or ubuntu servers are going through shortage of bandwidth

---

