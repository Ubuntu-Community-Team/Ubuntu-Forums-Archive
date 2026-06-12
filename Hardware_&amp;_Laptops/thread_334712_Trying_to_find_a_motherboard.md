---
title: "Trying to find a motherboard"
date: 2007-01-09
forum: Hardware &amp; Laptops
---

### Post by kwaanens on 2007-01-09
I'm planning to build a work station (i.e. a multimedia station), and I'm  looking for a motherboard that will work well with Ubuntu.

I'm now looking at [Asus P5B DLX/WIFI-AP, P965, Socket-775, ATX, 2xGbLAN, SATAII, Firewire, PCI-Ex16]("http://www.komplett.no/k/ki.asp?sku=321779&view=detailed") and I'm wondering if anyone knows anything about it.

What I need to know: 
- Does all features of it work with Ubuntu?
- How's the audio?
- How's the network speed? (Network adapter is said to be "Ethernet, Fast Ethernet, Gigabit Ethernet, IEEE 802.11b, IEEE 802.11g")

If you haven't tried it, but know something about the different components included, I still want to hear your voice :)

Here's the list I'm looking at: [http://www.komplett.no/k/kl.asp?bn=10492&sortBy=p&minprice=&maxPrice=&sortOrder=d](http://www.komplett.no/k/kl.asp?bn=10492&sortBy=p&minprice=&maxPrice=&sortOrder=d)

I want a motherboard that can be extended with sufficient RAM for some years (using Ubuntu with "all" the eye candy I can find, as well as large files and my/postgresql (with amarok), so the top half of the list would be the place to look at I guess. If anyone here is using any of these with everything working, please let me know.

- Ketil

---

### Post by robenroute on 2007-01-09
Motherboards based on Intel's 965 chipset are a bit of a hit & miss experience. Check Ubuntu's UDSF HCL and phoronix.com for info.

---

### Post by kwaanens on 2007-01-09
Thanks for this tip!
Which category would be safe to go for? At least I think I'm going Intel, but feel free to convince me otherwise :)

<rant>It really is a pain to find out which hardware will actually work with Ubuntu :( </rant>

- Ketil

---

### Post by robenroute on 2007-01-09
Yes, it can be a quest, finding all the right hardware. I'm currently building a new system of my own; I'm going the AMD X2 route, for several reasons: good support for the nForce chipset, similar performance to Intel's C2D, consumes less power, and a lot more affordable. Having said that, there certainly are good Intel-based solutions. I know several people with very nice Intel systems, based on Intel's 945 and 975 chipsets.

---

### Post by kebes on 2007-01-09
Be warned that the Intel 965 chipset has many known problems with Ubuntu:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

(This is fixed in the 2.6.18 kernel, but the Edgy CD ships with 2.6.17.) The ASUS P5B seems to be one of those affected.

You should take a look at the hardware database and see what others have said about various motherboards:
[https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards](https://wiki.ubuntu.com/HardwareSupportComponentsMotherboards)

---

### Post by kwaanens on 2007-01-09
What about: [EVGA nForce 680i SLI, nForce-680i SLI, Socket-775, 2xGbLAN, DDR2, 2xPCI-Ex16]("http://www.komplett.no/k/ki.asp?sku=327567&view=detailed")
Does anyone know anything about this?

- Ketil

---

### Post by kebes on 2007-01-09
> **kwaanens said:**
> 
<rant>It really is a pain to find out which hardware will actually work with Ubuntu :( </rant>


Yup, it's a pain. Too bad companies like Intel don't send the kernel devs a note when they are about to (for instance) remove legacy IDE support in their upcoming chipset!

As robenroute said, if you go for AMD + nForce chipset, the support is quite good. Usually it just works, no questions asked. (I recently built an AMD X2 with ASUS motherboard and it works quite nicely.)

However the Intel Core2duo is a very nice chip with excellent performance, and so it may be worth doing the research and finding a motherboard that supports it properly. I know they exist (just not sure which one to suggest).

---

### Post by robenroute on 2007-01-09
> **kwaanens said:**
> What about: [EVGA nForce 680i SLI, nForce-680i SLI, Socket-775, 2xGbLAN, DDR2, 2xPCI-Ex16]("http://www.komplett.no/k/ki.asp?sku=327567&view=detailed")
Does anyone know anything about this?

- Ketil

nForce 600 series is just too new. nForce 4 and 500 series is well-supported. Do yourself a favour and read a few reviews over at [Phoronix]("http://www.phoronix.com").

---

### Post by kwaanens on 2007-01-09
Sorry about the nagging... :)
I checked up my first mobo on phoronix, and found this: "Overall, the ASUS P5B Deluxe motherboard as a whole should work well with any Linux distribution using a recent Linux 2.6 kernel."

---

### Post by robenroute on 2007-01-10
You're not nagging, I understand your point. However, like I stated before, it's a bit of a hit & miss mission to get the 965-based boards working with Linux; you have to know exactly what you're doing and keep your fingers crossed. So, to avoid headaches, aggravation, frustration, tearing out hair, and limbs, steer away from the 965 boards, for now. Some time this year, I'm sure, the 965-based boards will be supported just fine, but for the time being, 945 and 975 boards are the way to go, if you're going the Intel route. Of course, AMD has some interesting offerings as well: nForce 4 and 500 series would be the preferred chipset there, as the new 600 series isn't properly supported yet.

---

