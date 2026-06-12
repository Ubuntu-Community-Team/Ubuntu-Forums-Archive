---
title: "Ubuntu 13.04 and Sapphire Radeon HD7750 low profile graphics card support"
date: 2013-08-17
forum: Hardware
---

### Post by pebuilder on 2013-08-17
I have a Dell XPS 435mt PC that dual boots Ubuntu 13.04 and Fedora 19.  I have all always used the drivers direct from Ubuntu and Fedora and never installed proprietary drivers.  The default ones have always done the job for me.

The Radeon HD 4850 card is over heating > 80C on idle and looks like it is about to die...I have had this for a number of years.

The case is a bit cramped so I had to find a new graphics card that would fit and give me about the same performance as the HD 4850.

I found a Sapphire HD7750 low profile which would fit perfectly,  normal sized graphics cards would just not fit.  I checked Fedora 19 support and it seems all is good for support of the HD7750...but Ubuntu 13.04 seems to be an issue.

I noticed on the RadeonDriver Community page that [COLOR=#333333][FONT=UbuntuMono]Radeon HD 7000/"Southern Islands" series are supported with no 3D acceleration.
[/FONT][/COLOR]
I have both Unity and KDE desktops, I mainly use the KDE desktop for day to day use.  Unity is only used on the system administrator account.

I guess my question is will the HD7750 not work at all under Ubuntu 13.04 or will it work with limited capability?

Are there any special tweaks I need to do to get the HD7750 working with Ubuntu 13.04 without resorting to proprietary drivers?

Do I need to run Ubuntu in a degraded graphics mode until full support is available?  If so what do I need to do!

I would really appreciate assistance / constructive advice please on how to get the HD7750 working with Ubuntu 13.04.  As I mentioned there does not seem to be a problem with Fedora 19, so it must somehow be workable.

I hope there is someone who can assist me please?

Thanks
Peter

---

### Post by Yellow Pasque on 2013-08-17
You need glamor support (that's why Fedora works). There's a nice PPA to make it easy: [https://launchpad.net/~oibaf/+archive/graphics-drivers/](https://launchpad.net/~oibaf/+archive/graphics-drivers/)

If you use kernel 3.11, you can also use dpm: [https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later](https://help.ubuntu.com/community/RadeonDriver#Kernel_3.11.x_.28Ubuntu_13.10.2BAC8-Saucy.29_and_Later)

---

### Post by JDorfler on 2013-08-17
Before you start adding more and more PPAs and other softwares, make sure your card's thermal paste and thermal pads are in good working order.  Everyone seems to want to blame drivers and software and they haven't squared away their hardware.

---

### Post by pebuilder on 2013-08-18
The existing HD4850 is on its last legs that is why I am replacing it.  The difficulty I have is finding a suitable card that will fit in the case and not go backwards in terms of performance.

I have always kept my Ubuntu and Fedora fairly pure and not added PPAs etc.

I know Fedora will work, what do I need to do to get Ubuntu 13.04 working with the new HD7750 card.  Do I need to disable some graphics aspect until Ubuntu has "glamor support".

Could you please let me know?

---

### Post by JDorfler on 2013-08-18
You shouldn't have to do anything special except make sure you use the fglrx-updates instead of the fglrx drivers.

---

### Post by pebuilder on 2013-08-18
Thanks for your response, so if I do "sudo apt-get install fglrx-updates" will I have full functionality as per Fedora?

Is this something I should do now (i.e while the HD4850 is installed) and then it is there and ready for the HD7750 install?  Or should I wait until I have installed the HD7750?

This fglrx-updates package, is this part of the Ubuntu repository and will be kept up to date by Ubuntu developers or is it proprietary and only maintained by AMD?

---

### Post by JDorfler on 2013-08-18
You can do that now. There shouldn't be any issues.

---

### Post by pebuilder on 2013-08-18
Cheers thanks for your help, I will post back once I have installed the new HD7750 as others may benefit from this experience

---

### Post by Yellow Pasque on 2013-08-18
> **JDorfler said:**
> You can do that now. There shouldn't be any issues.

There will be issues since fglrx doesn't support the 4850 in Raring...

---

### Post by JDorfler on 2013-08-18
> **Temüjin said:**
> There will be issues since fglrx doesn't support the 4850 in Raring...

Are you sure?  I've never had a problem.  Last I checked the 4000 series was still being included in the Catalyst driver updates.  He should just be able to install the drivers, then swap cards.  I have yet to see Ubuntu not reconfigure on the fly even if the entire OS hard drive has been removed and installed in another PC.

---

