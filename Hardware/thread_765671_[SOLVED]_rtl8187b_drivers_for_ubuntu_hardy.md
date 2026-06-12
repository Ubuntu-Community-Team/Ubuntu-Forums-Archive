---
title: "[SOLVED] rtl8187b drivers for ubuntu hardy"
date: 2008-04-24
forum: Hardware
---

### Post by tjwoosta on 2008-04-24
today i installed ubuntu hardy (dual booting with gutsy for now)

but my problem is i cant seem to get my wireless driver to work in hardy

in gutsy i used a patched (hacked up) driver that i got from this thread
[http://ubuntuforums.org/showthread.php?t=571046&highlight=rtl8187b]("http://ubuntuforums.org/showthread.php?t=571046&highlight=rtl8187b")
more specifically this link to get the driver
[http://www.datanorth.net/~cuervo/rtl8187b/]("http://www.datanorth.net/~cuervo/rtl8187b/")

this driver seems to do i fine job in gutsy ,for what i need for, although ive noticed that it is fairly buggy 
(for instance the signal strength meter never goes above one bar despite the actual strength of the signal)

i have downloaded the exact same driver onto hardy
(i still had the original tar.gz file )

but anyway i cant get it to work on hardy
this is the error i get when i try to run ./makedrv
```

tj@tj-laptop:~/rtl8187b-modified$ sudo ./makedrv
[sudo] password for tj: 
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/tj/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/tj/rtl8187b-modified/ieee80211/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/tj/rtl8187b-modified/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-16-generic/build M=/home/tj/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/tj/rtl8187b-modified/rtl8187/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/tj/rtl8187b-modified/rtl8187] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [modules] Error 2

```
this is the error i get when i try to run ./wlan0up
```

tj@tj-laptop:~/rtl8187b-modified$ ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory

```

also i tried the newer tar.gz files that are on the link i posted but the same thing happened to all of them

can anybody help me?   
or maybe does anybody have a better driver i could use for this card?

---

### Post by dougtron on 2008-04-24
I'm right there with you. Same error messages and all. I'll spread the word to the few who really helped in the last RTL8187B forum and see if they can't figure out what's going on.

---

### Post by acirilo on 2008-04-24
i never got those modified drivers to work with hardy either... using the*** ./makedrv*** process and such

the only method that worked for me was the one i explained in my blog..but it has failed for some people. 

[http://mycirilo.com/?p=24]("http://mycirilo.com/?p=24")

---

### Post by dougtron on 2008-04-24
Yeah I definitely appreciated your efforts with the ndiswrapper way. But it seemed to fail miserably for me. I think it is bizarre that you didn't need the .sys file like you mentioned in your blog. Ndiswrapper is always weird though. I'm considering just finding a 40$ usb dongle that has known working linux drivers and saying eff the one that came with these stupid laptops haha. However, I emailed cuervo who originally modified it. We'll see if he has any idea what's going on.

Thanks again,
Doug

---

### Post by acirilo on 2008-04-24
> **dougtron said:**
> Yeah I definitely appreciated your efforts with the ndiswrapper way. But it seemed to fail miserably for me. I think it is bizarre that you didn't need the .sys file like you mentioned in your blog. Ndiswrapper is always weird though. I'm considering just finding a 40$ usb dongle that has known working linux drivers and saying eff the one that came with these stupid laptops haha. However, I emailed cuervo who originally modified it. We'll see if he has any idea what's going on.

Thanks again,
Doug


it is weird.. 

Sorry I'm not much help..

---

### Post by glenndebacker on 2008-04-25
I didn't had any problems compiling the drivers (i've downloaded  rtl8187b-modified-jadams-2-1-2008.tar.gz from the site mentioned above) under hardy, but even so it doesn't work well. 

I can get the interface up and running, scan for networks and connect to open networks that doesn't have WEP enabled. But from the moment that I want to connect to a WEP enabled network,  Ubuntu just freezes. 

Ndiswrapper doesn't work here, can't connect to any network.

---

### Post by pjasnos on 2008-04-25
Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz

wget http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

---

### Post by pjasnos on 2008-04-25
Now I'm working on making sis671 module working... ;)

---

### Post by tjwoosta on 2008-04-25
awesome pjasnos, it worked for me too when i applied the patch myself

now i can scan for networks and i found my network but for some reason it wont let me type in the bssids box(dosn't freeze up, it just dont let me type)
so i cant figure out how to connect to my network

does anyone know a way to connect to my home network through the terminal?

and perhaps set the default so it will connect everytime i do ./wlan0up?

EDIT: Nevermind  i figured it all out,   the driver works fine now 
(aside from the fact that the signal strength meter lies) but thats no biggy for me

---

### Post by dougtron on 2008-04-26
Thanks pjasnos, got it working. Sad that it's WEP only.

---

### Post by glenndebacker on 2008-04-26
Yes it idd works - thank you very much !

---

### Post by pjasnos on 2008-04-26
Actually, it should work with WPA as well (I just don't have any at hand to test it), as in Linux WPA is done programmatically - (via wpasupplicant).Try using manual configuration in network manager (I never got it working in "roaming mode") and type your password there.

---

### Post by pjasnos on 2008-04-26
I don't know if it helps you, but I added full path to the wlan0up to my /etc/rc.local
(just before exit 0 line), so that it is loaded automatically whenever I turn on the computer.
EDIT:
So now it looks like:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/pawel/rtl8187/wlan0up
ifconfig wlan0 up
dhclient wlan0
exit 0

I observed that if my wi-fi card is switched off when booting linux, network manager would often not see it and not configure it when I switch it on, so I put three commands into a simple script which I've got on my desktop as "fixwireless.sh" which resolves it. Here's the script, if you are interested
> 
#! /bin/bash
sudo iwconfig wlan0 essid myNet
sudo iwconfig wlan0 key WEPKEYWEPKEY
sudo dhclient wlan0

---

### Post by tjwoosta on 2008-04-26
that definatly helps alot, thanks

ever since i started using this driver in gutsy iv had to manually do ./wlan0up every boot

---

### Post by pana.corbului on 2008-04-26
I have a toshiba l40-14f with a rtl8187b chipset wireless card. I've been google it all day long trying to connect to my linksys router and the only solution in hardy was to install ndiswrapper with [this](http://mycirilo.com/wp-content/uploads/2008/04/net8187b.inf) modified win98 driver. 

It connects on unsecured wifi and wep networks using 128 hexa key using cli: 

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "your_network_essid"
sudo iwconfig wlan0 key your_wep_key
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

Hoping that someone will manage to connect to wifi usings wpa.

---

### Post by saskunah on 2008-04-27
> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

It works perfectly, thanx!!

---

### Post by I_ch on 2008-04-27
+1 to Saskunah:

Pjasnos, many thanks, it works for me, too. :)

---

### Post by game_plan on 2008-04-28
I've got the patch installed and only parts of wireless is working. Network Manager knows its up and shows my neighbors open network so i know its working. And I can *iwlist wlan0 scan* to find my hidden network. But iwconfig can't find any wlan0, says it "does not exist"

Any ideas whats happened here would be great, I've tried everything I could think of.

---

### Post by Fran89 on 2008-04-30
Thanks, thats the exact method I used (but sadly i had to figure it out by myself) but it works perfectly, I have not tried WPA but i can run WEP smoothly

---

### Post by game_plan on 2008-05-02
> **game_plan said:**
> I've got the patch installed and only parts of wireless is working. Network Manager knows its up and shows my neighbors open network so i know its working. And I can *iwlist wlan0 scan* to find my hidden network. But iwconfig can't find any wlan0, says it "does not exist"

Any ideas whats happened here would be great, I've tried everything I could think of.

Can anyone explain why this does this? I would really like to get my wireless up and working correctly. Thanks for your help.

---

### Post by I_ch on 2008-05-02
As I said a few replies above, my NIC works now. But the only annoying thing is that I have to start wlan0 up manually each time I boot up the system (this is done in terminal). Could anyone tell me how can I start my wireless NIC automatically at startup? Thank you all :)

---

### Post by tjwoosta on 2008-05-02
READ THE THREAD!  page two third post down

---

### Post by I_ch on 2008-05-02
Oops... :) sorry, I've missed this.

---

### Post by ramosjosep on 2008-05-03
Thanks!!! This helped me a lot. I was going crazy with this wireless card. Now everything works.

---

### Post by perfran on 2008-05-03
> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

I had the same error and the patch worked as well for me ;)
Thanks very much :)

