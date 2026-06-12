---
title: "setup external monitor on dell 1420"
date: 2008-03-26
forum: Hardware &amp; Laptops
---

### Post by udutronik on 2008-03-26
Hello,

I am trying to set an external monitor on my dell 1420 inspiron laptop

The monitor is a dell SE198WFP

My graphic card is nVidia Corporation GeForce 8400M GS (restricted driver installed OK)

Here is what i tried so far:

1) go to system/administration/screens and graphics. No results. Even after adding my monitor from the .inf driver provided by dell

2) of course, googled around, with no luck


Can anyone help me in this process? 

Thanks!

---

### Post by Sam Lars on 2008-03-26
Can you run
```
sudo nvidia-settings
```
and configure two screens in that program?

---

### Post by udutronik on 2008-03-26
SOLVED

That was as simple as that!

Thanks Sam!

---

