---
title: "Prints are moved up"
date: 2006-08-18
forum: Hardware &amp; Laptops
---

### Post by i386DX on 2006-08-18
I'm trying to use a Oki B4100 on my linux system (ubuntu 6.06). Because there are no drivers for it, I use those for the B4200. (The printer does work with a HP-driver, but the quality isn't as good then)
My printer is recognized and it prints, but I have 2 problems.

I always have to push on the //-button on my printer before printing starts, don't know how to solve this.

Also (it's a bigger problem), al my prints are moved up. So at the bottom of the page the margin is much bigger and at the top it's very small (sometimes text is cut off). Because it's difficult to explain I will try to give an example:

what it should be:            
```

 ----
|A  |
|B  |  <-paper
|C  | 
 ----

```

what it is
```

 ----
|B  |
|C  |
|   |
 ----

```
Is it possible to solve this? Maybe by changing something in the *.ppd-file?
(this is the original ppd:
[http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz](http://belgium.oki.com/binaryData/6683/ok4200pcl.ppd.gz))

---

### Post by zxee on 2006-08-18
Have you tried Page Set Up and then Margins & Header/Footer?

---

