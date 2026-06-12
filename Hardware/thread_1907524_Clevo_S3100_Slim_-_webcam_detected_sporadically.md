---
title: "Clevo S3100 Slim - webcam detected sporadically"
date: 2012-01-11
forum: Hardware
---

### Post by Gelupah on 2012-01-11
Hi,

I have a laptop running on 11.10 64 bit. Things run fine. Webcam used to work, and now I can't seem to detect it. Cheese doesn't find it. Cheese used to work fine...

My question :

Should the webcam show up when I do a "lsusb", regardless of drivers ? (i.e., is there an easy way of finding whether it's driver related or just a bad contact somewhere ?)

Thanks,

Tony

---

### Post by Gelupah on 2012-01-11
Forgot to mention, it's an internal webcam - part of the notebook...

Thanks!

---

### Post by Gelupah on 2012-01-12
would 'lshw -C webcam' necessarily show it? Can't seem to find anything related when I type in just 'lshw'...

---

### Post by Gelupah on 2012-03-13
Well, I think I have the answer. 'lsusb' should indeed list the webcam. For some reason, it didn't. I can only assume a bad wiring connection, can't think of any other thing.

---

