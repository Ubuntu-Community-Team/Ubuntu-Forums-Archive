---
title: "3D acceleration in  nVidia GeForce Go 6100"
date: 2010-06-09
forum: Hardware
---

### Post by olegsmall on 2010-06-09
hello, 
please help to configure video card nVidia GeForce Go 6100 on Ubuntu 10.04. Installed nvidia-current driver, it works well, but with a nasty bug: 
to operate 3D acceleration after booting the system need to run NVIDIA X Server Settings, go to the tab X Server Display Configuration change any parameter (eg refresh rate), and click Apply. After that, everything works well.*And so it should be done after each boot. 
I read this [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) and this [https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto), but nothing helped


Ubuntu x64 installed on my notebook MSI MegaBook M670
I spent a few tests and noticed the following:
Immediately after boot **lsmod** shows me 
[B]Module----------Size----------Used by
nvidia----------10799466----------[COLOR="Red"]40[/COLOR] [/B]
and **xdpyinfo**
[B]screen #0:
  dimensions:    1280x800 pixels ([COLOR="red"]332x212[/COLOR] millimeters)
  resolution:    98x96 dots per inch[/B]

After I  change any parameter on tab X Server Display Configuration in   NVIDIA X Server Settings lsmod shows me 
[B]Module----------Size----------Used by
nvidia----------10799466----------[COLOR="red"]44[/COLOR] [/B]
and **xdpyinfo**
[B]screen #0:
  dimensions:    1280x800 pixels ([COLOR="red"]331x211[/COLOR] millimeters)
  resolution:    98x96 dots per inch[/B]

---

### Post by olegsmall on 2010-06-15
please help

---

