---
title: "Lenovo s10-3 hdd anti shock"
date: 2010-06-04
forum: Hardware
---

### Post by Dziurgis on 2010-06-04
Hi all,

I am rather new to Ubuntu.
I recently installed Ubuntu netbook 10.04 on my Lenovo S10-3.
The netbook came with Windows 7.
Does hard drive anti-shock included in 10.04 already or should I install some software.

Thank you for answers.

Dziurgis

---

### Post by weirdtalk on 2010-06-04
Don't quote me on this, but I recall reading somewhere that it was a feature on the linux kernel, so it should be supported without any package needed.

---

### Post by Phocean on 2010-06-04
The module, hdaps, is now part of the kernel.

However, you have to install the userspace daemon :
$ aptitude install hdapsd

And that's it. Sensivity can be adjusted in /etc/default/hdapsd.

---

### Post by weirdtalk on 2010-06-04
huh, learn something new everyday.

thanks Phocean.

---

### Post by outerspacerace on 2010-06-24
I'm thinking of getting one of these & just wondering how you're finding it after having used it a while?

Seems like a great netbook, though many reviews complain about the trackpad being hard to use, did you get used to it?

Also, how is 10.04 going? I saw this bug [https://bugs.launchpad.net/ubuntu/+bug/590174](https://bugs.launchpad.net/ubuntu/+bug/590174) about the webcam and was wondering if you'd ran into any other problems?

I'm guessing the webcam issue is no biggie and will be fixed soon.

Thanks in advance.

---

