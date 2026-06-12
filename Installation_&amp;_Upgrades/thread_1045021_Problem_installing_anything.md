---
title: "Problem installing anything"
date: 2009-01-20
forum: Installation &amp; Upgrades
---

### Post by Spoonstm on 2009-01-20
I am new to ubuntu and I am still not very good with it.  I have been having a problem getting anything to install.  Even the updates that come through the update manager give me the same error.  The error messages says:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have also noticed that on my system monitor my cpu usage has been very high (60% to 100%).  I have only been using this os for a few weeks. I am not sure if that would be a related problem or not.

I would greatly appreciate any advice or help anyone can give me on this.
Thanks!

---

### Post by overdrank on 2009-01-20
> **Spoonstm said:**
> I am new to ubuntu and I am still not very good with it.  I have been having a problem getting anything to install.  Even the updates that come through the update manager give me the same error.  The error messages says:
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I have also noticed that on my system monitor my cpu usage has been very high (60% to 100%).  I have only been using this os for a few weeks. I am not sure if that would be a related problem or not.

I would greatly appreciate any advice or help anyone can give me on this.
Thanks!

Hi and welcome, have you tried using the command suggest ```
sudo dpkg --configure -a
``` In the terminal located under applications, accessories.

---

### Post by Spoonstm on 2009-01-20
That worked! thank you so much for your help!

---

