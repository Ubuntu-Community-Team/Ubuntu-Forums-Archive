---
title: "Known issues with Ubuntu server and i7 CPUs"
date: 2011-06-05
forum: Hardware
---

### Post by mrgordonz on 2011-06-05
Hi there,

I am planning to purchase a PC which will be used purely as a host for virtual machines.  I plan to install Ubuntu server 10.04 LTS and VMware Server 2.  The reason I have opted for Ubuntu 10 and not 11 is I have read that there are issues getting VMware Server 2 to run on Ubuntu 11.  I have personally experienced some issues with installing VMware Server on Ubuntu 11 (Desktop edition), whereas on Ubuntu 10 it seems to be much more straight forward.

But that isn't my question.  I want to get a powerful desktop PC (probably from eBay) with 12 GB RAM, and most likely an i7 CPU (eg: i7-960 3.20 GHz).

Are there likely to be any issues running Ubuntu 10 on an i7 CPU?  If so, which quad core processors will play nice with Ubuntu 10?

If there is a processor which works well but it has graphics related issues, that might be OK because I plan to install Ubuntu Server, so it won't have a GUI.

Cheers,

Paul

---

### Post by mrgordonz on 2011-06-06
Or, if I don't limit myself to the i7, does that make a difference?  I have found a PC on eBay which has a Intel i5-2500 (Sandy Bridge) CPU for a great price.  

Will Ubuntu Server (10 or 11) run OK on this CPU?

---

### Post by cascade9 on 2011-06-06
Why on earth would you buy from ebay when brisneyland has several decent computer stores? 

The i7s have more CPU cache than the i5s, which will make a minor difference to virtualisation. Some i5s are only 2 core CPUs as well, which will make a much bigger difference vs 4 core or 6 core i7s. I would guess that the 6 core i7s are out of budget though, the cheapest of them is near enough $600 AU. 

If you wanted 6 cores, go AMD....a 6 core phenom IIs are well under half the cost of a 6 core i7. 

One of the issues you migth hit is if you try to use 'sandy bridge' intel HD video. It should work, but it can be buggy on *buntu 10.XX, you would probably need to get the newer intel video drivers (from a PPA). I'd hope that anybody buying a desktop i7 would avoid sandy bridge video, a decent video card is pretty cheap. 

12GB of RAM is possible with i5s (and non LGA 1366 i7s), but you will lose dual channel memory support. To use dual channel, you would need to get 8GB (2 x 4GB, 4 x 2GB) or 16GB (4 x 4GB, 2 x 8GB).

---

### Post by collisionystm on 2011-06-06
vmware server isn't maintained anymore. Just use vmware player if you choose to use ubuntu as your host os. It works great and will do exactly what you need.

---

### Post by Bucky Ball on 2011-06-06
Long-term support releases recommended for servers so good choice anyhow, regardless of the other issues. Supported until 2015 by which time you'll be ready to upgrade to the current LTS then, 14.04 LTS. ;)

---

### Post by Yellow Pasque on 2011-06-06
The built-in video probably won't work without a new kernel and video driver (maybe you'll be lucky to get a picture with vesa driver and that might be all you need for a server). Also, if the processor has "Turbo Boost" feature, that won't work without a newer kernel (>= 2.6.35 IIRC).

---

### Post by mrgordonz on 2011-06-06
> **cascade9 said:**
> Why on earth would you buy from ebay when brisneyland has several decent computer stores? 

Can you suggest any?  I would like to stay under $1000 if at all possible.  

> The i7s have more CPU cache than the i5s, which will make a minor difference to virtualisation. Some i5s are only 2 core CPUs as well, which will make a much bigger difference vs 4 core or 6 core i7s. I would guess that the 6 core i7s are out of budget though, the cheapest of them is near enough $600 AU. 

If you wanted 6 cores, go AMD....a 6 core phenom IIs are well under half the cost of a 6 core i7. 

One of the issues you migth hit is if you try to use 'sandy bridge' intel HD video. It should work, but it can be buggy on *buntu 10.XX, you would probably need to get the newer intel video drivers (from a PPA). I'd hope that anybody buying a desktop i7 would avoid sandy bridge video, a decent video card is pretty cheap. 

12GB of RAM is possible with i5s (and non LGA 1366 i7s), but you will lose dual channel memory support. To use dual channel, you would need to get 8GB (2 x 4GB, 4 x 2GB) or 16GB (4 x 4GB, 2 x 8GB).

The purpose of the server is solely to host a number of development VMs - a DB server, couple of app servers, that kind of thing.  Nothing I do will require HD graphics - these VMs are purely for web applications and the host will be Ubuntu server.

---

### Post by mrgordonz on 2011-06-06
> **collisionystm said:**
> vmware server isn't maintained anymore. Just use vmware player if you choose to use ubuntu as your host os. It works great and will do exactly what you need.

I didn't think I could create VMs with the player.  I need to create a range of VMs - mostly Windows Server, but the odd Linux VM as well.  Or do you use a service like EasyVMX?

---

