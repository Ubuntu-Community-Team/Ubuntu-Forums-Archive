---
title: "Updating NVIDIA drivers with no success."
date: 2010-07-25
forum: Hardware
---

### Post by LucasG on 2010-07-25
Well, I've tried installing the latest NVIDIA release on my Ubuntu laptop with no success. I stopped gmd and ran, but during installation I receive the following errors:

```
> The distribution-provided pre-install script failed!  Continue installation 
   anyway? (Answer: Yes)
```

```
ERROR: Unable to load the kernel module 'nvidia.ko'.  This happens most
       frequently when this kernel module was built against the wrong or
       improperly configured kernel sources, with a version of gcc that differs
       from the one used to build the target kernel, or if a driver such as
       rivafb/nvidiafb is present and prevents the NVIDIA kernel module from
       obtaining ownership of the NVIDIA graphics device(s), or NVIDIA GPU
       installed in this system is not supported by this NVIDIA Linux graphics
       driver release.
```

Any ideas?

---

### Post by johnnyis42 on 2010-07-25
I found a guide that got me passed this:


[http://yopensource.com/en/news/ubuntu-latest-news/1794-howto-install-nvidia-drivers-manually-on-ubuntu-1004-lucid-lynx](http://yopensource.com/en/news/ubuntu-latest-news/1794-howto-install-nvidia-drivers-manually-on-ubuntu-1004-lucid-lynx)

Unfortunately the new drivers didn't fix my woes, and I switched to my ATI onboard graphics which has fixed all my issues I was having with my 9600GT :s

---

