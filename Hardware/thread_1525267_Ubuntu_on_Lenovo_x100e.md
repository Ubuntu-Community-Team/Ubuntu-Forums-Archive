---
title: "Ubuntu on Lenovo x100e"
date: 2010-07-06
forum: Hardware
---

### Post by STSC on 2010-07-06
I am trying to install ubuntu on 23 netbooks that were recently purchased by our university. The purpose of these laptops is to allow our custodial staff to put in for leave time now that the university has gone paperless. The problem I'm having with these computers is that whenever they come unplugged from the wall the mouse stops working. We have tried using external mice with them and the touchpad, both stop working after being unplugged and require a restart with it plugged into ac power to work. Does anyone have a solution to this problem?

Also I noticed we are getting very low wireless signal and disconnects in a room that is right next to a access point, is there a driver somewhere that could fix this?

Thank you.

---

### Post by mörgæs on 2010-07-07
Is this both a problem with USB- and PS/2-mice?

---

### Post by anthony_barker on 2010-07-29
I believe its a bug in x to do with the kernel

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591699](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/591699)

---

### Post by juliobahar on 2010-08-05
You have to upgrade to the newest kernel.

try connecting the laptop with their chargers on to the internet using a wired LAN connection or use an external USB Wifi that can be recognized by ubuntu.

After upgrade is complete you will notice that this x100e computer hanging and freezing stops.

Ah! don't forget to install the proprietary ATI driver too. it is called "fglrx" And reboot.

```

sudo apt-get install fglrx

```

But you will have other issues, as thought x100e thinkpads are not will supported by ubuntu yet. I'm still trying to get my mic, bluetooth and keyboard fn key shortcuts to work under ubuntu

---

### Post by juliobahar on 2010-10-26
My Lenovo X100e Thinkpad, is better with ubuntu 10.10. As the new kernel provide thinkpad ACPI support. I've tried the 64-bit version and the laptop seems fast consuming lesser CPU threads than with the 32-bit version.

There is a new bios available at [http://www-307.ibm.com/pc/support/site.wss/MIGR-74463.html]("http://www-307.ibm.com/pc/support/site.wss/MIGR-74463.html").

I've also downloaded the ATI proprietary graphics' driver.

Now most of the function Keys are working, so does the built-in microphone, although I haven't tried to voice-chat yet, but I can see the input bar moving as I speak.

My only problem now is the TOUCHPAD that seems to have an unresponsive bottom edge that occupies around 1/3 of the surface area of the pad.

This is definitely a setting or xorg-server driver issue, as it works well on other versions of ubuntu.

It seems that the touch pad driver is reposting mispositioned x,y axises data to the OS. Did any one suffer of this issue?

---

### Post by mpierro on 2010-12-08
Hey Julio

Any luck on the touch pad thing? I've just installed ubuntu on my x100e and found I've got the same issue...

suggestions anyone?

---

