---
title: "Minimal (local)install for NFS over WIFI"
date: 2009-09-01
forum: Installation &amp; Upgrades
---

### Post by DJJo on 2009-09-01
hello.

I want to run ubuntu with minimal installation so i can run NFS over my wifi. 
i dit run with out a local harddisk. but i need a cable connection.

I think of putting /boot and /lib on my local disk?
but does this work? or do i have to do something else?

---

### Post by DJJo on 2009-09-01
no buddy?

---

### Post by denver on 2009-09-01
I've personally had bad experiences with remote file systems. They are great if you need access to non critical files, but if you wish to run you ubuntu system over wireless on a NFS mounted volume...well thats not the best ideea. Wifi is slow and you might end up waiting minutes for tasks that would normally take seconds.

To get NFS working on a standard ubuntu system all you need is the nfs-common package. That will install the portmap daemon and other dependencies, but like i said...i dont think its a good ideea to run your system on a NFS volume over WiFi.

---

### Post by DJJo on 2009-09-01
I know wat to install. but i want to install it on my local disk end the rest on my NFS

---

### Post by DJJo on 2009-09-02
no buddy?

---

### Post by DJJo on 2009-09-05
I was planning on putting this project behind me . until i readed a article in linux magazine (the Dutch version) about directory structure.

So now I was thinking to put "boot", "bin", "etc", "lib", "sbin" and "root" on my root(/) partition. and the rest i mount on my NFS partition.

but does this work[SIZE=4]
[/SIZE]

---

### Post by jerrydahfe on 2011-01-13
> **DJJo said:**
> hello.I want to run ubuntu with minimal installation so i can run NFS over my wifi. i dit run with out a local harddisk. but i need a [[COLOR=#000000]cable[/COLOR]](http://www.violetin.net/ja/fitness/acne-on-body-are-pimples-on-self-esteem.html) connection.I think of putting /boot and /lib on my local disk?but does this work? or do i have to do something else?This is what I'm looking for, Thanks for your explanation!

---

