---
title: "Plug 'n' Play Wireless in Linux"
date: 2011-01-07
forum: Hardware
---

### Post by thenkel on 2011-01-07
Hey all, recent convert here. Got fed up with Windows 7 Starter edition on my shiny new Lenovo s10-3, no explanation necessary. Been working with computers for 20 years now, since the introduction of the old Mac LCII into my living room in 1991.
Figure it's about time for me to move onto an open-source operating system. Rather than return my netbook and effectively throw in the towel on my Linux experience, I thought I'd give a shout out to see if anyone knows of an easy workaround to get my wireless working in Linux. I don't have my heart set on any particular operating system, I simply want something that just works. My understanding of the matter is that the touchpad on the Ideapad is incompatible with most distro's, but I have had an easy time getting integrated with Linux using PCLinuxOS and Ubuntu Lucid Lynx.
For three days now, I've spent every waking moment poring over the net trying to find an easy answer to my problem. I have installed, re-installed, and tried just about every workaround I could get my hands on. I even went out and bought a Belkin USB adapter in the hopes that it would work "out of the box."
Recently I have stumbled upon the Intel 4965AGN mini PCI-e card and am considering shelling out some dollars for one. From the little available information I have found on the net, I have observed (mostly) resounding success both with my model of netbook and with Ubuntu. Does anyone have any experience with this card, or are you willing to point me in the right direction in terms of finding a compatible WiFi adapter for my computer? I refuse to roll back to Windows, and even if I wanted to I couldn't since my purchase didn't include a CD. I'm really starting to get into this Linux thing, and even if I have to code the darn thing myself I WILL get this to work! Any human correspondence or weblinks are highly appreciated.

---

### Post by IcarusR on 2011-01-07
A lot of info on IBM & Lenovo laptops here

[http://www.thinkwiki.org/wiki/ThinkWiki]("http://www.thinkwiki.org/wiki/ThinkWiki")

Rather than buying yet another wifi adapter why not let us help you try to get the built in wifi to work ?

Post output of this terminal command so we can identify wifi chipset to start with.

```
lspci
```

---

