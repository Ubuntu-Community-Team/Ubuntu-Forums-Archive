---
title: "Installing Broadcom B43 Wireless Driver Firmaware"
date: 2008-09-09
forum: Hardware
---

### Post by jordanae on 2008-09-09
I downloaded the Ubuntu Hardy Heron beta a while back and ever since my wireless driver has not worked. But I checked my drivers and it said all I need is to get the firmware for my Broadcom B43 wireless driver. The only problem is that I don't know how. Can anyone help me out there?

---

### Post by MyNameIsEarlB on 2008-09-11
I just installed Ubuntu on my laptop, and i had the same exact problem, i read this post right before i found the firmware, less than 5 mins ago, so here you go!

[http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2](http://downloads.openwrt.org/sources/broadcom-wl-4.80.53.0.tar.bz2)

im about to try to get mine working now :)

this is the site i found it on
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by Dr_Dan on 2008-10-28
I've just had the same problem getting the broadcom b43 wireless driver on my compaq presario laptop after installing ubuntu 8.04. When I ran the live cd after booting it detected that I needed the driver and downloaded and installed in automatically when I connected to the internet after I hooked up via the ethernet cable.

I then installed ubuntu on the hard drive but since then it no longer detects the need for the driver (even if I try find hardware).

Ive tried what it says at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) BUT I don't understand what it means when it says

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd .. 

where do I type this to download and extract the fw-cutter and firmware?

---

### Post by UtopiaTheory on 2008-10-29
Hello,

If you go to 

System > Administration > Hardware Drivers 

You can check there if the B43 Driver is enabled or not.  If the check box is blank, just check it and follow the directions on the screen.  To actually fetch the firmware you will need a wired connection!  It will fetch it for you and get it running.  I hope this helps!

Tom

---

### Post by community nerd on 2009-09-30
I was able to install it but if i reboot, it does not autimatically use the driver. I have to manually activate it. Any answers on that?

---

### Post by Ayuthia on 2009-09-30
> **community nerd said:**
> I was able to install it but if i reboot, it does not autimatically use the driver. I have to manually activate it. Any answers on that?

You should be able to get it to load automatically by adding the module to /etc/modules:
```
echo b43 | sudo tee -a /etc/modules
```

---

### Post by woundedtiger40 on 2010-10-02
> **Ayuthia said:**
> You should be able to get it to load automatically by adding the module to /etc/modules:
```
echo b43 | sudo tee -a /etc/modules
```


That really works, thanks. But, what this command acc' does on back stage? Do you or anyone else knows the answer?

Thanks in advance.

---

### Post by miji.nyan on 2010-10-31
Okay, so I dont have a cable, but can i install the firmware manually via flash drive then install it on ubuntu with a terminal command?

---

### Post by Darth Bane on 2011-03-23
Ok,
folks i just stepped into the same technical issue with Kubuntu 10.10 and my HP Pavilion DV8000. I read almost all available wikis about this topic.

Final i solved it by my own:

1. Connect your laptop to the Internet by a wired Ethernet connection
2. Go to SYSTEM SETTINGS - Software Management
3. Search for new software (GET and REMOVE software)/search input field: b43
4. Select only: b43-fwcutter (install this package)
5. Now back to the search input field (search for): broadcom
6. You will find two packages:
- broadcom-sta-common
- broadcom-sta-source
You need to install both packages.
7. Now back to the search input field (search for): b43
Select "firmware-b43-installer" and install it
8. Reboot the system
9. Define your Wlan connection - the Wifi interface should now be shown within your desktop network manager

I know that many of you would say this does not fit together, but when i only used the b43 component package i was not able to get a stable wifi connection (i lost the connection after a couple of seconds - means i lost the complete wlan interface). By adding the broadcom package i was able to build a strong and lasting wifi connection with my b43 wifi card. 

Before i also lost the b43 connection after every restart or reboot, but now everything is fine - i double checked this twice.

May be this solution will also work for some of you out there. :D

---

### Post by ferchope on 2011-04-23
> **Darth Bane said:**
> Ok,
folks i just stepped into the same technical issue with Kubuntu 10.10 and my HP Pavilion DV8000. I read almost all available wikis about this topic.

