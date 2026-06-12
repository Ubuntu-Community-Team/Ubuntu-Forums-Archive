---
title: "Monitor Refresh rates"
date: 2004-11-21
forum: Hardware &amp; Laptops
---

### Post by ajulius on 2004-11-21
Hello.  My monitor, a Hitachi Smartscan 753 is detected and works fine however it is not enabled for the higher refresh rates by default.

I am also using the nvidia glx driver and dont know if that also is a factor or not as well.  

Any suggestions on how to fix this?

---

### Post by tfwo on 2004-11-21
Try commenting out HorizSync and VertRefresh fields in your XF86Config file. Nowadays, these values are retreived quite well by the X Server, but Ubuntu  sometimes puts incorrect numbers in the config file.

---

