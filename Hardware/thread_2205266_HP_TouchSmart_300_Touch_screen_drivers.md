---
title: "HP TouchSmart 300 Touch screen drivers"
date: 2014-02-12
forum: Hardware
---

### Post by mmiscool on 2014-02-12
Hello. I am running the latest version of linux mint on my machine. And yes I have tested with the latest version of ubuntu 64.

I have tried the information here
[http://ubuntuforums.org/showthread.php?t=1645591&highlight=touchsmart+300](http://ubuntuforums.org/showthread.php?t=1645591&highlight=touchsmart+300)
here
[https://www.ebower.com/docs/ubuntu-touchsmart/index.html#AEN83](https://www.ebower.com/docs/ubuntu-touchsmart/index.html#AEN83)
and attempted what was here
[http://www.fusionnetwork.us/index.php/articles/linux-tutorials/hp-touchsmart-300-touchscreen-linux-nextwindow-working/](http://www.fusionnetwork.us/index.php/articles/linux-tutorials/hp-touchsmart-300-touchscreen-linux-nextwindow-working/) 
to no avail.

Has any one gotten this to work?


The last link there had some instructions I attempted to follow.
I opened the deb and copied the src directory out of it and attempted to run a make on it.

The result was as follows:


make -C /lib/modules/3.11.0-12-generic/build M=/home/user/Downloads/nwfermi-0.6.5.0 modules
make[1]: Entering directory `/usr/src/linux-headers-3.11.0-12-generic'
  CC [M]  /home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.o
/home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.c: In function &#8216;fermi_open&#8217;:
/home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.c:268:3: error: implicit declaration of function &#8216;err&#8217; [-Werror=implicit-function-declaration]
   err ("%s - error, can't find device for minor %d",
   ^
/home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.c: In function &#8216;fermi_bulk_read_complete&#8217;:
/home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.c:503:3: error: implicit declaration of function &#8216;dbg&#8217; [-Werror=implicit-function-declaration]
   dbg("URB Status: %d\n", urb->status);
   ^
cc1: some warnings being treated as errors
make[2]: *** [/home/user/Downloads/nwfermi-0.6.5.0/nw-fermi.o] Error 1
make[1]: *** [_module_/home/user/Downloads/nwfermi-0.6.5.0] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.11.0-12-generic'
make: *** [all] Error 2

---

