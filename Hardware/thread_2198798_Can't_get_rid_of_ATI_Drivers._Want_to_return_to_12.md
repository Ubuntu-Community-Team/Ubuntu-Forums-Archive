---
title: "Can't get rid of ATI Drivers. Want to return to 12.04 shipped drivers."
date: 2014-01-10
forum: Hardware
---

### Post by Noble Bell on 2014-01-10
I am using Ubuntu 12.04 LTS on my Toshiba laptop. I have an ATI Radeon 3100 video card. I found some driver last night on a website that said it was for ubuntu and I installed it. After I installed it, it informed me that it did not work properly and Unity was operating in 2d mode. I went in and tried to remove it the best that I could but form some reason I cannot get rid of it and get back to the drivers that came with the 12.04 release. Can someone guide me in getting back to the originally-shipped 12.04 drivers so that I don't have to do a complete re-install of Ubuntu and loose me stuff?

Thanks in advance for your time.

---

### Post by QIII on 2014-01-10
Hello!

Could you provide a link to the instructions you followed so we can assess what has been done to do the installation?

---

### Post by Mark Phelps on 2014-01-10
Typically, the following manual commands will properly uninstall -fglrx:

  > sudo apt-get remove --purge xorg-driver-fglrx fglrx*
  sudo apt-get install --reinstall libgl1-mesa-glx libgl1-mesa-dri xserver-xorg-core
  sudo dpkg-reconfigure xserver-xorg

---

### Post by Noble Bell on 2014-01-10
When I get home from work I will get the information that I used to install. When I was uninstalling went to the package manager and had it install anything that I seen with the name ati in it.

NB

---

### Post by Noble Bell on 2014-01-10
> **Mark Phelps said:**
> Typically, the following manual commands will properly uninstall -fglrx:

When I try this, I get the following...

> Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libgl1-mesa-glx : Depends: libglapi-mesa (= 8.0.4-0ubuntu0.7)
E: Unable to correct problems, you have held broken packages.

---

### Post by Noble Bell on 2014-01-12
I am marking this closed. I am sure the above answers would work fine but I have done something to my install. I broke down and re-installed and chalked this up as a learning experience on don't fix it if it is not broken. Thanks for the help.

---

