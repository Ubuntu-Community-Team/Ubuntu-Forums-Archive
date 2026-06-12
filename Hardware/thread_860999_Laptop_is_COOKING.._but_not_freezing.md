---
title: "Laptop is COOKING.. but not freezing"
date: 2008-07-16
forum: Hardware
---

### Post by Curse on 2008-07-16
Hey all, did a search, tried some stuff to no avail, so here I am.

I have a 2.5 year old HP laptop with a 2.2ghz AMD Turion 64 processor, integrated ATI 200m GFX card, 1gb of RAM, 80gb HDD, and it runs HOT.

It did it with XP, which I ran for years, and since I use my laptop a lot more now (since I <3 Xubuntu), its becoming and issue.

The laptop itself will get very hot, as in uncomfortable to have on your lap, you can feel it through the top keys (around ESDF area) and all over the bottom. The fan runs 99% of the time.

I'm guessing its a graphics card issue, because my processor runs @ 800mhz when I'm just browsing. I ran acpi -t
and got:

      Battery 1: charged, 100%
     Thermal 1: ok, 0.0 degrees C

Anyone have any ideas? :x



OH, on a semi-unrelated note, the only issue I'm having with Xubuntu is getting apps onto my top toolbar, I can't seem to find the right file to link to? And for the command line... no idea. Even getting a simple Terminal button seems beyond me... I can get the icon there, but leave the "Command Line" section empty and get a non-funtional button :(

---

### Post by Cotopaxi on 2008-07-16
a crazy idea: use a laptop cooler. Here just a link form amazon:

[http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=Laptop+Cooler&x=0&y=0](http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=Laptop+Cooler&x=0&y=0)

one of these devices is activated by the USB port, so you can use it on a travel, of course at the expense of loosing battery time.

I have had two laptops and they got hot like ovens, so I know the problem. When I was on a trip, I allways tried to put 4 small cups under the laptop, to increase airspace below the laptop, for improving ventilation.

If you have a technical service nearby, make him open the laptop and blow through with "dry air" (In Spanish they call it this way). The ventilator of the laptop may be quite filled with dust, so its ventilation capacity could have decreased dramatically.

I hope this helps!

---

### Post by Curse on 2008-07-16
> **Cotopaxi said:**
> a crazy idea: use a laptop cooler. Here just a link form amazon:

[http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=Laptop+Cooler&x=0&y=0](http://www.amazon.com/s/ref=nb_ss_gw?url=search-alias%3Daps&field-keywords=Laptop+Cooler&x=0&y=0)

one of these devices is activated by the USB port, so you can use it on a travel, of course at the expense of loosing battery time.

I have had two laptops and they got hot like ovens, so I know the problem. When I was on a trip, I allways tried to put 4 small cups under the laptop, to increase airspace below the laptop, for improving ventilation.

If you have a technical service nearby, make him open the laptop and blow through with "dry air" (In Spanish they call it this way). The ventilator of the laptop may be quite filled with dust, so its ventilation capacity could have decreased dramatically.

I hope this helps!

Hey, thanks for your reply! 

I always wondered if those coolers actually worked... might have to try one of those out :)

On another note, I found a processor governor applet and have set it to 800mhz, seems to cool her right down :)

Thanks!

---

