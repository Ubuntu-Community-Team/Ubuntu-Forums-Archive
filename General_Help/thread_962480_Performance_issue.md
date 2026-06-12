---
title: "Performance issue"
date: 2008-10-29
forum: General Help
---

### Post by mnrbig on 2008-10-29
Hi all

I have a 3 client edubuntu setup at home.

Specs:

Software: Edubuntu 8.04.1

Server: Athlon 64 3700+
        1 Gig Ram
        60Gb ATA 100 HDD

Clients: 800 mhz CPU
         128Mb Ram

Network: Server Dual 100Mb Lan Cards
         3 Com Router
         100Mb Lan Cards for clients


My problem is peformance. I use the server as a workstation and have 3 thin clients connected.I am able to log into the thin client with no issue, however when I attempt to do anything of use on the system i.e browse the internet,the thin client and server slow down so much, that they become unusable. This occurs when I use only one client.

I have setup the server according to the documenation found on the Edubuntu docs and have enable port forwarding and NAT transversal.

Does anyone have any ideas as to the cause of this? 
 
Thanks

---

### Post by Titan8990 on 2008-10-29
Have you checked to see if you BIOS supports hardware virtualization? It will work without it but will run slow as you are experiencing. Sometimes it is not on by default so you may want to check your BIOS to make sure that it is enabled.

Are you trying to use a terminal across the internet? I doubt that will ever work well due to the low amount of bandwidth that can usually be attained across the internet.

What type of software are you using on your server for your terminal clients?

Couple things to look in to there.

Edit: Also, I don't think that 1GB of RAM would be enough to support 3 clients.

---

### Post by mnrbig on 2008-10-30
Hi

Thanks for the reply

My bios doesn't support virtualization. - Only hyperthreading

I am not using the terminal over the internet, but the terminals are very slow when using it.

The software is ltsp5

I will look at memory, but according to the docs, i only need 128m per terminal and 2000 mhz cpu should be enough for 20 clients.

---

### Post by Titan8990 on 2008-10-30
I would say that lack of virtualization support is probably where your performance drain is coming in.

Now, about CPU clock rates. The clock speed of a CPU has not been a good indication of its performance for about the past 3 years. My 2.66 Ghz Core 2 Duo would absolutely destroy a 4Ghz single core CPU in many performance benchmarks. This is not just due the addition of multiple cores but the fact that many new chips (especially from Intel) can perform more operations per clock cycle than older CPUs.

> I will look at memory, but according to the docs, i only need 128m per terminal and 2000 mhz cpu should be enough for 20 clients.

I wouldn't run my own computer on only 1Gb of RAM let alone 20 others....

---

### Post by alienprdkt on 2008-10-30
I see what your saying I ran thin clients on windows 2003 server with 5 clients and only 1 gb ram and a p4 2.4GHz. (must add it didn't do too much, just internet browsing, text editing, and common things) It should be able to handle it. I would try a different distro for thin client computing.

This should be an easy task for a pc. Along with your problems  I have an intel core-duo 3.0GHz 2 gb ram, and an AMD Athlon 64 X2 6000+ 3.0GHz again with 2gb ram. When trying to connect to either one of these with VNC, NOMACHINE, or just plain old remote viewing. It runs terribly slow. I had gentoo running on these machines before and the same romote functions worked great!!! which makes me believe that Ubuntu has a hard time with terminal services. This is no longer an issue for me for security reasons I now only administer my box on site.

My guess would be for Thin clients try a different distro if increasing ram dosen't solve anything.

---

### Post by mnrbig on 2008-10-31
I have increased the Ram in the thin client to 256mb. There was not remarkable change in performance. Shurely my specs will be sufficient for one terminal?

---

### Post by alienprdkt on 2008-10-31
> **mnrbig said:**
> I have increased the Ram in the thin client to 256mb. There was not remarkable change in performance. Shurely my specs will be sufficient for one terminal?
Should be yes, but like I said (I don't know if I am the only one experiencing) performance issues with Terminal Services in Ubuntu. Weather it be thin client, or remote desktop connection of any kind, runs very slow and choppy. (well for me,) with both of my dual core 3.0GHz, 2gb ram (intel and amd64x2) on just a local LAN.

---

