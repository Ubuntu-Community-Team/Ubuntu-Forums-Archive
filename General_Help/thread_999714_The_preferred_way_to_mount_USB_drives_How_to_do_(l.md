---
title: "The preferred way to mount USB drives How to do? (ltsp-related)"
date: 2008-12-02
forum: General Help
---

### Post by lievendp on 2008-12-02
Hello,

I'm currently looking for a solution to automount usb drives. 
After looking around on the net here and there, I see there are various ways to automount an usb stick. But which is currently the best way to do it? There should be no desktop interaction. Already tried autfs without success.

My system is a xubuntu 8.04.1 with ltsp-server-standalone v5.0.40 installed and I followed the ubuntu & ltsp guide + troubleshooting for local devices.
When someone puts a usb drive in one of the client systems, I can see the usb showing up with dmesg, partitioned and all and I can mount it manually.
However, automount doesn't work at all (I tried autofs)

So the problem is related to ltsp but my question is a little bigger: How does this work? What is the standard way (daemon??) to automount usb?

thanks!

---

