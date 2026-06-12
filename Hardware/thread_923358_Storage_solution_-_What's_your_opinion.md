---
title: "Storage solution - What's your opinion?"
date: 2008-09-18
forum: Hardware
---

### Post by zenkaon on 2008-09-18
Hello all,

I am looking to buy some new hardware and I would like to hear some peoples opinion and get some advice. I am looking to add a 1TB+ storage solution to my home network.

I currently have a PC which runs XP and Ubuntu and I have 2 laptops which run Ubuntu. My better half has a work laptop running XP. I have a Buffalo WHR-HP-G54-1 wireless router running the openWRT embedded Linux distro.

I am looking for a storage solution which I could plug into my router via ethernet and allow me access to the hard disk from any of my PC/laptops without having to rely on any of the other PC/laptops being on.

Ideally the hard disk will be fully encrypted and have LVM managing various ext3 partitions with a samba share for the XP boxes. This is not essential, but desirable. The main thing is that both the XP and Linux machines can read and write.

Looking at the market, I see external hard disks which attach via USB, which is not the solution I am looking for. I also see hard disk cases which have ethernet and you plug in your own 3.5" IDE drive. I'm not sure how some of these devices play with Linux.

Can anybody offer me some advice about what hardware to buy / what to avoid? Also, if anybody has done anything similar, I would like to hear how you have done it and how you feel your solution works.

---

### Post by TigerWolf on 2008-09-18
I am unsure about many solutions that are able to do what you want that are just a hard drive and plug into the network. Would you consider a mini server to do you needs? It wouldn't have to be very powerful at all and cheap.

---

### Post by SecretCode on 2008-09-18
I haven't investigated the area myself ... although it's on my to-do list. I believe there are lots of offerings. The key term you should look for is "Network-attached storage" or NAS. This is just what you've defined, a hardware device that connects to your ethernet and provide Samba/CIFS or other protocols (NFS? ftp? ...), with really any kind of stripped-down OS that provides those protocol interfaces. And some web admin.

I've seen Netgear punt their offerings quite heavily but I don't know about their quality. One place to start looking might be [Network-attached storage - List of hardware suppliers](http://en.wikipedia.org/wiki/Network-attached_storage#List_of_hardware_suppliers).

I see no reason why any wouldn't work with Ubuntu - but you shd prob check with the vendor for "Linux support"

---

