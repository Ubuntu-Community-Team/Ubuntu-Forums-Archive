---
title: "dual graphics cards"
date: 2007-06-20
forum: Hardware &amp; Laptops
---

### Post by Cubicegg on 2007-06-20
hi, my laptop (rock pegasus 650) has 2 graphics cards - enabled via a sliding switch at the front  before boot-up.

i installed ubuntu feisty on the laptop when the nvidia geforce 6600 was active. i have since enabled the intel integrated graphics and can not successfully boot into the ubuntu gui but instead am thrown into a command prompt.

i have tried running dpkg-reconfigure with no luck in rebooting with the modified settings.

i hope someone might have some ideas?

thanks James

---

### Post by ukripper on 2007-06-20
Can you post output of the following command:

```
lspci | grep VGA
```

---

