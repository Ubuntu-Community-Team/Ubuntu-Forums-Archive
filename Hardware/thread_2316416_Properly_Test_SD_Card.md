---
title: "Properly Test SD Card"
date: 2016-03-07
forum: Hardware
---

### Post by Elijah_Duffy on 2016-03-07
What tools should I use to properly test both the speed and capacity of a Micro SD Card that I purchased off of Aliexpress? 

Information Claimed by Seller:
Transcend Premium 400x
32 GB Micro SDHC
Class 10

---

### Post by Bucky Ball on 2016-03-07
*Thread moved to **Hardware**.*

The class should be written on it. As far as size, put it in the machine, open Disks or Gparted. Have a look.

* Is [this what you're talking about]("http://www.transcend-info.com/Products/No-264")? I see no class written on there. Might be somewhere so have a look. If you have that card, wouldn't worry about speed. Designed for it.

Further note: [https://duckduckgo.com/?q=Transcend+Premium+400x+class](https://duckduckgo.com/?q=Transcend+Premium+400x+class)

---

### Post by sudodus on 2016-03-08
Does the card do what you want it to do? For example - can it store video that you are recording (without problems)?

1. If it does, fine :-)

2. If the card does not do what you want it to do - test if it can read and write at the speed specified (and check the size as suggested by Bucky Ball). If this is the case, please come back and we can talk about testing the performance. It depends how you intend to use the card.

---

### Post by Elijah_Duffy on 2016-03-08
Yes, the class is written on it and claims to be class 10. The size both written on and shown in Disks shows up to be 32GB as claimed. However, as I mentioned I bought this from China and in the past I have received quite a few fakes cards that trick the computer into showing the fake storage. For example a 32GB Class 10 was actually a 6GB Class 4 or below. 

Because of this it has become a habit to test SD Cards while I can still get my money back. When I ran Windows I used H2TestW, which I can run (and have previously) through Wine, however, I would like to test it using a different program built for Ubuntu / Linux.

Thanks!

---

### Post by sudodus on 2016-03-08
I see. I think the easiest way is to continue using H2TestW via Wine. Maybe someone else knows a corresponding tool for linux. But if you know how fast you should be able to read from and write to the card, you can do it 'manually' with linux commands and measure the speed and check that it it possible to use the nominal size (all 32 GB ~ 29.8 Gibibytes).

[https://en.wikipedia.org/wiki/Secure_Digital](https://en.wikipedia.org/wiki/Secure_Digital)

> Class 10 	**10 MB/s** 	Full HD (1080p) video recording and consecutive recording of HD stills (high-speed data bus)

Class 10 asserts that the card supports 10 MB/s as a minimum non-fragmented sequential write speed and uses a High-speed bus mode.

This means writing a huge single file (which is 'easier' than writing many small files of the same total size).

---

### Post by Bucky Ball on 2016-03-08
If it came in a sealed Transcend packet, says Class 10 and is showing as 32Gb, me thinks that's what it is. Going to the trouble of getting a fake card into a sealed Transcend packet is no mean feat and probably worth more effort than selling the card.

But test away, but all means. You never know ...

---

