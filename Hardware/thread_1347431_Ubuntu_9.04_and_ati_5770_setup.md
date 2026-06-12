---
title: "Ubuntu 9.04 and ati 5770 setup"
date: 2009-12-06
forum: Hardware
---

### Post by OLDUSER on 2009-12-06
well, after some installation problem i would like to share my experience 
some step to setup the ati 5770 driver on ubuntu 9.04
 
1. install ubuntu 9.04 and do all the system upgrade
 
2. don't install the driver ati (the ubuntu driver ati) but
 
3. download the driver from here 
 
[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)
 
4. install the driver but before read how to
 
see jpg and before command type sudo
 
5. after driver installation type in terminal
 
cd  /etc/X11
sudo aticonfig --initial

6. now and only now you can reboot [IMG]http://ubuntuforums.org/images/icons/icon4.gif[/IMG]
 
7. you are now able to see this
see jpg
 
8. video work good even at 1920x1080 resolution, full hd too
 
if someone know other ways to install this driver please post

---