---

### Post by pana.corbului on 2008-05-03
I'm using that win98 driver on ndiswrapper. ```
network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:16:44:6f:2c:6d
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8187b driverversion=1.52+Realtek Semiconductor Corp. ip=192.168.0.122 multicast=yes wireless=IEEE 802.11g

```It connects to wep wireless but I have not succeded to connect using wpa 1. 
Here is the output of my network ```
iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:E3:4E:E8
                    ESSID:"octavianus"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:65/100  Signal level:-54 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
``` and here is my wpa_supplicant.conf ```
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="octavianus"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="Xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
        pairwise=TKIP
        group=TKIP
} 
```Any ideeas ?

Should I use instead linux realtek driver? Is it working with hardy? I can connect succesfuly to wep wireless but no to wpa1. 
 Here is the output ```
sudo wpa_supplicant -Dwext -iwlan0 -c /etc/wpa_supplicant.conf -w
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Associated with 00:1d:7e:e3:4e:e8
WPA: Key negotiation completed with 00:1d:7e:e3:4e:e8 [PTK=TKIP GTK=TKIP]
CTRL-EVENT-CONNECTED - Connection to 00:1d:7e:e3:4e:e8 completed (auth) [id=0 id_str=]
CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
^[[23~Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
Trying to associate with 00:1d:7e:e3:4e:e8 (SSID='octavianus' freq=2437 MHz)
Authentication with 00:00:00:00:00:00 timed out.
cioctl[SIOCGIWSCAN]: Resource temporarily unavailable

```

---

### Post by pana.corbului on 2008-05-04
It appears that knetwork manager from kde is doing his job in hardy. Now, I'm able to connect to my network using wpa and wpa2 [AES] no problem. All from gui! [It didn't worked from cli]

---

### Post by lupul.din.codru on 2008-05-04
> **pana.corbului said:**
> It appears that knetwork manager from kde is doing his job in hardy. Now, I'm able to connect to my network using wpa and wpa2 [AES] no problem. All from gui! [It didn't worked from cli]

Hello pana.corbului,

That's great news!

I would really appreciate if you could detail (from A toZ) your solution for using wpa with this wifi chipset in hardy.

I'm a beginner in linux so please feel free to give as much details as possible and attach all the files you consider necessary :)

Multzam,
lupul din codru

---

### Post by pana.corbului on 2008-05-04
OK. I'll try to be as straight as I can. 

First you have to be sure that your wireless card is using the rtl 8187b chipset. You can check this by issueing lsusb command in consle```
octav@toshiba:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
**[red]Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.**[/red]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Next, you'll install ndiswrapper which is a software for using Windows wireless drivers with Linux, if the current linux kernel doesn´t support a certain device.```
sudo apt-get install linux-headers-`uname -r` build-essential ndiswrapper-utils-1.9 
``` 

Stop the network ```
 sudo /etc/init.d/networking stop
```

Download driver from [here](http://mycirilo.com/wp-content/uploads/2008/04/net8187b.inf) and save it to your deskop and install it using ndiswrapper```
 ndiswrapper -i ~/Desktop/net8187b.inf 
```

Check if it was properly installed```
 sudo ndiswrapper -l 
``` The output should be something like net8187b : driver installed    device (0BDA:8197) present;

If there were no erros you can build kernel module ```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Start networking ```
sudo /etc/init.d/networking restart
```

Activate wireless interface from laptop's switch. 

Optionally [to start ndiswrapper at boot] sudo gedit /etc/modules and add ndiswrapper.

Reboot and check gnome network applet for wireless networks. Mine works only if I select connect to other wireless network enter network essid previously detected and than select the encryption type.

---

### Post by game_plan on 2008-05-04
I've tried following the steps for ndiswrapper, and tried every driver in the realtek package (Windows 98,ME,2k and XP and Vista's 32 and 64 bit drivers) 

NONE will show the device is present. I've removed and tried every driver in the set and same thing every time...
```

root@laptop1:/home# ndiswrapper -l
net8187b : driver installed

```

. Yet I know I have the chip since lsusb shows...
```

root@laptop1:/home# lsusb
Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

And the modified driver with the patch shows WEP networks (without signal mind you) but I cannot get WPA1 or 2 to work.

iwconfig still says wlan0 does not exist, yet network manager and iwlist scan both see and use the device.

PLEASE help :'(

---

### Post by seddonym on 2008-05-05
Thanks Pjasnos for your instructions which got it working for my Toshiba Equium running a Hardy Heron.

I did however have to configure the DNS afterwards, so for the sake of completeness here's a quick explanation:

If you followed Pjasnos' instructions, and got the bars in the top right corner which showed you were connected, but still couldn't browse the internet, you probably need to sort out the DNS.

1. Open the Network Settings wizard, unlock it, and go to the DNS tab.
2. Add the following two IP addresses: 208.67.222.222 and 208.67.220.220.

Now open Firefox and you should be able to browse the internet!

---

### Post by ramosjosep on 2008-05-08
> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps



I made this and everything worked for a few days, then one day I tried to connect and got this error (or whatever it is):

insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Invalid module format 
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Invalid module format 
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Invalid module format 
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Invalid module format 
insmod: error inserting 'ieee80211-rtl.ko': -1 Invalid module format 
insmod: error inserting 'r8187.ko': -1 Invalid module format 

Any idea to help me to solve this? I just don´t know what happened. Somebody please help me!

---

### Post by badfish591 on 2008-05-08
> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

when i try to run the command "patch -p1 < 2.6.24.patch" it tells me that i don't have the program patch and gives me a bash error? Do i need to install something before attempting this? if so what should i get?

---

### Post by ASULutzy on 2008-05-08
Reall weird... I got the driver to work, and I can talk on Pidgin for a little bit, but after maybe about 10 minutes, my keyboard stops responding and I am forced to restart.

This patched driver is screwing with my system's interrupts.

If anyone knows a solution, I'd love to hear it.

Otherwise I'd suggest that everyone use this at their own risk.

edit:Bus 007 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
is the device I attempted to make this work on. It's Trendnet's TEW-424ub

---

### Post by grozni on 2008-05-09
> **pana.corbului said:**
> OK. I'll try to be as straight as I can. 

First you have to be sure that your wireless card is using the rtl 8187b chipset. You can check this by issueing lsusb command in consle```
octav@toshiba:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
**[red]Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.**[/red]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Next, you'll install ndiswrapper which is a software for using Windows wireless drivers with Linux, if the current linux kernel doesn´t support a certain device.```
sudo apt-get install linux-headers-`uname -r` build-essential ndiswrapper-utils-1.9 
``` 

Stop the network ```
 sudo /etc/init.d/networking stop
```

Download driver from [here](http://mycirilo.com/wp-content/uploads/2008/04/net8187b.inf) and save it to your deskop and install it using ndiswrapper```
 ndiswrapper -i ~/Desktop/net8187b.inf 
```

Check if it was properly installed```
 sudo ndiswrapper -l 
``` The output should be something like net8187b : driver installed    device (0BDA:8197) present;

If there were no erros you can build kernel module ```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Start networking ```
sudo /etc/init.d/networking restart
```

Activate wireless interface from laptop's switch. 

Optionally [to start ndiswrapper at boot] sudo gedit /etc/modules and add ndiswrapper.

Reboot and check gnome network applet for wireless networks. Mine works only if I select connect to other wireless network enter network essid previously detected and than select the encryption type.




I've followed what you suggested, after trying to apply inf file. I've received

```

couldn't find "RTL8187B.sys" in "/home/ids-admin/Desktop"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/ids-admin/Desktop" -
installation may be incomplete
```


Where can I find complete driver? The one from Realtek site doesn't work

---

### Post by I_ch on 2008-05-09
> **badfish591 said:**
> when i try to run the command "patch -p1 < 2.6.24.patch" it tells me that i don't have the program patch and gives me a bash error? Do i need to install something before attempting this? if so what should i get?

You should "sudo apt-get install patch" :) Its a program, too...

