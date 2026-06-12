---
title: "Has anyone installed ipw2200 with vanilla kernel?"
date: 2005-11-25
forum: Hardware &amp; Laptops
---

### Post by Sunnz on 2005-11-25
I now have ipw2200 installed on Breezy with the default Ubuntu kernel and it works great, thanks to this [guide]("http://www.nickselby.com/articles/technology/?a=1807").

However I have compiled and installed the latest kernel from kernel.org with some custom settins of my own... and I can't seem to follow the guide and install the driver... so I am wondering if it can be done at all?

I don't get the meaning of linux-headers... what are they? What do they do?

Thanks.

---

### Post by bonzodog on 2005-11-25
The linux headers are the kernel headers. They provide the header files for referencing during module builds. You will need the ones for your kernel, although if you have installed a fresh kernel from kernel.org, they should be with it, as the kernel would need the headers itself, for building any modules that were specified during config.

---

