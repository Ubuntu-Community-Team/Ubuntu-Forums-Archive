---
title: "Dell D600 CRT/LCD switching"
date: 2007-07-20
forum: Hardware &amp; Laptops
---

### Post by tbourgault on 2007-07-20
OK Im brand spanking new to Linux and Ubuntu, how do I get my Latitude D600 to swtich from CRT to LCD ( the laptop screen to a monitor)  I appreciate the help.  Please write this for a new person...Im using the latest version 

thanks:)

---

### Post by w4ett on 2007-07-20
Usually it's a function key toggle F7, F8 or something like that.  Not sure on your particular model.

---

### Post by tbourgault on 2007-07-20
Ok my bad I wasnt clear....It switches with the F8 key but the video does not display, on earlier versions there was a driver tweak...is there one for the new version....and how do i do it.  I appreciate any input...thanks gang...I might get used to this OS

---

### Post by tbourgault on 2007-07-20
anyone have an idea?

---

### Post by w4ett on 2007-07-20
What need to be done is to modify your xorg.conf for 2 monitors.  I've never done it myself, but here is a posting....a bit old, but the same concepts still apply:

[http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display](http://www.wahlau.org/ubuntu_hoary_thinkpad_t43_and_xorg_dual_head_display)

Creating a custom configuration for your xorg.conf is definately a learning experience, but has to be done to achieve custom configurations.

Just a thought, try booting the live cd with you external monitor, and save that configuration to a flash drive. That at least will give you a starting point with which to tinker.  :)

---

