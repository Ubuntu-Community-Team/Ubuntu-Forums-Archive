---
title: "Acer Aspire 1522/24?"
date: 2005-06-14
forum: Hardware &amp; Laptops
---

### Post by nocturn on 2005-06-14
I'm about to buy a portable and two models of Acer have made the final list.
So I was wondering if anyone had an Aspire 1522 or 1524 and if everything works.

So far, I have seen on this forum that Sound, graphics, dvdwriter, synaptic touchpad all work.

I'm wondering about the graphics in widescreen mode.
The Wlan card should work with Ndiswrapper (can anyone confirm).  Can it be done native?

Thanks

---

### Post by daugirdas on 2005-06-14
I've got it. Widescreen will work with modified x.org. Sound is fine, synaptic works. Wlan works only in 32bit mode (even though there are 64bit win drivers). cd/dvd burning is sort of ok, there might be some hw reliability issues. Suspend is broken. 
nb. acer doesn't seem to respond to any queries or even warranty issues. You may be left without anything even if you bought extended warranty. Their customer service simply doesn't exist. If that is important you may want to consider hp with linux preinstalled instead.


For more information see [http://www.michelemariottini.it/Acer_1524WLMi.html](http://www.michelemariottini.it/Acer_1524WLMi.html)

---

### Post by nocturn on 2005-06-15
[QUOTE=daugirdas]
nb. acer doesn't seem to respond to any queries or even warranty issues. You may be left without anything even if you bought extended warranty. Their customer service simply doesn't exist. If that is important you may want to consider hp with linux preinstalled instead.
[/QUOTE]

Thanks for the information.  Is it really that bad? (anyone else experienced this).
I was also thinking of buying the extended warranty (3 years pick up and return, repair within 5 days)...

Does HP offer better support?  (I had some bad experiences with them on printers, don't know about other products though).

---

### Post by nocturn on 2005-06-15
[QUOTE=daugirdas]I've got it. Widescreen will work with modified x.org. Sound is fine, synaptic works. Wlan works only in 32bit mode (even though there are 64bit win drivers). cd/dvd burning is sort of ok, there might be some hw reliability issues. Suspend is broken. 
nb. acer doesn't seem to respond to any queries or even warranty issues. You may be left without anything even if you bought extended warranty. Their customer service simply doesn't exist. If that is important you may want to consider hp with linux preinstalled instead.


For more information see [http://www.michelemariottini.it/Acer_1524WLMi.html](http://www.michelemariottini.it/Acer_1524WLMi.html)[/QUOTE]

Another question to you Daugirdas, is ACPI (quering battery status etc) working on that machine?  I read something about recompiling the kernel to get it working?

---

### Post by faqpete on 2005-06-16
Hi!
Im running Ubuntu Hoary on an Aspire 1522 WLMi without any problems - out of the box. WLan does the job with ndiswrapper, Sound, Graphics, DVD and CD-burning ... no problems, eben battery-stat works fine **without** recompiling the kernel.

faqpete

---

### Post by fxalpha on 2005-08-12
i have 1524wlmi and everything works in ubuntu i386 hoary. in 64bit, wireless doesn't work, but that's the win drivers for you! (complains about wrong os)
my box overheats if i don't raise it to improve airflow underneath. I had it shut down in the middle of a zsnes session and decided to make sure all vent were free of shite. Open the ram panel underneath and you know those stickers on th ram dimms? there was a small screw stuck to one of them, think it was bridging some contacts. explains why some days it was better than others. i've been free from random restarts for a week now. don't buy from acer. it has good linux compatibility but it's a nightmare to get through to anyone apart from sales. centrino is a good tech, but is made by intel. i use linux because of microsofts business practices. i use amd because of intel's. just 2 cents

---

### Post by xristos on 2005-08-26
I own a 1524 and I am prety happy with ubuntu .
One problen is suspend to RAM and to DISK . They simply don'y work . But then again I don't know if there is a laptop out there that has these problems with linux solved.

Also Linux is lighter than windows so there is significantly less heat coming out from the laptop and  when i work with ubuntu the fan works in less rpms and you can't hear it. :grin:

hope that i helped

---

