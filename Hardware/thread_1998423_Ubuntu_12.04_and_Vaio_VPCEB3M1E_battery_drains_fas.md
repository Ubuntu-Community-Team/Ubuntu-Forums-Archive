---
title: "Ubuntu 12.04 and Vaio VPCEB3M1E battery drains fast"
date: 2012-06-06
forum: Hardware
---

### Post by Segnale007 on 2012-06-06
Hello folks,

I have got installed Ubuntu 12.04 on my Sony Vaio VPCEB3M1E a couple of weeks ago, and I realized the battery drains in really no time. Like, with the brightness turned all the way down and just surfing the web and doing some xchat the battery will last at the most one hour, while with brightness at 50% the battery wont even last 40 minutes, not to mention if I watch some flash videos on youtube or worst case I use the webcam. 

On windows 7 though with the same settings, again brightness all the way down I can get two hours and half of usage, also doing some webcam session as well as watching some videos on youtube. If I increase the brightness of a 40/50% up the battery will last a little less than two hours, but still way longer than Ubuntu.

I am using stock kernel 3.2.0-24-generic 64 bit, and that's the output of **/proc/acpi/battery/BAT0/info**

```

present:                 yes
design capacity:         42180 mWh
last full capacity:      31730 mWh
battery technology:      non-rechargeable
design voltage:          109630 mV
design capacity warning: 1000 mWh
design capacity low:     1 mWh
cycle count:		  0
capacity granularity 1:  100 mWh
capacity granularity 2:  100 mWh
model number:            
serial number:           
battery type:            LiOn
OEM info:                Sony Corp.

```

Any help would be much appreciated.

Thanks

---

### Post by Segnale007 on 2012-06-07
Any idea ??

---

### Post by Redblade20XX on 2012-06-07
Try looking up cpu scaling. Most likely your cpu is set to the maximum clock rate when it's busy and when it's idle causing huge power loss. I would also advise you to look into laptop-mode tools ( a set of scripts that implement cpu scaling, hard drive spin down, network power management) but I don't know how it works with Ubuntu. Here is something you should read through : [https://wiki.archlinux.org/index.php/Laptop_Mode_Tools](https://wiki.archlinux.org/index.php/Laptop_Mode_Tools)

-Red

---

### Post by Segnale007 on 2012-06-08
> **Redblade20XX said:**
> Try looking up cpu scaling. Most likely your cpu is set to the maximum clock rate when it's busy and when it's idle causing huge power loss. I would also advise you to look into laptop-mode tools ( a set of scripts that implement cpu scaling, hard drive spin down, network power management) but I don't know how it works with Ubuntu. Here is something you should read through : [https://wiki.archlinux.org/index.php/Laptop_Mode_Tools](https://wiki.archlinux.org/index.php/Laptop_Mode_Tools)

-Red

Thanks for the helpful suggestions. I have been away from linux for quite long time now and I am trying to get back on track :)

Anyways, I installed the laptopt-mode-tools and I spent a bunch of hours configuring it.. However somethings must be wrong with it, I think..

According to the developer FAQ, if laptop_mode tool is working properly the **/proc/sys/vm/laptop_mode** value should be a number greater than 0, but I don't get anything greater than 0.

I have also set the value vm.laptop_mode = 1 to /etc/sysctl.conf but neither this helped.

However, according to **/etc/init.d/laptop-mode** it seems that its working just fine (please correct me if I am wrong).

Here's the **/etc/init.d/laptop.mode**  [output]("http://pastebin.com/W1enDYJH").


One more thing. How do I adjust the cpu scaling in order to set the cpu to a lower frequency when the laptop is running on BATT?
I have seen through the laptop_mode man that this can be done with laptop_mode, but this feature is only supported from kernel 2.6.X and I am running on 3.2.0-24.

Thanks

---

### Post by infotechlogic on 2013-02-27
For sony vaio users:
To make the battery life longer

Use the power saving function.
Your computer has two distinct power saving modes which apply to the computer not in use: Sleep mode and Hibernate mode.

Place the computer into Sleep mode as often as possible and into Hibernate mode when you do not use it for a while, and turn it off when you do not intend to use for an extended period of time.
 
Adjust the LCD brightness of your computer screen. Decrease the volume of the speakers or headphones. Disconnect any peripheral devices not in use. 

However , To extend the battery lifetime
Your computer has the battery care function. By setting the maximum charge level lower with the function, you can slow battery degradation and extend the battery lifetime. 
Effects on battery capacity at the different maximum charge levels
Vertical axis: battery capacity, horizontal axis: duration of use

Thanks,
InfotechLogic.com

---

