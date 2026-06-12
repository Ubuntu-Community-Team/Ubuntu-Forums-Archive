---
title: "mounting 2 drives under the same mount point"
date: 2005-07-05
forum: Hardware &amp; Laptops
---

### Post by kubuntuuser on 2005-07-05
Does anyone know if it is possible to mount 2 physical drives under 1 mount point.

I have a laptop with the following config 

30 gig total 
------------------
ntfs  - 23gig windows
ext3 - 4gig /  
ext3 - 2gig /home
swp - 1gig /swap  

I am fast running out of space but really dont want to re partition and then reinstall. 

I would like to create a new partition from free space on my windows partition and have it mounted with the current "/" partition to give / more space. 

I performed a default install originally and use kubuntu.

Many thanks

---

### Post by Lunde on 2005-07-05
[QUOTE=kubuntuuser]Does anyone know if it is possible to mount 2 physical drives under 1 mount point.

I have a laptop with the following config 

30 gig total 
------------------
ntfs  - 23gig windows
ext3 - 4gig /  
ext3 - 2gig /home
swp - 1gig /swap  

I am fast running out of space but really dont want to re partition and then reinstall. 

I would like to create a new partition from free space on my windows partition and have it mounted with the current "/" partition to give / more space. 

I performed a default install originally and use kubuntu.

Many thanks[/QUOTE]
 if you want more space at / you can mount it as /usr and move the /usr/* content there. at my system that's about 1,7 gb

---

