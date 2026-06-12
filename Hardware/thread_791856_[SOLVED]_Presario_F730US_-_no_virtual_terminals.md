---
title: "[SOLVED] Presario F730US - no virtual terminals"
date: 2008-05-12
forum: Hardware
---

### Post by mykrob on 2008-05-12
Hey-

Just got a new Compaq Presario F730US. 

[http://www.shopping.hp.com/webapp/shopping/store_access.do?template_type=product_detail&product_code=GR967UA%23ABA&jumpid=oc_R1002_USENC-001_Compaq%20Presario%20F730US%20Notebook%20PC&lang=en&cc=us](http://www.shopping.hp.com/webapp/shopping/store_access.do?template_type=product_detail&product_code=GR967UA%23ABA&jumpid=oc_R1002_USENC-001_Compaq%20Presario%20F730US%20Notebook%20PC&lang=en&cc=us)

It has nvidia graphics onboard, i have it cranked up to 128MB, and have added 1GB of RAM, making it 1.5GB.

Anyway, if i press Control+Alt+F1, i cannot see any virtual terminals. I assume that may be because i have no resolutions defined in my xorg file. Also, sometimes if the laptop is left sitting, the screen blanks, and it takes an act of God to bring it back up. How do i remedy this issue? I would like to stop the blanking, as well as make the virtual terminals visible. I think i may have stopped the blanking temporarily by issuing the command "xset -dpms", but how do i make this permanent?


Thanks,
-myk

---

### Post by mykrob on 2008-05-12
SOLVED

Manually installing the nvidia driver 100.14.23 solves the problem. Found a thread at the nvnews forum, the problem is with the nvidia driver.

---

