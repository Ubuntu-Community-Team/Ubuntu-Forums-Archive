---
title: "network adaptor issues"
date: 2010-12-05
forum: Hardware
---

### Post by sigma_z_1980 on 2010-12-05
hi everyone, 

I got an issue with the internet on Maverick Meerkat. The USB adaptor is Linksys WUSB54GC. I downloaded ndiswrapper to make it work under Ubuntu but for some reason I can't install it. Every time I run *make install* I get a list of errors such as 

struct net device ha no member named mc_count
 
struct net device has no member named mc_list

so without the upgrade the internet connection just dies every few minutes.

thanks

---

### Post by IcarusR on 2010-12-05
Ndiswrapper is in the repos so you should not need to compile it yourself. But I don't think this is the way to go.

What chipset does this use ?? Post output the following command & we maybe able to help you, or search forums for the chipset (I believe it is Ralink possibly rt3070)

```
lsusb
```

Ralink provide drivers on their website.

---

### Post by sigma_z_1980 on 2010-12-06
> **IcarusR said:**
> Ndiswrapper is in the repos so you should not need to compile it yourself. But I don't think this is the way to go.

What chipset does this use ?? Post output the following command & we maybe able to help you, or search forums for the chipset (I believe it is Ralink possibly rt3070)

```
lsusb
```

Ralink provide drivers on their website.

OK it's ID 1737:0077 WUSB54GC v3 802.11g Adapter [Ralink RT2870]

hope it helps 

Alex

---

### Post by IcarusR on 2010-12-06
Do a google search for "RT2870 ubuntu" with the quotes & do some reading like I've just done.
I believe this chipset is supported out of the box, but maybe a module conflict.

See this page...

[http://ubuntuforums.org/showthread.php?t=1342593]("http://ubuntuforums.org/showthread.php?t=1342593")

---

