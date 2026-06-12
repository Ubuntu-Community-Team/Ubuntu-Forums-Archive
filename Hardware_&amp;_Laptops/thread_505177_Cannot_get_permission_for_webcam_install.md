---
title: "Cannot get permission for webcam install"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by Tuxoid on 2007-07-20
I've spent past hour mentally beating my head into the figure out how to install ov51x v1 for my nexxtech vga pc webcam. Before trying ov51x, I both easycam 1 & 2 and tested it out with both camorama & xawtv (neither worked). So I started the install for with everything going smoothly according this: [https://help.ubuntu.com/community/Ov51x](https://help.ubuntu.com/community/Ov51x)

But when I type:
```
sudo depmod
sudo modprobe ov51x-jpeg

```

I does not even tell me it did anything!

I tried installing v0.5.4 but it gives this error when I install the modules by hand
```
insmod: error inserting '/lib/modules/2.6.20-16-generic/extra/ov51x.ko': -1 Operation not permitted
```

Even though I am definitely using sudo.

---

### Post by Tuxoid on 2007-07-20
I just tried the v0.5.4 using root but this time, instead of saying it was not permitted to insmod, it did and said nothing. I am very new to Ubuntu and Linux in general. In fact, I only installed a week ago. I believe the model number on the webcam is 2516515 but I do not! The manufacturer did not label any number as the model number!

---

