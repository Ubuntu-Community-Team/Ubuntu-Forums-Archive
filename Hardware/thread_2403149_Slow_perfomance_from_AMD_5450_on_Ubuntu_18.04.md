---
title: "Slow perfomance from AMD 5450 on Ubuntu 18.04"
date: 2018-10-08
forum: Hardware
---

### Post by spyros6 on 2018-10-08
Hello, I'm trying to figure out why the AMD 5450 is slow on Ubuntu 18.04.
First i thought of drivers, but after searching around it appears the latest drivers are included in the kernel. I also have an Intel i5 7400 with                                                                                                                                                                                Intel HD Graphics 630 and someone suggested to use that instead because it's more powerful but the UI is still laggy. 
The weird thing is that if If i type ```
lspci -nn | grep -E 'VGA|Display'
``` i see ```
Mobility Radeon HD 5430
``` instead of 5450. Is it possible my installation doesn't recognize the GPU correctly and hence the poor performance ?

Also note that i drive 2 monitors with 1080p resolution with my graphics card.

---

