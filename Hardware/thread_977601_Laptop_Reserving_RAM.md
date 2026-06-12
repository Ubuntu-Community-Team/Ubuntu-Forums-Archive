---
title: "Laptop Reserving RAM"
date: 2008-11-10
forum: Hardware
---

### Post by metroidnemesis13 on 2008-11-10
I've never had a laptop before this one.  I just put Ubuntu 8.10 64 bit on my HP/Compaq Presario v2000 and I noticed something strange.  I think the video card or something is reserving 128 MB of my RAM (total ram 512 MB) and it's causing stuff to lock up because I'm out of RAM.  Does anyone elses laptop do this, and is it normal?

---

### Post by prshah on 2008-11-10
> **metroidnemesis13 said:**
>  I think the video card or something is reserving 128 MB of my RAM (total ram 512 MB) and it's causing stuff to lock up because I'm out of RAM.

Yes, especially Intel Graphics chipsets share RAM with the system. While the newer chipsets use RAM dynamically (usually starting with 8Mb and then moving upward when required), earlier chipsets used a fixed amount. Usually, this amount can be adjusted in the BIOS.

With only 256Mb, I'd suggest you use a graphics memory of 4Mb if possible, or 8Mb at most.

---

### Post by metroidnemesis13 on 2008-11-10
Excellent.  That's exactly the answer I wanted.  Thanks a lot, I've been asking around for an explanation like this.  So will 8 MB really cut down my graphical power?  I'm not going to play games on this thing, and I only have 512 MB (I ordered a gig stick in the mail, it's coming in two days).  Then I'll have 1.256 Gigs to mess with.  So how much ram do you recommend I set aside for the vga card if I have 1.3 gigs of ram and I'm only surfing the net and using open office?

---

### Post by prshah on 2008-11-10
> **metroidnemesis13 said:**
> So will 8 MB really cut down my graphical power?  

If you're playing games, 8Mb will not suffice for most higher end games. However, graphics "power" depends more on the chipset than the amount of Graphics RAM. If you're using Intel onboard, games performance will be only "acceptable" no matter how much RAM you throw at it.

For ordinary uses, 8Mb Graphics RAM is more than enough to give you a desktop of 1280 x 800 @ 24 bit color (Windows calls this 32bit color).

---

