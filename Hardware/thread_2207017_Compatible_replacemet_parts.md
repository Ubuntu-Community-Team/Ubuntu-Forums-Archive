---
title: "Compatible replacemet parts"
date: 2014-02-21
forum: Hardware
---

### Post by Tristan_Williams on 2014-02-21
I am wanting to upgrade the hardware in my Dell Vostro 220 Desktop, running Ubuntu Minimal 13.10.

I am not very literate in the hardware field. I focus all my knowledge at software (time to change that i guess)

Here is the page containing all of the hardware specs for my particular computer:
[http://www.newegg.com/Product/Product.aspx?Item=N82E16883155003](http://www.newegg.com/Product/Product.aspx?Item=N82E16883155003)

I want to upgrade my processor to a quad-core (if possible)
I also want to upgrade to an SSD

What are my options as far as a better processor, and SSD?

---

### Post by mörgæs on 2014-02-21
For the most detailed information about your present setup please run
```
sudo lshw -sanitize > lshw.txt
``` 
and post lshw.txt in CODE tags.

---

### Post by Yellow Pasque on 2014-02-22
> **Tristan_Williams said:**
> I want to upgrade my processor to a quad-core (if possible)

The first thing you should do is make sure your BIOS is updated (for best CPU support). The Vostro 220 was later sold with Core2 Quad CPU's and I see reports that some people have done the upgrade successfully. You'll need a Core2 Quad with Socket LGA775 (aka Socket T), so basically you're looking for a Kentsfield or Yorkfield chip. See list of models here:  [https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#.22Kentsfield.22_.2865_nm.29](https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#.22Kentsfield.22_.2865_nm.29)

> SSD?

The SSD is the easy part. The mobo has SATA2 ports, so any SATA2 or SATA3 drive should work. SATA3 drives will have max speed limited in theory, but IIRC, most people won't notice a difference.

---

### Post by Yellow Pasque on 2014-02-22
Oh, and I guess I would be remiss if I didn't point out that your current CPU (assuming it's the 3.0GHz Core 2 Duo E8400 that you linked to) will be faster in many instances than most of the compatible Core 2 Quads, because your Duo is clocked faster and has more L2 cache per core. It really depends on what you have planned for the CPU. If you're going to be doing a lot of video encoding, for instance, then a slightly lower-clocked quad core will beat your E8400. If you're planning on gaming, the money would be much better spent on a discrete GPU.

The newer Yorkfields are really the chips you want: [https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Yorkfield_.2845_nm.29](https://en.wikipedia.org/wiki/List_of_Intel_Core_2_microprocessors#Yorkfield_.2845_nm.29)

---

