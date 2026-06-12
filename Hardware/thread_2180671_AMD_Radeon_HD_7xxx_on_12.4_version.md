---
title: "AMD Radeon HD 7xxx on 12.4 version"
date: 2013-10-14
forum: Hardware
---

### Post by grzegorz-szylo on 2013-10-14
Hello 

I would like to know which driver is most appropriate for my Radeon graphics and some help to install it.
I have downloaded a RUN file with the driver (laptop Toshiba Satelite) from the amd website.
The problem is I don't know how to properly uninstall the drivers I have and then install the RUN package.
Last time I played with the graphics driver my graphic interface crashed and only tty would load and I could not even login to that as the login failed kept on poping up. 
Could you please help me with code to uninstall the current video drivers packs and to install the RUN package?
I am not sure if this is the best solution but maybe somebody has experience with those drivers and has got a better idea?
Other source/driver maybe.
Many thanks,

Greg

---

### Post by Yellow Pasque on 2013-10-14
> The problem is I don't know how to properly uninstall the drivers I have
What drivers are you talking about? The open-source radeon driver that comes with Ubuntu or something else you installed?
Removing: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Removing_Catalyst.2Ffglrx)
Install: [http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29](http://wiki.cchtml.com/index.php/Ubuntu_Precise_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29)

As far as the version to use, AMD's site is still recommending Catalyst 13.4, but you can also try 13.11 Beta if 13.4 gives you "unsupported hardware" watermark.

---

