---
title: "Can't decrease fan speed in bios..."
date: 2014-09-30
forum: Hardware
---

### Post by john205 on 2014-09-30
I have a fan in my system that can do 4000 RPM, and can get it down to 50% (~2200) It's connected to the SYSFAN1 header, Which I read has no PWM capabilities.
The problem is, That's quite loud. How can I decrease it further?
Motherboard: MSI A55M-E33(original BIOS version)

---

### Post by Mark Phelps on 2014-09-30
You can try out tlp:

>  sudo add-apt-repository ppa:linrunner/tlp
sudo apt-get update
sudo apt-get install tlp tlp-rdw

    
> sudo tlp start

---

