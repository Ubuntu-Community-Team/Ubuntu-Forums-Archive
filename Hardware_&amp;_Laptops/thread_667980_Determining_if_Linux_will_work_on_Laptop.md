---
title: "Determining if Linux will work on Laptop"
date: 2008-01-14
forum: Hardware &amp; Laptops
---

### Post by The Fire Snake on 2008-01-14
Guys,
   I am feverishly shopping for a laptop that is Linux compatible.  If I choose a laptop with an Intel X3100 GPU, an Intel 965 Express chipset, and Intel wireless card am I guaranteed it will work with the latest Ubuntu release, or very soon(next release)?  What about audio, what audio is supported in Linux, Intel only?  What about RealTek, are their any drivers, proprietary or open source that will give me sound?  I know that some laptops, more than others have little multimedia buttons and suspend issues.

I guess I am trying to get a set of general rules of what modern laptops hardware will work and what does not or will be a pain(ex: broadcom).  That way when I go shopping and look at the specs and I see broadcom, ATI, etc I can be like this is too much work or impossible to get working in Linux.  Obviously I am not asking for a comprehensive list of all hardware that will work with Linux or not but a lot of the same products are being used across most product lines.  For example you usually see Intel, ATI or nVidia for the graphics card, Atheros, realtek, Intel for the wireless etc

---

### Post by Yellow Pasque on 2008-01-14
If you're one of those people that just HAS to have desktop effects, avoid the X3100 Intel graphics, as they're blacklisted from running it because of various issues (unless there's been a fix recently).

Audio: Most everything has a Realtek, Sigmatel, or some other cheap Intel HDA-compliant chip. Some of the newer ones require various fixes because Gutsy never got updated to ALSA 1.0.15
[https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller)
[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

[https://wiki.ubuntu.com/LaptopTestingTeam](https://wiki.ubuntu.com/LaptopTestingTeam)

---

### Post by Casual Fan on 2008-01-14
Your best bet is to buy a laptop built with Ubuntu or another Linux distro.

[COLOR="RoyalBlue"][Dell]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DNCWJL1&s=dhs")
[System 76]("http://www.system76.com/")
[Asus]("http://eeepc.asus.com/global/product.htm")[/COLOR]

---

### Post by odin1965 on 2008-01-15
A friend of mine just bought this refurbished Gateway laptop from Tigerdirect for 499.

[http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3135617&CatId=2510](http://www.tigerdirect.ca/applications/SearchTools/item-details.asp?EdpNo=3135617&CatId=2510)

I have been thinking about getting one for my parents, but didn't know how Gutsy would run on it. I am NOT doing the vista support thing for them. So I tried a 7.10 live CD and everything important worked, though I didn't have time to test suspend/hibernate. Wireles (intel 3945), sound and graphics (intel 945) all worked OOTB. I even had 1280x800 and desktop effects.

---

