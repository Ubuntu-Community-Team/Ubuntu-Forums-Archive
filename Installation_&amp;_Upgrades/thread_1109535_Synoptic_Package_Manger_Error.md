---
title: "Synoptic Package Manger Error"
date: 2009-03-28
forum: Installation &amp; Upgrades
---

### Post by pastormatt on 2009-03-28
I searched the documents and forums to no avail. If this is addressed somewhere, I aplogize and ask you to direct me there.

I tried to install cairo dock and now I am getting this error when I open the Synaptic Package Manager: E: Type 'dep' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report. 
Looks to me like I typed something wrong, dep instead of deb? I am not sure how to "go to repository dialog to correct the problem"...Any assistance would be much appreciated.

ubuntu 8.10

---

### Post by ooburns on 2009-03-28
In a terminal, do ```
gksu gedit /etc/apt/sources.list
``` There's probably a line in that file that starts with 'dep'. Change it to deb, save, and try again.

---

### Post by pastormatt on 2009-03-28
gksu gedit /etc/apt/sources.list worked.
Thank you very much!

---

