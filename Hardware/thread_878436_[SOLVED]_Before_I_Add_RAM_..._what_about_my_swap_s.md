---
title: "[SOLVED] Before I Add RAM ... what about my swap size?"
date: 2008-08-02
forum: Hardware
---

### Post by mfdc1969 on 2008-08-02
OK, so the old saying goes, "The only stupid question is the one you don't ask."

I want to add more RAM to my Acer 5610Z-2013 laptop - it currently has 1GB and the max supported is 2GB (as per [Acer support website]("http://www.acerpanam.com/synapse/forms/portal20.cfm?recordid=522&formid=3404&website=AcerPanAm.com/canada&siteid=7297&words=all&keywords=&areaid=17"))

**I have no problem cracking open my laptop and stuffin' in the new RAM there but I must ask, "Is there any preparation to the swap/disk partition?"**

Currently I am running Hardy and the swap is set at about 4Gb - I once read somewhere that swap should = 4x the RAM. If that is true should I just resize my swap partition to 8GB? If so should I do it before or after adding the RAM. Or, does it really matter?

Any help, suggestions or comments are welcome!

Thanks in advance.

---

### Post by ZeldaFan on 2008-08-02
Personally, I've always heard that your swap should always be 2x your RAM. But either way, if you are upgrading to 2 GB RAM, do not worry about enlarging your swap partition. Sure you could, but regardless of what a silly formula says, doing so will not give you any performance boost. Swap is really only useful when you threaten to use a lot, if not all, of your RAM, but with 2 GB that should never be the case. I can say from my own experience with my laptop that I have 2 GB RAM and not once has my computer tapped into a single byte of my swap space. It would be a waste of HDD space to enlarge your swap and its probably a waste taking up 4 GB right now, but you can keep it at its current size if you do not feel comfortable deleting or reducing it.

---

### Post by mfdc1969 on 2008-08-12
I am marking this as SOLVED as I have had some input from the Community in addition to the Ubuntu resources and I feel my questions have been answered.

I also found this useful
Swap Partition FAQ
[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

Thanks!

---

