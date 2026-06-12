---
title: "Problem with Hp Nx6125 Wifi"
date: 2007-02-04
forum: Hardware &amp; Laptops
---

### Post by Stuggi on 2007-02-04
I have some problems with getting my wlan up and running.

I've used ndiswrapper to install the bcmwl5.inf, and I've also ran ndiswrapper -m

But, the network thingy in gnome won't find my card... It did while using the original bcm43xx... which I've blacklisted

When I ran modprobe ndiswrapper it failed
When I grepd the startuplog it seems as if ndiswrapper fails to load at startup

And btw, the bottom of my laptop says Broadcom BCM94318MPG...

Help me!

---

### Post by Stuggi on 2007-02-05
Bump...

---

### Post by Stuggi on 2007-02-06
Bump

---

### Post by Stuggi on 2007-02-06
Got it working, the problem consisted of two things.

1) ndiswrapper 1.15 didn't load properly, but when I removed everything with synapsis and resintalled 1.18 it worked

2) On my laptop one have to push the wifibutton for a couple of sec before it lights up! I thought it was like in windows when you just press it, but in linux is seems as if one have to hold it down for 3 sec or so for anything to happen! ](*,) 

And I just want to say thanks to the linux community for so much documentation on every single problem. I'm fairly noob when it comes to desktop nix, so it's good to have all the gurus around!

---

### Post by iamkrazee on 2008-06-12
I was happily married to sabayon back then, but if I'd stumbled upon this back then, I'd have let you know that ndiswrapper is a big long boring method. All you need to do is to get b43-fwcutter from repo, it asks you to extract firmware and bam! Almost like a 5 second thing, with some 2-3 clicks.

---

