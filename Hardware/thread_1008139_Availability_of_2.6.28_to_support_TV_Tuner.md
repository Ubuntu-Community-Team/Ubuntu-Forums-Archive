---
title: "Availability of 2.6.28 to support TV Tuner"
date: 2008-12-11
forum: Hardware
---

### Post by mathew42 on 2008-12-11
I have an Asus G71v laptop which has a TV tuner based on the "STK7700D" chipset. This chipset is common to many Asus laptops .

According to this [thread]("http://www.linuxquestions.org/questions/linux-hardware-18/stk7700d-tv-tuner-in-ubuntu-linux-8.10-686500/"), the [V4L/DVB (9041): Add support YUAN High-Tech STK7700D (1164:1f08)]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commitdiff;h=8751aaa6c8be191171cd8c7db01a9b4e01892b08") patch will enable support.

I'd appreciate some guidance on the best way forward to enable support:
[LIST=1]
[*]Wait for a 2.6.28 kernel to be released fro 8.10. Will this happen?
[*]Attempt to patch the 2.6.27 kernel. Should I submit a bug report?
[*]Upgrade to 2.6.28.
[/LIST]
I've previously compiled kernels for other distributions, but I'd prefer to follow the best way for Ubuntu rather than mangling my system.

---

### Post by Ayuthia on 2008-12-11
I have not seen any of the Ubuntu versions ever change kernel from 2.6.x to 2.6.y.  There are releases that will come in for 2.6.27 though.

Have you tried using mercurial and building the modules from linuxtv.org:
[http://www.linuxtv.org/repo/](http://www.linuxtv.org/repo/)

I have done that with my TV tuner in Arch and it has been working well for me.  Of course, you will have to compile the modules every time there is a kernel update.

---

### Post by mathew42 on 2008-12-12
Thanks for your advice. I was able to follow the instructions and compile the module. The only issue I had was that the firmware in /lib/firmware was out of date. I couldn't find an "official" firmware repository, but I was able to download it from [http://www.wi-bw.tfh-wildau.de/%7Epboettch/home/files/dvb-usb-dib0700-1.20.fw](http://www.wi-bw.tfh-wildau.de/%7Epboettch/home/files/dvb-usb-dib0700-1.20.fw).

Now it looks like I need to connect the card to a decent antenna, as scan is reporting that "tuning failed".

---

### Post by radu_radu on 2009-07-02
I'm sorry to necro this thread, but can you tell me if your tuner worked?

---

