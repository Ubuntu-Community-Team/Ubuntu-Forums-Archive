---
title: "Broadcom wireless driver problems"
date: 2008-11-20
forum: Hardware
---

### Post by posterberg on 2008-11-20
Hi,

I'd like to know if more people experience problems with the proprietary wireless Broadcomm  STA wireless driver.

I used the ndiswrapper driver, without any problems at all, up until the second half of Hardy Heron. I don't remember when but I got suggested to switch to the prop. driver after one of the system updates in Hardy.

Then I started to not be able to see certain networks that I used to be able to see.

I just assumed that there might have been a collision in the upgrade and also assumed that the problems would be resolved when I did a clean Intrepid install.

This was unfortunately not the case, the same networks are still invisible to me. Networks that always showed up in the list with the ndiswrapper driver.

One of the particular networks that I can't see is provided by a 3CRWER100-75 OfficeConnect 3com wireless router. It is a WPA2 network, if that has anything to do with it. I am not sure if it has, I am quite certain that I have been able to connect to other WPA2 networks.

It is also not a problem with connecting to the network, the problem is that I don't even see it in the list of available networks, no matter how many times I try to update the list.

So... Has anyone experienced the same problems with this driver?

Thanks,
Peter

---

### Post by Yezinki on 2008-11-20
Works great  for me...........??

---

### Post by posterberg on 2009-01-02
I think the problem was the following, the driver stopped allowing channels 12 and 13 when I switched driver.

This solved the problem in my other laptop, can't wait to get my hand on the broadcom laptop now and see if this helps on that one as well:

[http://ubuntuforums.org/showthread.php?p=6477829#post6477829](http://ubuntuforums.org/showthread.php?p=6477829#post6477829)

---

