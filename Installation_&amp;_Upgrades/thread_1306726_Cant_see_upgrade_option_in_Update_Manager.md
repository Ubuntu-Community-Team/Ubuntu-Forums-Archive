---
title: "Cant see upgrade option in Update Manager"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by ilano on 2009-10-30
Hi,

I am not sure if there is a problem with my synaptic or sources.list.

I think I have fully updated 9.04.

However I do not see any option to upgrade to 9.10

I don't know if this is the cause.

Lately I am getting this error when reloading sources:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

How do I fix this?

TIA

ilano

---

### Post by corncob on 2009-10-30
Go to System > Administration > Software Sources, then to the Updates tab.  At the bottom of the box (Release Upgrades), change it to "Normal Releases".

---

### Post by ilano on 2009-10-31
It already is selected. Normal Releases

---

### Post by corncob on 2009-10-31
I don't know what else to say then.  I'm having my own upgrade problem: it stopped cold at "fetching file 912 of 1988".  Looks like I'll just have to cancel and start over.  I might save my home folder and go for a fresh install.  That worked fine on my netbook and it formatted it to ext4.  Upgrading, somebody correct me if I'm wrong, will keep the ext3 format.

---

### Post by JBAlaska on 2009-10-31
Did you try:
```
sudo apt-get dist-upgrade
```

---

### Post by ilano on 2009-11-02
i dint know about that. Shall give it a try. Thanks

---

### Post by ilano on 2009-11-02
That didnt work either:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

What do I do... Is there an issue with my sources.list

---

### Post by zey on 2009-11-02
i have the same problem with you. its not shown on update manager.

so i do a fresh install ubuntu 9.10

and its good.. i have no problem with the installation

just dont forget to backup your data first...


i recommend you to do the same as me.

---

### Post by sherk on 2009-11-21
I also Cant see upgrade option in Update Manager when upgrading from 9.04 to 9.10 plz help anyone

---