### Post by collisionystm on 2011-06-06
> **mrgordonz said:**
> I didn't think I could create VMs with the player.  I need to create a range of VMs - mostly Windows Server, but the odd Linux VM as well.  Or do you use a service like EasyVMX?

yes you can create VM's with the player. I use it all the time. Ever used virtualbox? Same deal, but 100x better.

If you are looking for a nice platform for your server, check out [www.xbyte.com](www.xbyte.com) ( if you are in the states )

---

### Post by psusi on 2011-06-06
> **Temüjin said:**
> The built-in video probably won't work without a new kernel and video driver (maybe you'll be lucky to get a picture with vesa driver and that might be all you need for a server). Also, if the processor has "Turbo Boost" feature, that won't work without a newer kernel (>= 2.6.35 IIRC).

No, the kernel doesn't know or care about Turbo Boost; that is something the motherboard does.

10.04, 10.10, and 11.04 all work fine for me on my i5-2500K.

---

### Post by Yellow Pasque on 2011-06-06
> **psusi said:**
> No, the kernel doesn't know or care about Turbo Boost; that is something the motherboard does.

10.04, 10.10, and 11.04 all work fine for me on my i5-2500K.
Hmm, I've seen some threads where users report otherwise.

---

### Post by psusi on 2011-06-06
> **Temüjin said:**
> Hmm, I've seen some threads where users report otherwise.

That is because they are confused by the fact that the kernel does not *KNOW* about it, and they expect it to.  Silly way for Intel to design it, but that's how it works.

---

### Post by mrgordonz on 2011-06-06
> **collisionystm said:**
> yes you can create VM's with the player. I use it all the time. Ever used virtualbox? Same deal, but 100x better.

If you are looking for a nice platform for your server, check out [www.xbyte.com](www.xbyte.com) ( if you are in the states )

I haven't used virtualbox, but after reading a bunch of reviews I will be giving it a go - especially given that VMware Server is so old and no longer being developed. Although, I never knew you could create VMs with Player.

