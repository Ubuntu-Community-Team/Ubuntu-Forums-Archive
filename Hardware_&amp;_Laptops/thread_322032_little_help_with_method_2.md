---
title: "little help with method 2"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by DaveL22 on 2006-12-19
Hey guys, i almost feel bad asking because it seems like video card issues are beat to death here but i am in the process of installing the ati 8.32.5 driver for my Radeon m300.  

I am doing method 2 from the ati wiki and i keep getting hung up on one part, i think the problem is that i dont understand the instructions. Here is the instructions
> 
Create .deb packages:

sudo ln -sf bash /bin/sh
bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
sudo ln -sf dash /bin/sh


and when i get to the second line of that i get this
> 
dave@dave-laptop:~$ bash ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
bash: ati-driver-installer-8.32.5-x86.x86_64.run: No such file or directory
I downloaded the driver to the desktop, do i need to change the location or something?

---

### Post by pay on 2006-12-19
```
bash Desktop/ati-driver-installer-8.32.5-x86.x86_64.run --buildpkg Ubuntu/edgy
```

---

### Post by DaveL22 on 2006-12-19
thanks, that worked perfect

---

