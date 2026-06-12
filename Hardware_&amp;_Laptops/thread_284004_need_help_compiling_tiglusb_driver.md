---
title: "need help compiling tiglusb driver"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by blanny on 2006-10-25
Hi, I'm trying to get my Ti-89 titanium connected.  I'm running kernel 2.6.17-10 and I have all the headers installed.  I downloaded tidev-modules and tried to install using module-assistant, but for some reason it only builds the tipar driver.  I got the .tgz source and tried to compile from that, but I got a bunch of errors.  Can someone tell me what file I need to edit to get m-a to compile the right driver from the package?

I tried to edit the main Makefile and put

```
 TIMODULE = tiglusb 
```

but that didn't work.  I need some help.  I got my desktop all set the way i want and it bums me out to boot Windows.  I attached a picture of my setup, hehe.  Anyways, help would be greatly appreciated cuz I have a big test coming up. Thanks,

Blanny
[IMG]http://www.blanny.tv/Screenshot.png[/IMG]

---

