---
title: "Dell Vostro 1000 Laptop, UK"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by mjwhitfield on 2007-10-23
Hello all.

First, forgive me if I'm covering ground that's already been dealt with.  I appreciate that this laptop has already been discussed, however following the release of 7.10 and the big steps forward that have been taken with drivers and "out of the box" success, I'd just like to check what the status of this machine will be from a clean install of 7.10.

I've found a great post here > [http://ubuntuforums.org/showthread.php?t=553057]("http://ubuntuforums.org/showthread.php?t=553057") Which lists the graphics card (ATI Radeon Xpress 1150) and the wireless card (Dell 1390 Wireless Card).

Can anyone tell me if these will work from a fresh (7.10) install without much fiddling?  I've checked the laptop testing pages on the wiki, however they have only tested a 1500 model, and I'm not sure what the hardware differences will be.

Many thanks,
Matthew

---

### Post by Marcelo Fernández on 2007-10-23
I just installed Ubuntu 7.10 in this laptop. The ATI driver and the wireless card installs OK, only clicking in the Restricted Manager checkboxes, it was really easy. Desktop Effects didn't work, but because the ATI drivers doesn't do AIGLX (to make Compiz work, you have to install XGL).

Regards,
Marcelo

---

### Post by mjwhitfield on 2007-10-23
How do you install XGL? Is it a tricky process?

This guide here says it is not the same for 7.10 > [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

---

### Post by mate84 on 2007-10-28
I have a problem. After when I did the wireless connection, here is an other one with my ATI 1150. In the restricted drivers manager I get this information: fix broken packages first. And in the terminal:
mate@mate-laptop:~$ fglrxinfo
The program 'fglrxinfo' is currently not installed.  You can install it by typing:
sudo apt-get install xorg-driver-fglrx
bash: fglrxinfo: command not found
mate@mate-laptop:~$ sudo apt-get install xorg-driver-fglrx
[sudo] password for mate:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  xorg-driver-fglrx: Depends: libstdc++5 (>= 1:3.3.4-1) but it is not installable
E: Broken packages
mate@mate-laptop:~$
 
At the moment I have large icons.....
Can anybody help me?

---

