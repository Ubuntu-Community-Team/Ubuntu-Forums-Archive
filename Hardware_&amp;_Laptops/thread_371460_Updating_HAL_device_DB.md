---
title: "Updating HAL device DB"
date: 2007-02-26
forum: Hardware &amp; Laptops
---

### Post by bill.albertson on 2007-02-26
Hello,

I have been searching around, but have not found much information on how I may update my own HAL driver database on my laptop.

Backstory- recently, I installed a wireless networking card from MSI with a Ralink wireless chipset that was recommended on the compatibility list from (I believe) kernel.org.  The card itself works flawlessly, but does not interface at all with any of the gui network device managers under Ubuntu.  After doing some digging, I found that this is because this card is not registered in the HAL device database.  It comes up as Unknown (0x0302).

hal-device-manager can pull up alot of information about the MSI wifi card, but the card is not registered.  Therefore, it can't interoperate with network-manager, etc.  

So, does anybody know how to update the HAL database on a system?  I haven't been able to find any tools, processes, howtos, faqs, etc, that would answer this question so far.

:KS PS- I just read the HALD man page, and was redirected to freedesktop.org- [http://freedesktop.org/wiki/Software/hal](http://freedesktop.org/wiki/Software/hal)
      I will be posting more on updating HAL registry data as soon as I can grok the new info.

---

