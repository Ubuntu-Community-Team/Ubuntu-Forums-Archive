---
title: "No WiFi on HP Mini after installing 9.10"
date: 2009-10-31
forum: Installation &amp; Upgrades
---

### Post by mbr78 on 2009-10-31
I just did a clean install of Ubuntu 9.10 Netbook Remix on my HP-Mini 110 and now wireless doesn't work. Wireless used to work in 9.04 but it doesn't in 9.10. I don't think it is detetcting the internal wireless adapter (it is turned on). How do I get wireless to work in 9.10?

---

### Post by PhilMize on 2009-11-02
I'm having the same problem. 

> 
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.



---

### Post by PhilMize on 2009-11-02
LOL! Ok, I feel sort of dumb here but. I did some poking around and turns out if you just go to the system settings section and click the hardware drivers icon. Make sure you have an ethernet connection, and enable the Broadcom Wireless STA driver. Your wifi should click on. It didnt say too, but I restarted. My wifi is working perfectly now.:popcorn:

---

### Post by anthony47 on 2009-11-04
I have the same problem with my mini & 9.10, however when I go to hardware drivers it looks around and finally says 'no proprietary drivers are in use on this system.' When I click on help it just sends me into a loop that eventually ends up at the same place: the system does not recognize any driver.
If anyone has any advice I would appreciate it!

---

### Post by PhilMize on 2009-11-04
did you enable the restricted extras under software sources? do that then update and see if something comes up.

---

### Post by mbr78 on 2009-11-11
I got wireless working on HP Mini. I searched the USB stick I used to install 9.10 for "bcmwl-kernel-source". I then right clicked the package and reinstalled it. Then after a reboot my wireless worked.

---

