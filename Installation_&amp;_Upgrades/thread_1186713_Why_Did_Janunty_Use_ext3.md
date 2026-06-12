---
title: "Why Did Janunty Use ext3?"
date: 2009-06-13
forum: Installation &amp; Upgrades
---

### Post by cinajohn on 2009-06-13
Recently did a fresh jaunty install on a blank drive.  During the install I was looking out for any file system options as I wanted to try ext4 but don't remember seeing any.  Now the primary partition shows as ext3, did I miss something?  I was under the impression that Jaunty defaults to ext4.

---

### Post by presence1960 on 2009-06-13
> **cinajohn said:**
> Recently did a fresh jaunty install on a blank drive.  During the install I was looking out for any file system options as I wanted to try ext4 but don't remember seeing any.  Now the primary partition shows as ext3, did I miss something?  I was under the impression that Jaunty defaults to ext4.

I would choose the manual option at the Prepare disk space window of the partitioner. Then you must choose type of partition, Use as (this is where you get to choose which filesystem) and mountpoint (/).

I believe ext 3 is still the default on an install.

---

### Post by xavierp94 on 2009-06-13
> **presence1960 said:**
> I would choose the manual option at the Prepare disk space window of the partitioner. Then you must choose type of partition, Use as (this is where you get to choose which filesystem) and mountpoint (/).

I believe ext 3 is still the default on an install.
Ubuntu 9.04 has ext4 installed by default.

---

### Post by cinajohn on 2009-06-13
that is what i thought xavier, any idea why mine used ext3?

---

### Post by albinootje on 2009-06-13
> **cinajohn said:**
> Now the primary partition shows as ext3, did I miss something?  I was under the impression that Jaunty defaults to ext4.

Luckily it does not default to ext4. 

See here : [http://www.ubuntu.com/getubuntu/releasenotes/904overview](http://www.ubuntu.com/getubuntu/releasenotes/904overview)

> 
Ext4 filesystem support

Ubuntu 9.04 supports the option of installing the new ext4 file system. ext3 will remain the default filesystem for Jaunty, and we will consider ext4 as the default for the next release based on user feedback. There has been extensive discussion about the reliability of applications running on ext4 in the face of sudden system outages.


I've read somewhere that ext4 is only considered safe in Jaunty with a kernel 2.6.30 (PPA).

See also : [https://launchpad.net/+search?field.text=ext4](https://launchpad.net/+search?field.text=ext4)

---

### Post by cinajohn on 2009-06-13
alright I see, thanks guys.  I'll leave ext3 for this install and consider it with 9.10.

Thanks again

---

### Post by presence1960 on 2009-06-13
[https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview](https://wiki.ubuntu.com/JauntyJackalope/TechnicalOverview)

ext 3 is the default filesystem for Jaunty.

---

