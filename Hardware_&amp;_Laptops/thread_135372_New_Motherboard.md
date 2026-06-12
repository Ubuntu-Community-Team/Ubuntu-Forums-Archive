---
title: "New Motherboard"
date: 2006-02-23
forum: Hardware &amp; Laptops
---

### Post by WelterPelter on 2006-02-23
I'm thinking of getting a new motherboard for my ubuntu box. If I do this, I'll just use all the same drives, etc., so only the motherboard will change. I don't want to change my ubuntu setup, but I assume the kernel will have to be reconfigured somehow? What is the process? 


Also, any recommendations on sweet motherboards for Linux? Not looking for a gaming machine, more like a ballsy development box.

---

### Post by el3ktro on 2006-02-23
It all depends on what your current chipset is, and what the chipset on your new mobo will be. If your new mobo has the same chipset, or at least from the same brand, then you won't have many problems, Ubuntu should detect your hardware and automatically load the necessary modules. If you use an onboard graphics card, you may have to reconfigure xorg.conf.

Tom

---

### Post by WelterPelter on 2006-02-23
I haven't chosen a brand yet, so I don't know about the chipset. But let's just say that it turns out to be completely different. How can I go about doing this so that I don't have to reinstall everything, just reconfigure?

---

### Post by mjwood0 on 2006-02-23
While you could theoretically reconfigure everything, I think you'll find it easier to backup your /home and anything else you want and then re-install.  I know it sounds like a lot of work, but unless you have a totally custom install, it shouldn't be too bad.

---

### Post by WelterPelter on 2006-02-23
It makes sense. Probably just have to bite the bullet.

---

### Post by el3ktro on 2006-02-24
Well I might be wrong, but AFAIK Ubuntu configures everything at startup via hotplug anyway, so all hardware is being detected during bootup, and the appropiate modules are loaded - so there's no need to reconfigue anything - except xorg.conf, where you might have to use another graphics driver. Well before choosing a mobo, I'd first really find out about it's Linux support, NVidia chipsets are always a good idea. One thing you also have to consider is the kernel. If you have an 386 kernel, then you're free to choose a CPU (P4, Athlon etc.). But i you use a specific P4 or AMD kernel, then you should install a generic 386 kernel first so that you can boot from it.

But of course I agree with mywood: You can backup your /home (or if you have it on a separate partition, just don't touch it, and propably also backup your /etc, and then just re-install Ubuntu.

Tom

---

### Post by WelterPelter on 2006-02-24
Any recommendations on a motherboard, el3cktro?

---

### Post by el3ktro on 2006-02-24
Well this highly depends on what you want to do with your computer, and if you're pro-AMD or pro-Intel. I'm absolutely pro-AMD, and for me MSI mainboards always have been a good choice. I'd recommend an NVidia chipset, Linux supports them very well. I'd also recommend NForce4 together with an AMD64 CPU. Even if you don't use 64bit applications, you get a very good price/performance relation. Look at the MSI K8N boards, they have NForce4, and depending on if you need it or not you can have additional SATA-RAId etc.

Tom

---

### Post by mjwood0 on 2006-02-24
I would second the Nvidia Chipset as well.

Depending on the Socket of the processor you are going with, your two best options for AMD are Socket 754 or Socket 939.  If you go with the 939, you can get a reasonably inexpensive CPU and upgrade all the way to a dual core.  Something to keep in mind.

Also to note about the Nvidia chipsets.  Anything with the GeForce 61XX / NForce 4X0 may still have some Linux compatability issues.  Search these forums for what it takes to get them running currently (I was looking at these) and see if you feel up to it.  Basically, from what I can tell, it may involve compiling a newer kernel than comes with Breezy.

Good luck and just remember to search these forums for info about particular hardware.  There is a wealth of information here!

---

### Post by WelterPelter on 2006-02-24
I'm definitely an AMD fan. So far, fishing around online, this looks like it might be a good setup. BTW, MSI motherboards get a bad rap in general on these forums, so I looked at other K8N boards. Still not sure about the 939 sockets. 

Asus K8N Socket 754 Mainboard
AMD Solution Motherboard - Athlon 64 Motherboard:

    * Chipset: nVidia nForce 3 250Gb
    * Processor Support: AMD Athlon 64 3400+ or higher
    * Memory Support: Up to 3GB PC 3200 DDR
    * Expansion Slot: 1x 8X AGP, 5x PCI,
    * Other Features: SATA RAID, USB 2.0, 7.1 Channel Audio, Lan
 
AMD Sempron 3100+ Boxed Processor

    * CPU Speed: 1.8GHz
    * Cache: L2 - 256KB
    * Retail Box Kit - CPU Fan Included
    * 3 Year Limited Manufacturer Warranty

---

### Post by nickle on 2006-02-24
I changed my MoBo recently. I had an A7N8X-X with a Nvidia chipset. But I got a SATA disk and somebody gave me an A7V600-X with a VIA chipset and an on-board SATA controller. I simply rebooted the system and the right drivers were found automatically at boot up. These are not the newest MoBos so I guess the support for them is quite good. With very new hardware, this may not necessarily be the case

---

