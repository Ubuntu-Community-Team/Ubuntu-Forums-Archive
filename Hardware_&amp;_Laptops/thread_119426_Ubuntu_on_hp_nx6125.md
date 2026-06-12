---
title: "Ubuntu on hp nx6125"
date: 2006-01-19
forum: Hardware &amp; Laptops
---

### Post by talger on 2006-01-19
Hello!
I bought a Hp nx6125 ([PY421EA]("http://h10010.www1.hp.com/wwpc/hu/hu/sm/WF06b/1090717-1124059-1124059-1124059-1124115-12225192-53005531.html"), Sempron 3100+), and I would like to install ubuntu on it. I tryed install breezy and dapper flight 3, but everytime something doesn't work.
I try to start ubuntu first time with 'noacip nolacip' but the system is very slow. 
(the installation take more than 2hours... :( )
I can't set up the wireless lan. On breezy I load the driver into the ndiswrapper, and it say 'driver and the hardware present', but i can't connect to my network. On Dapper I needn't use ndiswrapper, because the system recognize it, but i can't use it. (every case i set the essid,channel,wep,etc).

So, how can I install ubuntu linux on my laptop? :)
(sorry my english)

---

### Post by brk3 on 2006-01-19
Well, this mightnt be the answer you wanted to hear(sorry about that!) but, i would recommend trying opensuse 10([www.opensuse.org)](www.opensuse.org)).  Because I got a hp pavilion zv6175 which is probably similar and ubuntu gave alot of problems aswell. Opensuse set up everything perfectly first time and I havent looked back since! Well maybe once ubuntu gets up to scratch ;)

---

### Post by dragdusan on 2006-04-27
I bought same latop hpnx6125(ek107es) and had same problems with it. I solve problem, when I disabled PowerNow! in bios settings.When I finished installation
I enabled PowerNow! and it works just fine for me. Try this...

Good Luck

Dragosavac Dusan
-----------------

---

### Post by talger on 2006-04-27
[QUOTE=dragdusan]I bought same latop hpnx6125(ek107es) and had same problems with it. I solve problem, when I disabled PowerNow! in bios settings.When I finished installation
I enabled PowerNow! and it works just fine for me. Try this...

Good Luck

Dragosavac Dusan
-----------------[/QUOTE]
Thank you the advice, i will try it.

Can you use the wireless lan?

What did you install on it? Breezy or Dapper?

---

### Post by dragdusan on 2006-04-27
no, but trust me when I get it going, i will tell you, ok???

by the way my English isn't that much good, so sorry for any mistakes, ok??

Dragosavac Dusan
--------------------

---

### Post by sloser on 2006-08-03
just at the first welcome screen hit F6, then just append "noapic nolapic" at the end of the line that appears and press Enter. 

and after that Live CD will fly... and after instalation (about 20 min) ubuntu will work on hp nx6125 perfectly...

---

### Post by Similar on 2006-08-09
Basically, the Topic Starter used the wrong kernel options..or at least he spelled them wrong.

He said that he used "noacip nolacip" when its supposed to be noapic nolapic..but the above poster said that already


What i'm particularly curious about is wether or not you guys got the graphics card working..I tried it with different methods (the apt-get, and the one posted on these forums) and it didn't work for me..

---

