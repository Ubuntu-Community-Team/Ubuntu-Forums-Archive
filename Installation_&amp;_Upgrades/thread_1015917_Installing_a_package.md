---
title: "Installing a package"
date: 2008-12-19
forum: Installation &amp; Upgrades
---

### Post by nikhilneela on 2008-12-19
Hi everyone,
when i try to install a package i get the following errors.

E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

what does it mean and how should i correct these errors so that i can install my packages without any problems....

---

### Post by SuperSonic4 on 2008-12-19
It means you have something else open, either apt-get in a terminal, a deb file installing or synaptic open

Close all of them and try again. If the problem doesn't go away **and you have no package manager open!** you can run

```
sudo rm /var/lib/dpkg/lock
```

source: [http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html](http://www.ubuntugeek.com/how-to-fix-lock-varlibdpkglock-open-11-resource-temporarily-unavailable-error.html)

---

### Post by nikhilneela on 2008-12-20
When i try to install any package i am getting the following error
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I am a beginner to UBUNTU...please provide me a clear solution....I dont even know abc of Ubuntu....please bear me
Thanks

---

### Post by lovelyvik293 on 2008-12-20
You have two package manager working at same time.
Make sure that only one package manager is running.

---

### Post by nikhilneela on 2008-12-20
I am a beginner to Ubuntu....how should i turn one of the package manager off when two are running....Thanks

---

### Post by taurus on 2008-12-20
Look at the output of this command from a terminal to see if you have anything related to synaptic, add/remove, or adept running.

```
ps -A
```

---

### Post by nikhilneela on 2008-12-20
When i try to install any package i am getting the following error
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

I am a beginner to UBUNTU...please provide me a clear solution....I dont even know abc of Ubuntu....please bear me
Thanks

---

### Post by taurus on 2008-12-20
Why start a new thread since you already have one active?

[http://ubuntuforums.org/showthread.php?t=1016725](http://ubuntuforums.org/showthread.php?t=1016725)

---

### Post by nikhilneela on 2008-12-20
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory

why am i getting this error..........how should i recover...provide me a detailed solution i am a beginner to ubuntu.....please please please help me out........
thanks

---

### Post by chrisamiller on 2008-12-20
It would be helpful if you told us what you were trying to do when you got the error.  

Usually this means that another process is using apt.  You can't, for example, use apt-get to install software while synaptic is running (or update-manager is running, or aptitude is running, etc).  

Also, try searching these forums and google with your error message.  I get a dozen results that look like they might help you if you read through them.

[http://www.google.com/search?q=Could+not+get+lock+%2Fvar%2Fcache%2Fapt%2Farchives%2Flock+-+open&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.com/search?q=Could+not+get+lock+%2Fvar%2Fcache%2Fapt%2Farchives%2Flock+-+open&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by bapoumba on 2008-12-20
4 threads merged.

---

