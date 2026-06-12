---
title: "Post-install blues"
date: 2006-02-09
forum: Installation &amp; Upgrades
---

### Post by pkaplan on 2006-02-09
So I finally got kubuntu installed.  During the installation, networking was correctly configured.  But since installing I have no network connection.

As far as I can tell, the problem is that no modules are loading during the boot process.  During boot I'm getting a message to the effect "cant find /lib/modules/2.6.12-9-386/module.dep".

lsmod shows that only the reiserfs module is installed (I installed on a reiserfs volume.)

ifconfig shows only the loopback device (lo) present

ifconfig eth0 up says no such device

the network configuration page in the sysconfig gui shows no devices

lspci reports my Intel ethernet card exactly as it does when the machine is booted to another distro.

So what's happening?  Why can't I get a connection?
Paul

---

### Post by aysiu on 2006-02-10
If you use a live Ubuntu CD, does it detect your internet connection?

Just because the installer says the network's configured, it doesn't mean your network's actually working.

---

