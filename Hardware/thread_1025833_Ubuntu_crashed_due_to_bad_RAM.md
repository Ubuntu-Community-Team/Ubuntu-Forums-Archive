---
title: "Ubuntu crashed due to bad RAM"
date: 2008-12-30
forum: Hardware
---

### Post by abeo on 2008-12-30
Hi all,

Firstly, sorry about my English because i'm not an english native speaker.

I'm using UBUNTU 8.04 on an old desktop of 3 DDR SDRAM modules (bus 333), each has 256MB. I've taken the test with memtest86 and encountered some error with my RAMs (There are some error addresses). I think that is the main problem which made my system crashing down and didn't work anymore until i restarted my computer. So my question is: Is there any way to make the operating system avoid these bytes of error so it can use the bad memory?

Thank for reading my question.
Any help will be appreciated

---

### Post by Nostalos on 2008-12-30
I had a similar issue with an old server I had here.  After a little research I came up with 2 possible solutions to the problem.  

I do not have the details on it at this time, but at the time you could pass memory addressing to the kernel to not be used.  After a little more research into this it required (at the time) to have a kernel patch installed.

Not wanting to deal with custom kernels the other option was the mem kernel parameter.   The box I was using had 4GB of memory to run an app that really didnt need more than 1GB.   My bad memory was somewhere around 3.9GB block.   The solution for me was to add "mem=3800" to the kernel parameter in grub so the kernel only used the first 3.8GB of RAM.


This was several years ago.  Perhaps someone else has a better solution for you.

---

### Post by Rohan Kapoor on 2008-12-30
> **abeo said:**
> Hi all,

Firstly, sorry about my English because i'm not an english native speaker.

I'm using UBUNTU 8.04 on an old desktop of 3 DDR SDRAM modules (bus 333), each has 256MB. I've taken the test with memtest86 and encountered some error with my RAMs (There are some error addresses). I think that is the main problem which made my system crashing down and didn't work anymore until i restarted my computer. So my question is: Is there any way to make the operating system avoid these bytes of error so it can use the bad memory?

Thank for reading my question.
Any help will be appreciated
Unfortunately, you can't tell it to only use bytes of the memory anymore in 8.10 as far as I know. I tried with a really old guide I found it killed my Ubuntu install! I would reccomend running memtest86 on each module of RAM independently to see which ones have the problem and then replacing them. I have found DDR333 really **cheap** on [www.newegg.com](www.newegg.com)

---

### Post by abeo on 2008-12-31
Thanks so much for your advices,
I've tested each of my RAMs (fortunately, only one module has errors), and then I've made a best arrangement for them, so now the errors are somewhere around 703.3MB . By adding the parameter "mem=703m" to the boot text sequence, the OS now only uses 703 MB of Ram, and with the total of 768MB, i think that my problem is completely solved here.

One more time, thank you so much.

---

### Post by glotz on 2008-12-31
And, if you're into custom kernels, here's the mentioned patch. I haven't tried it myself though and would be interested in hearing any positive results. [http://rick.vanrein.org/linux/badram/index.html](http://rick.vanrein.org/linux/badram/index.html)

---

### Post by Rohan Kapoor on 2008-12-31
> **abeo said:**
> Thanks so much for your advices,
I've tested each of my RAMs (fortunately, only one module has errors), and then I've made a best arrangement for them, so now the errors are somewhere around 703.3MB . By adding the parameter "mem=703m" to the boot text sequence, the OS now only uses 703 MB of Ram, and with the total of 768MB, i think that my problem is completely solved here.

One more time, thank you so much.

Sounds good! Glad to hear that you solved it! Though you may just want to replace that one with another DDR 333 piece such as anything on this page:

[http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000147&Description=ddr%20333&bop=And&Order=PRICE](http://www.newegg.com/Product/ProductList.aspx?Submit=ENE&N=40000147&Description=ddr%20333&bop=And&Order=PRICE)

---

### Post by abeo on 2009-01-06
Thanks for your informations, but i just dont need to replace the bad 333DDR module with a new one just to get only about 60MB fresh RAM.
With 700MB of RAM, i can do almost my daily studies and works.

---

### Post by Rohan Kapoor on 2009-01-06
> **abeo said:**
> Thanks for your informations, but i just dont need to replace the bad 333DDR module with a new one just to get only about 60MB fresh RAM.
With 700MB of RAM, i can do almost my daily studies and works.

Ah allright then! Just trying to help:D

---

### Post by abeo on 2009-01-07
You are too kind, thanks again :).

---

### Post by Rohan Kapoor on 2009-01-07
> **abeo said:**
> You are too kind, thanks again :).
Kind is my middle name! Bye

---

