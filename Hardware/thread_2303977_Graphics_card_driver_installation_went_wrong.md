---
title: "Graphics card driver installation went wrong"
date: 2015-11-23
forum: Hardware
---

### Post by Namal23 on 2015-11-23
Hello, 

I just tried to manuely install newest driver for my GTX660. I downloaded the drivers from nvidia site, disabled the lightdm and run the script. I did it several times before. But then during the installation I got a message that DKMS could not be build and that the binary package for the driver could not be found. The installation has failed and I couldn't run xfce again. If I restart my pc it's now either the console if I am lucky or just a blank screen with blinking underline in the top left corner. 

I don't know what to do now and don't want to mess it even further. Please help.

Edit: Ok, I just looked at the make.log file and it says that it needs gcc 4.8.2, but the system is using 4.9.3 and that is why it cannot be installed, wtf??

Ok guys. I know now what is going on. 352.63 were bugged and but nvidia site didn't offer any newer drivers than that. I found in another forum people had same problem and that there are now 358.16 drivers that fix that installation problem.

---

### Post by Yellow Pasque on 2015-11-23
> I downloaded the drivers from nvidia site, disabled the lightdm and run the script.

That's not a good idea. Use the PPA: [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

Anyway, if this thread is solved, please mark it solved.

---

