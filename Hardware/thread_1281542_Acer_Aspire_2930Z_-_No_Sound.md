---
title: "Acer Aspire 2930Z - No Sound"
date: 2009-10-03
forum: Hardware
---

### Post by SonicEpsilon on 2009-10-03
I recently installed Xubuntu 9.04 on an Acer Aspire 2930Z. The only issue is that I can't get any sound working on the front ports (where the headphone, microphone and line-in ports are). This is an annoyance since I use my headphones all the time. How can I get this to work?
NOTE: I have used both Ubuntu and Kubuntu on this and they don't work either with the front ports.

---

### Post by moster on 2009-10-03
I have acer aspire too. But different version. I have installed new kernel and everything is better. Maybe it will solve your problem too. 

Ok, here is the steps.
1. download and **install** this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630_2.6.30-020630_all.deb")

2. then this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-headers-2.6.30-020630-generic_2.6.30-020630_i386.deb")

3. then this: [http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.30/linux-image-2.6.30-020630-generic_2.6.30-020630_i386.deb")

4. Done! restart and select new kernel at startup. Wish luck.

reason why I did not recommend 2.6.31 is because it do not work on my acer aspire. I get black screen only.

27 more days till Karmic Koala :) You can try beta now..

---

