---
title: "Single Board Computer HD Sharring"
date: 2009-10-22
forum: Hardware
---

### Post by WithoutMeItsJustAweso on 2009-10-22
I recently got a SBC(PCI interface) to run in my tower so two people could be using our computer at the same time.
 
I have ubuntu 9.04 on main computer and 9.10 on the SBC.
 
Everything is running alright but what I want to know is if it is possible to share a HD between the two systems. Not the drives with the OS's but if i put in an additonal HD for simply file storage is it possible for that HD to be plugged into the main backplane and then somehow accessed through my SBC? So that files can be shared between the two without transfering to some form of external media and transfering it over?
 
My end goal is to be able to share files between the two, since their in the same tower and connected in hardware i figured there has to be a way to do this? 
 
My computer knowledge is higher-intermediate i'd say. I'm a recent linux convert so i'm more familiar with windows but i'm learning quick. I am comfortable with command line and c coding.
 
thanks!

---

### Post by lloyd_b on 2009-10-22
> **WithoutMeItsJustAweso said:**
> I recently got a SBC(PCI interface) to run in my tower so two people could be using our computer at the same time.
 
I have ubuntu 9.04 on main computer and 9.10 on the SBC.
 
Everything is running alright but what I want to know is if it is possible to share a HD between the two systems. Not the drives with the OS's but if i put in an additonal HD for simply file storage is it possible for that HD to be plugged into the main backplane and then somehow accessed through my SBC? So that files can be shared between the two without transfering to some form of external media and transfering it over?
 
My end goal is to be able to share files between the two, since their in the same tower and connected in hardware i figured there has to be a way to do this? 
 
My computer knowledge is higher-intermediate i'd say. I'm a recent linux convert so i'm more familiar with windows but i'm learning quick. I am comfortable with command line and c coding.
 
thanks!

Having two computers accessing the same hard drive is pretty much guaranteed to produce errors - there should be one and only one OS in control of the drive, otherwise there'll be consistency errors in the disk caches/buffers of the two OSes.

I know little of SBC's, so all I can do is ask questions.  Is there some sort of network connection between the two machines?  If so, then standard network sharing (Samba or NFS) would probably be the way to go (have the main tower OS acting as a server, and the SBC connecting as a client).  

(Ideally, it *should* be possible to implement the networking over the PCI bus, which would be super fast, but Google hasn't turned up any information on whether this is supported.)

Lloyd B.

---

