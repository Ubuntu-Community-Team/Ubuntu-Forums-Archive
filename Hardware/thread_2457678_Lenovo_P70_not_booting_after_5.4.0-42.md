---
title: "Lenovo P70 not booting after 5.4.0-42"
date: 2021-02-06
forum: Hardware
---

### Post by pwahl on 2021-02-06
Dear All, both my wife and I have the same Lenovo P70 laptop, and we both need them to work from home. Laptop gone, work gone, so it's kind of urgent :-)

Ever since the OS upgrade (both 18.04 LTS and 20.04 LTS) upgrades to a kernel newer than 5.4.0-42; they won't boot anymore, and the only thing we can do is re-image our computers.

I have added this to both our machines:

/etc/apt/apt.conf.d/01autoremove-kernels-stop

APT::NeverAutoRemove
{
   "^linux-image-*-generic$";
   "^linux-headers-*-generic$";
   "^linux-image-extra-*-generic$";
   "^linux-signed-image-*-generic$";
   "^.*-kernel-*-generic$";
   "^linux-tools-*-generic$";
};

(taken from [https://itectec.com/ubuntu/ubuntu-keep-old-kernels](https://itectec.com/ubuntu/ubuntu-keep-old-kernels))

but that can only be a work-around, not the final solution. That gives us the ability to choose 5.4.0-42 from the Ubuntu boot menu.

What can we do? We do NOT want to go back to Windows, I have been using Ubuntu for a very very long time and it never let me down.

Thank you very much in advance, Peter & Celine

---

