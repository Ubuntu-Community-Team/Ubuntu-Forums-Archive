---
title: "Help-Recommended Hardware for running Ubuntu LTSP for - 100users"
date: 2008-07-03
forum: Hardware
---

### Post by Avinash.Rao on 2008-07-03
Dear all,

I would like to know the recommended hardware to run Ubuntu Studio or Ubuntu Desktop edition with LTSP. I will have about 100 users connecting to the ubuntu server machine through LTSP! 
Currently, i am running it on a new AMD 64-bit workstation motherboard with 2GB RAM and i have tested 10 users and its seems to be working fine. Below are my requirements.

1) LTSP + DHCP
2) Squid - Broadband Modem connected to the server machine and Proxy configuration - so 2 NIC's
3) File Server- about 20-25 windows clients may access the server through SAMBA to store their files.
4) 100Mpbs LAN
5) Client hardware are mixed, they have a minimum of 512MB RAM + P4.

I heard there is a hardware benchmark to run specific OS and services. 
What hardware configuration do you recommend to run these services. I just want to rule out all hardware issues before deployment.


Thanks in advance
Avinash

---

### Post by Avinash.Rao on 2008-07-03
Kindly help.

---

### Post by dominiquec on 2008-07-03
Hi, Avinash:

It depends.  LTSP server sizing involves a lot of hand-waving guesstimates.  You might want to start with the sizing guide at [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html)

For example, memory considerations:

> Edubuntu, being a GNU/Linux based operating system, makes efficient use of memory. The usual formula that's used for adding memory to a thin client server is:

256 + (128 * users) MB

So, if your target is to have a server with 20 terminals, you'll need:

256 + (128 * 20) = 256 + 2560 = 2816 MB

Rounding up, you'll need 3 1 Gig simms. Making sure you've got enough memory is the single most important thing you can do to help the performance of an Edubuntu/LTSP thin client server. If you do not have enough memory in your server, you'll find your server will have to use the hard drive as an overflow "virtual" memory. Hard drives are much slower than memory, so you'll find things getting very slow if this happens.

If you intend to make heavy use of graphics work in your curriculum, you may want to add even more, perhaps doubling the previous estimate. 

There's more on CPU, disk, and network in the document.

In the end, it depends on your workload.

If you realize you can't support 100 clients on a single server, you may need to add additional LTSP servers and split the workload among them.

---

### Post by dominiquec on 2008-07-03
Another solution you might want to look at is Diskless Remote Boot Linux. [http://drbl.sourceforge.net/](http://drbl.sourceforge.net/)  This solution is more ideal if you're using newer machines (more CPU and more memory and built-in networking) for your clients.

Unlike LTSP, you don't run the applications on the server; you run them on the clients themselves.  They just access their disks remotely (though no disks are needed if you're using some LiveCD image as your operating system.)

Your mileage with this, as with LTSP, may vary, though.

---

### Post by Avinash.Rao on 2008-07-04
I will go through the document. But, would this be the same for Ubuntu, i guess similar? 

> **dominiquec said:**
> Hi, Avinash:

It depends.  LTSP server sizing involves a lot of hand-waving guesstimates.  You might want to start with the sizing guide at [http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html](http://doc.ubuntu.com/edubuntu/edubuntu/handbook/C/server-hw.html)

For example, memory considerations:



There's more on CPU, disk, and network in the document.

In the end, it depends on your workload.

If you realize you can't support 100 clients on a single server, you may need to add additional LTSP servers and split the workload among them.

---

### Post by dominiquec on 2008-07-04
Edubuntu is a Ubuntu variant, but with LTSP components as well as educational tools.

---

### Post by Avinash.Rao on 2008-07-04
I have not checked the server edition OS. I started with Ubuntu 7, then Studio, installed LTSP and it worked fine. Studio is more off a Desktop OS.

Will i be able to run LTSP  in the server edition? will the clients get the GUI, coz i heard the server edition doesn't come with GUI or is not enabled or installed by default.

What OS do you suggest to run SQUID, LTSP, DHCP, File Server etc?

---

