---
title: "Upgrade to Jaunty removed xinetd"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by neilneil2000 on 2009-04-25
I have just upgraded my 8.10-desktop to 9.04-desktop (64 bit) using the do-release-upgrade

Before I did this I backed up my /etc.

I just noticed that the following are now missing

/etc/inetd.conf
/etc/xinetd.conf
/etc/xinet.d/

Also...
```
neil@neil-desktop:/etc$ sudo apt-get -s install xinetd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed
  xinetd
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Inst xinetd (1:2.3.14-7ubuntu1 Ubuntu:9.04/jaunty)
Conf xinetd (1:2.3.14-7ubuntu1 Ubuntu:9.04/jaunty)

```

I was using xinet to run rsyncd for my backups.

Is there are reason for these to be removed?  Replaced by something else perhaps.  Or maybe (I hate to say it) this is a bug?

Any insight gratefully received

---

### Post by cariboo on 2009-04-25
It looks like you simulated install worked, did you try to install the package, as it is not installed by default.

---

### Post by neilneil2000 on 2009-04-26
I realise the simulated install worked.

The reason for the post is that xinetd was installed before I ran "do-release-upgrade".

Is it expected behaviour that upgrading to Jaunty would remove it.  That doesn't seem logical to me, as it caused my server to stop working.

I can understand the package not being default, (I think it was in 8.10) but surely additional packages installed by the user should be left untouched when an upgrade is initiated, unless they are superceded or replaced by a similar product.

Am I missing something here?

---

