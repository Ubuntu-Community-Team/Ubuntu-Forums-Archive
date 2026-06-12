---
title: "What happened to sonypi? (Ubuntu Maverick Meerkat 10.10 - 32 bit)"
date: 2010-10-20
forum: Hardware
---

### Post by lisdavid89 on 2010-10-20
I can't find the sonypi module anymore. This basically means that I can't adjust my laptop's brightness. Did this get pulled out in the 10.10 update?

---

### Post by coffeecat on 2010-10-20
I believe the sonypi module was deprecated some time ago. On my Sony Vaio VGN-NS20S I still have Jaunty and Karmic installed on spare partitions (don't ask). Jaunty still has the sonypi.ko module but it doesn't get loaded and the Fn keys for brightness work anyway. In Karmic I can't find the sonypi.ko module anywhere in /lib/modules - and the Fn brightness keys work.

There's some inconclusive discussion in this thread:

[http://ubuntuforums.org/showthread.php?t=1586254](http://ubuntuforums.org/showthread.php?t=1586254)

As you can see, I can get the Fn brightness keys to work in Maverick with my particular model Vaio by using the Lucid kernel (which is not a very attractive option). What model do you have?

---

### Post by zebtonson on 2010-10-21
sonypi was replaced by sony-laptop 

Info at:

[http://www.mjmwired.net/kernel/Documentation/laptops/sony-laptop.txt](http://www.mjmwired.net/kernel/Documentation/laptops/sony-laptop.txt)

---

