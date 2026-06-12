---
title: "Embedded Linux - Thin Client"
date: 2006-05-10
forum: Hardware &amp; Laptops
---

### Post by bluecherry on 2006-05-10
Hi all,

I'm thinking of building a thinclient, just to get some hands-on experience. 
If I ever succeed I'll probably use it as an extra workstation that connects to either a Win32 or Ubuntu desktop over the network.

I'm just really interested in this thinclient - server stuff.

My Own Research on hardware:

**IDE based Flash Drives**
Transcend 256MB: €20,10
Transcend 512MB: €26,60

**System**: 
*256MB RAM
* CPU VIA 800Mhz/1Ghz
* Barebone: Lex-Systems Neo 
[http://www.myelectronics.nl/index.html?lang=en-us&target=d159.html](http://www.myelectronics.nl/index.html?lang=en-us&target=d159.html)

**My questions:**
* Does anyone know Lex-Systems? I've found this manufacturer's products all over the place, but couldn't find a website.

* Which Flash drive should I choose? 
- I would go with 256MB since it 'll be a custom streamlined linux build with only the very necessary functions and almost no local apps. Maybe leave some space free as a buffer for data that needs to be stored on the NAS/server?

* How efficient would running a remote desktop be? 
1. Will an X-based app require equal host and client memory (eg: someapp requires 1056KB to run locally, in this setup will it require 1056KB from host AND client?). Any benchmarks on this available?

2a. Does this affect general network performance? I'm sure it does... 
We've got 100Mbit/s wired everywhere so I suppose 1 thinclient won't have a big impact, but what happens if I decide to run 4 or 5? 

2b. And just out of interest, how do companies running hundreds of thinclients map their network..

* Suggestions on software to include in the custom build to make it all work? - *I know there are thinclient distro's out there, and I'm already looking at what they are including, but where's the fun in installing an out-of-thebox linux? I want to build my own, streamlined version :D.*

* Any experience, please share! I'm intreged by the idea of building my own embedded device :-).

***I'm still looking into online resources, but would really like to hear your personal experiences!***

Thanks all!

---

### Post by jdusablon on 2006-05-10
A thin client typically has no local media except removable, like CD or floppy. In most thin client environments, the thin client boots from the network and receives a small image from a server, which it loads into memory. This image contains just enough software (network drivers, VNC, CITRIX or RDP client, etc.) to allow it to connect to a terminal server of some type, where all the apps will actually run. Dedicated (hardware) thin client already have a very small "OS" built in, so booting from network isn't necessary for them.

Given that, if you really would like to experiment with thin clients, start with a super cheap computer and try to create a diskless boot environment. I suggest [http://ltsp.org/](http://ltsp.org/) and [http://k12ltsp.org/](http://k12ltsp.org/) which has actual pre-built server distros and plenty of thin client how-tos.

1. No. In such an environment, apps run on the server, so the server needs more RAM than the client(s) by far. Modern dedicated thin client machines only use 128MB or 256MB, while serious terminal servers will often have 4GB or more.

2a. 100 MB/s Network should be fine, but don't expect to run a thin client network on hubs or very cheap switches without some trouble. In scenarios I've dealt with, the network activity lights stay ON constantly.

2b. I don't really know what you mean by "map their network," but be sure that your servers can handle the load, since they'll be running everything. Again, [http://ltsp.org/](http://ltsp.org/) will give you an idea of what to expect. *hint* for more than 4 or five clients, you better have gobs of RAM.

---

### Post by bluecherry on 2006-05-10
Niiice 8) .

I thought I was really smart finding these flash drives as an alternative to a hd, but if I don't even need those to boot.
So I guess everything will be loaded directly into memory and kernel-img updates are just a 'replace on server-side' matter?!

...awesome! 

Sorry, I'm pretty new to this all and I feel like a kid in a candyshop :). Still need to get used to the flexibility of Linux after years of Windows.

I'm already reading the wike and docs at  [http://ltsp.org/](http://ltsp.org/), will check [http://k12ltsp.org/](http://k12ltsp.org/) out later today.

Thx!

---

### Post by bluecherry on 2006-05-10
[QUOTE=jdusablon]
2b. I don't really know what you mean by "map their network," but be sure that your servers can handle the load, since they'll be running everything. Again, [http://ltsp.org/](http://ltsp.org/) will give you an idea of what to expect. [/QUOTE]

I meant; dealing with a large number of thinclients requires a lot of network bandwidth (at least I assume it does). So how do companies with hundreds of thinclients connecting to servers all day cope with that? Running a Gbit network wouldn't be enough I expect. 

But I guess they just layout their network to provide enough bandwidth to each station, so that mistery is solved :).

Thx!

---

### Post by jdusablon on 2006-05-10
Larger setups will have more than one server and will also break up the server duties to lighten their loads. For a 100-client environment, home directories might go on one dedicated storage server, and 2 or 3 beefy servers probably handle the terminal server duties. I would run gigabit in a heavy environment like this, but one could probably get away with 100Mb/s, depending on the type of apps required.

---

### Post by bluecherry on 2006-05-10
Thx for your help!

I'm going to have to experiment and find out the rest by myself ;).

---

