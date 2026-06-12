---
title: "Installed 9.04 and There are no nVidia Drivers After Install..."
date: 2009-04-26
forum: Hardware
---

### Post by ajr901 on 2009-04-26
Today i installed 9.04 on my HP dv6707us and i installed "along with windows" giving ubuntu a 55 GB partition on vistas C:/ drive. Everything seems to work fine after the install, however,...there are no nvidia drivers installed. Its really wierd because when i tested it with the "live cd" option there WAS nVidia drivers under System > Administration > Hardware Drivers!!! If i go into display setting there is only the option for 600 X 800. My screen is a 1200 X 800 screen. So how come after i install there are no drivers located in there for me to activate/deactivate. My nVidia card is an nVidia 7100m / geforce 650.

---

### Post by grahamu on 2009-05-03
I have also found this.  The nvidia drivers were presented when using the live cd then once properly installed they are not there.

How can we get the nvidia drivers?

---

### Post by X1R1 on 2009-05-03
Have you installed the ubuntu restrcited extras? those drivers are propietary and cant be installed automatically.

Go in synaptic, then type "ubuntu restricted" and install the ubuntu restricted extras...then reboot and ubuntu will start checking for the drivers of your video card telling you there is some hardware drivers to install.

or if that doesnt work...manually download here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

hope it works
regards

---

