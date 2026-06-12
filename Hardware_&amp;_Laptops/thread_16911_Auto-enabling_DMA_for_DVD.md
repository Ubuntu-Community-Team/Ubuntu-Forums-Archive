---
title: "Auto-enabling DMA for DVD"
date: 2005-02-24
forum: Hardware &amp; Laptops
---

### Post by stoffe on 2005-02-24
Hello,

I was wondering if there was any way to get DMA enabled automatically with hdparm for my DVD player (and why not my CDRW as well while we are at it?).

I can enable it manually from the commandline just fine, but it would be nice if I didn't have to do that everytime, but that it could do it automatically.

I'm almost sure I pulled this trick off in Gentoo (that was under KDE though if that matters) but I can't for my life remember how, and I can't seem to find any info for Ubuntu right now. Been googling and reading the hdparm manpage, but I'm not sure what to do anyways.

Any ideas?

---

### Post by p!=f on 2005-02-24
```

[~] > sudo gedit /etc/hdparm.conf

```
That file is well documented. Tweak settings to fit your needs. It will be run on every boot.

---

### Post by stoffe on 2005-02-24
[QUOTE=p!=f]```

[~] > sudo gedit /etc/hdparm.conf

```
That file is well documented. Tweak settings to fit your needs. It will be run on every boot.[/QUOTE]

Erm... well, thanks, but I don't think it is. Or rather, I don't understand it well enough I suppose. It is not that there aren't documentation, but it doesn't speak language I understand at all times. :)

I've been in that file and looked, and for instance, it has a few example entries like this: > #/dev/discs/disc0/disc {
# mult_sect_io = 16
# write_cache = off
# spindown_time = 240
#}

#/dev/discs/disc1/disc {
# mult_sect_io = 32
# spindown_time = 36
# write_cache = off
#}

#/dev/cdroms/cdrom0 {
# dma = on
# interrupt_unmask = on
# io32_support = 0
# 

Especially the last one seems a bit like what I want, but I am not sure. I've been reading the docs, like I said, and I'm unsure of what all the other values mean, and do I need them, or are they recommended? Is there differences for DVDs and CD/CDRW? And for different brands?

I just don't want to set something wrong by mistake, although I suppose that is less dangerous for a DVD drive than it would be for a HDD. :)

Does that make a bit more sense? Sorry if I was unclear.

---