---

### Post by grozni on 2008-05-09
I'm using rtl8187b-modified-dist.tar.gz + patch applied. Everything works except when WEP authentication is set to shared, then my laptop Toshiba L40-14F hangs, and I have to use button to shut down. When I set authentication to open everything works like charm. Problem with authentication I had with Gutsy and how with Hardy. I just wanted to report this.

---

### Post by badfish591 on 2008-05-09
> **I_ch said:**
> You should "sudo apt-get install patch" :) Its a program, too...

my thoughts exactly, but when i typed that it said that there was no such program. i tried three times before posting here


badfish591@badfish591-laptop:~$ sudo apt-get install patch
[sudo] password for badfish591: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package patch
badfish591@badfish591-laptop:~$

---

### Post by ASULutzy on 2008-05-09
> **grozni said:**
> I've followed what you suggested, after trying to apply inf file. I've received

```

couldn't find "RTL8187B.sys" in "/home/ids-admin/Desktop"; make sure all driver files, including .inf, .sys (and any firmware files) are in "/home/ids-admin/Desktop" -
installation may be incomplete
```


Where can I find complete driver? The one from Realtek site doesn't work

I am also looking for the .sys file to try and make this work.
I have the ```
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp.
``` wireless USB adapter and haven't been able to get it to work for more than a few seconds without it either hard locking my system or causing a general protection fault. Any guidance would be greatly appreciated.

---

### Post by H_a_D_3_z on 2008-05-09
I don't mean to sound like a butt.  But did you have your ubuntu cd in the computer.  I think thats what the E: stands for.  An uneducated guess, but just trying to help.

---

### Post by I_ch on 2008-05-10
**badfish591,**

I guess, the previous post by **H_a_D_3_z** is dedicated to you.) Maybe you also should check your remote (not CD) repositories to be enabled? Sorry I know this is quite simple but this is the only thing I can suppose. Also you can try to install "patch" with Synaptic (from GUI).

---

### Post by pana.corbului on 2008-05-10
I-ch, I also have a toshiba l40-14f \\:D/


Here is a link with drivers that worked for me

[rtl drivers tar gz](http://www.upload.ro.im/upload/DOWNLOAD/9ee302256/rtl_drivers.tar.gz)

another link [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58)

---

### Post by badfish591 on 2008-05-10
> **I_ch said:**
> **badfish591,**

I guess, the previous post by **H_a_D_3_z** is dedicated to you.) Maybe you also should check your remote (not CD) repositories to be enabled? Sorry I know this is quite simple but this is the only thing I can suppose. Also you can try to install "patch" with Synaptic (from GUI).

yeah it was the remote repositories..... i swore i already did that:confused:
anyways, now it actually acknowledges that i have a wireless card, but still i cannot connect to my router and access the internet.

---

### Post by grozni on 2008-05-11
> **pana.corbului said:**
> I-ch, I also have a toshiba l40-14f \\:D/


Here is a link with drivers that worked for me

[rtl drivers tar gz](http://www.upload.ro.im/upload/DOWNLOAD/9ee302256/rtl_drivers.tar.gz)



Can you upload somewhere else please? Link is down

---

### Post by I_ch on 2008-05-11
**grozni**,

I've managed to download the archive with this link, so it works. Anyway you can write me a pm, I'll send it to you (if you wish:))

**pana.corbului**,
 are you using WPA in your network? I use the patched driver by Cuervo&Co. now, but I have to connect to unencrypted networks only.

**badfish591**,
 so what is your progress now?

---

### Post by grozni on 2008-05-11
> **I_ch said:**
> **grozni**,

I've managed to download the archive with this link, so it works. Anyway you can write me a pm, I'll send it to you (if you wish:))


Works now. Thanks!

---

### Post by pana.corbului on 2008-05-11
Yes, I'm using wpa2 [AES] on my linksys wrt54gl with tomato. 

Is Cuervo's patched driver capable to connect to wpa wireless networks? 

I can also  connect to unecrypted networks from knetwork manager [I use kubuntu 8.04] . It also shows me available networks.

Also it automatically connects to wireless at boot without having to enter credentials if wired connection is unavailable [cable pull out].

---

### Post by badfish591 on 2008-05-11
> **I_ch said:**
> **badfish591**, so what is your progress now?

sorry for not posting back, i reset my router and re-entered my info into the network tab, and now i'm all set. kinda a pain to have to mess with it everytime i boot up but, at least it's working.
I tried to edit my /etc/rc.local 
but it had no effect, so if anyone knows another way to get it working at startup i would love to try it out

---

### Post by grozni on 2008-05-12
pana.corbului:


your driver works. My wireless network is wep secured, open system 128bit hex key. I connect to my wireless network fine, signal strength is shown, but I can't browse thru internet. First I thought firestarter is problem, so I bring firewall down, DNS servers are fine. My wireless network uses DHCP, but when I connect to my network, IP is not assigned via DHCP, so I tried manually entering adresses also, all the same, can't browse. Any suggestions?

---

### Post by pana.corbului on 2008-05-12
In my previos posts I've managed to connect my laptop to wep 128 bits hexa using a script that I ran at boot. This was for me the only way that I could get an ip using dhcp. Try using these commands to connect to your network. Edit somefile and paste this content, then "chmod +x somefile" and afterwards "./somefile" to run it.

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "your_network_essid"
sudo iwconfig wlan0 key your_wep_key
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0

---

### Post by I_ch on 2008-05-13
**badfish591**,

Did you read **_[this]("http://ubuntuforums.org/showpost.php?p=4798570&postcount=13")_**? This post is located at current thread at page 2.

---

### Post by badfish591 on 2008-05-14
yes acutally i did, with no luck, however i just did it agian(with some slight modifications) and i believe i got it working, thanks to everyone who posted here.

---

### Post by rookie2008 on 2008-05-27
Hello everyone,

My wifi was working just fine using pjasnos' method 

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

until I installed the updates that GNOME recommended I download and install earlier today.  I am using Ubuntu 8.04 64bit desktop edition.  Now I am getting some of the same errors you all have mentioned - 

notavailable@CENSORED:~$ cd rtl8187b-modified
notavailable@CENSORED:~/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
notavailable@CENSORED:~/rtl8187b-modified$ dir

2.6.24.patch  install	    ReadMe.txt	  wlan0dhcp  wlan0up
ieee80211     makedrv	    release_note  wlan0down  wpa_supplicant-0.5.3
ifcfg-wlan0   README.FIRST  rtl8187	  wlan0rmv
notavailable@CENSORED:~/rtl8187b-modified$ 

Any help would be greatly appeciated!  I thought the updates were  supposed to fix problems, not create them.  Maybe I should email the developers?

---

### Post by tjwoosta on 2008-05-27
i had the same issue where my driver stopped working after todays updates

it was simple to fix (just run the ./makedrv and ./install commands again)

i think the updates today must have reset something that the driver relies on, no problems now though

---

### Post by rookie2008 on 2008-05-27
Ok...

I just did the following:

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

And it is back online again.  I am tempted to mess around with  rtl8187b-modified-jadams-2-1-2008.tar.gz from [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)   to see if it supports WPA instead of strictly WEP.

---

### Post by MasterSander on 2008-05-28
I've been using the same modified driver as you guys, it worked good enough on gutsy, just no WPA and no signal strength. But on hardy my whole computer freezes when I try to connect to a wep encrypted network. An idea how to fix this?

---

### Post by MasterSander on 2008-05-29
If it's of any help, he also freezes when I try to load my webcam. Could these be in conflict with each other?

---

### Post by pjasnos on 2008-06-03
Hi,

