---
title: "toshiba l510 wireless"
date: 2010-04-23
forum: Hardware
---

### Post by Andrew Golightly on 2010-04-23
Hi there,

I was looking at buying the Toshiba L510 ([specs]("http://www.dse.com.au/cgi-bin/dse.storefront/4bd188c101367f50273fc0a87e0106b4/Product/View/XC6462")). I took in Karmic Koala and booted off it. Wireless didn't work...

I found this comment..
```

This is on the Ubuntu forums, but I wanted to keep a reference here, as so I wouldn't forget.
The current release of Ubuntu (Karmic) does NOT have the latest kernel which includes the required drivers for the wireless card on this laptop. The wifi card this laptop has is as described in by lspci below.


03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8192 (rev 01)



At the time of writing, the development version (Ubuntu lucid) ships with the 2.6.32 kernel which HAS the required module but NOT the required FIRMWARE (I'll get to that later).

So, either install this kernel manually, or update to lucid using synaptic or update-manager -d, or do-release-upgrade -d.

Once you have done that, the network manager will list the wifi card as wlan0, but wifi operations will not be permitted (For example, the Network Manager will display "disconnected" under the wireless networks menu, as the firmware cannot be found, and you will not be able to do anything with it.

To install the firmware, do as follows. (You will need to apt-get git-core if you haven't already done so)


cd /tmp
git clone git://git.kernel.org/pub/scm/linux/kernel/git/gregkh/firmware.git
sudo cp -av firmware/RTL8192E /lib/firmware/



Reboot your system. You should now have wireless! 
```

I couldn't find this on the forums here... and just wondering if Toshiba is not the best route for Ubuntu?? I've pretty much always been able to run Ubuntu on other models no problem :)

---

### Post by jbiggs12 on 2010-04-23
Have you tried applying that configuration yet? If so, how far can you get? Does it show up in ifconfig/iwconfig?

---

### Post by Andrew Golightly on 2010-04-23
no I haven't tried that because I haven't actually bought that laptop. It was just one I was interested in.. good model, specs and price. I brought the 9.10 CD in and booted off it to test.

But I'm hesitating buying a machine if I have to do too many post install configurations. I'd rather not deviate from the main updates and what not...

I don't fully understand the impact of manually copying in firmware.

---

### Post by Andrew Golightly on 2010-04-24
So who can educate me a bit on the kernel of linux??

I understand that it includes firmware (software that communicates directly with a piece of hardware like the wireless card), that other pieces of software can then use communicate with to perform operations like sending an audio stream to the soundcard.

What is a module then?

And this kernel in linux is common to all linux OS's right... it's more the flavour of the look and feel.. and package management that make it a particular distro like Ubuntu??

thanks

---

### Post by edfoxx36 on 2010-04-30
would that solve the problem here [http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510](http://ubuntuforums.org/showthread.php?t=1466920&highlight=toshiba+l510)

---

### Post by vipulsawant on 2010-05-02
Hi,

To enable wireless on toshiba Satellite L500/L510, run "lspci" command to find out the network controller.

On L510, lspci shows:
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8172 (rev 10)

For Realtek 8172 or 8192 controller, download the "RTL8192SE" driver files and follow the steps mentioned at the link -

[http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10](http://www.linwik.com/wiki/using+the+realtek+8172+and+8192se+wireless+controller+with+ubuntu+9.10)

These steps worked correctly for me :)

---

### Post by edfoxx36 on 2010-05-05
Thanks, Any idea if that will work for the RTL8191SE instead of the "92SE ?

---

