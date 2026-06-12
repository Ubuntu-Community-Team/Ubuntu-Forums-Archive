---
title: "problem with kernel 2.6.27-13 generic"
date: 2009-03-07
forum: Installation &amp; Upgrades
---

### Post by zozio32 on 2009-03-07
Hi,

I have installed the 2.6.27-13 generic kernel a few days ago, and my Ubuntu turn into a black screen before getting to the login screen.
I am now using the previous that was fine, 2.6.27-12 generic.
I am using it on an xps 1330 dell laptop, and I am running Intrepid.
How can I uninstall the latest one?

---

### Post by mikewhatever on 2009-03-07
You can do it from Synaptic or <sudo apt-get remove linux-image-2.6.27-13-generic>

---

### Post by soltanis on 2009-03-07
I have the same problem; black screens on the 2.6.27-13 kernel, but the 2.6.27-12 boots fine.

Relevant log attached; I think that the kernel developers would do better with it though.

---

### Post by jrb114 on 2009-03-11
Just to add a me too, to this. Running using the nvidia drivers, although it seems to be nothing to do with that as Ctrl-Alt-F1/2/etc failed to get out of it. 

Hope this gets fixed, seems a bit of a critical bug to me. Check launchpad and having a quick Google I can't seem to find any other information about it.

2.6.27-12 works fine, though.

=== edit ===
I stand corrected. See below two links.

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1086852](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=1086852)

and

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337019/](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/337019/)

---

### Post by mikewhatever on 2009-03-12
I rather doubt it would get fixed, at least not until 2.6.27-13 is the current version for Intrepid.
[http://packages.ubuntu.com/search?suite=intrepid&searchon=names&keywords=linux-image](http://packages.ubuntu.com/search?suite=intrepid&searchon=names&keywords=linux-image)

---

### Post by bossfn on 2009-03-13
+1
Thanks for the tip on removing the kernel, sick of hitting esc and selecting -11 every time i start up my laptop!

---

### Post by trananhquanapt on 2009-03-16
My Laptop is Dell Precision M4300, and i had the same error :(
Thanks for your tip

---

