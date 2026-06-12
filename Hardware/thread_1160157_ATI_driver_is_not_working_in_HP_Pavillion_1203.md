---
title: "ATI driver is not working in HP Pavillion 1203"
date: 2009-05-15
forum: Hardware
---

### Post by sourabindu on 2009-05-15
Hi 
I installed the ati driver in my laptop.
Here is the code :

 akmod-fglrx
  fglrx-config-display enable
  reboot
  aticonfig --initial --input=/etc/X11/xorg.conf
 
when I try to open the ati catalyst driver from application->systemtools-> ati catalyst control center it is giving me the following message:
"There is a problem initializing catalyst control center linux edition.It could be caused by the following : No ATI graphics driver is installed or the ATI driver is not working properly.Please install the ati driver appropriate for your hardware or configure using aticonfig"
Then I consulted many post in the forum but I did not get the solution.
**Here is my compiz-check output :**
[http://pastebin.com/m619cd2b0](http://pastebin.com/m619cd2b0)
Here is my **glxinfo **output :
[http://pastebin.com/d1a183b42](http://pastebin.com/d1a183b42)
This is my lpsci o/p
[sourabindu@ranger ~]$ **lspci | grep VGA**
01:00.0 VGA compatible controller: ATI Technologies Inc Mobilitiy Radeon HD 3400 Series
[sourabindu@ranger ~]$ **rpm -qa | grep fglrx**
xorg-x11-drv-fglrx-9.3-2.fc10.i386
kmod-fglrx-2.6.27.5-117.fc10.i686.PAE-9.3-1.fc10.i686
akmod-fglrx-9.3-1.fc10.i686
xorg-x11-drv-fglrx-libs-9.3-2.fc10.i386kmod-fglrx-2.6.27.21-170.2.56.fc10.i686-9.3-1.fc10.i686

**cat /var/log/Xorg.0.log**
Partial log file is here:
[http://pastebin.com/d615a797b](http://pastebin.com/d615a797b)

This is the** xorg **file :
[http://pastebin.com/ddaaac43](http://pastebin.com/ddaaac43)

All this command I got from reading various posts in the forum.:confused:

---

