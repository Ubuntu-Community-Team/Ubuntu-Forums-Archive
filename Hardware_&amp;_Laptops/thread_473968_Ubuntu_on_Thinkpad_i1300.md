---
title: "Ubuntu on Thinkpad i1300"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by pfh on 2007-06-14
Short version:
Is there anyway for me to start a 7.04 installation, but with an older kernel? Say 2.6.x where x < 15? My laptop crashes no matter what I do with the stock 7.04 cd and the alternate cd.

Long version:
I have an old IBM ThinkPad i1300 with a 750Mhz Celeron and 128 MB RAM and 10 GB HD.

I want to install Ubuntu (preferably 7.04/Feisty) on it, but neither 7.04 nor 6.06 is able to get very far during installation (let alone completing an installation). I also tried the alternate cd and I tried pressing F6 and adding various combinations of kernel options that I found googling (irqpoll, pci=conf2, noacpi, and many more), and so on. Nothing solves the problem completely. 

The best I was able to do was booting on 7.04 alternate (can't seem to find 6.06 alternate anywhere), giving some combination of kernel parameters that I don't remember (I think the most important one was irqpoll or pci=conf2), and then it would actually get further on with the text mode installation, letting me choose keyboard etc. But it still hangs later in the process.

I've since read here [http://www.maniar.ca/news/2007/05/051607.html]("http://www.maniar.ca/news/2007/05/051607.html")
that while the linux kernel before 2.6.15 worked fine on i1300, later kernels just don't work on it. I would that a step back :)

Now, is there anyway for me to start a 7.04 installation, but with an older kernel? Say 2.6.x where x < 15?

Or is there another solution?

Thanks in advance!

/pfh

---

### Post by pfh on 2007-06-14
Anyone, please?

---

### Post by bjstults on 2007-06-14
Total memory is just too low.

---

### Post by pfh on 2007-06-15
> **bjstults said:**
> Total memory is just too low.

Really?! Are you sure? I am almost certain that you are wrong. I seem to have read about many people running Ubuntu on old computers with 128 MB RAM. Why wouldn't the installer be able to load in 128 MB? And for actually running the system (which I never get around to), swap would be used.

Please, anyone?!

---

### Post by moh64 on 2008-03-16
i installed SuSE 10.1(kernel 2.6.16.13-14)  using "hdc=none irqpoll" boot parameters , then after install finished i removed "hdc=none" from menu.lst

kubuntu 6.06(kernel 2.6.16) install cd booted with" irqpoll"

---

