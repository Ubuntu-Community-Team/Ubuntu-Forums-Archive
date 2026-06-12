---
title: "NEC ND-3540 Burning Speed"
date: 2005-06-30
forum: Hardware &amp; Laptops
---

### Post by lakerssuperman on 2005-06-30
I just got my new NEC 3540 burner.  However, i can't burn at 16x in K3b.  I can burn at this speed in windows but not in linux even though k3b reports that it is using 16x burning speed.  I an using Ridata 16x DVD+R disc from Newegg.com.  Does anyone know how i can get burning at 16x.  Thank You

---

### Post by PhilippWollermann on 2005-06-30
I had a similar problem today - I burned some audio CDs and the burner should be able to use 16x (and k3b even said, that it would burn using 16x). The speed was more about 8x the whole time. I haven't found a solution to my problem yet, but could you please try

sudo hdparm -I /dev/hdb

Just set "hdb" to the right device, so you're querying the DVD burner. Please post the output here, so I'll see whether DMA is enabled.

Philipp

---

### Post by lakerssuperman on 2005-06-30
I thought i enabled dma.  Apparently i didn't. I just enabled it and am going to burn a disc and see what happens.  Thanks

---

### Post by lakerssuperman on 2005-06-30
I successfully burned a DVD at 16x after i enabled DMA.  The only other problem is that CD ripping is extremely slow, around 1.5x even after enabling DMA.  My old Liteon drive gets around 4x or so and is set to slave in my system.  Any idea what could be causing this problem.  Thanks for the help.

---

### Post by PhilippWollermann on 2005-07-01
That's great, that the burning worked at 16x! :-)

Is audio-ripping faster when you try it in Windows? Maybe your drive is simply rather slow (some unfortunately are). However, I think it's more probable, that some kind of "error correction" is activated, which extremely slows the ripping down. Which program do you use to rip the audio from the CD?

Philipp

---

### Post by lakerssuperman on 2005-07-01
I haven't yet tried ripping audio in windows but i use sound juicer, ripperx, and goobox and all are slow.  I find it weird that audio ripping would be that slow.  I will try ripping in windows later and let you know

---

### Post by lakerssuperman on 2005-07-02
Just read through the forums and there is a noted problem with Ubuntu and cd ripping speeds.  It has to do with the kernel and a patch that hasn't been applied yet.  Hopefully it gets fixed in Breezy.

---

