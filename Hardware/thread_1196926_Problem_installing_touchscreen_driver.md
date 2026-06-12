---
title: "Problem installing touchscreen driver"
date: 2009-06-25
forum: Hardware
---

### Post by NCLI on 2009-06-25
I'm trying to install the linux driver for my eGalax touchscreen for the eeePC 1000HE, but as you can see, not all is going a planned:
```
(*) Linux driver installer for TouchKit controller 

(I) Check user permission: root, you are the supervisor.
(I) Begin to setup the TouchKit driver.
cp: cannot stat `TouchKit.tar.gz': No such file or directory
tar: TouchKit.tar.gz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors
(I) Extract TouchKit driver archive to .
(I) Create TouchKit utility shortcut in /usr/bin.
chmod: cannot access `/TouchKit': No such file or directory
(I) Create TKCal tool shortcut in /usr/bin.
chmod: cannot access `/TKCal/TKCal': No such file or directory
(I) Check X window version: 6.9.0 ~ 7.2.0
(I) Copy X module: x69/egalax_drv.so to /usr/lib/xorg/modules/input.
cp: cannot stat `/Module/x69/egalax_drv.so': No such file or directory
```
The archive it's complaining about, "TouchKit.tar.gz," is in the same directory as the installer (setup.sh)!

---

### Post by syrex314 on 2009-06-25
This may be a typo in your posting... it's complaining about "TouchKit.tar.gz" and you've said there is a "TouchSmart.tar.gz" in the directory.

---

### Post by NCLI on 2009-06-25
Fixed.

---

### Post by NCLI on 2009-06-26
Bump.

---

### Post by eats7 on 2009-11-03
same problem, same computer.

---

### Post by eats7 on 2009-11-03
got it working..


1.) download this driver
[http://home.eeti.com.tw/web20/drivers/t](http://home.eeti.com.tw/web20/drivers/t) … k26.tar.gz
its in beta but it works, didnt try the other one

2.)once its done downloading open up the tar, and copy the whole folder to /home/your-username-here/

3.) once that is done, open up terminal, and type this: 

cd /home/your-username-here/eGalaxTouch32

after that type :

sudo sh setup.sh

enter your password, then select 3. USB

4.) once thats all done, restart your eee, then open terminal up again and type:

eGalaxTouch

and then configure it to how you want. for some reasong trying to touch the buttons in eGalaxTouch didnt work, but everywhere else they do. oddly terminal kept saying aborted every few minutes with eGalaxTouch opened.  i just kept opening it and finished up.

---

