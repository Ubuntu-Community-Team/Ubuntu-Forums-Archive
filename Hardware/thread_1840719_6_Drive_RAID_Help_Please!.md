---
title: "6 Drive RAID Help Please!"
date: 2011-09-08
forum: Hardware
---

### Post by imperium2335 on 2011-09-08
Hi,

I am quite new to Ubuntu server/Linux and need some help with RAID.

I am trying to setup a file server for my company and I have 6 identical drives.

What I would like is to have a 6 drive RAID 10 setup but my hardware RAID config will only allow a max of 4 in the array.

So what I thought was to have 3 stripped arrays in mirror with each other. i.e. 3 sets of 2 as hardware, then mirror them all using software RAID.

How would I go about setting this up?

Kind regards,

Tom.

---

### Post by imperium2335 on 2011-09-09
Just realised it was the wrong way around.

Regardless, I have tried so many different RAID setups including RAID6 and it seems none of these work with the Ubuntu Server installation.

I have tried 3 hardware stripes (from 6 drives), then strung together using a software mirror, but the installation will not install the boot loader to it.

It will also not install onto a standard hardware or software RAID.

Can someone please help me!

---

### Post by fdrake on 2011-09-09
did you try this [http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx](http://www.ainer.org/raid-5-6-install-setup-configuration-guide-for-ubuntu-10-04-lts-lucid-lynx) ?

since you r installing a server will be bater to install a lts version(10.04)

---

