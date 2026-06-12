---
title: "Touchpad not fully working"
date: 2017-03-01
forum: Hardware
---

### Post by elle5125 on 2017-03-01
I am new here, so my apologies if this is in the wrong place.

Installed Ubuntu 16.04 lts yesterday alongside windows 10 on my laptop (Asus F556UA-AB54) 

The touchpad works as a pointing device but two finger scrolling doesn't work. Under system settings touchpad isn't an option, it just seems to recognize it as a mouse. It would be great to have multi-gesture features, but not necessary. 

There's not any additional proprietary drivers available when I use the additional drivers tool that are applicable to mouse/touchpad. 

xinput returns

&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (
&#9116;   &#8627; FTE1001:00 0B05:0101                    	id=11	[slave  pointer  (2)]

I'm not particularly familiar w/ ubuntu or terminal commands, but I can take instructions fairly well. 

Is the hardware just not compatible? 

I've done some searches on google and there seems to be a trend with asus laptops having touchpad issues but there were a lot of conflicting methods. 

Any help is appreciated on where to go from here.

Thanks.

---

### Post by redmcg2 on 2017-04-17
[COLOR=#111111][FONT=Ubuntu]The driver for your Touchpad (FTE1001) was only added to the kernel in version 4.10.

[/FONT][/COLOR][COLOR=#111111][FONT=Ubuntu]Ubuntu 16.04 currently uses Kernel v4.8 (or v4.4). It will receive v4.10 in four months.
[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]In the meantime - you can:[/FONT][/COLOR]

[LIST]
[*]Install Ubuntu 17.04 (which uses Kernel v4.10); or
[*]Follow the instructions here: [https://github.com/vlasenko/hid-asus-dkms](https://github.com/vlasenko/hid-asus-dkms)
[/LIST]
[COLOR=#111111][FONT=Ubuntu]Following the instructions at the link above will install a DKMS driver. A DKMS driver is basically a driver that wasn't built with the rest of the Kernel. However - it is the same driver that is used in Kernel v4.10.[/FONT][/COLOR]

---

### Post by redmcg2 on 2017-04-17
Apologies - it looks like Ubuntu have back-ported this driver to their Kernel v4.8. So as long as you are running Kernel v4.8.0-34 (or later) - you shouldn't need to do anything.


You can install Kernel v4.8 by running:
sudo apt-get install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04


See [https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus](https://wiki.ubuntu.com/Kernel/LTSEnablementStack#Ubuntu_16.04_LTS_-_Xenial_Xerus) for further details.

---

