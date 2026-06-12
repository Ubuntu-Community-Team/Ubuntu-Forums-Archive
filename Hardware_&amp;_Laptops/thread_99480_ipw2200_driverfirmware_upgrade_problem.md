---
title: "ipw2200 driver/firmware upgrade problem"
date: 2005-12-05
forum: Hardware &amp; Laptops
---

### Post by KasperTech on 2005-12-05
Dear All.

I have a huge and **very** urgent problem on the wireless part of the ever lovely Ubuntu. You see my network works fine. For about 5 minutes at the time. Then the driver instance "ipw2200" crashes, and writes the following into the file /var/log/kern.log:
> Error. Firmware error detected. Restarting.
I've downloaded the firmware upgrade as well as the driver update from ipw2200.sourceforge.net, but the update (removal of the old + installation of the new) fails with the reasons:
> "Old references found" and
"Unknown function gcc-3.4 in /usr/lib/gcc-version.h".
Could you help me, I'm literally desperate? *(Yes, I have read the read-me, it doesn't support troubleshooting at all)*
Thank you in advance.

--
Regards from Kasper

---

### Post by Houman on 2005-12-05
Hi there;

I think this has been discussed a couple time, here is one thread you should check out [http://ubuntuforums.org/showthread.php?t=75612]("http://ubuntuforums.org/showthread.php?t=75612")
and this one, which was started by me and noone replied to (i think because i hadnt done a proper search before posting, since there was a few open threads already about this problem):
[http://www.ubuntuforums.org/showthread.php?t=97160]("http://www.ubuntuforums.org/showthread.php?t=97160")

ok if youre going to compile your ipw2200 (like i did) follow this howto:
[http://www.ubuntuforums.org/showthread.php?t=26623]("http://www.ubuntuforums.org/showthread.php?t=26623")

I ran into the same problem as you, the reason for this is that these drivers need the old version of GCC, but breezy ships with the new one (gcc-4) , there are a few ways to overcome this problem and the simplest is to just download the old version from synaptic, just search for gcc and youll see gcc-3.4, and then install it, 
the other solution would be to create a simlink from the new gcc so the makefile thinks its the old gcc (doesnt work, i tried it :p)

also keep in mind that if youre going to compile these drivers there is a high chance of failure because first you have to remove the old drivers before you can install them and unfortunately the remove-old scripts in these drivers didnt work for me, so i ended up searching for everything ieee* and ipw* and deleting them from my system (i dont recommend this, dangerous if you dont know what youre doing)

ok, its seems aside from not searching before posting you have double posted this message, I think since youre a new member its a good idea to read the forum faq and guidelines [http://ubuntuforums.org/faq.php?faq=new_faq_item_gp#faq_new_faq_item]("http://ubuntuforums.org/faq.php?faq=new_faq_item_gp#faq_new_faq_item")
keep in mind its proper etiquette not to double post 

good luck;

---

