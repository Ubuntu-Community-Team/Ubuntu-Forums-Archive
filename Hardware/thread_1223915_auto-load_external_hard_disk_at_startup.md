---
title: "auto-load external hard disk at startup"
date: 2009-07-26
forum: Hardware
---

### Post by d3ngar on 2009-07-26
Hello,

I bought a mini desktop computer to run as my 'movie-box' about a year ago. It was running Windows Vista Home as it came factory shipped and it took me this long to change the OS, even though the home edition was pretty tiresome to configure and many things wouldn't work like I'd like them too.

Anyways, this weekend I installed ubuntu Jaunty...
Obviously there are now problems :)

This post is regarding the external hard disk that is connected via USB:

When the machine boots up, it doesn't recognise the hard disk and I can't navigate to it.

The device is also not listed in the /dev/ folder...

Once I plug another device in, or uplug the hard disk and re-plug it, it works like a charm...

What could I do to auto-load the hard disk at either login or startup?

Thanks,

Chris

---

### Post by d3ngar on 2009-07-26
By the way, I tried writing the external hard disk into /etc/fstab, but because the device /dev/sdb is not existent it doesn't load...

---

