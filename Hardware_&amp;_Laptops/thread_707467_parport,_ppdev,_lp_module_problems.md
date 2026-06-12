---
title: "parport, ppdev, lp module problems"
date: 2008-02-25
forum: Hardware &amp; Laptops
---

### Post by friendoftux on 2008-02-25
Hello I am trying to write a device driver for the parallel port for a school project. I have followed the following tutorial to get me started [http://www.freesoftwaremagazine.com/...nux?page=0%2C8](http://www.freesoftwaremagazine.com/...nux?page=0%2C8)
I have had great success compiling and inserting the driver module and have looked at cat /proc/ioports and saw that it is indeed reserving the correct memory address to control the port. My problem is that when I remove the modules manually using
rmmod ppdev
rmmod lp
rmmod parport_pc
rmmod parport

The parport module is still somhow interfearing with my driver. I have tried blacklisting all those modules but somehow they still load at boot. finally out of desperation i deleted the actual parport module and now when i try and insert my new module i get a device busy error. To correct this i reinstalled Ubuntu. 

What is the correct way to make all of those modules not load at boot????????????

The reason I am trying this is because others that have followed the tutorial said this was the only way they could get the driver they created to work.

Thanks
:confused:

---

