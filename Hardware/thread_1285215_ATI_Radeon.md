---
title: "ATI Radeon"
date: 2009-10-07
forum: Hardware
---

### Post by jumel on 2009-10-07
I have HP Compaq 6730s Notebook PC: Intel Core2 Duo Processor T5870, ATI Mobility Radeon HD 3430.
If I try  to activate driver in "Hardware Drivers", after reboot I don't have desktop anymore, just black screen. I reinstall Ubuntu 9.04 and I still didn't find the way to activate Desktop Effects. I downloaded driver from ATI web site (ati-driver-installer-9-9-x86.x86_64.run) but I am afraid I'll have same result-black screen. Does anybody know how to solve this problem? I tried to find some answers but it seems it is not suitable for my Graphic Card ( [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) , [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

Can anyone help please.
[]("http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue")

---

### Post by webcrawler03 on 2009-10-07
Did you downgrade XOrg 1.6? Its not compatable with Jaunty 9.04 unless you do. Try this link [http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue](http://tan-com.com/posts/technology/fix-ubuntu-904-ati-driver-issue)

Edit: Sorry just noticed that was your second link you posted also... let me look a little further into this.

---

### Post by doas777 on 2009-10-07
I always use the driver from ati when working with their stuff. i see a huge difference over the restricted everytime.

if the install does fail though, just hit cntrl + alt + F1, to go to a vtty, and login at the command line. then enter this, reboot and you should have basic graphis again:
```
sudo dpkg-reconfigure -p High xserver.xorg
```

---

### Post by markbuntu on 2009-10-07
The 3430, along with many other newer Radeon cards in the 3xxx and 4xxx series are not supported by the driver  installed from hardware manager but are by the latest from the ati site. If you have not enabled the harwdware manager driver, do not do so. If you have , remove it and download and install the latest driver from the ati site. 

Be sure to read the release notes and installer instructions. There is also links from the download page to many distribution specific installation instructions.

---