Just a couple of notes: if you read the driver sources, you would see in comments that only open authentication and managed mode is supported (no shared auth or ap mode, at least for now). According to Cuervo's blog, Andrea Merello (the original writer of the rtl8187 driver which Cuervo patched) has contacted him and would probably become the maintainer again - which is a very good news :-).

as for non-working rc.local - most probably you entered wrong path to wlan0up (wrong case?)

MasterSander - have you tried first running wlan0down and then wlan0up? 

As for the update, recently a new kernel version was pushed down the update pipe, which is binary incompatible with the drivers - hence you would probably need to re-compile whenever you see something beginning with linux-image- in the update list.

---

### Post by MasterSander on 2008-06-05
I'll try recompiling the newest patch and I'll let you know how it worked out.

---

### Post by MasterSander on 2008-06-06
It worked!

---

### Post by Shachiel on 2008-06-09
Thanks a lot pjasnos, worked like a charm... unfortunately the wlan intensity won't be shown... :S, other than that its perfect.

Thanks again!

---

### Post by stchman on 2008-06-09
I went to Realtek's website and they do not yet support Linux with the rtl8187b.

They do have drivers for the rtl8187l and rtl8185l models.

Will using ndiswrapper work?

---

### Post by tjwoosta on 2008-06-10
> 
I went to Realtek's website and they do not yet support Linux with the rtl8187b.


this we all know, that is why we are using this hacked driver mentioned on the first page

> 
They do have drivers for the rtl8187l and rtl8185l models.

Will using ndiswrapper work? 


yes some people here have had luck using ndiswrapper (you need to read the whole thread, everything is here)

---

### Post by carlo82 on 2008-06-12
Hi everbody! I have almost the same problems, my laptop is a Toshiba L300-11A (PSLB0E) and I have a realtek rtl8187b of course.
I tried almost anything I found across forums, also this

> **rookie2008 said:**
> 
wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 



and all variations (with/without patch, mods, etc), but nothing works. Just because I'm very lucky, the LAN card rtl8101E (rev 02)(realtek again...) does not work as well (I had to disable that from the bios to make the system boot, at least).

Anyway I've been struggling for days, also with ndiswrapper, and it seems to me that my problem is the IDPROD. I got it with
```
lsusb
```
and I discovered that is 0bda:8198 and I noticed that is different from the others I've been seeing around.

Suspecting the drivers weren't working for this I also tried the
```
./wlan0up force_card=0x8198 
``` as suggested in the README.FIRST of the rtl8187b-modified-dist.tar.gz with no luck again.

I'm also triing with ubuntu 7.10 (other versions are not working for different other hardware problems), but no luck.

Suggestions?
PS. (a bit OT) Is there any way of making the cable LAN working, I don't know, with some standard driver? It would be great at least having that!

Thanks everybody!

---

### Post by sayid on 2008-06-12
> **tjwoosta said:**
> this we all know, that is why we are using this hacked driver mentioned on the first page



yes some people here have had luck using ndiswrapper (you need to read the whole thread, everything is here)

Hello!
I have been proving several solutions, the only that works for me was the hacked driver mencioned by tkwoosta. I write a post with more details [here]("http://ubuntuforums.org/showpost.php?p=5170274&postcount=6").

**My questions are**
Exist any possibility that somebody do reverse engineering? 
Or something that help changing driver code (no cracking an old driver with "if model is 'rtl8187' *and 'rtl8187b'*..." )?
Knows someone how to ask that ubuntu's developers consider this driver in future kernels?

---

### Post by bluesman78 on 2008-06-13
This post is awesome.  I am brand new to Ubuntu and Linux.  I have basically been copying and pasting stuff from this site right into my terminal window.  I am successful at getting the driver working.  I see tons of wireless networks. I can't connect to my own network!!

Also, when I reboot the computer I have to run the command manually, is there anyway to have it start from scratch.  

Extremely frustrated!!  Would love to get rid of Vista on this laptop and just use Ubuntu!

Thanks!

---

### Post by MasterSander on 2008-06-13
> **pjasnos said:**
> I don't know if it helps you, but I added full path to the wlan0up to my /etc/rc.local
(just before exit 0 line), so that it is loaded automatically whenever I turn on the computer.
EDIT:
So now it looks like:
> #!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/home/pawel/rtl8187/wlan0up
ifconfig wlan0 up
dhclient wlan0
exit 0


I observed that if my wi-fi card is switched off when booting linux, network manager would often not see it and not configure it when I switch it on, so I put three commands into a simple script which I've got on my desktop as "fixwireless.sh" which resolves it. Here's the script, if you are interested

>  #! /bin/bash
sudo iwconfig wlan0 essid myNet
sudo iwconfig wlan0 key WEPKEYWEPKEY
sudo dhclient wlan0



Try that, you just need to give your sudo password when starting up. It's better than having to do it manually each time. Haven't needed the fixkey script myself. Or you can write a script to ./wlan0up and execute that yourself each time (place it on your desktop or something like that). But you have to enter your password in a terminal as well, so it stays the same.

---

### Post by sayid on 2008-06-15
> **bluesman78 said:**
> This post is awesome.  I am brand new to Ubuntu and Linux.  I have basically been copying and pasting stuff from this site right into my terminal window.  I am successful at getting the driver working.  I see tons of wireless networks. I can't connect to my own network!!

Also, when I reboot the computer I have to run the command manually, is there anyway to have it start from scratch.  

Extremely frustrated!!  Would love to get rid of Vista on this laptop and just use Ubuntu!

Thanks!

Hello bluesman78, I was using the driver like you for a couple of days, after known that this driver is the only one (for me is really bad, but the only that works) I put only one line in a file that solve the problem.

> sudo vi /etc/rc.local

/PREVIOUS_PATH/rtl8187b-modified/wlan0up

Remember that PREVIOUS_PATH is the place where you have the driver's folder located.


After this changes when you reboot, you should see your realtek in action! 

If you are using KnetworkManager and your network device is switched off, no matter! only switch on it and wait, it'll recognize your network in a few seconds.  

Maybe this post will help you,
Regars,
Sayid...

---

### Post by ThossZA on 2008-06-20
Hi, I'm very new to Linux and I'm stuck trying to get this driver working. When I run ./makedrv it seems to do it's thing, but when I try ./wlan0up I always get the same message. Running .wlan0down doesn't seem to help.

> Directory/Desktop/rtl8187b-modified# sudo ./wlan0up 
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
Directory/Desktop/rtl8187b-modified# sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modulesi
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules

---

### Post by tjwoosta on 2008-06-20
> Hi, I'm very new to Linux and I'm stuck trying to get this driver working. When I run ./makedrv it seems to do it's thing, but when I try ./wlan0up I always get the same message. Running .wlan0down doesn't seem to help.

[QUOTE]
Directory/Desktop/rtl8187b-modified# sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: can't read 'r8187.ko': No such file or directory
Directory/Desktop/rtl8187b-modified# sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modulesi
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules [/QUOTE]


have you already applied the patch to the driver, like mentioned on the first page?

cuz that looks like the same error i was getting before i applied the patch

---

### Post by louis_gas on 2008-06-25
> **pana.corbului said:**
> OK. I'll try to be as straight as I can. 

First you have to be sure that your wireless card is using the rtl 8187b chipset. You can check this by issueing lsusb command in consle```
octav@toshiba:~$ lsusb
Bus 007 Device 001: ID 0000:0000
Bus 006 Device 001: ID 0000:0000
Bus 005 Device 003: ID 04d9:0499 Holtek Semiconductor, Inc.
Bus 005 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
**[red]Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.**[/red]
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

Next, you'll install ndiswrapper which is a software for using Windows wireless drivers with Linux, if the current linux kernel doesn´t support a certain device.```
sudo apt-get install linux-headers-`uname -r` build-essential ndiswrapper-utils-1.9 
``` 

Stop the network ```
 sudo /etc/init.d/networking stop
```

Download driver from [here](http://mycirilo.com/wp-content/uploads/2008/04/net8187b.inf) and save it to your deskop and install it using ndiswrapper```
 ndiswrapper -i ~/Desktop/net8187b.inf 
