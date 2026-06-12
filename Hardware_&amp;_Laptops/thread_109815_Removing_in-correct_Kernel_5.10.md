---
title: "Removing in-correct Kernel 5.10"
date: 2005-12-29
forum: Hardware &amp; Laptops
---

### Post by Nightwind on 2005-12-29
Hi Ya'll
Today is not my day, this should be posted in upgrades, my apoligies.
We made  boo boo :rolleyes: and installed the incorrect kernel, wanted the 686 for a Pent II dual cpus box but after installing it we have a kernel panic. We can boot to the 386 kenel when we stop grub and select the 386.
Questions are: Can we remove the incorrect kernel? If so how? Did I missunderstand the post on the 686 and it will not work on Pent II dual cpus. I also think that we installed the K-7.  Please understand I am 700 miles from the computer and my brother is trying to do this via the phone 

Worst case we can rebuild the box, but would rather not.
Thanks
Trish 
We will not give up!

---

### Post by chimera on 2005-12-29
sudo apt-get remove kernel-you'd-like-removed     (make sure it's not the one you're currently booted in)

---

### Post by Nightwind on 2005-12-29
[QUOTE=chimera]sudo apt-get remove kernel-you'd-like-removed     (make sure it's not the one you're currently booted in)[/QUOTE]
Thank you  SO much. We love Ubuntu and the people that are here are so understanding and helpful. I talked my brother in to trying Ubuntu and he loves it too even though we are Newbies to it in a BIG way. I am going to get the rest of my family (in 5 states hooked too).
I'll post back with the details.
Thanks again!

---

