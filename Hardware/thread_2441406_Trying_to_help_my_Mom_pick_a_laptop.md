---
title: "Trying to help my Mom pick a laptop"
date: 2020-04-23
forum: Hardware
---

### Post by jonato-pik on 2020-04-23
My Mom had an old System76 lemur for years that she loved, and then she was robbed. They recovered it, but the machine was broken. She really wants to stick with Ubuntu (the switch to Ubuntu from Windows years ago made her life SO much easier), but the new System76 models are out of her/our price range. We're looking into Lenovo, and she kind of fell in love with this particular one, but as Im searching these forums, Im not confident I'm getting a clear sense of whether the model she likes will be compatible. 

Here's the model she likes:
[https://www.amazon.com/Lenovo-Performance-Dual-Core-802-11ac-Bluetooth/dp/B083ZRVZGY](https://www.amazon.com/Lenovo-Performance-Dual-Core-802-11ac-Bluetooth/dp/B083ZRVZGY)

Any compatibility red flags on that one? If so, any similar models yall might recommend for her? Sorry if I'm going about this the wrong way. I did try to search the other posts, but its overwhelming for my little brain.

---

### Post by mommoon on 2020-04-23
This machine has a good hardware configuration, with SSD and 8GB of RAM, it will work beautifully with Ubuntu.


See the system installation requirements at this link: [https://help.ubuntu.com/community/Installation/SystemRequirements?_ga=2.53255016.1576552971.1587648247-1769573616.1587648247](https://help.ubuntu.com/community/Installation/SystemRequirements?_ga=2.53255016.1576552971.1587648247-1769573616.1587648247)

---

### Post by CatKiller on 2020-04-23
> **jonato-pik said:**
> Any compatibility red flags on that one?

Nothing that stands out, particularly, from the specs listed on that page. A search for "model number Linux" often picks up potential problems that people have experienced. "Value-added" sound devices or weird non-standard network devices are the things that tend to be problematic. And Optimus (Nvidia/Intel) graphics are a pain. 

Linux compatibility doesn't fit into Lenovo's decision making at all: they don't deliberately make things work or deliberately make things not work - Windows is all they're interested in. Dell, on the other hand, sell machines with Linux pre-installed, so they have incentive to go for Linux-friendly parts across their range to simplify their supply lines. It might be worth looking to see if they have anything similar. 

You could also contact System 76 to see if they're able to repair the old one. They won't have an infinite supply of spare parts for older models, but they might still have something.

---

### Post by CelticWarrior on 2020-04-23
Considering this will be Ubuntu only, no dual-boot, it shouldn't have any major issue. That said, you should use the preinstalled Windows for a couple of actions prior to installing Ubuntu:
[LIST]
[*]Update UEFI ("BIOS")
[*]Update SSD's firmware (if available)
[/LIST]

Those are (arguably) easier to do in Windows because vendors typically provide such updates as Windows executable files.
Once done try a live session of Ubuntu 20.04 (such hardware - AMD APUs - benefits from newer OS releases, more than anything else in the market today) in order to check hardware, namely the internal storage (SSD) and WiFi.
If the SSD isn't recognized you need to change the SATA mode in UEFI to AHCI.
If the WiFi isn't supported out-of-the-box it will need additional drivers. Note down its specifications: Run 'lspci' to find out. Then research here about it.

In a nutshell, it should be poerfectly fine with Ubuntu but it'll likely need firmware updates, some UEFI tweaking and eventually additional drivers for the WiFi.

---

### Post by mörgæs on 2020-04-23
If she is interested in used gear here are some experiences:
[https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006)

---

### Post by jonato-pik on 2020-04-28
> **CelticWarrior said:**
> Considering this will be Ubuntu only, no dual-boot, it shouldn't have any major issue. That said, you should use the preinstalled Windows for a couple of actions prior to installing Ubuntu:
[LIST]
[*]Update UEFI ("BIOS")
[*]Update SSD's firmware (if available)
[/LIST]

Those are (arguably) easier to do in Windows because vendors typically provide such updates as Windows executable files.
Once done try a live session of Ubuntu 20.04 (such hardware - AMD APUs - benefits from newer OS releases, more than anything else in the market today) in order to check hardware, namely the internal storage (SSD) and WiFi.
If the SSD isn't recognized you need to change the SATA mode in UEFI to AHCI.
If the WiFi isn't supported out-of-the-box it will need additional drivers. Note down its specifications: Run 'lspci' to find out. Then research here about it.

In a nutshell, it should be poerfectly fine with Ubuntu but it'll likely need firmware updates, some UEFI tweaking and eventually additional drivers for the WiFi.

Great, thanks for this tip! That's important to know

---

### Post by jonato-pik on 2020-04-28
> **mommoon said:**
> This machine has a good hardware configuration, with SSD and 8GB of RAM, it will work beautifully with Ubuntu.


See the system installation requirements at this link: [https://help.ubuntu.com/community/Installation/SystemRequirements?_ga=2.53255016.1576552971.1587648247-1769573616.1587648247](https://help.ubuntu.com/community/Installation/SystemRequirements?_ga=2.53255016.1576552971.1587648247-1769573616.1587648247)

Thanks! She'll be happy to hear this

---

### Post by jonato-pik on 2020-04-28
> **CatKiller said:**
> Nothing that stands out, particularly, from the specs listed on that page. A search for "model number Linux" often picks up potential problems that people have experienced. "Value-added" sound devices or weird non-standard network devices are the things that tend to be problematic. And Optimus (Nvidia/Intel) graphics are a pain. 

Linux compatibility doesn't fit into Lenovo's decision making at all: they don't deliberately make things work or deliberately make things not work - Windows is all they're interested in. Dell, on the other hand, sell machines with Linux pre-installed, so they have incentive to go for Linux-friendly parts across their range to simplify their supply lines. It might be worth looking to see if they have anything similar. 

You could also contact System 76 to see if they're able to repair the old one. They won't have an infinite supply of spare parts for older models, but they might still have something.

Yeah, that's a good point about System 76 repairs. Not sure if it would be worth the cost, but it couldn't hurt to look into it. Appreciate the insight into what hardware normally creates issues. Looking through the specs on the one she wants, it seems like it free from those, unless I'm missing something. The Dell Linux machines I could find all seemed pretty pricey.

---

### Post by jonato-pik on 2020-04-28
> **mörgæs said:**
> If she is interested in used gear here are some experiences:
[https://ubuntuforums.org/showthread.php?t=1543006](https://ubuntuforums.org/showthread.php?t=1543006)

thanks. i did browse through this thread a bit...boy is it overwhelming! lol.

---

### Post by jonato-pik on 2020-04-28
I want to thank everyone who responded so far. It's really been helpful! She hasn't pulled the trigger on this or any other laptop yet, but the replies here have helped enlighten both of us.

---

### Post by CatKiller on 2020-04-28
> **jonato-pik said:**
> Yeah, that's a good point about System 76 repairs. Not sure if it would be worth the cost, but it couldn't hurt to look into it. Appreciate the insight into what hardware normally creates issues. Looking through the specs on the one she wants, it seems like it free from those, unless I'm missing something. The Dell Linux machines I could find all seemed pretty pricey.

I was mistaken about Lenovo, as it turns out: they're going to be selling some laptops with Fedora pre-installed. 

Linux machines are generally going to be more expensive to make than Windows ones. Whatever happens, it's going to be a smaller production run, so you miss out on economies of scale. It makes sense to do that for expensive machines, or if you're a boutique company anyway, but not really otherwise. Some companies did experiment with budget machines with Linux back in the netbook era, saving money on the cost of a Windows licence, but they didn't really take off.

---

### Post by kurt18947 on 2020-04-29
Based on my experience with Ryzen on a desktop, specifically the Vega video, I'd certainly recommend 20.04. I noticed a good improvement in Ryzen compatibility from 18.04 to 20.04. It does appear to have Intel WiFi which may make your life simpler.

---

