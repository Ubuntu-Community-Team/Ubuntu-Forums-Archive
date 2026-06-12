---
title: "Uninstall Ubuntu Server and replace with desktop"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by pavsid on 2009-03-13
Hi, recently i installed Ubuntu server over the top of desktop, however now i want to switch back - is it possible to uninstall server in order to revert to desktop without losing all my data?

Thanks

---

### Post by avtolle on 2009-03-13
Do you have a separate partition created for home? If so, install the Desktop on the existing root (mount point /) partition. If no separate partition for home, transfer your data files to external media and then reinstall them after installing the Desktop edition. 

N.B. Even if you have a separate partition for home, backing up your data files is a good idea; "better safe than sorry". It goes without saying that a routine back up of data files is recommended "best practice" in any event.

---

### Post by zvacet on 2009-03-13
Making separate home partition will help you.After making separate home just install desktop edition on the root partition.[This]("http://psychocats.s465.sureserver.com/ubuntu/separatehome") is good guide for making separate home.

---

### Post by pavsid on 2009-03-13
Hi,

i have a separate home partition but don't want to have to re-install any programs etc - will they be ok?

I'd rather just change the grub menu round so it boots into generic by default than risk having to reinstall all my programs

Thanks

---

### Post by avtolle on 2009-03-13
If you do a reinstall of Desktop, AFAIK you will loose your programs (I presume this means various application packages which you have installed). From the rather cryptic comment about Grub, I presume you contemplate as an alternative course of action installing the Desktop edition on another, separate partition, which could be an option; but if the "programs" are in the server installation, you would need to boot to it to run them, if you do not install them under the Desktop edition. 

Someone more knowledgeable than I could likely discuss creating a separate /usr partition (I believe that is where most applications install) but this likely would be more troublesome than installing the Desktop edition and the desired programs independently, IMO.

---

### Post by pavsid on 2009-03-13
> **avtolle said:**
> If you do a reinstall of Desktop, AFAIK you will loose your programs (I presume this means various application packages which you have installed). From the rather cryptic comment about Grub, I presume you contemplate as an alternative course of action installing the Desktop edition on another, separate partition, which could be an option; but if the "programs" are in the server installation, you would need to boot to it to run them, if you do not install them under the Desktop edition. 

Someone more knowledgeable than I could likely discuss creating a separate /usr partition (I believe that is where most applications install) but this likely would be more troublesome than installing the Desktop edition and the desired programs independently, IMO.

No problem, i was planning to install 64bit soon anyway so will just bear with it till then, just wanted to know if it was as easy to revert back as it was to 'upgrade'. I guess not though!

Thanks for your help

---

### Post by zvacet on 2009-03-13
@ **pavsid**

All packages you installed with apt-get are in /var/cache/apt/archives.You can use **aptoncd** (it is in synaptic) and make CD/DVD of all your packages.See [here]("http://aptoncd.sourceforge.net/") about aptoncd.

---

### Post by nonconventional on 2009-03-13
Before you do anything drastic, you don't need to do any reinstall or worry about partitions. GRUB should reconfigure itself to handle any kernels that have been removed.

Use:
dpkg --getselections>packagelist.txt
edit packagelist.txt to leave only things that you wany manually installed and ubuntu-minimal
dpkg --clearselections
dpkg --setselections<packagelist.txt

And then I don't remember exactly how to actually apply the settings. I think running dselect is one way. Actually, just apt-get would probably work since they all use the same list for requested status. Try it and see.

---

### Post by pavsid on 2009-03-14
Thanks for your help folks, i'll give them a go and see what happens....

---

### Post by pavsid on 2009-03-14
> **nonconventional said:**
> Before you do anything drastic, you don't need to do any reinstall or worry about partitions. GRUB should reconfigure itself to handle any kernels that have been removed.

Use:
dpkg --getselections>packagelist.txt
edit packagelist.txt to leave only things that you wany manually installed and ubuntu-minimal
dpkg --clearselections
dpkg --setselections<packagelist.txt

And then I don't remember exactly how to actually apply the settings. I think running dselect is one way. Actually, just apt-get would probably work since they all use the same list for requested status. Try it and see.

Getting this error:

```
dpkg: unknown option --getselections
```

Am i doing something wrong?

---

