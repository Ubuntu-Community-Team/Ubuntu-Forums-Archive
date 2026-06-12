---
title: "problem enabling nvidia-glx-new"
date: 2008-03-01
forum: Hardware &amp; Laptops
---

### Post by alberto0 on 2008-03-01
Hi 
I am trying to enable my restricted drivers but I am getting the error:
"The software source for the package nvidia-glx-new is not enabled."

From repository, I have enabled restricted, universe and mltiverse, but if I search for nvidia-glx-new, there is nothing available.

I also tried:
$ sudo apt-get install nvidia-glx-new
Reading package lists... Done
Building dependency tree      
Reading state information... Done
Package nvidia-glx-new is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx-new has no installation candidate

but I am still not able to enable the video card
Any clue?

Thanks in advance

---

### Post by alberto0 on 2008-03-01
I found the problem the system needed an update after adding the repository, after that repeat the enabling operation from the restricted drivers

---

