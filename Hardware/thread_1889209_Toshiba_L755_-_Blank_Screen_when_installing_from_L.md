---
title: "Toshiba L755 - Blank Screen when installing from LiveUSB"
date: 2011-11-30
forum: Hardware
---

### Post by yathaid on 2011-11-30
Hey

So I am trying to install Ubuntu on my new Toshiba Satellite L755D.
THIS is the specific machine :
[http://www.amazon.com/dp/B005LF3RHW/ref=pe_175190_21431760_cs_sce_dp_1](http://www.amazon.com/dp/B005LF3RHW/ref=pe_175190_21431760_cs_sce_dp_1)

I have a blank screen when I tried booting from the liveUSB. I tried the noquiet nosplash nomodeset option when booting (by changing the cfg file unetbootin's bootloader uses) now it went upto bringing up a command line interface.

I tried running startx from the CLI and it gave an error that looked something like this:

(EE) Radeon needs .... KMS blah... (dont remember what was exactly here)
(EE) Screen(s) found but none with usable configuration.


If anyone knows a workaround, I would be really grateful. I really cannot function without a linux boot.

Update : with xforcevesa I could get into a GUI, but wireless isn't working. I am off to look for solutions to that, will post back if I find any. If someone already knows how to solve it, do let me know. Thanks!

Update 2 : [Solved] The latest **kubuntu** iso played nice with my wireless. The process was like this :

1. In the live USB boot option, make "... quiet splash"  into "noquiet nosplash radeon.modeset=0 xforcevesa" . This allows you to boot and install the OS.
2. To install the display driver -
You can do this from the Live USB itself by mounting the installed ext3/4 partition and chroot to that.
[sudo chroot /media/partition_name]

Follow the instructions in here to get the display driver working :
[http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Oneiric_Installation_Guide)
Sections 3.2, 3.3 & 3.4 are the relevant ones.

3. Reboot and you should be ready to go.

---

