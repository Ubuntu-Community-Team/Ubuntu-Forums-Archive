---
title: "TV-out through VGA on Mobility x1400"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by FredPiano on 2006-07-18
I have an IBM ThinkPad Z61m, runnung Ubuntu Dapper.  It has an ATI Mobility x1400, and I've read that the S-Video out isn't supported under Linux.  Lo and behold, I tried it and it doesn't work.  So, I looked for an adapter that might help, and I found this: [http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10401&cs_id=1040113&p_id=2509&seq=1&format=2&style=]("http://www.monoprice.com/products/product.asp?c_id=104&cp_id=10401&cs_id=1040113&p_id=2509&seq=1&format=2&style=")
From what I understand, this will only work on some video cards.  What I want to know is if it will work on mine or not.

Thanks

---

### Post by nicbink on 2006-07-19
Did you do any experimenting with the TV out?  If you plug it in while it's running it probably won't display anything until the xorg.conf is setup to either run a dual display, cloned, or single tv out.

ATI claims that their FGLRX driver supports TV out.  Are you using that driver?  

Search around the forums/interweb for someone's ATI xorg with TV out enabled.


That dongle probably won't work, I used to have one of those and it only worked with my Matrox cards.

---

### Post by FredPiano on 2006-07-20
I  didn't think it would work.  This is where I read that the TV-out doesn't work at all: [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html#181179](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.26.18.html#181179)
Mine's an x1400.  I could be misreading it.  I'll go try again and let you know how it turns out.

---