```

Check if it was properly installed```
 sudo ndiswrapper -l 
``` The output should be something like net8187b : driver installed    device (0BDA:8197) present;

If there were no erros you can build kernel module ```
sudo ndiswrapper -m
sudo modprobe ndiswrapper
```

Start networking ```
sudo /etc/init.d/networking restart
```

Activate wireless interface from laptop's switch. 

Optionally [to start ndiswrapper at boot] sudo gedit /etc/modules and add ndiswrapper.

Reboot and check gnome network applet for wireless networks. Mine works only if I select connect to other wireless network enter network essid previously detected and than select the encryption type.

hi! i can't get WPA working.. Do you know why when i run "sudo ndiswrapper -l" on console i get only "net8187b : driver installed" and not the "device (0BDA:8197) present" thing? :)

---

### Post by pana.corbului on 2008-06-25
i assume you don't have a rtl8187b wireless chipset? :D

check please using lsusb and see if you get 

Bus 007 Device 001: ID 0000:0000
Bus 003 Device 002: ID 0bda:8197 Realtek Semiconductor Corp.
Bus 003 Device 001: ID 0000:0000

---

### Post by louis_gas on 2008-06-25
I have :)

Bus 007 Device 001: ID 0000:0000  
Bus 006 Device 002: ID 0bda:8197 Realtek Semiconductor Corp. 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  


thanks for your quick reply ;)

---

### Post by pana.corbului on 2008-06-25
indeed you have..are you sure you followed all steps ...including downloading correct driver?   [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58) 

if you need to uninstall the current driver and install this one [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58)  use ```
sudo ndiswrapper &#8211;e <drivername>
```

---

### Post by louis_gas on 2008-06-26
> **pana.corbului said:**
> indeed you have..are you sure you followed all steps ...including downloading correct driver?   [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58) 

if you need to uninstall the current driver and install this one [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58)  use ```
sudo ndiswrapper –e <drivername>
```

i uninstalled and installed again. nothing happened. :(
In network manager i can see wireless connection but when i try to connect there is not WPA to choose from. I tried also with KDE manager as you said in previeous posts but it was showing a message saying "WPA Supplicant is not started, encryption cannot be configured".

---

### Post by louis_gas on 2008-06-26
well i found the problem. 
I had to add
```
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200
```
into the section IDs for X64 in the inf file.
I suppose this is because i use 64bit ubuntu.


Can you please tell me how to connect to a wpa2 or at least wpa network? When i choose my network from the list and asks for my password i has only wep and leap.
[IMG]http://http://ubuntuforums.org/attachment.php?attachmentid=75389&stc=1&d=1214486791[/IMG]

---

### Post by bigjseph on 2008-06-29
> **pjasnos said:**
> I don't know if it helps you, but I added full path to the wlan0up to my /etc/rc.local
(just before exit 0 line), so that it is loaded automatically whenever I turn on the computer.
EDIT:
So now it looks like:


I observed that if my wi-fi card is switched off when booting linux, network manager would often not see it and not configure it when I switch it on, so I put three commands into a simple script which I've got on my desktop as "fixwireless.sh" which resolves it. Here's the script, if you are interested

alright so i'm a total noob and i have no idea how to do any of this
i followed the earlier instructions and i can now connect to my network but i have to do it through the terminal every time i boot and that's a bit annoying so how can you edit the local file and whatnot

---

### Post by bigjseph on 2008-07-04
alright i found it just have to do the gksu gedit
thanks anyway

---

### Post by calman on 2008-07-06
**ThossZA**, **rookie2008**, and **ramosjosep** have all mentioned the problem of:

```

caleb@jcpc:/media/CALEB/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 File exists
insmod: error inserting 'ieee80211-rtl.ko': -1 File exists
insmod: error inserting 'r8187.ko': -1 File exists

```

which is probably related to

```

caleb@jcpc:/media/CALEB/rtl8187b-modified$ sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules

```

although some people have fixed it, I've still got this problem and doing the same thing over and over does not work.  Does anyone know what this means or how to fix it?

I believe it might (in my case) have to do with the fact that I'm using a **Belkin F5D7050 v5000** USB stick.  Other versions of this model used different chipsets, but the version I just stated uses the rtl8187b chipset.  Most of the users here seem to be using a Realtek brand stick with the same chipset?

I'd think as long as they have the same chipset it doesn't matter, but maybe it does -- and that's why everyone's running into trouble.

Maybe someone can clear this up for me.  Thanks.

---

### Post by tjwoosta on 2008-07-06
calman

did you see any errors at all while doing ./makedrv ?

---

### Post by calman on 2008-07-06
Thanks for the quick reply.  I don't get any errors but I get plenty of warnings:

```
caleb@jcpc:~/Music/rtl8187b-modified$ ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/caleb/Music/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:709: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1553:4: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1593:2: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2251: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2473: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2474: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1553:4: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1593:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/caleb/Music/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.o
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2280: warning: cast from pointer to integer of different size
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2290: warning: cast to pointer from integer of different size
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'


