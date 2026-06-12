---
title: "To those of you installing on netbooks"
date: 2009-06-26
forum: Installation &amp; Upgrades
---

### Post by ktstowell on 2009-06-26
Hello all,

I'm rather new on these forums and in the Unix/Linux world as well, but I have been given some awesome feedback by the nice community here so i thought I'd pay it forward.

I saw a few threads by users trying to install Ubuntu on their netbooks. Popular searches would have you believe this is a long and drawn out process*, but I found it to be the opposite. Here's why:

1. Upon unpacking your netbook, keep the shipped version of XP on there (acer aspire one) and DL the netbook distro of ubuntu from the main site ubuntu.com.

2. Use partion magick ( or if you are/have the know how to put your own version of a windows os on it and will be formatting/making your own partitions anyways: make a separate partition for ubuntu) to make a new partition dedicated for ubuntu w/o incurring any data loss.

3. Via alcohol 120%/Ultra ISO/ Power ISO (whatever you mount your ISO's with) mount your DL'd distro and select the install within Windows option. However, when asked the install location, choose your dedicated partition. This will almost override intalling within windows and will cause you to choose from a boot menu to load ubuntu ( instead of a desktop icon in windows).

4. Even though you are installing via a virtual drive, when ubuntu reboots to finish the install, it doesn't interfere. In fact, ubuntu set-up will become a boot option (to be later replaced by just "ubuntu"). Finish the install and voila your done.

As stated in the asterik comment below, this really only applies with a dual boot operation. If you wish to have ubuntu as the sole OS on your netbook, you will need to install from a flash drive, usb cd drive, or get a notebook HDD enclosure and gut your netbook's HD and hook it up to your desktop and install it from there ( not as fun).

The only issue w/ Ubuntu you will have is the WLAN drivers, which is easily remedied with NDISwrapper and NDISGTAK wich will allow ubuntu to utilize your windows drivers to kick your WLAN adapter into action.

This is technically my first guide so feel free to pick it apart or offer some advice. I'm just proud to have pulled off a quad-boot of XP, Vista, MS 2K8 and Ubuntu all on this lil' guy.


Thanks guys.

Ktstowell






*I suppose this may be true if ubuntu is the ONLY OS you wish to have on your netbook, if so, this guide is kinda moot

---

