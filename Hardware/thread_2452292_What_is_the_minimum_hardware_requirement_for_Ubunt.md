---
title: "What is the minimum hardware requirement for Ubuntu Setup?"
date: 2020-10-20
forum: Hardware
---

### Post by dezintop on 2020-10-20
Sorry for my noobish question. But I believe that thousands of newbies looking for answer 

What is the minimum hardware requirement for Ubuntu Setup?

---

### Post by deadflowr on 2020-10-20
Ubuntu Desktop recommends at least 4GB RAM, and a dual core 2GHZ cpu or better.
Ubuntu Server recommends at least 1GB of RAM, and a 1GHZ cpu or better.

Desktop requires at least 25GB of Hard Drive space.
Server requires at least 2.5GB of Hard Drive space.

References:
[https://ubuntu.com/download/desktop]("https://ubuntu.com/download/desktop")
[https://ubuntu.com/server/docs/installation]("https://ubuntu.com/server/docs/installation")

---

### Post by guiverc on 2020-10-20
See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

It varies depending on what you want to perform etc...

I have Lubuntu running on a 2005 laptop, though there are a number of things I'd not want to do on that laptop (it's 1GB of RAM means its slow for some tasks; thankfully it's not my main box).  The 1GB RAM also means I'm very careful with how I do things, ie. I may read a news site in a browser & have a music player running, but I'm careful with tabs open & ultra careful selecting the apps I have running at the same time... 

I QA-test installed Ubuntu *flavors*  on older boxes than my main dell desktop from 2009, but your needs will vary on what you install, and what you want to use it for. On my primary box I can be less careful with app choices (having multiple browsers open, loads of tabs, loads of programs), but it has 8GB of RAM so can cope, even with it's old c2q-9400 cpu (ie. the generation before i5/i7).  I also prefer lighter desktops usually (*I have GNOME installed; the default desktop of Ubuntu, but rarely use it as I get better performance & actually prefer the other lighter choices I have installed too*).

You didn't specify if you're after a server, desktop, or happy with *flavor* etc, let alone release (the IBM thinkpad t43p won't use the latest releases, being stuck on 18.04 LTS) but I'd try reading the wiki I provided at the start first.

---

### Post by dezintop on 2020-10-20
> **deadflowr said:**
> Ubuntu Desktop recommends at least 4GB RAM, and a dual core 2GHZ cpu or better.
Ubuntu Server recommends at least 1GB of RAM, and a 1GHZ cpu or better.

Desktop requires at least 25GB of Hard Drive space.
Server requires at least 2.5GB of Hard Drive space.

References:
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)
[https://ubuntu.com/server/docs/installation](https://ubuntu.com/server/docs/installation)

I got 8 GB ram and 1 TB. That should be fine then.

---

### Post by dezintop on 2020-10-20
> **guiverc said:**
> See [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

It varies depending on what you want to perform etc...

I have Lubuntu running on a 2005 laptop, though there are a number of things I'd not want to do on that laptop (it's 1GB of RAM means its slow for some tasks; thankfully it's not my main box).  The 1GB RAM also means I'm very careful with how I do things, ie. I may read a news site in a browser & have a music player running, but I'm careful with tabs open & ultra careful selecting the apps I have running at the same time... 

I QA-test installed Ubuntu *flavors*  on older boxes than my main dell desktop from 2009, but your needs will vary on what you install, and what you want to use it for. On my primary box I can be less careful with app choices (having multiple browsers open, loads of tabs, loads of programs), but it has 8GB of RAM so can cope, even with it's old c2q-9400 cpu (ie. the generation before i5/i7).  I also prefer lighter desktops usually (*I have GNOME installed; the default desktop of Ubuntu, but rarely use it as I get better performance & actually prefer the other lighter choices I have installed too*).

You didn't specify if you're after a server, desktop, or happy with *flavor* etc, let alone release (the IBM thinkpad t43p won't use the latest releases, being stuck on 18.04 LTS) but I'd try reading the wiki I provided at the start first.


I'm looking to host my own website. So, server.

---

### Post by CelticWarrior on 2020-10-20
> **dezintop said:**
> I'm looking to host my own website. So, server.

Self-hosting is not that easy and there are lots of requirements for the internet connection.
Better rent it somewhere else.

---

### Post by TheFu on 2020-10-20
> **dezintop said:**
> I'm looking to host my own website. So, server.

There is little difference between a "desktop" and a "server" internals on Linux, but there is 1 huge difference.  "Server" doesn't have any GUI, so if you aren't already comfortable managing a system from a shell, then you should install a lite desktop and install the specific server packages you need.

Additionally, the minimum requirements are rules of thumb.  I have "servers" with 384MB of RAM and 1 vCPU which handle the jobs they are required easily.  Then I have others with 3GB of RAM and 2 vCPUs which struggle.  

IME, all desktops require much more CPU and RAM and servers. GUIs have lots of overhead and are best avoided. GUIs also provide more attack vectors to the system, more chances for memory leaks to use system resources and you'll be much happier with a more capable GPU.  It is possible to run a "server" without any GPU at all.

As for disk storage, I'd say 2-4G is the minimal for a specialized "server" and somewhere around 10G is the minimal for a lite desktop that doesn't get lots of GUI programs install and completely avoids using any snap packages.  But since snaps have been forced onto us with 20.04, the typical storage has increased by about 10G.  I've been running and migrating an Ubuntu desktop since 2008.  It ran 10.04, 12.04, 14.04, 16.04 and fit the entire OS and my perl programming tools in 15-17G of storage.  Last June, I moved it to 20.04 and now I needed over 30G of storage due to bloat. By default, snaps like to keep 3 versions and there doesn't seem to be any method to automatically make that 1 version.

How much CPU and RAM and storage are required depends on the workload and data requirements for the tasks to be run and what crap data you have/allow on the system.  There are lots of disk layout questions and answers in these forums.  Linux isn't Windows. Storage is a little more complex. Having to live with a bad choice because you are new is something everyone goes through.  After a few months, it usually becomes clearer about the bad decisions. It also shows that we each have to learn certain things on our own.

---