I am in Australia so xbyte.com is not much good to me. :(

Thx for the tip about virtualbox - sounds like the solution to my problems (although I am a little nervous that it is owned by Oracle - I don't trust Oracle).

---

### Post by collisionystm on 2011-06-06
> **mrgordonz said:**
> I haven't used virtualbox, but after reading a bunch of reviews I will be giving it a go - especially given that VMware Server is so old and no longer being developed. Although, I never knew you could create VMs with Player.

I am in Australia so xbyte.com is not much good to me. :(

Thx for the tip about virtualbox - sounds like the solution to my problems (although I am a little nervous that it is owned by Oracle - I don't trust Oracle).


Oracle is the devil. They destroyed SUN and their open source movement.

Go with VMware player. Here is a screen shot of it on my natty.

---

### Post by tgalati4 on 2011-06-06
If I was setting up a similar machine I would purchase a used Dell 1950 or 1750 (loud fans) for around ~300 US, add some RAM and bigger disks and compile a custom Xen hypervisor kernel for Lucid.  You will get a solid dual processor (4 cores total) machine with decent I/O performance.  Add a low-profile nVidia card and you will have a killer machine that could host hundreds of VM's.

---

### Post by collisionystm on 2011-06-06
> **tgalati4 said:**
> If I was setting up a similar machine I would purchase a used Dell 1950 or 1750 (loud fans) for around ~300 US, add some RAM and bigger disks and compile a custom Xen hypervisor kernel for Lucid.  You will get a solid dual processor (4 cores total) machine with decent I/O performance.  Add a low-profile nVidia card and you will have a killer machine that could host hundreds of VM's.


Maybe not Hundreds =)

Each windows VM will need atleast 1gb of ram to avoid getting paging file errors. So I would say you could host up to 55-60 virtual machines on a 64gb box... but that would cost a bundle of cash. Your 300 dollar server suddenly turned into 20,000.

---

### Post by mrgordonz on 2011-06-06
> **collisionystm said:**
> Oracle is the devil. They destroyed SUN and their open source movement.

Go with VMware player. Here is a screen shot of it on my natty.

But I plan on only using Ubuntu Server (ie: no GUI).  Is VMware player any good on Ubuntu Server?  Plus, I notice in your screenshot that to take snapshots I need to upgrade to Workstation - I need to be able to take snapshots.

---

### Post by collisionystm on 2011-06-06
Well then you may as well install Virtualbox then! It works great with Ubuntu Server... just make sure to download it from oracle or sun. The OSE in the software center isn't supported much anymore ( or so I hear ) . I have sucesffuly used vbox for ubuntu server, windows server 2008 and 2003, windows 7, XP...linux distros. It works great. But Like I said, Vmware offers more features... I guess you get what you pay for!

---

### Post by tgalati4 on 2011-06-06
I was thinking of hosting several different linux instances (some 128 MB, some 256 MB, and creating discrete swap files on a common disk).  True several Windows instances would gobble up RAM.

Dell does sell the "Sumo", 96 TB of disk storage in 4RU.  And that's only $100K.

---

### Post by mastablasta on 2011-06-07
> **cascade9 said:**
>  I'd hope that anybody buying a desktop i7 would avoid sandy bridge video, a decent video card is pretty cheap. 
 
 
 
just got a word yesterday that they (intel) improved the linux graphic drivers significanlty, however it will take a bit of time for them to spread arround distributions.

---

### Post by mrgordonz on 2011-06-07
Well, I bought my server today (it should arrive in a couple of days).  Specs are:

[LIST]
[*]Intel Core i7 2nd Generation 2600 (3.4GHz Quad Core)
[*]16GB DDR3 RAM
[*]1TB SATA Hard Drive
[*]Dual-Layer DVD-Writer
[*]Mini ATX Tower Case with 550w PSU
[/LIST]

At this stage I plan to go with Ubuntu Server 11.04 64-bit and Virtualbox as my virtualisation platform.

All the VMs are boring work related environments where fancy graphics are not required (don't even need audio for that matter).

Can anyone see any glaring problems with my plan?  Any suggestions on how I can improve the plan?

Cheers,

Paul

---

### Post by mrgordonz on 2011-06-07
Just been doing some reading and it seems that while running Vbox on Ubuntu Server will certainly work, the process of creating new VMs is a little clunky in that it is done via the CLI (not necessarily a deal breaker, but a GUI interface for creating VMs would be nice).  One forum post I read said that it is way easier to create new Vbox VMs with a GUI, so they recommend installing one of the desktop variants of Ubuntu.  Another post I read suggested installing Ubuntu Server, and then install the gnome GUI (or something like that - Linux terminology is not my strong suit).

With 16 GB RAM I will need a 64-bit OS, and I don't want the OS using resources un-necessarily.  It doesn't need music players or IM clients or Open Office or anything like that - it just needs to run Vbox.

Any suggestions? :confused:

---

### Post by psusi on 2011-06-07
There is a reason why the CLI is so prevalent on servers.  A GUI is helpful the first time you do something, or when you only do it every once in a while, because it helps guide you to figuring it out.  Once you know what you are doing and do the same thing ( like set up VM after VM ) repeatedly, it just gets in the way.

---

### Post by mastablasta on 2011-06-07
only one disk?
 
BTW you could always install some basic windows environment like for example IceWM or something.
 
though for server you really should learn a bit more about CLI. it cna be quite fast if you know how. i am still on GUI but i've seen a pro... and it was fast.

---

### Post by mrgordonz on 2011-06-07
For the most part I am pretty comfortable with CLI (although definitely not an expert). I provide hosting for a number of customers, and much of it is Linux based stuff with no GUI.  But that is because the servers are internet facing and need to be as secure and as fast as possible, hence, no GUI.

But this new server will be sitting in my home office, is my own dev/demo server, and I'm just being lazy. \\:D/

I'll probably start with CLI and if it gives me the s**ts, then I might think about adding a GUI.  Or I might just go with something like Linux Mint to begin with.  So many options!! :roll:

---

### Post by matt_symes on 2011-06-08
Hi

Have you considered a raid array to provide some redundancy ? I did not see it mentioned in the thread.

Kind regards

---

### Post by mrgordonz on 2011-06-08
> **matt_symes said:**
> Hi

Have you considered a raid array to provide some redundancy ? I did not see it mentioned in the thread.

Kind regards

To be honest, no.  Too much hassle - I'll probably just stick in an extra drive I have lying around and backup the VMs periodically.

---

### Post by cascade9 on 2011-06-10
> **mrgordonz said:**
> Can you suggest any?  I would like to stay under $1000 if at all possible.  

I'd checked back before this, but you ahd already said you were buying (probably from ebay). 

What was the damage on that system? I'd bet that you could have got the same sort of setup cheaper from a store in brissy....umart and msy are probably the cheapest of them and are pretty good.  Theres a few other stores with good prices in birsbane, but I wont point people toward them due to issues with those stores. 

[http://www.umart.com.au/](http://www.umart.com.au/)
[http://www.msy.com.au/](http://www.msy.com.au/)

> **mrgordonz said:**
> The purpose of the server is solely to host a number of development VMs - a DB server, couple of app servers, that kind of thing.  Nothing I do will require HD graphics - these VMs are purely for web applications and the host will be Ubuntu server.

Intel HD graphics = the newest set of intel video chips (to make sure you have to get them, they are on the CPU now...damned intel).

---

### Post by mrgordonz on 2011-06-18
> **cascade9 said:**
> I'd checked back before this, but you ahd already said you were buying (probably from ebay). 

What was the damage on that system? I'd bet that you could have got the same sort of setup cheaper from a store in brissy....umart and msy are probably the cheapest of them and are pretty good.  Theres a few other stores with good prices in birsbane, but I wont point people toward them due to issues with those stores. 

[http://www.umart.com.au/](http://www.umart.com.au/)
[http://www.msy.com.au/](http://www.msy.com.au/)

It ended up costing me $799, which for a 16GB i7 seemed pretty good to me.  I'm not a big fan of MSY or Umart - I haven't had great experiences with them.

The server arrived on Friday, and while the case is not particularly high end, I'm pretty happy with what I got for the price.

---

