---
title: "ASUS DVD Burner"
date: 2006-03-02
forum: Hardware &amp; Laptops
---

### Post by bluevoodoo1 on 2006-03-02
I have an [ASUS DRW-1608P2 DVD burner]("http://www.newegg.com/Product/Product.asp?Item=N82E16827135046") and I've had some problems with it since the beginning. In this [post]("http://ubuntuforums.org/showthread.php?t=117772") I described the trouble to get DMA working (still haven't gotten DMA to work). I was wondering if there are any people that have or use this drive and got DMA to work. 

If not, what are some other potential ideas I could try that is hardware-related... change jumper cables, new IDE cable, firmware[?] etc. etc. to get this working? Or anything software related. Would a newly configured kernel give this drive DMA support? I'm running the 2.6.12-10-686 kernel. Will waiting for Dapper help?

I probably should have looked up DVD burners before I bought this one (oh well, that's what I get for buying something on sale!)

---

### Post by bluevoodoo1 on 2006-03-03
Well... I compiled a kernel with DMA support... still no luck...

What brand/model DVD burners do you all use???

---

### Post by StefanoCole on 2006-03-03
I have a Philips internal DVD burner, model is: DVDR1628K/00. I have used it successfully with Gnomebaker. Before using it I have enabled DMA editing the file hdparm.conf 

Stefano

---

