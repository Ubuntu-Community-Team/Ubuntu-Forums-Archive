---
title: "Boot hang up after Edgy upgrade!"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by mcglnx on 2006-12-19
Daer All,

I got some random booot hangs up saying "BUG!: soft lockup on CPU#0"  in rescue mode whenever I disable my wireless (Intel WLAN 3945) before booting (using Fn+F2 on inspiron 6400)

Is it something you heard about?
Is there a work around?

Thanks,
M

---

### Post by 1000i1 on 2006-12-19
I've got the same problem, but in my case my system hangs up on boot every time, unless I turn on my wireless(which I don't use at all and I don't have enabled). My wireless is Intel too, don't know which model. Hope anyone knows how to solve this cause I'm not used to turn it on, so I have to restart every time I turn on the computer.

---

### Post by mcglnx on 2006-12-20
I've found some links saying the same.
It seems it is realted to a bug from the Intel Wireless card switched off + ipw3945 driver + SMP kernel.

And it's true that I've never had the issue with -386 kernel, and have the issue with 686-SMP Kernel with Intel Wireless switched on.

I've removed the ipw3945 in /etc/modules as well blacklisted to be sure. Will re-enable whenever necessary.

Thanks again!
M

---

