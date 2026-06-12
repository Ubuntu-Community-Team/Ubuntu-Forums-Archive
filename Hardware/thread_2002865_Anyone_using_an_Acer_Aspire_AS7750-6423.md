---
title: "Anyone using an Acer Aspire AS7750-6423?"
date: 2012-06-13
forum: Hardware
---

### Post by blasmat on 2012-06-13
Has anyone installed Ubuntu 12.04 (or any other version for that matter) on the Acer Aspire AS7750-6423? I am going to be purchasing a new laptop within the next few weeks, and I found [this model]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=2159767&CatId=4965") at a much lower price than any other laptop with comparable specs. All the reviews I've seen of the machine itself have been positive, but I haven't been able to find anything in the forums or anywhere else about running any linux distro on it. 

As far as I can tell, the hardware seems like it should be perfectly compatible, but I'm no expert. Any input?

---

### Post by N0oki3 on 2012-06-13
Hello there and welcome to the forums. If I quote the laptop from the link you have gave 
> 
Graphics Specifications
Graphics Description	**Integrated Graphics**
GPU/VPU	**Intel HD Graphics 3000**


This graphic card does not support unity 3D and you will have problems with all applications that requires openGL.


I would recommend you [this notebook](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1933206&CatId=4935)

It does cost a bit more but it is long way better and also I never had problem with dell (well RIP after 7 years of usage...but than I have made a mistake buying HP)

This laptop has discrete graphic card or if we could say "real graphic card" you also won't have problem by running unity 3D nor any application that requires openGL

But than again if you don't need / want 3D support than acer or any other cheaper notebook is awesome for you

ps: in [this topic](http://ubuntuforums.org/showthread.php?t=1543006) you can see all the notebooks that people have and have shared their expiriance with them. There are also old notebooks so check date of the post.

---

### Post by blasmat on 2012-06-13
Thanks for the reply!

I am getting rather confused about which graphics cards to look for - I have seen multiple posts on various forums indicating that Ubuntu 12.04 does *not* play well at all with NVIDIA or AMD Radeon cards, but [this thread]("http://askubuntu.com/questions/140032/is-there-a-driver-for-the-intel-hd-3000-graphics-processor-on-ubuntu-11-10-or-12") indicates that Intel HD 3000 graphics work perfectly out of the box...

---

### Post by N0oki3 on 2012-06-13
More or less all of the notebooks have hybrid graphic cards (**intergrated** for desktop and low performance applications for power saving and such and **discrete**for high performance and using direct X, openGL and stuff...)

At the moment linux is not quite compatible as windows so there is quite problematic. Mostly users with locked bios - to set default graphic card to use on boot and radeon HD 5xxxM series have problem. As they cannot use DGPU (the better one) -> result of no openGL and unity 3D.

Also under intel HD 3000 it depends which 1 you get. For instance Intel HD 3000 -> Vesa SandyBridges = does not support unity 3D

in this [topic](http://ubuntuforums.org/showthread.php?t=1930450) you can see that alot of people with hybrid graphic cards doesn't have problem while some of us have :)

---

