---
title: "Cannot get hdapsd to run"
date: 2008-04-19
forum: Hardware &amp; Laptops
---

### Post by Lord Xeb on 2008-04-19
O_o I spent almost 4-5 hours working on this: [APS]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.04_on_a_ThinkPad_T43") and when it is all said and done, I cannot activate the daemon that stops the my disc...

When I do try and activate it in terminal I get: 

```
open(protect_file): No such file or directory
```

It exists, but nothing happens




Does anyone have an idea of what is going on?

---

### Post by Axx83 on 2008-05-24
this is the same problem I get, i loaded the tp_smapi module AND the hdaps_ec module and they work fine, I installed hdaps packets via synaptic and when I run hdaps-gl IT WORKS it shows my comp moving when I move it and the movement is 100% correct, but when I run the only thing that is useful, the deamon to protect my hard drive it just says:

open(protect_file): No such file or directory

---

