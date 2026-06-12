---
title: "DVB-T with MSI TV@nywhere A/D"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by steefjeqv on 2006-11-11
Hello,

I'm going to build a media PC based on an AMD64-socket 939 setup using Edgy 64bit as OS.

I'd like to use the MSI TV@nywhere A/D for watching DVB-T broadcasts.
It's hard to find any info on the compatibility with linux.

Has anyone had any experience with these cards ?

[http://www.msi.com.tw/program/products/multimedia/mut/pro_mut_detail.php?UID=609]("http://www.msi.com.tw/program/products/multimedia/mut/pro_mut_detail.php?UID=609") 

Greetings,
Steven

---

### Post by Rodneyck on 2006-12-03
I am not running 64bit, but 32, but I don't think it matters. So,you can try the application Tvtime (I think I downloaded if with Synaptic.) The problem is that MSI TVanywhere  uses a number of different chips depending on how old your card is and so forth, so determining what chip you have is the first step. Usually this is printed on the chip itself sitting on the card.

Mine uses cx23881-27 and under Tvtime I can get it to work, sort of. It is stuck on one channel which comes in fine, so a good start. To change the channels, from what I have read, I need to somehow specify the card type (usually the manufacturer) and tuner type (not sure what they mean here, still investigating) via the Terminal or by editing some file (still looking into this.) Unfortunately, the install and driver is not intuitive enough to pick up the exact card and assign all the "Channel_up", "channel_down" and the other functions. Basically, its been a headache and if anyone can lend some assistance on how exactly to do this, I would much appreciate it.

Also, I can't get my volume to work, but one step at a time.

---

