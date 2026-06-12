---
title: "NVIDIA 96 Display Problem"
date: 2009-05-04
forum: Hardware
---

### Post by Rosemachinegun on 2009-05-04
Hello people of Ubuntuland,

Today I installed Ubuntu 9.04 onto my Dell Inspiron 2650 with GeForce 2 Go graphics card. I tried activating the Nvidia legacy driver 96 through the hardware drivers menu, but when I reboot the machine I get a bizarre display problem. The right half of the screen is completely black and the desktop is completely squeezed into the remaining space on the left. I can easily undo it by removing the drivers but I would like to get the driver working. Any advice? 

Thanks for reading!

---

### Post by Claus7 on 2009-05-06
Hello and welcome,

the bad thing is that you have an old graphics card and jaunty is not so fond of old graphics cards. Now, you can install the driver from intel's web site and see what you get with that. That's the first thing I would advice you. If things do not work from there as well then either I would try 71 version of the driver or I would downgrade. Have in mind that you might have to edit the xorg.conf file manually. Because I see that this is your first post, do you understand how these things can be done, so as to make the best decision? Unfortunately, it is not so easy, if you are a new user, to do such modifications.

edit:have a look here:
[http://www.nvidia.com/object/IO_32667.html](http://www.nvidia.com/object/IO_32667.html)

Regards!

---

