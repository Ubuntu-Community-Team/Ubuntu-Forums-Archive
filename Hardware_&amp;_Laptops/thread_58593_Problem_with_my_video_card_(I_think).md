---
title: "Problem with my video card (I think)"
date: 2005-08-20
forum: Hardware &amp; Laptops
---

### Post by dueY on 2005-08-20
I just installed Ubuntu last night and everything went pretty smoothly.  Installed Ubuntu, booted into it, downloaded the new packages.  Then after all the packages were downloaded my screen just turns weird colors.  

I'm thinking this could be because the video card on this computer is on the PCIe, whereas every computer I had installed Ubuntu on before was AGP.  

I can access the command line by pressing ctrl+alt+f2.  I need some help with what to type for commands to change or select my video card from the command line.  

Here's a screen shot (taken by my cellphone) of what the messed up colors look like for reference:

[http://img367.imageshack.us/img367/4403/wtfubuntu3qj.jpg](http://img367.imageshack.us/img367/4403/wtfubuntu3qj.jpg)

If any other information is needed just ask.

---

### Post by yoshic on 2005-08-21
use this:
```
sudo dpkg-reconfigure xserver-xorg
``` 

and follow the instructions :smile:

---

### Post by dueY on 2005-08-21
Thanks for that command, I used it and tried a few combinations of the options.  I'm actually posting this from my Ubuntu install now, but I'm in VGA 4bit color with a disgustingly low resolution.  So I'm guessing it's an issue with my card/the nv driver.  Can anyone please tell me how to fix this before staring at this grainy screen causes my eyes to bleed?

---

### Post by coolclassic on 2005-08-21
Try installing the nvidia drivers full instructions are given here:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by dueY on 2005-08-21
[QUOTE=coolclassic]Try installing the nvidia drivers full instructions are given here:

[http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)[/QUOTE]

Thanks so much, I was looking for that guide but on ubuntu.com instead of ubuntuguide.  I installed the NVIDIA driver and reconfigured my xserver and now everything works and looks beautiful. Thanks for the help coolclassic and yoshic.

---

