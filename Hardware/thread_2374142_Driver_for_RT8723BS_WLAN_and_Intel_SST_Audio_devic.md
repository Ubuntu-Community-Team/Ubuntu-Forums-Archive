---
title: "Driver for RT8723BS WLAN and Intel SST Audio devices"
date: 2017-10-13
forum: Hardware
---

### Post by omiazad on 2017-10-13
Hi,
I am working with a non profit project who needs to run some survey on the field and needs to use Ubuntu. In Bangladesh (that is where I am from) we have a brand called i-Life who sells cheap laptops made in China. This laptop's WLAN is Realtek RTL8723BS and Sound card is Intel SST Audio Device with ES8316 AudCodec. This is how they looks on Windows.

WLAN:
[IMG]https://i.stack.imgur.com/3GQsJ.png[/IMG]

Sound Card:
[IMG]https://i.stack.imgur.com/Qicex.png[/IMG]


[IMG]https://i.stack.imgur.com/1VJ0w.png[/IMG]

Now for this RTL8723BS I have follwed some instructions on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1581711") and tried to get the drives from GIT, compile and install it, but seems like the make command is not working for some reason. this is the output I get -
```
root@ZED-AIR:/usr/local/src/rtl8723bs# make
root@ZED-AIR:/usr/local/src/rtl8723bs# make install
root@ZED-AIR:/usr/local/src/rtl8723bs# sudo depmod -a
root@ZED-AIR:/usr/local/src/rtl8723bs# sudo modprobe r8723bs
modprobe: FATAL: Module r8723bs not found in directory /lib/modules/4.10.0-19-generic
root@ZED-AIR:/usr/local/src/rtl8723bs# 
```

I have also tried to downlaod and install the rtl8723bs-dkms_4.4.1+17245.20160325.2_all.deb from the launchpad link, but when I try to install that, it says "dkms not installed." Then when I try to install dkms, it doesn't work.

For the sound card, I actually could not locate any solution online.

We need 20 machines to run Ubuntu for our field survey and run some scripts but unfortunately I do not find any solution anywhere for them. So can anyone please help me with these?

---

