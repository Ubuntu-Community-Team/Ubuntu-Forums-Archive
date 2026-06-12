---
title: "Asus N550JV Driver GT750M"
date: 2014-01-22
forum: Hardware
---

### Post by 20daniele10 on 2014-01-22
Hi all, 
I have the laptop ASUS N550JV, with Kubuntu 13.10 and I have some problems with the graphic card drivers.
First I had some problems (in additional drivers it said that the driver was activated but not in use) but I found that it was not a problem because it was how bumblebee works...


The problem is that I realized it late and after several trials and repository purges, I can not make as before, for example with:
```
glxgears
```
I get
```
Error: couldn't get an RGB, Double-buffered visual
```


while with 
```
optirun glxgears
```
I get this
```
[  736.649295] [ERROR]Cannot access secondary GPU - error: Could not load GPU driver
[  736.649325] [ERROR]Aborting because fallback start is disabled.
```


Could you help me?  ](*,)

---

