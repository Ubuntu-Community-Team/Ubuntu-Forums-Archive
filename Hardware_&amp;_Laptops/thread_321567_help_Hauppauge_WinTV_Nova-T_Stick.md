---
title: "help Hauppauge WinTV Nova-T Stick"
date: 2006-12-19
forum: Hardware &amp; Laptops
---

### Post by vb2006 on 2006-12-19
I'm a Linux newbie so I have no idea what I'm doing. I've tried using the instructions found on this forum and by using Google and no matter what I try, I can't get the Hauppauge WinTV Nova-T Stick recognised on my pc.

Can anyone point me to some instructions that I can follow from start to finish which don't jump around from website to website? What do I need to view digital TV? :KS 

 system specs:
kubuntu 6.10 - winxp home
AthlonXP 2600+
2g ram
512mb nvidia video card
 thanks

---

### Post by anaconda on 2006-12-19
You need to find this file: dvb-usb-dib0700-01.fw
(google might be of help)
and copy it to /lib/firmware  -folder

[http://rpm.pbone.net/index.php3/stat/4/idpl/3597773/com/dvb-firmware-usb-20061120-1plf2007.0.noarch.rpm.html](http://rpm.pbone.net/index.php3/stat/4/idpl/3597773/com/dvb-firmware-usb-20061120-1plf2007.0.noarch.rpm.html)

And then you need to check that you have all these modules loaded to your kernel:
[http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB0700.29](http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB0700.29)

[http://www.osdir.com/ml/linux-dvb@linuxtv.org/msg20750.html](http://www.osdir.com/ml/linux-dvb@linuxtv.org/msg20750.html)

And if/when you get it working just install kaffeine, and you can start watching TV.. 

Hope I helped you a bit. 

PS. the easiest thing is to buy hardware that you know works well with linux. eg. my
hauppauge wintv nova-t USB2 (digibox)

---

### Post by frafu on 2006-12-22
@vb2006

Did you succeed in getting it to work?

---

### Post by Sha01in on 2007-03-01
I have grabbed the firmware and put it in my root firmware folder and the two generic folders. Reconnected the stick and nothing... kaffeine says that no dvb device found, so it will hide dvb options. Doing lsmod, i don't have any of the listed modules loaded, and I can't find any of the modules listed in ubuntu site. So I'm at a loss at what to do. I don't really fancy compiling the kernel as I'm a complete newbie. Any ideas?

---

### Post by frafu on 2007-03-01
Hello, 

You don't have to recompile the kernel. I got it working on edgy without recompiling a new kernel; the tuner was then available in kaffeine and I could do a channel search which only found one channel once. (I think there is very bad reception where I am located. 

Unfortunately, I only remember vaguely what I did. However here are a few hints that might help you: 
- There is the possibility to load kernel modules dynamically ( /etc/modules ?)
- I remember also using (probably among others) the information on this page:
[http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB0700.29](http://www.linuxtv.org/wiki/index.php/DVB_USB#DiBcom_USB2.0_DVB-T_devices_.28based_on_the_DiB0700.29)

I hope somebody else will be able to give you more precise help. In fact, my main answer is that it should be possible to make it work with recompiling the kernel. (I succeeded in doing it.) 

Have a nice day.

---

### Post by panch0 on 2007-03-02
Does it show up in lshal?

lshal | grep WinTV

If the device is recognized and a device node is created in /dev, KPlayer will show it in the list of devices.

---

### Post by wieman01 on 2007-08-24
Try this...

[http://ubuntuforums.org/showthread.php?t=533528]("http://ubuntuforums.org/showthread.php?t=533528")

My WinTV Nova-T Stick works fine in Feisty.

---

