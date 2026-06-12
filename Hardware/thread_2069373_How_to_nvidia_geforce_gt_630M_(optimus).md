---
title: "How to: nvidia geforce gt 630M (optimus)"
date: 2012-10-10
forum: Hardware
---

### Post by doomsword2001 on 2012-10-10
I recently had problems installing drivers for my Nvidia 630M and i thought i should post the solution for others. I had random system freezes. Please note i can't guarantee it will work for you, but i know it worked for me.

1) Install bumblebee
sudo add-apt-repository ppa:bumblebee/stable
 sudo apt-get update
sudo apt-get install bumblebee bumblebee-nvidia

When installed bumblebee my nvidia wasn't shown in hardware drivers on ubuntu 12.04 
and i had system freezes. Then i installed the new kernel. 3.3.6

2) 
sudo add-apt-repository ppa:upubuntu-com/kernel
sudo apt-get update
sudo apt-get install linux-kernel-64  (thats for 64 bit of course)
need to restart after installing. type uname -r to check the version if you want.

After installing the kernel 3.3.6 i can see the nvidia drivers in hardware drivers (jockey)
This did stop ubuntu from freezing.

Thats all i got it working for me and thought some one may had same problem.
I am not sure if i post it on the right place but i just wanted to help. 
Cheers.
):P

---

