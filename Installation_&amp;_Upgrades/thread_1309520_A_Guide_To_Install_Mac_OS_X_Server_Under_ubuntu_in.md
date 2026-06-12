---
title: "A Guide To Install Mac OS X Server Under ubuntu in Vmware"
date: 2009-11-01
forum: Installation &amp; Upgrades
---

### Post by eeshan.mulye4 on 2009-11-01
This is a guide to install MAC OS X 10.5 server in Ubuntu under vmware

What you require
1.A 64 bit processer of sse 3 or sse 4
2.Enable VT in bios of host computer
3.VMware Player 3.0

This is a simple guide to install MAC OS X Server under vmware player

Make a new Virtual Mechine and select free bsd 64 bit as the guest os.Then use a briged network connection and take minimum 1GB of ram.Get the latest free bsd 64 bit tools from vmware upon first start then close the virtual mechine and go to the following directory

home/user/vmware/(the name you have given your virtual mechine)

edit the .vmx file with gedit and change the  (guestOS = "free bsd-64") to (guestOS = "darwin-64") then when you start vmware player it will show the guest os as mac os x server 10.5.

enjoy.but remember to enable VT in bios or it will not work

---

### Post by eeshan.mulye4 on 2009-11-01
If Any Problems While Installation Please Report.

---

