---
title: "How to Get my AMD Graphics to work for games on xubuntu 13.10"
date: 2013-12-01
forum: Hardware
---

### Post by samgabbay on 2013-12-01
[COLOR=#333333][FONT=UbuntuRegular]How do i get my AMD Graphics to work for games to be less laggy on xubuntu 13.10.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]For GTA SA And COD 4[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Graphics: AMD Mobility Radeon HD 4225/4250 Driver 
Chipset: amd m880g chipset 
PC/Specs:[http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c02618765](http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&docname=c02618765)[/FONT][/COLOR]

---

### Post by mikewhatever on 2013-12-01
AMD/ATI no longer provides a Linux driver for the HD 4xxx searies, nothing you can do.

---

### Post by samgabbay on 2013-12-01
Alright But before i close this thread i have 2 questions.

Someone has suggested me to follow this from askubuntu: [http://askubuntu.com/questions/368893/radeon-7770-breaks-when-upgrading-from-13-04-to-13-10](http://askubuntu.com/questions/368893/radeon-7770-breaks-when-upgrading-from-13-04-to-13-10)
And then told me to use this guide:[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

should i or its simply not worth trying.

my second question is, if i shouldnt try both those methods, Should i dual boot windows for my games?

Thank you for your reply in advance

---

### Post by Yellow Pasque on 2013-12-02
> **mikewhatever said:**
> AMD/ATI no longer provides a Linux driver for the HD 4xxx searies, nothing you can do.

They dropped support on the closed-source driver, but the open-source driver is very actively developed...

---

### Post by Yellow Pasque on 2013-12-02
> **samgabbay said:**
> Someone has suggested me to follow this from askubuntu: [http://askubuntu.com/questions/368893/radeon-7770-breaks-when-upgrading-from-13-04-to-13-10](http://askubuntu.com/questions/368893/radeon-7770-breaks-when-upgrading-from-13-04-to-13-10)
And then told me to use this guide:[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Installing_Catalyst_Manually_.28from_AMD.2FATI.27s_site.29_BETA.2FEXPERIMENTAL)

Those are poor suggestions as they aren't relevant to your older GPU.

> Should i dual boot windows for my games?
If the open-source driver's 3D performance is not up to your liking, then that may be be the best solution.

To get the best performance out of open source driver in Saucy, use this PPA: [https://launchpad.net/~oibaf/+archive/graphics-drivers](https://launchpad.net/~oibaf/+archive/graphics-drivers)
I would also suggest the "radeon.dpm=1" trick to reduce power consumption: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

The last option is to install an older version of Ubuntu (i.e. 12.04.1) that supports the proprietary fglrx/Catalyst Legacy driver. I personally wouldn't recommend it, but some people who don't mind running older versions of Ubuntu would prefer it.

---

