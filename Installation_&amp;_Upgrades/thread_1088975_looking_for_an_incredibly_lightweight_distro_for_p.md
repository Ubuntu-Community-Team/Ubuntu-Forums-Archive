---
title: "looking for an incredibly lightweight distro for ppc imac"
date: 2009-03-06
forum: Installation &amp; Upgrades
---

### Post by moore.bryan on 2009-03-06
does anyone in the community know of a *really* lightweight distro for a ppc imac (g4, [http://en.wikipedia.org/wiki/IMac_G4)?]("http://en.wikipedia.org/wiki/IMac_G4%29?") i have intrepid running xfce and it's still painfully slow if more than one program is running at a time.

thanks for any input!

---

### Post by kestrel1 on 2009-03-06
How about Puppy Linux or Antix. Both very small, so should run well on that system.

---

### Post by avtolle on 2009-03-06
Is there a ppc version of either Puppy or Antix?

---

### Post by moore.bryan on 2009-03-06
i don't think so, i was just looking around their forums. antix doesn't seem very well supported and puppy has a thread with a developer saying he doesn't think a ppc port will ever happen.

on several sites, it's suggested to simply install debian as a base and add wm from there... i'm not adverse from that, but wondering what the major difference would be since i tried openbox with a server install of ubuntu on this imac and it was still pretty slow.

oh, and has anyone used finnix? it looks promising.

---

### Post by kestrel1 on 2009-03-06
Sorry, wasn't thinking.
you could try debian, but I dont know if it will work any better than what you have now:
[http://www.debian.org/ports/powerpc/](http://www.debian.org/ports/powerpc/)
Or you could try arch linux:
[http://www.archlinuxppc.org/](http://www.archlinuxppc.org/)

---

### Post by moore.bryan on 2009-03-06
no worries... you must have read my mind and posted while i was editing my above post. i didn't think debian would be much faster. i've heard from several source arch is *really* fast, so maybe that's the way to go...

---

### Post by avtolle on 2009-03-06
Is there any way to increase the RAM on your box? That will be helpful to you, whether in Xubuntu or other distros. I've not used Arch or Finnix; have used Yellow Dog and openSUSE 11.1, but Ive upgraded the RAM on the G4 Cube to 576mb. Didn't like Yellow Dog; openSUSE runs quite well, but am sticking with Ubuntu (8.10 at present) even with the "fiddling" needed to get the graphics usable.

EDIT: Not very knowledgeable about your computer, but IIRC, you could upgrade to 512mb RAM. That said, RAM for our "more mature" macs is pricey, relative to newer computers.

---

### Post by moore.bryan on 2009-03-06
good question; i haven't really looked into it. the imac g4 is one of those "lamp" ones... i can't imagine upgrading the ram would be easy; it barely looks like the base opens! ;-)

---

### Post by kestrel1 on 2009-03-06
We have a couple of imacs at work & from what I remember there is a cover that needs to be removed to allow access for RAM upgrades.

---

### Post by moore.bryan on 2009-03-06
thanks for the info... a little research and i found a photo-guide for the process. it looks pretty straight-forward, but leaves me wondering why in the world apple would make one, basically, desktop memory and the other laptop. seems silly, but who am i to judge.

---

### Post by Scotso on 2009-03-06
[http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions#Architecture_support](http://en.wikipedia.org/wiki/Comparison_of_Linux_distributions#Architecture_support)

Pretty useful.

---

### Post by moore.bryan on 2009-03-06
thanks scotso! i didn't even see that table; i must have been partially asleep when looking at that page before...

i think i'm going to upgrade the ram (found some not-to-expensive options) and see how the 'buntu handles.

---

### Post by avtolle on 2009-03-06
Well, if your experience is like mine, after upgrading the Cube to 256mb, it "ran", and Xubuntu was the best option I tried; after upgrading the Cube to 576mb, it runs well; not going to win any races with a newer, higher performance CPU to be sure, but definitely usable for my purposes. If you are running OpenBox on top of your *buntu install, it ought to run noticeably quicker, and Xubuntu should definitely be usable. 

For grins, I put Xubuntu 32-bit on a dual core 64-bit system w/1 gb RAM to compare it with a 64-bit 8.10 Ubuntu (Gnome) install; noticeably faster. This is a laptop, and monitoring temps, the one thing that keeps me primarily using the 64-bit install (which is quite "snappy" in its own right) is that the 64-bit system runs cooler; some 5-7 degrees F cooler, by casual monitoring of the temps of the cores, the GPU, and the HDD. I'd found the same thing with 32 vs. 64 bit installs of Linux Mint 6, BTW.
Sorry for that last OT bit.

---

### Post by moore.bryan on 2009-03-06
excellent... at least there's some hope for the current doorstop of an imac.

---

### Post by ajgreeny on 2009-03-06
What about fluxbuntu which is based on ubuntu but has fluxbox, one of the lightest desktops available.  Get it from here for your architecture if you want to have a look at it.

[http://wiki.fluxbuntu.org/index.php?title=Get](http://wiki.fluxbuntu.org/index.php?title=Get)

---

### Post by snowpine on 2009-03-07
> **ajgreeny said:**
> What about fluxbuntu which is based on ubuntu but has fluxbox, one of the lightest desktops available.  Get it from here for your architecture if you want to have a look at it.

[http://wiki.fluxbuntu.org/index.php?title=Get](http://wiki.fluxbuntu.org/index.php?title=Get)

I can't recommend Fluxbuntu because it will become obsolete next month when 7.10 reaches end of life. Much better to simply install fluxbox on top of a current version of Ubuntu/Xubuntu.

Debian is probably the best suggestion so far; the Debian project really makes an effort to support alternate architectures. They have a new LXDE version which is probably the fastest.

---

