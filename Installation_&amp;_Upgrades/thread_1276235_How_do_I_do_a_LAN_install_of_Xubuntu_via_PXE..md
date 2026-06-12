---
title: "How do I do a LAN install of Xubuntu via PXE."
date: 2009-09-26
forum: Installation &amp; Upgrades
---

### Post by running_rabbit07 on 2009-09-26
The laptop I am trying to install Xubuntu 8.04 on is an old HP Omnibook with no CD ROM drive and the BIOS does not see USB devices. 

There is no working OS on the laptop.

It does give the ability to be booted over the network via PXE 2.1.

I have downloaded the ISO and need to know how to get the network set up to install to the laptop.

Can anyone help me out?

Thanks.

---

### Post by jflaker on 2009-09-26
no CD huh?  Do you have a USB port?

---

### Post by running_rabbit07 on 2009-09-26
BIOS doesn't see them.

---

### Post by jflaker on 2009-09-26
did you attempt a USB boot?

---

### Post by running_rabbit07 on 2009-09-26
> **jflaker said:**
> did you attempt a USB boot?

I have tried with a unetbootin loaded thumb drive and external CD ROM. BIOS does not see USB devices.

---

### Post by rreese6 on 2009-09-26
how about a floppy drive?:
you could install a small distro.
partition the HD.
then download a mini.iso
mount the iso
install from the HD using a network install.

---

### Post by running_rabbit07 on 2009-09-26
That sounds good. My only problem is getting a Floppy. None of my working systems have a floppy drive.

---

### Post by running_rabbit07 on 2009-09-26
If at all possible, I would like to do this with a crossover cable.

---

### Post by rreese6 on 2009-09-26
then go to Google and start reading up on making a PXE server. so you can connect to it...I have never used PXE Network installation...
Although I had installed a system through tftp years ago...I don't think that will work here, sorry

---

### Post by running_rabbit07 on 2009-09-27
Alright. I think I have found the best tutorial that goes in depth and is as close as I think I'll find to being usable for installing Xubuntu. Does anyone know how to add Ubuntu repositories instead of Debians in the last few commands on this [link]("http://www.debian-administration.org/articles/478")?

Again, thanks.

---

### Post by rreese6 on 2009-09-27
Hey Rabbit, take a look at this site, I just happened to stumble upon ;)

[http://www.pyrosoft.co.uk/blog/2008/04/03/setting-up-a-pxe-install-for-linux/]("http://www.pyrosoft.co.uk/blog/2008/04/03/setting-up-a-pxe-install-for-linux/")

this one seems much better and uses Ubuntu 8.04LTS server.

Let us all know how this is coming along..and take notes...it will be easier to fix or to do again...maybe you could write a tutorial and we could attach it to our sigs.

Have fun:popcorn:

---

### Post by running_rabbit07 on 2009-09-28
I am working on using the link you provided. The Debian one is having install issues.

---

### Post by running_rabbit07 on 2009-10-01
I installed the DHCP3, but it will not start. Does anyone know what commands I have to give it?

---

