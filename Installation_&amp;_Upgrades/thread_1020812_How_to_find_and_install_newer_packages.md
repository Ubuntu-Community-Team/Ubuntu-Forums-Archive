---
title: "How to find and install newer packages?"
date: 2008-12-24
forum: Installation &amp; Upgrades
---

### Post by mfyahya on 2008-12-24
I'd like to install a newer version of Asterisk. The version supplied with 8.10 is 1.4, but 1.6 is available on the Asterisk website. I'd rather not download and install from source tarballs manually. Is there an ubuntu repository for newer packages? Something like Debian testing or unstable? 

I've seen .deb src packages as well. How do they work? If I install from that, will APT know that Asterisk is installed, and account for it when calculating dependencies?

Any pointers or links to documentation would be most appreciated. TIA

---

### Post by 2hot6ft2 on 2008-12-24
System>Administration>Synaptic Package Manager then settings>Repositories then Updates tab and select Unsupported Backports close then hit reload and bam more current unsupported versions.

---

### Post by zeronothing on 2008-12-24
have you looked into creating your own .deb packages from source. it took a little time but I got the hang of it. so if something new comes out I can take the source and create a .deb package compatible with my current version of ubuntu. after you do it a couple of times it becomes very simple.

---

### Post by mfyahya on 2008-12-24
I had unsupported backports enabled already. It didn't fetch the latest version of Asterisk.
Does Ubuntu have any other repositories?

---

### Post by Partyboi2 on 2008-12-25
Asterisk 1.6 is not in the ubuntu repos yet. Because its a rc1 you might be better of compiling it or wait till someone comes out with a deb package for it.

---

### Post by namdung on 2008-12-25
> **mfyahya said:**
> I'd like to install a newer version of Asterisk.

If you are considering a PBX system with Asterix consider the following:

[http://www.elastix.org/](http://www.elastix.org/)
[http://pbxinaflash.net/](http://pbxinaflash.net/)

With a little help from friend Google u'll find more options.

I myself am in the middle of Elastix implementation and found it very easy and useful.

---

