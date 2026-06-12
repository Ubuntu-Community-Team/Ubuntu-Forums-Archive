---
title: "Problem with making Intel/ATI Hybrid GPU work."
date: 2014-10-08
forum: Hardware
---

### Post by undeadleech on 2014-10-08
Hello ubuntuforum, 
I recently installed ubuntu because I thought it's the best choice for my intel/ati gpu setup in my Lenovo G500 Laptop. But my current problem is that I can not make this thing work. The first thing I have tried is installing the non-free ati driver fglrx but aticonfig is always telling me something about "there is no such device" or something like that. 
After searching the web I found out that this might mean, that I have a muxless setup and am unable to use fglrx. So I tried getting it work with the free drivers. 
First I was trying to use vgaswitcheroo but I think it's outdated on Ubuntu 14.04. The other thing was DIR_PRIME. It seemed to be working first but when starting cs:go to test my fps DIR_PRIME=1 or not didn't make any differences. So I started benchmarking. With some benchmarks I reached higher fps but a blackscreen with the amd gpu. 
The only benchmark that really worked for both was glmark2. But the results were surprising. With Intel I got an average score of 1606 and a score of 819.5 on ati. This results are very weird because even if the ati gpu would be worse (it is not) there was zero difference in cs:go starting it with "steam steam://rungameid/730". And now I am pretty much out of ideas. 
The Intel GPU is the "Intel HD Graphics 4000" and the ati GPU is the "AMD HD 8750M".

Now my question: Does anyone have other ideas to test for me? I really don't want my main gpu to get wasted.

Ty for all answers!

Greetings UndeadLeech

---

### Post by ajgreeny on 2014-10-08
I've never needed ity as Intel on-board graphics is more than powerful enough for what I do but I think you need to have a good read up on the bumblebee project
[http://askubuntu.com/questions/tagged/bumblebee](http://askubuntu.com/questions/tagged/bumblebee)
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)

---

### Post by undeadleech on 2014-10-08
"Bumblebee aims to provide support for [NVIDIA Optimus]("http://www.nvidia.com/object/optimus_technology.html") laptops for GNU/Linux distributions."
That's what I can get out of the wiki. And that's everything what I've thought so far? Same with nvidia-prime.
Or am I wrong? I can see no way to get this work with Intel/ATI.

---

### Post by ajgreeny on 2014-10-08
Whoops!

Sorry but I think you are correct.  I just noticed hybrid graphics and immediately thought "bumblebee".

---

### Post by undeadleech on 2014-10-08
No problem. I gathered some informations and it seems like there might  not really be a good solution for this yet. Or doesn anyone has better  informations? Does anyone know about the next Versions of ubuntu? Will  this problem get fixed somewhere in the future?

---

