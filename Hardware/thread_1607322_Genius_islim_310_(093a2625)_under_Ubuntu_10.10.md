---
title: "Genius islim 310 (093a:2625) under Ubuntu 10.10"
date: 2010-10-27
forum: Hardware
---

### Post by ikalce on 2010-10-27
After 1 day compiling and patching kernels,searching the net etc. i finally SOLVE the problem with the islim 310:

Go to:  [http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/](http://kyleabaker.com/2010/07/12/microsoft-lifecam-vx-1000-linux-gspca-patch/)

Read how to install this patch and install it(This patch is not only for the LifeCam VX-1000). Reboot u PC after installing!

in this patch in module gspca_pac7302 is added VID(903a) PID(2625) and is used by gspca_main to work with that hw. U can chk this by typing:

#modinfo gspca_pac7302    , after installing patch :)

and u can see module working in lsmod 

GOOD LUCK !
i hope u will find this helpfull

---

### Post by manodigital on 2010-11-14
:):guitar:  [SIZE=4]hey, it has worked! I can not believe it, thank you very much for this contribution[/SIZE]

---

