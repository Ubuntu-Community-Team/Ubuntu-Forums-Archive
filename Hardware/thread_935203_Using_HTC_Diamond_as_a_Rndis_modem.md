---
title: "Using HTC Diamond as a Rndis modem"
date: 2008-10-01
forum: Hardware
---

### Post by StevenHarper on 2008-10-01
Hi, after a small amount of investigation I have finally got the HTC Diamond working as a Rndis modem over the USB port.

What this means is that you can use the Internet connection sharing function of the Diamond to get a computer onto the Internet using the H or G phone data connection.

Please note that the first steps of this guide will work for any ACTIVESYNC connected HTC phone that has the Connection Sharing (it's in the Connection Manager on other HTC phones)

Obviously using data on your mobile costs money so be aware of this and make sure you have a package that has reasonable charges.

finally I have only tested this on an ORANGE HTC Diamond in the UK.

The reason you have to modify the source is that if you don't the rndis fails with an error like (this is seen in the /var/log/syslog)

```
[355.215268] rndis_host 5-3:1.0: dev can't take 1558 byte packets (max 1536)
```


*you need a working internet connection to set this up*

[LIST=1]
[*]Install Pre-requisites
[*]Get the Source
[*]Modify the source (Diamond only)
[*]Compile and make and install
[*]Start the Internet Connection Sharing
[*]Plug in the Phone (USB)
[/LIST]

Once you have done steps 1-4 you will only ever need to do steps 5 & 6 to get re-connected.



**Step 1 - Install Pre-requisites**

open a terminal (use same terminal in next steps)

```
sudo apt-get install subversion
```

**Step 2 - Get the Source**

```
svn co http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite
cd usb-rndis-lite/
```

**Step 3 - Modify the source (Diamond only)**

```
gedit rndis_host.c
```

on line 524, find this bit

```
       if (tmp < dev->hard_mtu) {
		dev_err(&intf->dev,
			"dev can't take %u byte packets (max %u)\n",
			dev->hard_mtu, tmp);
		goto fail;
	}
```

change it to this

```
       if (tmp < dev->hard_mtu) {
		dev_err(&intf->dev,
			"dev can't take %u byte packets (max %u)\n",
			dev->hard_mtu, tmp);
		retval = -EINVAL;  
                /* goto fail;*/
	}
```  

save the file

**Step 4 - Compile and make and instal**l

```
make
sudo ./clean.sh
sudo make install
```

**Step 5 - Start the Internet Connection Sharing**

On OLD Tytn II's open Comm Manager on your phone and click on the Internet Sharing Now make sure USB is selected and choose connect

On Diamonds it's a seperate program called *Internet Connection Sharing*

**Step 6 - Plug in the Phone (USB)**

Plug the phone in, once the Phone has a data connection the Internet connection sharing will say connecting, then connected.

If this takes a while the dhcp may timeout and you will have to run the following command.

```
sudo dhclient
```

You should then see that you have an ip on the rndis device

```
ipconfig
```


Thanks for this fix goes to
[http://www.solariz.de/blog/91-htc-touch-wm6-internetsharing-fuer-linux](http://www.solariz.de/blog/91-htc-touch-wm6-internetsharing-fuer-linux)

---

### Post by jazzroy on 2008-10-01
hi steven,
i'm evaluating the diamond as my next smartphone, but i have some unresolved questions.

do you easily sync agenda-calendar with ubuntu?

can you use it as external storage?

if yes, how you can do that? wifi, bluetooth, usb?

and finally, all reviews talk about really short battery life, sluggish interface and overheating, what's your opinion using it daily?

thanks a lot!

---

### Post by bimmerd00d on 2008-10-01
I get it to connect, however i can't get an IP Address when i do sudo dhclient.  What gives?!?!  I'm not getting the error anymore though :)  Using an HTC Kaiser using WM 6.1 and ICS.  Also, think this update to rndis will make its way into Intrepid Ibex?

---

### Post by StevenHarper on 2008-10-02
> **jazzroy said:**
> hi steven,
i'm evaluating the diamond as my next smartphone, but i have some unresolved questions.

do you easily sync agenda-calendar with ubuntu?

can you use it as external storage?

if yes, how you can do that? wifi, bluetooth, usb?

and finally, all reviews talk about really short battery life, sluggish interface and overheating, what's your opinion using it daily?

thanks a lot!

I have not tried the sync functionality.

Yes you can choose it to mount as a USB2 drive (the phone can't see it when its mounted)

This can only be done over USB

The speed is improved with the ROM update
ORANGES is here

[http://www1.orange.co.uk/diamond/RUU_Diamond_HTC_WWE_1.93.405.1_Radio_Signed_Diamond_52.29.25.12_1.00.25.05_Ship.exe](http://www1.orange.co.uk/diamond/RUU_Diamond_HTC_WWE_1.93.405.1_Radio_Signed_Diamond_52.29.25.12_1.00.25.05_Ship.exe)

DONT use that if your not using UK ORANGE DIAMOND HTC

They do seem to get warm, but I have not heard of a overheating one.

Daily use, I prefer my HTC TytnII, the Diamond has  a great screen but I NEED a keyboard, I will probably get the Diamond Pro (With Keyboard) in the long run.

---

### Post by jazzroy on 2008-10-02
thanks for the reply!

just one more question, battery life is really an issue as someone says?

thanks again!

---

### Post by hmu on 2008-10-08
> **jazzroy said:**
> thanks for the reply!

just one more question, battery life is really an issue as someone says?

thanks again!

I'd say depends. If you just use as a normal phone, you can get three days. If you use GPS or WiFi or generally play around with it a lot, it needs to be charged every night. The good thing is that the phone charges when connected to usb (in fact, the charger itself is nothing but a usb-port).

I sync my contacts and calendar following [this guide]("http://www.synce.org/moin/SynceWithUbuntu"). It generally works ok, most of the time. There even is a gvfs-plugin, so that you can browse the storage of the phone, even if it's not in usb-mode (when in usb-mode you can't access the internal storage from the phone - bit of a nuisance when you've got software installed there).

Generally, I like the phone a lot. You have to get used with the interface, but after that it's really neat. And speed improved a lot with the last ROM-Upgrade, which every supplier should be offering up to now.

---

### Post by kangol69 on 2008-11-07
So have any of you gotten rndis to work under intrepid. I had it working fine under hardy but I've gotten no where in ibex. What's weird is that I can get it to resolve domain names but I still can't reach the internet. Like I can type:
```
ping yahoo.com
```
and it will say:
```
PING yahoo.com (206.190.60.37) 56(84) bytes of data.
```
So DNS is working but nothing else. Which leads me to believe it's a problem with some sort of routing setting.  :confused:

---

### Post by kangol69 on 2008-11-10
Got it working. Turns out it was a problem with the phone. I was running a custom ROM on it and something must have been messed up. Any one know how to get back the original modules for rndis that came with intrepid?

---

### Post by bluebirdsolutions on 2008-11-22
Many thanks for this solution! I am using a HTC Touch Diamond in Swedish network Hi3G and it's working just fine with the help from this post. 

Great job and thanks again!

---

### Post by bharris25 on 2008-12-02
> **jazzroy said:**
> hi steven,
i'm evaluating the diamond as my next smartphone, but i have some unresolved questions.

do you easily sync agenda-calendar with ubuntu?

can you use it as external storage?

if yes, how you can do that? wifi, bluetooth, usb?

and finally, all reviews talk about really short battery life, sluggish interface and overheating, what's your opinion using it daily?

thanks a lot!

I love my diamond but when i bought it from Sprint the battery life did suck,but I put one of Juicys roms on it and the problem was solved


i

---

### Post by loudnlownoma on 2008-12-04
I've got the Verizon xv6900 - Verizon's version of the original HTC Touch (Vogue I believe under HTC's labeling).  Have ben trying to get this working but keep running into a problem...  The phone is my primary source of Internet connection at my home  :(

In a last-ditch effort the other night I used XP (where the connection works fine) to download the Subversion package and dependencies to get it installed properly.  The problem is I cant figure out how to get it to work without going to the site.  I have gone to the site and downloaded everything in the directory listed in the URL, but can't figure out a way to get subversion to look in a folder on the local drive instead.  Is this possible, or will it absolutely have to be connected to the Internet to get this connection working?

---

### Post by StevenHarper on 2008-12-05
The subversion command just downloads the files onto your hard disk

If you do that on Another computer, then copy them to the pc you want to install the package on, then follow the steps after that.

Steve

---

### Post by loudnlownoma on 2008-12-05
> **StevenHarper said:**
> The subversion command just downloads the files onto your hard disk

If you do that on Another computer, then copy them to the pc you want to install the package on, then follow the steps after that.

Steve

I tried running the make command from the next step but it errors out, even when I move to the folder the files are currently saved.  I have my laptop with me here at work today, so hopefully the wireless card is still working after the initial installation and I can get it squared away that way.  If not, I'll try this again while home and report back the exact error it gives me.

---

### Post by GhentK on 2008-12-26
I did all steps up to compiling from source and installing. When I "make", I get the following error, though:

```
user@computer:~/usb-rndis-lite$ make

make -C /lib/modules/2.6.27-8-eeepc/build SUBDIRS=/home/hcs/usb-rndis-lite modules

make: *** /lib/modules/2.6.27-8-eeepc/build: No such file or directory.  Stop.

make: *** [default] Error 2
```

I get the feeling that I'm making some awfully simple mistake, but I just can't think of what I'm doing wrong at this time of day, so if any of you can see it, any help would be appreciated. :)

Oh, and I'm running Eeebuntu with the modified Array kernel, in case it means something.

---

### Post by StevenHarper on 2008-12-29
It must be your modified Array Kernel.

Have you installed the Build essentials and the headers for your kernel.

```
sudo apt-get install build-essential
```

I have a friend who has these instructions working on a 701 and 901 eee pc.

---

### Post by razorbud on 2008-12-31
Hi,

I too have eeebuntu installed, I get exactly the same error even if the build-essentials are installed :(

its normaly not a problem, but im at home without a wired internet!!!

lol, thanks for the help so far.

---

### Post by GhentK on 2009-01-27
Alright, my boyfriend and I made it worked at long ******* last!

This worked on my Eee 1000 with Eeebuntu 2.0 BASE. I can't guarantee it to work on your computer, but you can try it if you feel bold and post the output if it doesn't work. :)

Follow steps 1-3 of Steven Harper's guide.

Open a terminal and write:

```
sudo apt-get install linux-headers-`uname -r`
cd /lib/modules/`uname -r`
sudo ln -s /usr/src/linux-headers-`uname -r` build
cd $HOME/usb-rndis-lite
make
sudo ./clean.sh
sudo make install
```

After this, continue the guide from step 5.

Of course you can combine my first line with step 1 of the guide to make the whole installation more concise. But if you don't know what I'm talking about, it's probably best to just follow it by the book. :)

---

### Post by splashhtc on 2009-03-13
hey...that works fine with the htc diamond...and the firestarter also recognizes it very well...actually the connection speed is much more faster than using the sim card with the original usb dongle which keeps heating up etc etc


as for the people asking bout the diamond...hmm..

well it does infact have a very bad battery life...doesnt even stay for one whole day as some say in there posts...and mine is only 2 months old...

its a cool looking mobile and it has a very fast connection...it does reach the 7 mb limit it says about in the manual...

as for the heating up...well i used to be a bit confused thinking its gonna blow up or something but it quite ok now...

u can download the radio software and turn of the 3g and just use edge if u dont need alot of speed but hell i dont care...i just use the diamond as a modem and as a pocket pc...dont use it as a mobile phone....i use a k8ooi which is way better....

---

### Post by kangol69 on 2009-03-13
The battery life is bad with a stock phone but you can flash it with user modified roms and with updated radios and the battery life will improve signifigantly. Check out [http://forum.xda-developers.com/forumdisplay.php?f=428](http://forum.xda-developers.com/forumdisplay.php?f=428) or [http://forum.ppcgeeks.com/forumdisplay.php?f=66](http://forum.ppcgeeks.com/forumdisplay.php?f=66)

The ppcgeeks one is if you have a CDMA Diamond (Sprint) and xda is mainly GSM.

---

### Post by buddy123 on 2009-05-05
Im having difficulties downloading the usb-rndis-lite.
Im using ubuntu 9.04,
When I do that command in the terminal I get this:

svn co [http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
svn: OPTIONS of 'http://synce.svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite': could not connect to server ([http://synce.svn.sourceforge.net](http://synce.svn.sourceforge.net))
eran@eran:~$ svn co [https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite](https://svn.sourceforge.net/svnroot/synce/trunk/usb-rndis-lite)
Error validating server certificate for 'https://svn.sourceforge.net:443':
 - The certificate hostname does not match.
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 11 Nov 2008 20:25:27 GMT until Mon, 11 Jan 2010 20:25:27 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: 04:b2:70:e9:ba:cf:70:fc:e8:8a:22:86:14:13:51:97:1b:6a:de:38
(R)eject, accept (t)emporarily or accept (p)ermanently? t
svn: PROPFIND of '/svnroot/synce/!svn/bc/3765/trunk/usb-rndis-lite': could not connect to server ([https://svn.sourceforge.net](https://svn.sourceforge.net))


Is there a way to install the package from syntaptic or something? Or maybe other way to get those files?

---

### Post by e1luca on 2009-05-12
Is this solution valable still for Ubuntu 9.04(64bit)? As I understand the code has to be modiffy because of the error "dev can't take 1536 byte packets (max 1536)". In var/log.syslog I get the error but the code seems to correct this automaticly:
```
May 12 12:46:12 vaio kernel: [ 3238.186160] rndis_host 2-3:1.0: dev can't take 1536 byte packets (max 1536), adjusting MTU to 1478
```

the conection seems to fail at :
```

May 12 12:46:27 vaio kernel: [ 3252.656076] eth1: no IPv6 routers present
```

Tnx for answering

here is the full val/log/syslog:
```
May 12 12:46:12 vaio kernel: [ 3237.852097] usb 2-3: new high speed USB device using ehci_hcd and address 15
May 12 12:46:12 vaio kernel: [ 3237.993044] usb 2-3: configuration #1 chosen from 1 choice
May 12 12:46:12 vaio kernel: [ 3238.186160] rndis_host 2-3:1.0: dev can't take 1536 byte packets (max 1536), adjusting MTU to 1478
May 12 12:46:12 vaio kernel: [ 3238.196400] rndis_host 2-3:1.0: RNDIS_MSG_QUERY(0x00010202) failed, -47
May 12 12:46:12 vaio kernel: [ 3238.216203] eth1: register 'rndis_host' at usb-0000:00:1d.7-3, RNDIS device, 80:00:60:0f:e8:00
May 12 12:46:12 vaio nm-system-settings:    SCPlugin-Ifupdown: device added (udi: /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00, $
May 12 12:46:12 vaio NetworkManager: <info>  (eth1): new Ethernet device (driver: 'rndis_host')
May 12 12:46:12 vaio NetworkManager: <info>  (eth1): exported as /org/freedesktop/Hal/devices/net_80_00_60_0f_e8_00
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): device state change: 1 -> 2
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): bringing up device.
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): preparing device.
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): deactivating device (reason: 2).
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): carrier now ON (device state 2)
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): device state change: 2 -> 3
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) starting connection 'Auto eth1'
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): device state change: 3 -> 4
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): device state change: 4 -> 5
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) successful.
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) scheduled.
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) started...
May 12 12:46:17 vaio NetworkManager: <info>  (eth1): device state change: 5 -> 7
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Beginning DHCP transaction.
May 12 12:46:17 vaio NetworkManager: <info>  dhclient started with pid 7512
May 12 12:46:17 vaio NetworkManager: <info>  Activation (eth1) Stage 3 of 5 (IP Configure Start) complete.
May 12 12:46:17 vaio dhclient: Internet Systems Consortium DHCP Client V3.1.1
May 12 12:46:17 vaio dhclient: Copyright 2004-2008 Internet Systems Consortium.
May 12 12:46:17 vaio dhclient: All rights reserved.
May 12 12:46:17 vaio dhclient: For info, please visit http://www.isc.org/sw/dhcp/
May 12 12:46:17 vaio dhclient:
May 12 12:46:17 vaio dhclient: wmaster0: unknown hardware address type 801
May 12 12:46:17 vaio dhclient: wmaster0: unknown hardware address type 801
May 12 12:46:17 vaio NetworkManager: <info>  DHCP: device eth1 state changed normal exit -> preinit
May 12 12:46:17 vaio dhclient: Listening on LPF/eth1/80:00:60:0f:e8:00
May 12 12:46:17 vaio dhclient: Sending on   LPF/eth1/80:00:60:0f:e8:00
May 12 12:46:17 vaio dhclient: Sending on   Socket/fallback
May 12 12:46:18 vaio dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
May 12 12:46:18 vaio avahi-daemon[2994]: Registering new address record for fe80::8200:60ff:fe0f:e800 on eth1.*.
May 12 12:46:18 vaio dhclient: DHCPOFFER of 192.168.0.102 from 192.168.0.1
May 12 12:46:18 vaio dhclient: DHCPREQUEST of 192.168.0.102 on eth1 to 255.255.255.255 port 67
May 12 12:46:19 vaio dhclient: DHCPACK of 192.168.0.102 from 192.168.0.1
May 12 12:46:19 vaio NetworkManager: <info>  DHCP: device eth1 state changed preinit -> bound
May 12 12:46:19 vaio NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) scheduled...
May 12 12:46:19 vaio NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) started...
May 12 12:46:19 vaio NetworkManager: <info>    address 192.168.0.102
May 12 12:46:19 vaio NetworkManager: <info>    prefix 24 (255.255.255.0)
May 12 12:46:19 vaio NetworkManager: <info>    gateway 192.168.0.1
May 12 12:46:19 vaio NetworkManager: <info>    nameserver '192.168.0.1'
May 12 12:46:19 vaio NetworkManager: <info>    domain name 'malx.rdscv.ro'
May 12 12:46:19 vaio NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) scheduled...
May 12 12:46:19 vaio NetworkManager: <info>  Activation (eth1) Stage 4 of 5 (IP Configure Get) complete.
May 12 12:46:19 vaio NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) started...
May 12 12:46:19 vaio avahi-daemon[2994]: Joining mDNS multicast group on interface eth1.IPv4 with address 192.168.0.102.
May 12 12:46:19 vaio avahi-daemon[2994]: New relevant interface eth1.IPv4 for mDNS.
May 12 12:46:19 vaio avahi-daemon[2994]: Registering new address record for 192.168.0.102 on eth1.IPv4.
May 12 12:46:19 vaio dhclient: bound to 192.168.0.102 -- renewal in 128881 seconds.
May 12 12:46:20 vaio NetworkManager: <info>  (eth1): device state change: 7 -> 8
May 12 12:46:20 vaio NetworkManager: <info>  Policy set 'Auto eth1' (eth1) as default for routing and DNS.
May 12 12:46:20 vaio NetworkManager: <info>  Activation (eth1) successful, device activated.
May 12 12:46:20 vaio NetworkManager: <info>  Activation (eth1) Stage 5 of 5 (IP Configure Commit) complete.
May 12 12:46:20 vaio kernel: [ 3246.300012] CE: hpet increasing min_delta_ns to 22500 nsec
May 12 12:46:22 vaio ntpdate[7570]: adjust time server 91.189.94.4 offset 0.005128 sec
May 12 12:46:27 vaio kernel: [ 3252.656076] eth1: no IPv6 routers present

```

---

### Post by Shwan.c on 2009-05-22
The change will work, I have tested it on Diamond, and today on my new Xperia X1 , you should patch it as well, I think the problem is the corrected value is not ok , it should be the maximum value !

---

### Post by Bazon on 2009-06-05
Thanks, works great with my HTC Touch Dual.
But only as long as I don't use synce-gvfs to browse my files on the mobilephone, it seems as if one has to decide between internet sharing and file browsing.

---

### Post by Andysan on 2009-06-14
Hi Steven,

Just wanted to say thanks for posting this - everything fell into place once i modified the source code!

Can anyone explain what this actually does though please?

Thanks.

---

### Post by MasBlaMan on 2009-08-12
So if one does just:

sudo ifconfig eth1(or what ever your rndis is) mtu 1000

I did it and it worked.

Before I just up-ed and dhclient eth1 and I could ping google, but I could not open the site in a browser.

There appears to be a problem in the packet size that rndis accepts. Ill look into it(ieee802.3 vs ethernet ?).

---

### Post by Milan Knizek on 2009-08-12
Thanks StevenHarper for sharing the source code fix, I have spent quite a lot of time trying to find out what's wrong with my HTC Touch HD and ICS.
I hope it gets ever into kernel tree some time (I use Ubuntu 9.04 Jaunty).

---

### Post by pi4r0n on 2009-11-06
Hello Guys

I have installed Ubuntu 9.10 (Karmic Koala) and it's seems that this solution does not work any more ??

Do you have any idea how to fix it? :(

Ta

pi4r0n

---

### Post by deejaypee on 2009-11-07
This solution has worked perfectly in the past, thanks for the info.
I also have upgraded to 9.10 and now can't get the HTC Diamond to work as a USB modem. 
I would appreciate any help in resolving this.
thanks

---

### Post by a_kemper on 2009-11-11
I have the same problem with 9.10, while I end up at the point when trying to recompile the rndis stuff as initially described:

root@netbook:~/usb-rndis-lite# make
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/root/usb-rndis-lite modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/usb-rndis-lite/usbnet.o
/root/usb-rndis-lite/usbnet.c: In function ‘usbnet_probe’:
/root/usb-rndis-lite/usbnet.c:1199: error: ‘struct net_device’ has no member named ‘change_mtu’
/root/usb-rndis-lite/usbnet.c:1200: error: ‘struct net_device’ has no member named ‘get_stats’
/root/usb-rndis-lite/usbnet.c:1201: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/root/usb-rndis-lite/usbnet.c:1202: error: ‘struct net_device’ has no member named ‘open’
/root/usb-rndis-lite/usbnet.c:1203: error: ‘struct net_device’ has no member named ‘stop’
/root/usb-rndis-lite/usbnet.c:1205: error: ‘struct net_device’ has no member named ‘tx_timeout’
make[2]: *** [/root/usb-rndis-lite/usbnet.o] Fehler 1
make[1]: *** [_module_/root/usb-rndis-lite] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Fehler 2

Obviously there are incompatibilities between the current kernel (headers) and the proposed version of usb-rndis-lite. Thus, is there anyone who can help to fix this particular issue?

Thx,
Andreas

PS: "ping" and "nslookup" yet work without any modification, but that's obviously not all..

---

### Post by LordLandon on 2009-11-11
Running ```
wget -qO- http://sprunge.us/BSjF | patch

``` before 'make' will fix the compilation problem.

---

### Post by a_kemper on 2009-11-11
Thanks first of all for the quick and helpful reminder on the patch. It fixed the compilation problem, but after all things in the end got worse compared to the original kernel module.

Basically after installing the compiled modules the following things changed:

o "eth1" became "rndis0"
o MTU further reduced from 1478 to 1394 (when SE Xperia is online), alternatively 8050 (!)
o "nslookup" which has been working with "eth1" doesn't work anymore after the update

Thus in a way the initial version providing "eth1" when Xperia was plugged via USB was more successful. From this trial I took a little capture during trying to load Google in Firefox.

Thx again,
Andreas

---

### Post by oponto on 2009-11-12
Works on my HTC Touch Diamond with Ubuntu 9.04, the basic tutorial (no extensional tutorial) , directly, exactly as you described.

Epic Job !
Thanks !

---

### Post by Rihards on 2009-11-14
Thanks,it worked

---

### Post by silenthatred on 2009-12-23
> **a_kemper said:**
> I have the same problem with 9.10, while I end up at the point when trying to recompile the rndis stuff as initially described:

root@netbook:~/usb-rndis-lite# make
make -C /lib/modules/2.6.31-14-generic/build SUBDIRS=/root/usb-rndis-lite modules
make[1]: Betrete Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /root/usb-rndis-lite/usbnet.o
/root/usb-rndis-lite/usbnet.c: In function ‘usbnet_probe’:
/root/usb-rndis-lite/usbnet.c:1199: error: ‘struct net_device’ has no member named ‘change_mtu’
/root/usb-rndis-lite/usbnet.c:1200: error: ‘struct net_device’ has no member named ‘get_stats’
/root/usb-rndis-lite/usbnet.c:1201: error: ‘struct net_device’ has no member named ‘hard_start_xmit’
/root/usb-rndis-lite/usbnet.c:1202: error: ‘struct net_device’ has no member named ‘open’
/root/usb-rndis-lite/usbnet.c:1203: error: ‘struct net_device’ has no member named ‘stop’
/root/usb-rndis-lite/usbnet.c:1205: error: ‘struct net_device’ has no member named ‘tx_timeout’
make[2]: *** [/root/usb-rndis-lite/usbnet.o] Fehler 1
make[1]: *** [_module_/root/usb-rndis-lite] Fehler 2
make[1]: Verlasse Verzeichnis '/usr/src/linux-headers-2.6.31-14-generic'
make: *** [default] Fehler 2

Obviously there are incompatibilities between the current kernel (headers) and the proposed version of usb-rndis-lite. Thus, is there anyone who can help to fix this particular issue?

Thx,
Andreas

PS: "ping" and "nslookup" yet work without any modification, but that's obviously not all..

If you are using 9.10, you don't need to recompile rndis, as it will work out of the box.  You do however need to manual adjust the mtu of your connection your phone uses, eth1 in my case, from automatic to 1000 (which is what it was set to in the fix).  I'm wondering if other values will work, but I can deal with a working connection for now.

---

### Post by silenthatred on 2009-12-23
Well I answered my own question...I figured out my max mtu is 1394, so changed it to that and it works.  I'm on AT&T, but I would imagine this would probably vary by provider and connection method.  If you don't know how to figure out your max mtu, google it, there are guides.

---

### Post by maestrobwh1 on 2010-04-01
Lucid 10.04 with HTC Touch Pro 2 Verizon

I got the package to build.  It still does not show up in "ifconfig" and I manually modprobed the drivers and then ran depmod -a and the modules do show up in lsmod

Phone is in modem mode.  

I tried bringing it up as "ifconfig rndis0 up"

Nothing.

sudo lshw -C network only shows my ethernet and wireless device

Fortunately it works in XP running VirtualBox with the Verizon software;-0

Of course, that means that I have to use XP sometimes:-(

---

### Post by cdrik on 2010-08-03
Hi,
I had the same problem of rndis with max 1536 with my htc touch hd and my ubuntu 10.04. I solve the problem by set the MTU to 1394 on my eth2 connection and now my phone works as a modem (with a correct user agent).

To set the mtu, i use the interface of connection manager on my task bar, choose "Modify connection", Select your connection (in my case eth2) and specify a correct mtu.
I need to deconnect and reconnect my usb cable and now all works. It's more easy than recompile rndis.

---

### Post by supernova79 on 2010-08-10
HY i have some problem with my htc universal and ubuntu 10.04.
When i connect my device ubuntu works fine and add a new connection in networkmanager (eth1).
Then i modify the mtu (1394) then i active che modem on my device (vmodem wm5) and the device disconnect automatically..
Any ideas.?
Thank you

---

