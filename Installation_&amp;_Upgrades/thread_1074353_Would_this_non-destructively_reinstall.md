---
title: "Would this non-destructively reinstall?"
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by frankwakeman on 2009-02-19
Two months into my Linux use I've got the hang of things more or less, but I'm curious about this:

If I use manual partition settings at installation, and choose only to format / and not /home, will that effectively give me a kind of system restore function?  (I've just learnt about remastersys and will be using that once I've got a good and sound setup.)

Elsewhere you can see I have a problem with repositaries; having done a fresh install two days ago it wouldn't inconvenience me too much to start again if necessary, but if I used the method I'm enquiring about would the repositary details be restored or are they kept in /home and would therefore the method outlined not get things resolved.

I ask that but I'm also just curious about this probably rudimentary point....

---

### Post by mcduck on 2009-02-19
That would keep all your personal files and settings, but not installed programs or system configurations.

---

### Post by linux_tech on 2009-02-19
Before doing any reinstall, upgrade or repair always back up your home directory and sources.list. I don't generally recommend upgrades, usually better to do a fresh install.  

There are many ways to repair a system, if this is what you wish to do. 
Repair being a general term, the correct solution really depends on the problem. 
Booting to safemode, then locating and fixing the issue is one commonly
used way to fix driver, video, etc problems. Packaging issues, disk issues, are handled differently. 
 
You can also use rescue mode, as described here-
[https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html](https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html)

---

### Post by theozzlives on 2009-02-19
> **linux_tech said:**
> Before doing any reinstall, upgrade or repair always back up your home directory and sources.list. I don't generally recommend upgrades, usually better to do a fresh install.  

There are many ways to repair a system, if this is what you wish to do. 
Repair being a general term, the correct solution really depends on the problem. 
Booting to safemode, then locating and fixing the issue is one commonly
used way to fix driver, video, etc problems. Packaging issues, disk issues, are handled differently. 
 
You can also use rescue mode, as described here-
[https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html](https://help.ubuntu.com/8.04/installation-guide/i386/rescue.html)

The only way I could get my scanner to work was to start with Gutsy and upgrade my way to Intrepid. Fresh installs just wouldn't do it. I am, however, planning a fresh install of Jaunty for Ext4.

---

### Post by linux_tech on 2009-02-19
True, good reason for upgrading.  Some scanners can be tough or impossible to get drivers for in linux.  Some releases are better than others.
Hardware support for older hardware, drivers, do not always work with new OS releases. In this case a upgrade is recommended.

Best to always run live cd first, check hardware with hcls,  do a little research beforehand before deciding whether to do upgrade or do fresh install

---

### Post by theozzlives on 2009-02-19
> **linux_tech said:**
> True, good reason for upgrading.  Some scanners can be tough or impossible to get drivers for in linux.  Some releases are better than others.
Hardware support for older hardware, drivers, do not always work with new OS releases. In this case a upgrade is recommended.

Best to always run live cd first, check hardware with hcls,  do a little research beforehand before deciding whether to do upgrade or do fresh install

It's not an old printer/scanner, just a stubborn one (Epson Stylus CX 8400). Anyhow if you don't format /home, there's very little config when it's all said and done.

---

