---
title: "Problems with Wifi and Nvidia Drivers"
date: 2011-06-29
forum: Hardware
---

### Post by reddevilcorp on 2011-06-29
Hi All,

I recently bought a Lenovo Z570 Ideapad with 2nd gen i5 Sandy Bridge Processor and Nvidia 520M Optimus Graphics Card.


I installed Ubuntu Studio 11.04 recently, before that I was using Ubuntu 10.04. I noticed that after I installed Ubuntu 11.04, the wireless has stopped working. It showed Disabled by Hardware Switch.After some googling around, I was able to enable the wifi and use but now it has again become disabled. So it has become a cubersome task of running all the commands again to make it work..



In my model both the Bluetooth and WiFi are enabled by fn+F5 combination. There is also a hardware slider switch. Even if I was able to enable Wifi I am unable to start bluetooth. Since most of the fn combination keys don't work including the Brightness switch.


I checked out the sys.log and found when I pressed fn+F5 combination, the wireless driver was enabled as well as disabled in one go, along with some messages referring to the key combination not recognised.


I also read that Linux DOES NOT support NVIDIA optimus technology as of now, so we have to check out alternatives like debumblebee project. I tried running debumblee script but it cant find nvidia -dkms and nvidia-xconfig packages.
 

I tried everything out and now Finally I am posting here. Although there are similar issues reported. But this is all in one problem info I am facing in my Idepad Z570.


Kindly help me out..

:)

---

### Post by rickwright on 2011-07-09
You can find the solution to the WiFi and bluetooth here:
[http://ubuntuforums.org/showthread.php?p=11031061](http://ubuntuforums.org/showthread.php?p=11031061)

SO far I have not came up with a solution for the graphycs card.

Enjoy!

---

### Post by reddevilcorp on 2011-08-09
Thanks Rick I was able to fix the Wireless and Bluetooth issues after running the commands. However, the brightness applet does'nt seem to work, I guess its reported in other threads too, however I cant find any solutions to that either... Anyways Thanks.. :)

---

