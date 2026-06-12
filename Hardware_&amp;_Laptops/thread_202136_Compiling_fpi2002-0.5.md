---
title: "Compiling fpi2002-0.5"
date: 2006-06-22
forum: Hardware &amp; Laptops
---

### Post by jgordon510 on 2006-06-22
I'm trying to compile the fpi2002 enabler which is supposed to make my stylus on my Compaq TC1000 tablet pc work, but when I try to compile it I get the following error:

> make[1]: *** No rule to make tager 'modules'. Stop.
> make[1]: 'Leaving directory /lib/modules/2.6.15-386/build'
> make[1]: *** [fpi2002.ko] Error 2

I haven't the first clue what I'm doing.  Can somebody tell me what I should do?

Thanks.

---

### Post by hsalgado on 2007-05-22
You need to get the headers for the distribution you are using:  2.6.15

apt-get install linux-headers-2.6.15-23 linux-headers-2.6.15-23-686
apt-get install setserial

I don't know if you are using 2.6.15-23 or other...

I had the same problem and I just changed the 2.6.15-23 to my distribution and it did work.

Good luck!

---

