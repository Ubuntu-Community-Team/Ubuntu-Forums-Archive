---
title: "Where does the Nvidia driver source from?"
date: 2020-01-13
forum: Hardware
---

### Post by yaminb on 2020-01-13
Hi all,

I'm currently running the Nvidia 435 driver and it is working fine.

However, when I go to software update, I see the Nvidia 440 driver available.
I tried this a while back and it had issues.

But there are multiple builds of 440. 440.26, 440.44...

Does it source from:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages)

How can I see the exact version it wants to install if I just choose the 440 driver from the 'Additional Drivers'  tab?

---

### Post by Autodave on 2020-01-13
I can't answer your question.....sorry.  But, I can tell you that if the 435 driver is working, then leave it alone for now.  I am still using the 430 driver and will probably stay with that for awhile.  I do not always go for the newest because the bugs haven't all been worked out yet.  When something higher than 440 comes out, I may move to 440 one or I may just keep using the 430 for awhile longer.

---

### Post by CatKiller on 2020-01-14
> **yaminb said:**
> I'm currently running the Nvidia 435 driver and it is working fine. 

Great! If you aren't after whichever features or bug fixes that come with the 440 branch, there's no need to change it. 435 won't get any more updates because it's a short-lived branch. 

> But there are multiple builds of 440. 440.26, 440.44 

You already know the answer to this: the package manager picks the highest numbered version. 

>  Does it source from:
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa/+packages) 

Of course. 440 isn't in the main repositories yet, and you know that you added the graphics drivers PPA. 

> How can I see the exact version it wants to install if I just choose the 440 driver from the 'Additional Drivers'  tab?

```
sudo apt-cache policy nvidia-graphics-drivers-440
```

You can't upgrade cleanly between branches of the nvidia driver. The presence of the old one stops the new one installing properly. You need to purge all the nvidia stuff before you install the new branch.

---

### Post by yaminb on 2020-01-14
> Of course. 440 isn't in the main repositories yet, and you know that you added the graphics drivers PPA. 
I did the PPA. But perhaps a stupid misunderstanding. I have no idea how the 'Additional Drivers' tab got it's data. I assumed it would only get it from the main repositories.

>  sudo apt-cache policy nvidia-graphics-drivers-440

This did it! With a minor change to the package name :)
Thanks.

sudo apt-cache policy nvidia-driver-440
nvidia-driver-440:
  Installed: (none)
  Candidate: 440.44-0ubuntu0~0.19.10.1
  Version table:
     440.44-0ubuntu0~0.19.10.1 500
        500 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) eoan/main amd64 Packages

---

### Post by CatKiller on 2020-01-14
Glad to hear you're all sorted. 

> **yaminb said:**
> I did the PPA. But perhaps a stupid misunderstanding. I have no idea how the 'Additional Drivers' tab got it's data. I assumed it would only get it from the main repositories.

The PPAs are repositories like the others. You can see the entries in /etc/apt/sources.list.d/ if you're interested. The package manager will pull packages and updates from all the repositories it knows about. The big advantage of the PPA system is that it provides support, integration and hosting on the developer side; a small dev only needs to pop the critical packages up and launchpad essentially takes care of the rest. ppa-purge is handy, too, to automatically downgrade the packages, which was hard to do previously.

---

