---
title: "HP Pavilion dv7"
date: 2012-06-19
forum: Hardware
---

### Post by ronald911 on 2012-06-19
Hi..

I installed the latest Ubuntu distro on my HP Pavilion DV7 Laptop. (Specs: 8GB RAM, 2.0 GHz Intel i7 and ATI 6770m GPU. 

Everything works fine, BUT, it feels like it has a resource problem, especially compared to Windows 7 and Windows 8? 

The CPU will max out and feel like it's heating up and the fan will then spin like crazy -that's on Idle!

It doesn't happen at all when running Windows - which is strange, as I thought Ubuntu is very light on resources.

Any suggestions or recommendations on a possible cause / solution?

But other than that everything works fine - Wireless, touchpad, battery meter etc etc etc.

Thanks in advance.

Ronald

---

### Post by typhoon_tip on 2012-06-19
With ATI you need to install FGLRX driver, otherwise fan will always run at max speed, indirectly heating up the CPU as well.

[http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide)

Refer to the above guide only "Manually install driver".

---

