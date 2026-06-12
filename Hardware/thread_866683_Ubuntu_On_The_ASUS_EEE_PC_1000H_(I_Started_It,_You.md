---
title: "Ubuntu On The ASUS EEE PC 1000H (I Started It, You Finish It)"
date: 2008-07-22
forum: Hardware
---

### Post by banshie on 2008-07-22
Hello, a week ago I purchased the ASUS EEE PC 1000H, it comes with WindowsXP Home SP3 pre installed.
(on a side note the Atom does not have the x86_64 instruction set :( )
After a week with it I have 3D graphics, compiz, Ethernet but no wireless.

So first things first, I used the following guide to install Ubuntu from USB ( [here]("http://www.teamteabag.com/2008/03/07/install-ubuntu-804-hardy-heron-from-usb/") )

Out of the box, this doesn't include 3D graphics, Ethernet or Wireless.

To get Ethernet I followed this guide ( [here]("http://kunin.wordpress.com/2008/07/05/asus-eee-pc-901/") )

To get the Ethernet loading at boot, I created a init.d script, I loosely followed this guide ( [here]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#A_possible_problem_with_fglrx.ko_conflicts") )

After the kernel upgrade the Intel GMA's kicked in, which leaves only Wireless, I have tryed both the Ralink driver and ndiswrapper, failing with both.

I am willing to supply any and all lshw/etc reports just ask.

Thanks

---

### Post by banshie on 2008-07-22
Not that its exactly relevant to this but [meebo]("http://www.meebo.com") seems to crash firefox

---

### Post by snowpine on 2008-07-22
Hi Banshie, as much as I love Ubuntuforums, you really should save yourself some time and check out forums.eeeuser.com... they have a great sub-forum about Ubuntu on the eee, plus a detailed wiki, and you can even download eeexubuntu, a customized xubuntu that works perfectly with the eee wireless!

---

### Post by banshie on 2008-07-22
Thanks, I guess wireless is hard at the moment with linux, still its not really an EEE issue, its a Ralink Ubuntu issue.

---

### Post by snowpine on 2008-07-22
> **banshie said:**
> Thanks, I guess wireless is hard at the moment with linux

I agree, getting my Linksys wireless USB working with my (non-eee) laptop was the hardest part of learning Ubuntu. But it was very satisfying when I finally figured it out!

The great thing about the Linux community is that there are thousands of others out there who had the same problem as me. It took me days to find the right solution, but once I found it, it took less than 15 minutes and has worked perfectly ever since. It is all about knowing where to find answers and figuring out which advice to trust. Good luck!

---

### Post by Yannick Le Saint kyncani on 2008-07-22
> **snowpine said:**
> Hi Banshie, as much as I love Ubuntuforums, you really should save yourself some time and check out forums.eeeuser.com... they have a great sub-forum about Ubuntu on the eee, plus a detailed wiki, and you can even download eeexubuntu, a customized xubuntu that works perfectly with the eee wireless!

+1 to eeeuser.com and +1 to their wiki too :)

---

### Post by banshie on 2008-07-22
Well if you guys can't help me out, of course I'll head there, but you guys are simply the best site when it comes to Ubuntu, any reports/outputs that I should just post? I can think of a few but I don't know whats relevant and whats not.

---

### Post by snowpine on 2008-07-22
> **banshie said:**
> Well if you guys can't help me out, of course I'll head there, but you guys are simply the best site when it comes to Ubuntu, any reports/outputs that I should just post? I can think of a few but I don't know whats relevant and whats not.

Just introduce yourself and tell them you're a noob and you're looking to get wireless set up in Ubuntu. I promise you it is a very common question and someone will know EXACTLY what to do. :)

---

### Post by banshie on 2008-07-22
I'm pretty sure only the 901 share my wlan card, it being a Ralink, that being said Ralink do provide a driver but even after compiling it successfully things just wont work.

---

### Post by snowpine on 2008-07-22
> **banshie said:**
> I'm pretty sure only the 901 share my wlan card, it being a Ralink, that being said Ralink do provide a driver but even after compiling it successfully things just wont work.

OK 5 minutes and google and I found this for you:
[http://forum.eeeuser.com/viewtopic.php?pid=320958](http://forum.eeeuser.com/viewtopic.php?pid=320958)
[http://forum.eeeuser.com/viewtopic.php?pid=312755](http://forum.eeeuser.com/viewtopic.php?pid=312755)

That should get you started. :)

---

### Post by banshie on 2008-07-22
Thanks, but I've read those forums to no avail ndiswrapper dosn't seem to be an option, I've tried the driver from the disc and from a few sites all giving me the "invalid driver" error

---

### Post by banshie on 2008-07-22
Even though it is titled EEE PC, as its a Wireless problem and about Ubuntu I still think you guys could solve the problem, from what I've seen I'm just not compiling the driver correctly other sites do say "sudo make, sudo make install" but this still doesn't get me wireless.

---

### Post by banshie on 2008-07-22
I've double checked the BIOS, everything enabled, why is default settings WLAN disabled?

---

### Post by him610 on 2008-07-22
> I've double checked the BIOS, everything enabled, why is default settings WLAN disabled?

Maybe, to conserve battery power?

Cheers.

---

### Post by banshie on 2008-07-22
Good idea, anyway I tryed again with making sure WLAN is turned on in the bios still no success with either ndiswrapper or the native Ralink driver.

---

### Post by stmiller on 2008-07-23
ralink has open sourced all of their drivers, so it should work fine. This project page is the center of development:

[http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)

---

### Post by banshie on 2008-07-23
I might be wrong but, they don't seem to support my RT2860.

---

### Post by redw0lf on 2008-07-30
i followed the steps listed in [http://ubuntu-eee.com/index.php5?title=Getting_the_network_drivers_working_on_the_901](http://ubuntu-eee.com/index.php5?title=Getting_the_network_drivers_working_on_the_901)
under the native driver section and it worked perfectly for my 1000H

> 1) Download driver from: [http://www.ralinktech.com.tw/data/drivers/2008_0708_RT2860_Linux_STA_v1.7.0.0.tar.bz2](http://www.ralinktech.com.tw/data/drivers/2008_0708_RT2860_Linux_STA_v1.7.0.0.tar.bz2)

2) Unzip and move to USB drive(if working with second computer). Move to EEE.

3) cd into 2008_0325_RT2860_Linux_STA_v1.7.0.0

4) execute "nano os/linux/config.mk" (without the speech marks)

5) find the lines which read

Support Wpa_Supplicant HAS_WPA_SUPPLICANT=n

Support Native WpaSupplicant for Network Maganger HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=n

and change them to look like

Support Wpa_Supplicant HAS_WPA_SUPPLICANT=y

Support Native WpaSupplicant for Network Maganger HAS_NATIVE_WPA_SUPPLICANT_SUPPORT=y

6) ctrl + o to save, then ctrl + x to exit

7) sudo make

8) sudo make install

9) sudo modprobe rt2860sta

10) restart eee pc and notice the network manager now has wireless :D

---

### Post by banshie on 2008-07-31
Thanks this looks promising, what doesn't is my eee pc going back to asus tomorrow :( poor thing stopped booting one morning, guessing its a mobo short..somehow

---

### Post by gvazqu1 on 2008-08-28
Ndiswrapper (with the inf file from Windows) works fine for my 1000H

---

