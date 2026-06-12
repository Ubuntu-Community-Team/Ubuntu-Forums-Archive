---
title: "Looking to buy a new linux laptop"
date: 2007-02-16
forum: Hardware &amp; Laptops
---

### Post by scrook on 2007-02-16
Hi all,

I'm looking to buy a new laptop withing the next 4 months. I am looking within the $1000 to $1500 price range. 

Currently the two options I'm considering are to either buy a Macbook and run the few windows programs that I still need (Stuff for my EE classes which is not out for Linux such as PSoC designer) via parallels or find a good linux compatible laptop and run windows on VMware when needed.

While there are many more powerful machines than the Macbook from companies like Dell and Hp (particularly with respect to graphics), I'm not too sure what will and will not work properly with Ubuntu. (I have used ubuntu extensively on my desktop so I'm pretty familiar with it).

Does anyone know of a laptop which fits my price range and has good hardware compatibility with Ubuntu? Most particularly, I want Wi-Fi to work out of the box (no NDISwrapper if possible). I don't mind installing graphics drivers, but I'd much rather have an NVidia chipset as they have been much easier to work with in my experience.

Also, how well do those built in webcams built into a lot of new models fare on linux? Bluetooth?

Thanks,

Scott

---

### Post by incubus on 2007-02-16
Hey,

I just bought myself a Macbook.  It's a sweet sweet laptop.  Hardware quality is fantastic.

Now I'm not the best person to help you, because I haven't tried to install Ubuntu on it yet (except as a virtual machine).  This new line with Core 2 Duos come with an Atheros chipset that is not yet supported.  The MadWiFi team is working on it, but that means that we have to use ndiswrapper instead.

I don't want to use ndiswrapper either, so I'm waiting.

From what I've heard (in the forums), you can get most other things working without much effort.  That includes iSight and the trackpad, using appletouch.  Bluetooth, I think works out of the box.

Before buying the Macbook, I was considering buying a Thinkpad instead.  Take a look at those.  If you know somebody who works for IBM, you can get very good discounts and you get to your price range.

I hope that helps,
incubus

---

### Post by scrook on 2007-02-16
incubus,

Thanks for the reply :)

To clear up my previous post, I wasn't really planning on installing ubuntu if I was to buy the macbook, I would instead run it from within parallels (there are several linux only programs i'm hooked on along with the windows stuff I need).

My only real concern with the macbook is the lack of a dedicated graphics card. In your experience how does it hold up? What kind of programs can it run well?

---

### Post by Benitez on 2007-02-17
[SIZE="3"]
Hey.

Try a **[System 76]("http://www.system76.com")** laptop and get a larger hard drive for it. I'm pretty sure you can just use GParted and make a partition for WinXP and then have it be a dual boot device.

What you think?
[/SIZE]

---

### Post by scrook on 2007-02-17
Benitez,

I actually did find System 76's website yesterday after I posted this thread. 
Their Gazelle series looks interesting and I may just buy one of those. Instead of dual boot, I will instead run WinXP via VMware player as rebooting is a pain in the behind.

VMware player is free and pretty easy to install (I'm using it on my current desktop). I recommend it to anyone who needs to run windows programs that don't work well in Wine/Crossover (with the exception of games as hardware 3d acceleration is not fully supported in the guest OS's).

Scott

---

### Post by TmP on 2007-02-17
Also, you should consider the Graphics chip that's in the laptop.

I think XGL or similar is where the future of Linux user environment lies.

And bear in mind that some GPUs are a bitch to set up ( like my Radeon9000 ).

I would also wonder how well is the Macbook's GPU supported under Ubuntu.

---

### Post by scrook on 2007-02-17
I would think that the Macbook's GPU should be fully supported in just about any Linux Flavor as it is an integrated Intel GMA 950. As I recall the Intel drivers are currently (or soon will be) fully open source.

As far as discrete GPU's go I won't buy anything other than Nvidia for a machine that will run linux.

---

### Post by incubus on 2007-02-17
scrook,

As strange as it may seem, I bought the Macbook exactly because it doesn't have a graphics card.  My previous laptop was a customized ASUS with all bells and whistles, good graphics card for its time.

But the downside was heat, noise, and battery life.  I wanted a laptop that would be lightweight, portable, not a desktop replacement.  That's why I chose the Macbook over others.

Now back to Parallels, as long as you're not going to do anything too fancy (in terms of graphics), you'll be fine.  Parallels is pretty fast, I'm still impressed -- and I've used Xen and KVM.  VMware Fusion is also coming soon (the beta is publicly available).

Also remember there are lots of ports of open source stuff to the Mac OS.  It's very far from being like the debian/ubuntu repositories, but you can get many things done.

incubus

---

### Post by ctt1wbw on 2007-02-18
Here's my advice about buying a laptop for Linux:

It can be Billy Bob's Laptop, Inc. for all I care, as long as they don't use ATI graphics cards.  Make sure you get one that has an nVidia graphics card.  You will save yourself the time and aggravation and loss of hair by doing so.

---

