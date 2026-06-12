---
title: "Satellite Pro U500 - Switch between Graphic Cards"
date: 2010-09-14
forum: Hardware
---

### Post by jteddy on 2010-09-14
I am using a [Toshiba Satellite Pro U500 PSU9NA-00600N]("http://www.mytoshiba.com.au/products/notebooks/satellite/pro/u500/psu9na-00600n/specifications#details") and with my current setup of using the nvidia GPU the battery life is less than 2 hours.

I would like to setup Xorg so it uses the Intel Graphics Media Accelerator HM55 when on battery and the NVIDIA N11M-GE card when I have AC power.

I would appreciate any help in setting up Xorg to switch between these two graphic cards.

Thanks.

---

### Post by warfacegod on 2010-09-14
I don't *think* that would be possible without restarting the computer.

---

### Post by jteddy on 2010-09-14
I will start investigating the limitation then.

What would the solution be then?

What is the best way to boot into my desired card?  
How and is it possible to use Grub to boot into my desired card?  How is this achieved?

---

### Post by IcarusR on 2010-09-15
You can set up two xorg.conf files & set up a boot option to use each as in this thread. 
You will need to redo after a kernel update.

[http://ubuntuforums.org/showthread.php?t=923406]("http://ubuntuforums.org/showthread.php?t=923406")

---

