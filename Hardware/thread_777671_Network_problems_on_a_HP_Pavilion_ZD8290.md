---
title: "Network problems on a HP Pavilion ZD8290"
date: 2008-05-01
forum: Hardware
---

### Post by roggerooster on 2008-05-01
Hi,

I just recently installed Ubuntu 8.10 on machine mentioned above, and looks fine but the network card doesn´t seem to work.
For example when I type "ifconfig" all looks fine, but still it doesn´t broadcast anything.  
I figured out that the chipset is a broadcom, but still it looks like ubuntu already installed it. So now I am clueless what to do, any ideas?

---

### Post by Ayuthia on 2008-05-01
Ubuntu most likely has not installed the missing firmware for it because it is proprietary.  Can you post your lspci -nn so that we can see what options you have?  Not all the Broadcom chipsets are currently working with the b43 driver so you might have to use NDISwrapper.

---