Final i solved it by my own:

1. Connect your laptop to the Internet by a wired Ethernet connection
2. Go to SYSTEM SETTINGS - Software Management
3. Search for new software (GET and REMOVE software)/search input field: b43
4. Select only: b43-fwcutter (install this package)
5. Now back to the search input field (search for): broadcom
6. You will find two packages:
- broadcom-sta-common
- broadcom-sta-source
You need to install both packages.
7. Now back to the search input field (search for): b43
Select "firmware-b43-installer" and install it
8. Reboot the system
9. Define your Wlan connection - the Wifi interface should now be shown within your desktop network manager

I know that many of you would say this does not fit together, but when i only used the b43 component package i was not able to get a stable wifi connection (i lost the connection after a couple of seconds - means i lost the complete wlan interface). By adding the broadcom package i was able to build a strong and lasting wifi connection with my b43 wifi card. 

Before i also lost the b43 connection after every restart or reboot, but now everything is fine - i double checked this twice.

May be this solution will also work for some of you out there. :D
that's the solution i was looking for, straight to the point thank you very much

---

### Post by Megaptera on 2011-04-23
Thread started September 10th, 2008  and revived today ... it lives!!

---

### Post by Ryuzaki_Gt on 2011-04-29
> **Darth Bane said:**
> Ok,
folks i just stepped into the same technical issue with Kubuntu 10.10 and my HP Pavilion DV8000. I read almost all available wikis about this topic.

Final i solved it by my own:

1. Connect your laptop to the Internet by a wired Ethernet connection
2. Go to SYSTEM SETTINGS - Software Management
3. Search for new software (GET and REMOVE software)/search input field: b43
4. Select only: b43-fwcutter (install this package)
5. Now back to the search input field (search for): broadcom
6. You will find two packages:
- broadcom-sta-common
- broadcom-sta-source
You need to install both packages.
7. Now back to the search input field (search for): b43
Select "firmware-b43-installer" and install it
8. Reboot the system
9. Define your Wlan connection - the Wifi interface should now be shown within your desktop network manager

I know that many of you would say this does not fit together, but when i only used the b43 component package i was not able to get a stable wifi connection (i lost the connection after a couple of seconds - means i lost the complete wlan interface). By adding the broadcom package i was able to build a strong and lasting wifi connection with my b43 wifi card. 

Before i also lost the b43 connection after every restart or reboot, but now everything is fine - i double checked this twice.

May be this solution will also work for some of you out there. :D

Thank you very much!!! its the best solution to the problem!! :D

---

### Post by LSBurton on 2011-04-29
This worked for me. I thought I was going to explode. Thank you!

---

### Post by Macbook5 on 2011-07-28
> **miji.nyan said:**
> Okay, so I dont have a cable, but can i install the firmware manually via flash drive then install it on ubuntu with a terminal command?

I'm having a similar problem, the cable solution isn't working but I have access to another computer with internet and a thumb drive. I already downloaded the file, I just need to install it. Does anyone know how?

---

### Post by WarrenSH on 2013-01-06
After each fresh install I always have to do 

```
echo b43 | sudo tee -a /etc/modules
```

then restart my Compaq  Presario V5101US

---

### Post by roadie133 on 2013-04-23
> **Dr_Dan said:**
> I've just had the same problem getting the broadcom b43 wireless driver on my compaq presario laptop after installing ubuntu 8.04. When I ran the live cd after booting it detected that I needed the driver and downloaded and installed in automatically when I connected to the internet after I hooked up via the ethernet cable.

I then installed ubuntu on the hard drive but since then it no longer detects the need for the driver (even if I try find hardware).

Ive tried what it says at [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43) BUT I don't understand what it means when it says

wget [http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2](http://bu3sch.de/b43/fwcutter/b43-fwcutter-011.tar.bz2)
tar xjf b43-fwcutter-011.tar.bz2
cd b43-fwcutter-011
make
cd .. 

where do I type this to download and extract the fw-cutter and firmware?

[COLOR=#b22222]I intended to post the answers but now realize I need to verify the process first, will return when I can confirm.[/COLOR]

---

