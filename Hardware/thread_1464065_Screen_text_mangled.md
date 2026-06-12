---
title: "Screen text mangled"
date: 2010-04-27
forum: Hardware
---

### Post by VirusCollector on 2010-04-27
I've been following a guide somewhere on here about how to install a minimal Enlightenment DR17 setup. I did it on my own computer and it worked fine, so I decided I'd try it on my baby: a salvaged x-ray touchscreen computer.

Its hardware is dubious, but I do know that it works: I had a Windows XP installation on it, running barcode scanning software for grocery applications. I also had numerous Debian installs on it, back when I didn't know what I was doing. Not that I know now.

Attached are two pictures of the text. This is a 9.10 alternate CD command-line install. What is odd is that the BIOS and the initial setup screen looked perfectly fine. Then, when I started to install, everything just looked messed up.

I can't seem to get a graphical interface running. Despite my efforts at blind installs, I can't seem to install SLiM properly... So, what should I do? Is there some kernel parameter I should be passing? All of the vga=xxx options don't seem to do anything.

---

### Post by imbjr on 2010-04-27
> **VirusCollector said:**
> I've been following a guide somewhere on here about how to install a minimal Enlightenment DR17 setup. I did it on my own computer and it worked fine, so I decided I'd try it on my baby: a salvaged x-ray touchscreen computer.

Its hardware is dubious, but I do know that it works: I had a Windows XP installation on it, running barcode scanning software for grocery applications. I also had numerous Debian installs on it, back when I didn't know what I was doing. Not that I know now.

Attached are two pictures of the text. This is a 9.10 alternate CD command-line install. What is odd is that the BIOS and the initial setup screen looked perfectly fine. Then, when I started to install, everything just looked messed up.

I can't seem to get a graphical interface running. Despite my efforts at blind installs, I can't seem to install SLiM properly... So, what should I do? Is there some kernel parameter I should be passing? All of the vga=xxx options don't seem to do anything.

That has all the hallmarks of bad RAM to me. Try running the RAM test from the CD.

---

### Post by VirusCollector on 2010-04-27
OK, I'll do that. It's funny, though, because XP was just working fine... the boot time was just massive, so we didn't use it.

I managed to install SLiM properly, and now have a more coherent display. It's squished to half the screen, and a little wider than the screen actually is, but it allowed me to install the E17 repo.

RAM test gooooo!

---

### Post by VirusCollector on 2010-04-27
The RAM test was completely clear for an entire pass... So what now? Shouldn't VESA work just fine for this?

---

### Post by imbjr on 2010-04-28
> **VirusCollector said:**
> The RAM test was completely clear for an entire pass... So what now? Shouldn't VESA work just fine for this?

Gotta admit, that's me stumped. Your screencaps looked like classic bad RAM.

---

