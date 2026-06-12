---
title: "ubuntu 11.04 + BCM 4313 WIFI + lenovo b570"
date: 2011-10-01
forum: Hardware
---

### Post by s_jubeh on 2011-10-01
Hello, 

I have a new laptop lenovo B750 I Have checked the wireless card and it is 4313 14e4:4727.

I have checked the STA hypred driver and it seems that, this card is supported, I have downloaded the source code the fix patch and I have installed it. [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Note that, I am familiar with the installation procedure because I had the same problem with my other laptop which is dell 1545 where I was able to install the driver successfully.

The installation was successful, butI was not able to see any network and from ubuntu GUI I used to get the message device is not ready.

Also I make update and I have re-installed the BCM kernel from the repository

sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

and I have still the same Issue. 

What should I do next and what are the things I need to check. I have seen many post regarding this problem and most of them was a repetition of the content of  [http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)

How can I diagnose my problem, please help 

Regards

---

### Post by sedawk on 2011-10-05
After trying Fedora 15 and upgrading to Ubuntu 11.10 I found the solution
in the forum of a german online shop (for Ubuntu 11.04):

There is a module acer_wmi that conflicts with the wlan stuff
on the B570.

After doing a

```

rmmod wl
rmmod acer_wmi
modprobe wl

```

I can finally see wlan networks (Ubuntu, Broadcom device activated
via jockey-gtk).

---

### Post by sedawk on 2011-10-05
Some update:

After blacklisting acer_wmi in /etc/modprobe.d/blacklist.conf,
disabling the proprietary driver (with jockey-gtk) and a 
cold reboot I can see wireless networks. The
kernel has loaded the (new) brcm* modules (Ubuntu 11.10).

---

### Post by ssurell on 2011-12-31
With a system administrator account, I don't have permission to rmmod or save blacklist.conf (solved below).

Update:
For newbies like myself, probably should give a little prep.  Goto "Dash Home" icon on main toolbar and type "terminal" into the search bar and open "terminal" application.

type "sudo -s" to enter root (without quotes) and enter administrator password.

then type "rmmod acer_wmi && echo "blacklist acer_wmi" >> /etc/modprobe.d/blacklist.conf" to remove and blacklist the irrelevant acer controller.

reboot

Found walkthrough here:
[http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/](http://fakkelbrigade.eu/chris/blog/2010/12/wireless-not-working-in-ubuntu-on-the-lenovo-ideapad-s12/)

My Lenovo B570 with Broadcom wireless adapter is working great!

---

