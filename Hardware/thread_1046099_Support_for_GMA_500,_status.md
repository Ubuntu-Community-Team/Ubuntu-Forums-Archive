---
title: "Support for GMA 500, status?"
date: 2009-01-21
forum: Hardware
---

### Post by mathiasm on 2009-01-21
I know this has been discussed before, but I haven't quite figured out the exact status. 

Is the problem that there is no linux driver available supporting this chip, or is it just that the current driver is incompatible with the kernel version used in Intrepid?

---

### Post by CrazyDesi on 2009-01-23
I am curious about this also.

---

### Post by cb951303 on 2009-01-24
+1

I'm planning to build an ultra low power home server. I need to know if GMA 500 works with linux

---

### Post by AdamWill on 2009-01-29
There's currently no driver. The problem is the hardware is really a PowerVR chip, it's not at all the same architecture as previous Intel chips. Rumours have it that Tungsten (who develop the PowerVR chips) are working on a driver, but it's not been confirmed anywhere official that I can find.

---

### Post by cb951303 on 2009-01-30
> **AdamWill said:**
> There's currently no driver. The problem is the hardware is really a PowerVR chip, it's not at all the same architecture as previous Intel chips. Rumours have it that Tungsten (who develop the PowerVR chips) are working on a driver, but it's not been confirmed anywhere official that I can find.

hmm, is it VESA compliant. That's all I need for the server

---

### Post by AdamWill on 2009-01-30
Yeah, it works with the vesa driver OK. Slow, of course, and you won't get much resolution out of it, but it works.

I have been looking into this some more today. It's a mess.

[http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/](http://www.happyassassin.net/2009/01/30/intel-gma-500-poulsbo-graphics-on-linux-a-precise-and-comprehensive-summary-as-to-why-youre-screwed/)

---

### Post by Yashiro on 2009-01-31
Interesting info. I'll be staying clear of this product for now and advising friends to do the same.

---

### Post by stephanvaningen on 2009-05-11
Isn't there a possibility for porting binaries from Windows into Linux as is being done with wireless cipset drivers sometimes (I used ndiswrapper in earlier versions of Ubuntu to get a broadcomm -chipset running...)?

Why is that no option on video chipsets?

---

### Post by argor on 2009-07-16
> **AdamWill said:**
> There's currently no driver. The problem is the hardware is really a PowerVR chip, it's not at all the same architecture as previous Intel chips. Rumours have it that Tungsten (who develop the PowerVR chips) are working on a driver, but it's not been confirmed anywhere official that I can find.
there seems too be some misunderstanding  
Tungsten  just are are some company that intel hired too write  driver for the GMA 500(powervr SGX 535) as they(intel) did not use the drivers that 
Imagination Technologies(they make the chips) make 
as i understand it  Tungsten driver are crap compeer to imtec drives 
and imtec has linux driver

---