```

---

### Post by tjwoosta on 2008-07-06
hmm well i dont really know what the problem is but i can just list the steps that i took to get everything working


wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/

cd rtl8187b-modified

patch -p1 < 2.6.24.patch

./makedrv
(i restarted right here just incase)
then

sudo ./wlan0up  

if you still get the insmod error try running ./wlan0down once (dont worry about errors) 

then run ./wlan0up again

if you have done all of this and things are still not working then you might want to consider using ndiswrapper with the windows driver

---

### Post by Roasted on 2008-07-08
What in the world did I do wrong?


jason@jason-laptop:~/rtl8187b-modified$ sudo ./wlan0up
insmod: can't read 'ieee80211_crypt-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_wep-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_tkip-rtl.ko': No such file or directory
insmod: can't read 'ieee80211_crypt_ccmp-rtl.ko': No such file or directory
insmod: can't read 'ieee80211-rtl.ko': No such file or directory
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module
jason@jason-laptop:~/rtl8187b-modified$

---

### Post by Roasted on 2008-07-09
> **pana.corbului said:**
> indeed you have..are you sure you followed all steps ...including downloading correct driver?   [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58) 

if you need to uninstall the current driver and install this one [http://www.fileshare.ro/531529970.58](http://www.fileshare.ro/531529970.58)  use ```
sudo ndiswrapper –e <drivername>
```

I installed the wrong windows driver by accident. When I run that command to uninstall it, it says no such file or directory.

Is it just supposed to be:

sudo ndiswrapper -e net8187b.inf

????

---

### Post by pjasnos on 2008-07-10
Roasted, you are mixing the native Linux driver and Windows driver. If you have installed native Linux driver (as copied from my instructions by tjwoosta [-X ), then you don't need to uninstall it to use NDIS driver. Just delete the folder. But NDIS drivers are BAD, because: 
1. They are not open-source - not Free in the sense of freedom.
2. They are not written for Linux, but for windows, hence they are using a hackish compatibility layer named NDISWrapper
3. No one supports them (neither canonical nor any other linux vendor or developer, not even mentioning company that has written the driver). And if you report a problem to a kernel developer, he/she would be much less likely to help you if you use a hackish binary blob in a hackish wrapper (I am not trying to insult creators of ndiswrapper - they have done a very good thing allowing you to use your hardware if all else fails; but due to the nature of it, it will always be far from perfect).

Ok, end of lecture :-).

I may be able to help with the native linux driver if you show me all the commands that you used to compile it (have you followed my instructions, or someone else's?)


Also, from your above post, it seems that the ieee80211 drivers' didn't compile correctly or is already loaded (the latter is often the case) - did you get any errors during compilation? Have you tried doing ./wlan0down and then ./wlan0up ?
> **Roasted said:**
> I installed the wrong windows driver by accident. When I run that command to uninstall it, it says no such file or directory.

Is it just supposed to be:

sudo ndiswrapper -e net8187b.inf

????

---

### Post by pjasnos on 2008-07-10
Calman - has following the instructions below your post solved your problem? Your compilation log looks like you have been compiling unpatched version. Also, are you using 32 or 64 bit ubuntu? 

> **calman said:**
> Thanks for the quick reply.  I don't get any errors but I get plenty of warnings:

```
caleb@jcpc:~/Music/rtl8187b-modified$ ./makedrv
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/caleb/Music/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.o
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_scan_wq’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:432: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_probe_resp’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:709: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1553:4: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1593:2: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_associate_retry_wq’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2251: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c: In function ‘ieee80211_softmac_init’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2473: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2474: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2475: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2476: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2477: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:2478: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1553:4: warning: #warning CHECK_LOCK_HERE
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac.c:1593:2: warning: #warning CHECK_LOCK_HERE
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_rx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_tx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_module.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_softmac_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.o
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_aes_encrypt’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:87: warning: passing argument 1 of ‘crypto_cipher_encrypt_one’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_init’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:109: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:125: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_deinit’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:141: warning: passing argument 1 of ‘crypto_free_cipher’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c: In function ‘ieee80211_ccmp_set_key’:
/home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp.c:423: warning: passing argument 1 of ‘crypto_cipher_setkey’ from incompatible pointer type
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.o
  Building modules, stage 2.
  MODPOST 5 modules
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_ccmp-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_tkip-rtl.ko
  CC      /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/ieee80211/ieee80211_crypt_wep-rtl.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/caleb/Music/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.o
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_urbsubmit’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:934: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_rx_manage_urbsubmit’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:954: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_rtx_disable’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:1255: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_tx’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2220: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2227: warning: passing argument 6 of ‘usb_fill_bulk_urb’ from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_initendpoints’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2277: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2280: warning: cast from pointer to integer of different size
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2281: warning: ISO C90 forbids mixed declarations and code
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2290: warning: cast to pointer from integer of different size
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2310: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2256: warning: unused variable ‘i’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8187_usb_deleteendpoints’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2328: warning: format ‘%d’ expects type ‘int’, but argument 2 has type ‘long unsigned int’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: At top level:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: ‘struct struct_work’ declared inside parameter list
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2435: warning: its scope is only this definition or declaration, which is probably not what you want
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_wmm_param_update’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2437: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2439: warning: initialization from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_init’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2654: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:2702: warning: assignment from incompatible pointer type
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_adapter_start’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3054: warning: unused variable ‘bInvalidWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3053: warning: unused variable ‘SupportedWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3052: warning: unused variable ‘InitWirelessMode’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3051: warning: unused variable ‘ieee’
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c: In function ‘rtl8180_irq_rx_tasklet’:
/home/caleb/Music/rtl8187b-modified/rtl8187/r8187_core.c:3769: warning: ISO C90 forbids mixed declarations and code
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_93cx6.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_wx.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_rtl8225.o
  CC [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8180_rtl8225z2.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.o
  Building modules, stage 2.
  MODPOST 1 modules
WARNING: "ieee80211_wx_get_freq" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_start_protocol" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "free_ieee80211_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wlan_frequencies" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wake_queue_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_rx_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_shortslot" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_name_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_wap" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_scan" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_rate" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_is_54g" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_stop_queue_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_softmac_stop_protocol" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rawtx" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_scan_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wpa_supplicant_ioctl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_get_beacon" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_essid" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_mode" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_mode" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_encode_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_freq" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_rate" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_wap" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_get_encode_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_wx_set_essid" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "alloc_ieee80211_rtl" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
WARNING: "ieee80211_reset_queue" [/home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko] undefined!
  CC      /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.mod.o
  LD [M]  /home/caleb/Music/rtl8187b-modified/rtl8187/r8187.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'


```

---

### Post by tjwoosta on 2008-07-10
> Roasted, you are mixing the native Linux driver and Windows driver. If you have installed native Linux driver (as copied from my instructions by tjwoosta [-X


lol.. sry pjasons i wasn't trying to steal your glory 


i was just listing the steps i took  (it just happens that the steps i took were the ones you originaly wrote):)

---

### Post by Roasted on 2008-07-10
I redid the guide, copying everything you said and pasting it. I didn't even try to retype it for the sake of avoiding errors.

This is what I got.


jason@jason-laptop:~/rtl8187b-modified$ sudo ./wlan0up
insmod: error inserting 'ieee80211_crypt-rtl.ko': -1 Invalid module format
insmod: error inserting 'ieee80211_crypt_wep-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'ieee80211_crypt_tkip-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'ieee80211_crypt_ccmp-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'ieee80211-rtl.ko': -1 Unknown symbol in module
insmod: error inserting 'r8187.ko': -1 Unknown symbol in module



jason@jason-laptop:~/rtl8187b-modified$ sudo ./wlan0down
wlan0: ERROR while getting interface flags: No such device
ERROR: Module r8187 does not exist in /proc/modules
ERROR: Module ieee80211_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_ccmp_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_tkip_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_wep_rtl does not exist in /proc/modules
ERROR: Module ieee80211_crypt_rtl does not exist in /proc/modules
jason@jason-laptop:~/rtl8187b-modified$ 


I had a wireless USB 3Com adapter plugged in to get online to get these patches and such. Would that have interfered at all?

---

### Post by tjwoosta on 2008-07-10
> I had a wireless USB 3Com adapter plugged in to get online to get these patches and such. Would that have interfered at all? 

its possible

just to make sure, why not try the process without it?

also did you get any errors at all when you ran the ./makedrv command?

---

### Post by Roasted on 2008-07-10
I don't recall getting a single error during the entire process until I did wlan0up.

I guess I have to use the USB adapter through the wget process, though. Don't I? I guess I could yank it after that, give the system a solid 30 seconds to calm down and fully disconnect, then try the following commands to see what I get.

Hmm...

---

### Post by tjwoosta on 2008-07-10
> I guess I have to use the USB adapter through the wget process, though. Don't I? I guess I could yank it after that, give the system a solid 30 seconds to calm down and fully disconnect, then try the following commands to see what I get.

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

theese two commands only download the driver and the patch 

they will be in saved in the /home/username directory 

(thats also the directory the terminal starts out in when you first open it)

hmm..  i wonder    

try just clicking my links to download rather then using the wget option  (just save to /home/yourusername)

---

### Post by pjasnos on 2008-07-12
> **tjwoosta said:**
> lol.. sry pjasons i wasn't trying to steal your glory 


i was just listing the steps i took  (it just happens that the steps i took were the ones you originaly wrote):)

I was just kidding ;) 

Roasted, those "invalid symbol" messages indicate that you probably don't have linux kernel headers (or source) matching your kernel. Having the 3Com adapter plugged in shouldn't interfere as errors you get are clearly related to kernel sources/kernel binaries mismatch... Can you provide output from uname -a ?

---

### Post by Roasted on 2008-07-12
jason@jason-laptop:~$ uname -a
Linux jason-laptop 2.6.24-19-generic #1 SMP Wed Jun 18 14:43:41 UTC 2008 i686 GNU/Linux

---

### Post by chutiloco on 2008-07-15
SOLVED?

Hi!

My laptop is a Toshiba L300-10Q with rtl8187b-->8197 code

I installed Cuervo and patch driver, but it only works with open authentification. Somebody can connect WEP or WPA wifi?

I tried to install ndiswripper (with different options and drivers)...same results.


No solution found neither in [https://sourceforge.net/forum/forum.php?forum_id=652149](https://sourceforge.net/forum/forum.php?forum_id=652149)

---

### Post by tjwoosta on 2008-07-15
i can connect to wep fine with the linux driver mentioned on the first page with the patch

i havn not tried wpa but i have read this entire thread and by the sounds of it the ndiswrapper driver works better for wpa  (although i could not get the driver to work at all)

---

### Post by shawnrgr on 2008-07-16
This post is amazing. Great input from all you guys.

I was wondering if anyone figured out how to fix the whole "no signal strength thing". I can connect fine and speeds are good. but network manager does shows 0 signal for all wifi detected.

I ran through the steps for compiling the modified realtek driver without issues and it worked off the bat without errors. Signal strength seems to be my only issue aside from wpa. 

Any tips?

---

### Post by fbhz85 on 2008-07-16
Guys,

I just came here after like hmmm... 20 hours infront of my laptop trying to put my Realtek Wireless Card RTL8187B (Recognised by Ubuntu as RTL8189B) to work and connect via ndiswrapper OR native drivers... anyone I would be happy.

I tried A LOT of ways to get it working trying with native and ndiswrapper drivers.

I will try to describe exactly what I did... it will be hard once my memory is not one of the best! LOL

**My Laptop is a: Toshiba A210-1B1**

[B]VERY IMPORTANT: This tutorial worked for a REALTEK Wireless Card Internal USB 2.0 - Chipset: RTL8187B (RTL8197B | Linux)

WPA > is not working.

WEP > Couldn`t test it.

SIGNAL STRENGTH > Working
[/B]
=== Now my tutorial  for those who still have problems with the card ===

[B]Step 1 - Housekeeping
[/B]
First thing is to do some ¨housekeeping¨:

Open Terminal and type:
> 
sudo gedit /etc/modules

Now with the file ´modules' open on gedit remove the line ndiwsrapper (if it has it).

Save and Close. 

Done? Alright!

Open Synaptics and remove ALL versions of ndiswrapper: ndiswrapper; ndiswrapper-utils and ndiswrapper-common.
*> > > Mark the option: "Mark for complete removal"*

Ok. Done? Reboot your computer.

*Ps.: if you changed something else diferent than this options listed above, remember to put it back to the original.*

Now that everything is "clean" we can continue.

==========

**Step 2 - Downloading Files**

Download the files below and save them on a folder you will remember:

ndiswrapper-common 1.52 => [http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1ubuntu1_all.deb]("http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-common_1.52-1ubuntu1_all.deb")

ndiswrapper-utils 1.9_1.52 => [http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/ndiswrapper-utils-1.9_1.52-1ubuntu1_i386.deb")

To install, double-click on the files and install it.

*_Now one of the most important steps._*

**STEP 3 - Win98 Drivers**

Download the file:

RTL8187B - Windows 98 => [http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip]("http://www.thecashplanet.com/ubuntu/rtl-win98-ndiswrapper.zip")

***_IMPORTANT:_*** Download and USE the drive above, don't use other versions. Ps.: I was looking for this file for 5 hours today and this is the right one and maybe will help a LOT of people that still experience problems with this wireless card.

Now we have to make a modification in one of the driver files.

Open the file net8187b.inf and find the following lines:

> %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB/VID_0BDA&PID_8187&REV_0200
%RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8189&REV_0200

UNDER those lines add the following line:

> %RTL8187B.DeviceDesc% = RTL8187B.ndi, USB\VID_0BDA&PID_8197&REV_0200

Now, save the file on /YOUR_USER/Desktop/win98/ (you can save wherever you want to I will use this folder to make it easier) and close the file.

**Step 4 - Installing the Driver**

Assuming that you already have ndiswrapper installed just type the following on a terminal window:

> cd ~/Desktop/win98
sudo ndiswrapper -i net8187b.inf

Assuming NO ERROS, type:

> ndiswrapper -l

You should see something like this:

> Installed ndis drivers:
  {name of driver} driver present, hardware present

or

> {name of driver} : driver installed
       device ({Chipset ID}) present

Then, type:

> sudo ndiswrapper -m

sudo modprobe ndiswrapper

Now you should add one line to the startup:

> sudo gedit /etc/modules

add ***without quotes***

> 'ndiswrapper'

in the last line.

Save and Close the 'modules' file.

Restart your computer.

**Step 5 - Connecting to the network**

Now if everything went well you should see a icon near to the clock, network icon.

Click on this and select the network you want to connect!

**Ps.:** Like I told in the beginning, SORRY but this tutorial is only to connect to networks without WPA-PSK Key. Couldn test with WEP but I`m sure with WPA Auth it will NOT work.

Well guys, that´s all and probably you are connected!

If you have any questions just let me know.

LaNCeloT_RW

IRC: chat.freenode.net | #ubuntu
[http://odeiowindows.blogspot.com](http://odeiowindows.blogspot.com)

**_Ps.: Sorry about my English!!! LOL_**

[B]>>> Credits <<<
[/B]
[http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/]("http://security.ubuntu.com/ubuntu/pool/main/n/ndiswrapper/")

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/configuring-a-rtl8187b-wireless-card-on-a-toshiba-satellite-a215-s5802-in-ubuntu-7.10-631453/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/configuring-a-rtl8187b-wireless-card-on-a-toshiba-satellite-a215-s5802-in-ubuntu-7.10-631453/")

---

### Post by pmulgaonkar on 2008-07-18
I too am having problems with the installation. I have all the linux sources and headers installed. When I run the ./makedrv file, I get:

 am stuck trying to run the ./mkdrv file.
I get an error message that says: 
rm -fr *.mod.c *.mod *.o .*.cmd *.mod.* *.ko *.o *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/prasanna/Downloaded Packages/rtl8187b-modified/ieee80211 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Packages/rtl8187b-modified/ieee80211'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2
rm -fr *.mod.c *.mod *.o .*.cmd *.ko *~
make -C /lib/modules/2.6.24-19-generic/build M=/home/prasanna/Downloaded Packages/rtl8187b-modified/rtl8187 CC=gcc modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-19-generic'
make[1]: *** No rule to make target `Packages/rtl8187b-modified/rtl8187'. Stop.
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [modules] Error 2


I dont understand what the "no rule to make target" means and how to fix it. Any help will be much appreciated.

--prasanna

---

### Post by fbhz85 on 2008-07-18
If you don't want to follow the method I posted before, try to use these files:  [http://www.thecashplanet.com/ubuntu/rtl8187b-modified-patch.zip]("http://www.thecashplanet.com/ubuntu/rtl8187b-modified-patch.zip") to install the native drivers. Use the Patch inside the .zip archive, it will correct the error when compiling the driver.

Sorry but I don't remember exactly where I got this drivers with the patch neither how to do it with native drivers.

Good Luck!

---

### Post by pmulgaonkar on 2008-07-18
[Solved]

I finally figured it out after a bunch of poking on the web. I made two changes:
1. the name of the directory where I had the driver files had a space in it. Apparently, some scripts and makefiles can get confused by this\
2. secondly I changed all the files in the directory tree with the unpacked drivers, to be executable via a chmod -R +x *

This seemed to let the script run to competion. Hope this helps anyone else trying this.

The driver did allow me to bring up the wlan. However, it keeps going down intermittently and each time it does, it prompts me for the WEP key again. Manually setting the parameters through the iwconfig commands dont allow the access point to automatically reconnect.

I am tired of debugging this adapter and planning to switch (unless someone has a hint of how to make the adapter auto recover from a dropped connection).

Thanks all. Hope this helps others.

---

### Post by fbhz85 on 2008-07-19
WHy don't you try using ndiswrapper?

WPA doesn't work, but maybe WEP will.
My connection never drops, actually it dropped ONCE in 3 days because of the router.. after that didn't drop anymore.

Ndiswrapper is not the best solution BUT at least you have a connection working...

---

### Post by pmulgaonkar on 2008-07-19
That was the first thing I tried. But there seems to be an issue with NDISWRAPPER communicating the parameters with the Windows driver. With NDISWRAPPER, I could see the network, but could never connect to it. I run WEP with a 128b hex key.

--p

---

### Post by fbhz85 on 2008-07-20
Seems this method with Ndiswrapper is not working with WPA neither WEP.

For me it works pretty nice.
Never had a problem with the connection, but I don't use WPA nor WEP.

---

### Post by onewithnature83 on 2008-07-20
Here is my solution:

[https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b](https://help.ubuntu.com/community/WifiDocs/Device/RealtekRTL8187b)

--TJ (creator)

---

### Post by Roasted on 2008-07-23
Ahh... if only the day would come where WPA is supported, I would be a fan.

Until then, XP reigns primary holder of my laptop.

---

### Post by tjwoosta on 2008-07-24
lol..

if it ever came down to it i would just buy a cheapo wifi card that has good linux support

---

### Post by batje on 2008-08-04
Alternatively, you can send an email to [email]wlanfae@realtek.com.tw[/email] and they will send you a working driver, with WEP, WPA etc.

Saves a *lot* of hassle.

---

### Post by ktrain on 2008-08-06
Unfortunately, the driver I was e-mailed from the above locks up the system at "sudo ./wlan0up"

Any other ideas?

---

### Post by swidmer on 2008-08-13
> **pjasnos said:**
> I don't know if it helps you, but I added full path to the wlan0up to my /etc/rc.local
(just before exit 0 line), so that it is loaded automatically whenever I turn on the computer.
EDIT:
So now it looks like:


I observed that if my wi-fi card is switched off when booting linux, network manager would often not see it and not configure it when I switch it on, so I put three commands into a simple script which I've got on my desktop as "fixwireless.sh" which resolves it. Here's the script, if you are interested

:( I tried this rc.local and for whatever reason it does not like to work on my machine. By any chance is there another way to force this  card to turn on during the main pc boot process - for all users?

otherwise this new driver works wonderful :)

---

### Post by kentling on 2008-09-04
I can confirm this. I had been dinking with my system for some time, trying ndiswrapper and the native driver, so I had a bit more tweaking to get the driver emailed from realtek to work.  But it works, and mostly with networkmanagerapplet (I need to do dhclient at the cli). There seems to be some kind of module conflict that is eating my CPU (I assume with a previous and now conflicting module), but the driver has me connected with WPA2, consistently (so far), and with signal strengths (and ability to switch networks) in nm-applet.

Note, you need to ./makedrv, and you get lots of errors, just like the driver at [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/).

> **batje said:**
> Alternatively, you can send an email to [email]wlanfae@realtek.com.tw[/email] and they will send you a working driver, with WEP, WPA etc.

Saves a *lot* of hassle.

---

### Post by louis_gas on 2008-09-10
I try to install the driver that i was emailed by logitech but my system freezes when i enter "sudo ./wlan0up".
Any idea? Do I something wrong?

---

### Post by BrightLibra on 2008-09-16
> **rookie2008 said:**
> Ok...

I just did the following:

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up

And it is back online again.  I am tempted to mess around with  rtl8187b-modified-jadams-2-1-2008.tar.gz from [http://www.datanorth.net/~cuervo/rtl8187b/](http://www.datanorth.net/~cuervo/rtl8187b/)   to see if it supports WPA instead of strictly WEP.
Does not work....

....tearing bits of what remains from C class out, my driver won't open, says access denied and this is ugly.

What is so weird about the Realtek driver that it is not supported by more generic attempts?

Anyone know the "force Ubuntu to look for a wireless card" command?

 - - - In advance, thanks!

---

### Post by PocketDog on 2008-09-22
The RTL8187B guide originally posted worked fine for my RTL8189B card, I didn't need fbhz85's guide (page 10). I updated recently though. Wireless network strength is accurately reported now, too. I had to use manual connection (with no WEP/WPA) though - roaming mode dropped connection after a couple of minutes

---

### Post by roccity1 on 2008-09-25
You should try the compat-wireless drivers I have a rtl8187b id 8198 I have tried it on slackware ubuntu arch and debian all worked.all you have to do is add your wireless id to the file rtl8187_dev.c if you want I can give you the files I have.

---

### Post by speed32219 on 2008-09-26
In need of a little assistance.  Trendnet TEW-424UB USB WiFi adaptor with a Realtek RTL8187B chipset  and I downloaded the current driver from here [http://trendnet.com/downloads/list_s...UBTYPE_ID=1049](http://trendnet.com/downloads/list_s...UBTYPE_ID=1049).

I have a netgear MA101 802.b 11 Mbps wireless working on Wlan0 for a couple of years but now I want to move it up to a 54Mbps link.  I installed the ndiswrapper-common  from the repositories and two other files. (ndiswrapper-util and one other, all three will show up once selected using synaptic).  I then installed the dirver winxp/2000 from the link above.

I disabled Wlan0 prior to intalling the drivers, once the drivers were installed the light on the USB wireless device lit up.  I then found it in Network tools as Wlan1, went into gnome networking and configured the unit using wep, static ip, everthing I did for the netgear wireless.  Re-booted, eveything looks good and when I go into network tools it is there but not transmitting.  No transmit or recieve packets. I just can't get it to transmit one packet.  I then tested the device in my Xp machine and all is well, it works. Put it back in the hardy machine and same results, system does see it but it will not transmit.

Any suggestions?

---

### Post by darck on 2008-10-08
If lsusb gives:
Bus 007 Device 003: ID 0bda:8198 Realtek Semiconductor Corp.

use driver modified by me (it's basicly modified driver as written in this russian site). All others doesnt work with ID :8198!
Probably module included with kernel 2.6.27 douesnt work with that id too.
[http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html](http://rapidshare.com/files/152036377/rtl8187b_linux_driver_modified_for_0bda-8198_darck.zip.html)

following installation:
./makedrv
sudo nano /etc/rc.local
add to this file: /change/path/to/correct/wlan0up
sudo apt-get install wicd
after restart chenge in wicd settings wireless interface to correct one (usually wlan0 or wlan1, can be checked by iwconfig)

run wicd, press refresh, APs should be detected. Press connect, vuala :)
&#8212;&#8212;&#8212;-
!?!?!!:
-driver compilation ./makedrv requires libraries: linux-headers- (install if gets fatal error)
-this driver probably doesn&#8217;t work with ID other than: 0bda:8198.
OR:
use (in /etc/rc.local) wlan0up in following way:
lsusb gives for example: Bus 007 Device 002: ID 0bda:8198 Realtek Semiconductor Corp., so:
wlan0up force_card=0×8189
-I couldn&#8217;t compile this driver with kernel v. 2.6.27

---

### Post by styrofoam cup on 2008-10-08
Thanks everyone.
Thanks Darck, using your method I was able to see the routers, but not able to connect to any. I do have the PID 8198 type card.

Also how is it possible to remove the driver?

Thank you.

---

### Post by speed32219 on 2008-10-26
Finaly got the Trendnet 424UB working with this chipset.  Followed pjasnos post #7 in this thread.

Thank you Pjasnos.

---

### Post by MoebusNet on 2008-10-27
Just FYI for those of you running a Virtual Machine anyway, I've got my RTL8187b wireless card/antenna combo running in Ubuntu 8.10rc (guest) in VirtualBox 2.0.2 on Ubuntu 8.04 (host using -19 kernel). Once I got the VM up and running with USB enabled, the Realtek card was detected. All I had to do was select the card in the USB menu and it worked. Sure saved a lot of work to be able to run it in Intrepid!

---

### Post by Stoupeace on 2009-04-26
> **pjasnos said:**
> Hello,

I  got it working (with WEP et al. :) ) using the second patch.

simple tut:

wget [http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz](http://www.datanorth.net/~cuervo/rtl8187b/rtl8187b-modified-dist.tar.gz)

wget [http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch](http://www.datanorth.net/~cuervo/rtl8187b/2.6.24.patch)

tar -xzvf rtl8187b-modified-dist.tar.gz

cp 2.6.24.patch rtl8187b-modified/
cd rtl8187b-modified 
patch -p1 < 2.6.24.patch
./makedrv
sudo ./wlan0up 

:) Hope this helps

When i type ./makedrv it lists a bunch of stuff ending with "2 errors".

When i type sudo ./wlan0up it lists some files that cant be read "No such file or directory"

What can i do?

Thanx!

---

### Post by tjwoosta on 2009-04-26
first what kernel is hardy using now?

i believe this thread is outdated

im not using ubuntu anymore so i cant be sure what kernel hardy has now, but i do know that the rtl8187b drivers are included in the 2.6.27 and up kernels

try this ```
sudo modprobe rtl8187
```

---

