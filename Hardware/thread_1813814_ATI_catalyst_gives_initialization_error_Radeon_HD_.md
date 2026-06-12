---
title: "ATI catalyst gives initialization error Radeon HD 6770M"
date: 2011-07-28
forum: Hardware
---

### Post by Penguin360 on 2011-07-28
Laptop: HP Pavilion dv6
Graphic card: Radeon HD 6770M
Two VGA controllers: ATI and Intel 

I can use Unity if I use the default Ubuntu graphic driver, but the CPU gets very hot and the fan keeps running. So I decided to install the proprietary driver.

First, I installed ATI proprietary graphics driver by using Additional Driver, after the installation and reboot, I was told the my hardware does not meet the requirement for Unity. And when I try to run ATI Catalyst control center, I get an Initialization Error. So I deactivated the proprietary driver.

Then, I followed the instructions on [http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Natty_Installation_Guide#Installing_Proprietary_Drivers_a.k.a._Catalyst.2Ffglrx) to manually install ATI proprietary driver. The installation went well, until the last step when I ran this command:
```
sudo aticonfig --initial -f
```
It tells me that no adapter was detected.
Then when I try to run ATI control center, it gives me the same Initialization Error as above.

Can anyone help me to get it fixed?

Thanks,

---

### Post by Penguin360 on 2011-07-28
Anyone please?

---

### Post by khelben1979 on 2011-07-29
I think that you should install Ubuntu Natty (stable) instead and make sure to use the newest kernel available. I would guess that your current issue relates to your kernel (not sure) but I think it could be worth a try.

Radeon 6770M is a pretty recent graphics chipset, so anything which would be less modern would cause less trouble for you.

---

### Post by Penguin360 on 2011-07-29
I am using Ubuntu Natty, and I even tried to upgrade to 11.10 Alpha 2 to see if it will fix the problem by itself, but the upgrade didn't go well. I guess I will have to wait until 11.10 Beta is out hoping it will fix the issue.

---

### Post by weezilla on 2011-07-31
I just ran into the same exact problem when installing ati-driver-installer-11-7-x86.x86_64 from the ati website (dv7t, radeon 6770M). 

I am using LTS 10.04.3. My main problem is that I cannot go above 1280x1024 resolution, even though my screen supports 1920x1080. I was never prompted to install a restricted driver, oddly. 

Does anyone know how I can get 1920x1080 resolution?

KhelBen, I know I can't use 11.04. I'm not sure about dv6t laptops, but I doubt they can use it either due to a core-temperature problem/speed problem on these kinds of hp laptops.

I cannot see the bottom of my graphs from a software I'm running :(

---

### Post by weezilla on 2011-08-01
If you are only concerned about your open-source driver working, read this.

This page noted that I need to update my kernel for open source drivers to work (to 6.2.38). I am still trying to get catalyst to work, but at least for now my 1080p works !!
[http://wiki.cchtml.com/index.php/Hardware#Not_Yet_Supported_or_Unofficially_Supported](http://wiki.cchtml.com/index.php/Hardware#Not_Yet_Supported_or_Unofficially_Supported)

sudo apt-cache linux-image-2.6.38

I ran sudo apt-get install linux-image-2.6.38.10-generic to update my kernel. Restart after this and you can select from your new kernel, or your old one on grub.

I was worried that my DV7t might experience the same heating problems as running 11.04, but I've run powertop and it looks like I'm not encountering this problem (200 wakes per second is normal?)

---

### Post by .... on 2011-08-01
You both have hybrid graphics and fglrx doesn't support that unless both GPU's are AMD/ATI. Use the open-source drivers from xorg-edgers and vgaswitcheroo.

---

### Post by xkang on 2011-08-19
Have anyone tried the new AMD Catalyst 11.8 Linux Driver that were released on aug 17? If someone has, does it support HD 6770?

---

### Post by .... on 2011-08-19
> **xkang said:**
> Have anyone tried the new AMD Catalyst 11.8 Linux Driver that were released on aug 17? If someone has, does it support HD 6770?
Yes, it supports the 6770, but it still doesn't support intel/ati hybrid graphics....

---

### Post by xkang on 2011-08-19
If i install it i will still get the "initialization error" ?

---

### Post by bruise on 2011-08-23
suffering the same problem

but just like to know how this problem be solved under windows.

here's the guy who did re-package intel/amd driver and solved this problem under win7:
[http://leshcat.blogspot.com/](http://leshcat.blogspot.com/)

---

