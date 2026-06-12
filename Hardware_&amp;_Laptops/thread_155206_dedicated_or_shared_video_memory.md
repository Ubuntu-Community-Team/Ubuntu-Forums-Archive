---
title: "dedicated or shared video memory?"
date: 2006-04-04
forum: Hardware &amp; Laptops
---

### Post by zachtib on 2006-04-04
I'm entertaining the idea of upgrading to a new laptop, and I was looking at the new Dell Latitude D820 [link]("http://www1.us.dell.com/content/products/productdetails.aspx/latit_d820?c=us&cs=04&l=en&s=bsd")

For video, the options are intel integrated, or Nvidia Quadro with 256 or 512 mb.

however, I can't tell if that memory is dedicated to the video card, or shared with the system.  It does say Turbocache, but Dell usually states if a card uses shared memory.

---

### Post by az on 2006-04-04
[http://www1.us.dell.com/content/products/productdetails.aspx/latit_d820?c=us&cs=04&l=en&s=bsd&~section=specs#tabtop](http://www1.us.dell.com/content/products/productdetails.aspx/latit_d820?c=us&cs=04&l=en&s=bsd&~section=specs#tabtop)

I clicked on the "learn more about graphics" link And hit the details tab and it brought up a window.  Read the specs for your model, but it seem to be both local and shared:

512MB NVIDIA Quadro NVS 120M TurboCache - D820 only System Memory Local Physical GPU memory Total Reported Graphics Memory 
 
4GB 256MB 512MB 
2GB 256MB 512MB 
1GB 256MB 512MB 
512MB 256MB 256MB 
256MB 256MB 256MB 
The total of local and shared* system memory used by this graphics card is up to 512MB. Local on-board memory is 256MB. Up to 256MB of system memory may be allocated to support graphics, depending on system memory size and other factors.

256MB NVIDIA Quadro NVS 110M TurboCache System Memory Local Physical GPU memory Total Reported Graphics Memory 
 
4GB 128MB - D820 
64MB - D620  256MB 
2GB 128MB - D820 
64MB - D620  256MB 
1GB 128MB - D820 
64MB - D620  256MB 
512MB 128MB - D820 
64MB - D620  128MB 
256MB 128MB - D820 
64MB - D620  128MB 
The total of local and shared* system memory used by this graphics card is up to 256MB. Local on-board memory is 64MB on Latitude D620 systems and 128MB on Latitude D820 systems. On the D620 up to192 MB of system memory may be allocated to support graphics. On the D820 up to 128 MB of systems memory may be allocated to support graphics. The amount of system memory allocated is dependent on system memory size and other factors.

---

### Post by zachtib on 2006-04-04
excellent.  for my next question, does nayone know if turbocache can be disabled in bios?  if so, id likely buy the 512mb card with 256 dedicated and leave it at that.  I dont want my graphics card EVER thinking it needs more memory on its own and borrowing at will...

---

### Post by mitbac on 2006-04-16
you probably don't want to do that because the great thing about TurboCache is its ablility to grab and give back on demand.  TurboCache obviously isn't going to be faster than 2x 256mb sli graphics cards but with 8gb/s bandwidth on pci-e and assuming you're using ddr400 memory about 2.5gb/s bandwidth you have the equivilant bandwidth of about 10.5gb/s   .....which is a lot.  so yea good gpu especially for the cost/size factors.  You should really check out the nvidia web site.  btw im planning on getting the d820 also

---

