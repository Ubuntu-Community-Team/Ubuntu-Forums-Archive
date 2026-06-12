---
title: "Downsides of PAE to support 8GB RAM"
date: 2012-04-01
forum: Hardware
---

### Post by OliverHaslam on 2012-04-01
Hi guys,

I'm planning on upgrading my home server to 8GB of RAM from the current 2GB that is in there. Unfortunately the machine is running a 32-bit version of 11.10.

My question is this: am I OK just enabling APE, or do I really need to format and install a 64-bit release?

I'm loathe to format as I've used the machine as a learning tool, and thus has various things installed such as LAMP, support for an Apple Time Machine backup system and the like. I really don't want to have to start afresh.

Any thoughts on the best course of action or, even better, a good way of doing the reformat/install without having to start afresh?

Cheers guys!

---

### Post by Morbius1 on 2012-04-01
The thing about PAE is that more ram can be accessed in total but you are limited to the normal 4GB barrier by process or application so it depends on what you are trying to do.

For example, I have 16GB of ram on my system and I have a 32 bit PAE OS. I cannot create a Virtual Box guest and specify a ram of 6GB. But I can create 2 VBox guests that have 3GB each and run both simultaneously.

---

### Post by OliverHaslam on 2012-04-01
> **Morbius1 said:**
> The thing about PAE is that more ram can be accessed in total but you are limited to the normal 4GB barrier by process or application so it depends on what you are trying to do.

For example, I have 16GB of ram on my system and I have a 32 bit PAE OS. I cannot create a Virtual Box guest and specify a ram of 6GB. But I can create 2 VBox guests that have 3GB each and run both simultaneously.

To be honest I was only going to upgrade to 4GB, but there is a good deal on 8GB at the moment, so I thought I might as well take the extra head-room.

I'd like to be able to run virtual machines, say the main OS with 4GB and a VM with the rest. Should work fine, no?

---

### Post by Morbius1 on 2012-04-01
It has for me.

---

### Post by OliverHaslam on 2012-04-01
> **Morbius1 said:**
> It has for me.

Cheers.

I take it there is no easy way to switch to 64-bit without having to start afresh? What about copying config files out?

---

### Post by Morbius1 on 2012-04-01
I don't think so but I've never tried. In order for 64bits to run efficiently I would think it would need to be accompanied by 64bit applications. 32bit applications can still only address 4GB of memory so .... Anyway, I don't really know the answer to that question :wink:

---

