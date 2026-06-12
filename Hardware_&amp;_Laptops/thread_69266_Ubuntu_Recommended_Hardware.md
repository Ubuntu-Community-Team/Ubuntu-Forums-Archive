---
title: "Ubuntu Recommended Hardware"
date: 2005-09-26
forum: Hardware &amp; Laptops
---

### Post by dbott67 on 2005-09-26
My apologies if this is in the wrong forum.

I have noticed that there are a few threads on supported hardware for linux (as well as some at other forums), however, I was wondering if there was a definitive **"Ubuntu-recommended/supported"** hardware list somewhere.  Some of the sites listed linux-supported hardware, but I always seem to have some hardware issues when I switch between distros on the same machine (for example, SuSE does not recognize my wifi or sound; slackware seems to hate my video card and I had to finagle Ubuntu in Warty and Hoary.

Anyhow, I'm looking a purchasing a new computer soon and am leaning towards AMD-Athlon 64 (possibly the dual-core).  I have seen threads by AMD64 users who have had difficulty with their motherboard & integrated NIC.

Has anyone built/purchased a new system lately that pretty much just "worked" with Ubuntu?  I'll be dual-booting to XP Pro so I can take a crack at some of the more recent FPS-style games.

Any recommendations for the following components (or components to avoid):

- CPU (AMD64)
- Motherboard (open to suggestions)
- NIC (wired, 10/100, preferably integrated to MB)
- Hard drive (SATA)
- Sound card (open to suggestions)
- Video (leaning towards NVidia; dual-boot to XP for FPS-style games; open to suggestions, though)
- Any other components that I might need to be wary of

I've also been considering a laptop.  Linux Magazine ([http://www.linux-magazine.com/issue/58](http://www.linux-magazine.com/issue/58)) had a review in the Sept. issue of an HP 4200 laptop with Ubuntu.  The Ubuntu developers have a custom ISO for a few HP notebooks ([http://www.ubuntu.com/support/custom/hplaptops)](http://www.ubuntu.com/support/custom/hplaptops)), but they are more of a corporate notebook and are a bit on the pricey side.  I've been looking at the [Compaq R4125]("http://www.futureshop.ca/catalog/proddetail.asp?sku_id=0665000FS10063398&catid=22495&logon=&langid=EN") and was wondering if anyone has had any issues with Ubuntu.

Thanks,
Dave

PS - I'll definitely be installing Breezy when she's ready, so if there's any other "Breezy-specific" pitfalls, I'd love to hear about them.

---

### Post by Biased turkey on 2005-09-26
I have an Elitegroup KN1 extreme motherboard, very cheap and reliable with Linux.  It has an Nvidia Nforce4 chipset:
2 onboard NICs: both detected and running out of the box with Ubuntu
Onboard Sound: detected and running out of the box with Ubuntu
2 SATA Seagate 80 GB Barracuda drives: no problem
Nvidia Ge Force 6600 video board: No problem with 2D, I'll install the 3D drivers tonight.

That was my $ .0170  ( .02 $ Canadian )

---

### Post by John.Michael.Kane on 2005-09-26
[https://wiki.ubuntu.com/HardwareSupport?highlight=%28hardware%29](https://wiki.ubuntu.com/HardwareSupport?highlight=%28hardware%29)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=hardware&titlesearch=Titles)

Hope it helps..

---

### Post by dbott67 on 2005-09-26
Thanks, Snake!  Exactly what I was looking for.  Loved you in Escape from New York.  Say "Hi" to Goldie.  :)

-Dave

---

### Post by dbott67 on 2005-09-26
Thanks, BT.  Let me know how the 3D drivers go.

-Dave

---

### Post by najames on 2005-09-26
I have the following setups tested THOROUGLY with K/Ubuntu.  I don't think you will really have many hardware problems.

AMD64 3000+ Winchester
1 gig Corsair ValueRam
Chaintech VNF4 Ultra
Onboard gigabit ethernet
Onboard sound
SataII 80gig Hitachi Drive
Nvidia Gigabyte 6600 passive cooled

K/Ubuntu has no problems detecting any of this stuff as I recall.   I have 2 of these setups (one has an IDE drive).  I think I did a BIOS upgrade on both to the 4/27 version.  Do some work and install Nvidia drivers, they work much better than nv drivers.  Plus GLXGEARS is fun to run!!  These are cheap setups, and run very well.

I have also tried Suse 10 RC1 on these and it works well, but it flat sucks until you install Nvidia drivers too.  Sound for mp3s and stuff is not working out of the box but sound does work for included games and system stuff.  This SUSE setup is more stable, but I REALLY miss K/Ubuntu, synaptic, easy configuration, etc. 

AMD64 3200 Winchester
MSI Neo2 platinum Nforce3
1gig Patriot XBL TCCD
FX5300
Dual onboard networking (seems like it found one of the network connections)
onboard sound
SataII Hitachi 80gig

I think it found one of two network connections.  Mepis (KDE) 32bit is on it now and it also installed cleanly and works well.  It has firewire, though I haven't used it yet.

---

