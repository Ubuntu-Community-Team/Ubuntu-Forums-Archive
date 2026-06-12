---
title: "Wi-Fi on Lenovo s10-3t with Broadcom BCM4313 [14e4:4727] (rev 01)"
date: 2010-03-07
forum: Hardware
---

### Post by AllBuntu on 2010-03-07
Lenovo put out a Netbook S10-3t, which is a tablet with a multi touch screen. Unfortunately, as of Ubuntu 10.4 Lucid Alpha 3, the Wi-Fi device is not enabled after installation of x86 Netbook

The Wi-Fi device is Broadcom BCM4313 with pci code [14e4:4727], specification here:
[http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313]("http://www.broadcom.com/products/Wireless-LAN/802.11-Wireless-LAN-Solutions/BCM4313")

There is an open source driver b43 that as of 2.6.32-15-generic does not support this device code as can be seen here:
[http://linuxwireless.org/en/users/Drivers/b43]("http://linuxwireless.org/en/users/Drivers/b43")

Broadcom provides a binary/proprietary driver that does work as can be seen here:
[http://www.broadcom.com/docs/linux_sta/README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt")

**SOLUTION**
The driver does not work due to a packaging problem. The procedure to fix it is:
A. install bcmwl-kernel-source
B. activate broadcom driver via restricted drivers

here is a detailed link:
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html]("http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html")

---

### Post by ashleynathomas on 2010-03-08
Honestly I was looking for it from quite long. I didn't badly need it but yeah of course I was looking for it to fulfil my needs. And I am happy that finally I got it. :)

---

### Post by astrobeaver on 2010-03-16
I still get "**No** [B]proprietary drivers are in use on this system".

[/B]I have a Lenovo s10-3t as well[B].
[/B]

---

### Post by xjingyu on 2010-03-17
Try to do what's written in the README file from the Broadcom website, it worked for me.

---

### Post by yuanjia1024 on 2010-03-18
Can u tell me how to install this driver . I read the readme. it makes me confused. Thanks so much.

---

### Post by xjingyu on 2010-03-18
First download the latest drivers here :
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Then launch the Terminal and do the following steps :
- apt-get install build-essential linux-headers-generic
- apt-get build-dep linux
Then go to the directory where you downloaded the drivers then :
- mkdir hybrid_wl
- cd hybrid_wl
- tar xzf ../hybrid-portsrc.tar
- make
Now you should have a file called "wl.ko".
- rmmod wl
- mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
- cp wl.ko <path-to-prev-driver>/wl.ko
Where <path-to-prev-driver> is /lib/modules/<kernel-version>/kernel/net/wireless.
Then add some default drivers to blacklist :
- rmmod b43
- rmmod ssb
- echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
- echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
Finally load drivers :
- cd <path-to-prev-driver>
- modprobe lib80211
- insmod wl.ko
- modprobe wl
Now, your Wi-Fi should work.

---

### Post by flashvoid on 2010-03-19
It seems not all machines shipped with bcm 4313.

I went throw many intructions, including ndiswrapper, bcmwl-kernel-source package and manually compile linux_sta driver from broadcomm. 

All times i was successfull with loading driver, i am able to see wlan0 interface but wifi still wont work

in dmesg i see such errors
```

[   53.433042] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-4.ucode
[   53.435960] iwlagn 0000:07:00.0: iwlwifi-6050-4.ucode firmware file req failed: -2
[   53.435976] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-3.ucode
[   53.441241] iwlagn 0000:07:00.0: iwlwifi-6050-3.ucode firmware file req failed: -2
[   53.441257] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-2.ucode
[   53.446047] iwlagn 0000:07:00.0: iwlwifi-6050-2.ucode firmware file req failed: -2
[   53.446062] iwlagn 0000:07:00.0: firmware: requesting iwlwifi-6050-1.ucode
[   53.451146] iwlagn 0000:07:00.0: iwlwifi-6050-1.ucode firmware file req failed: -2
[   53.451158] iwlagn 0000:07:00.0: Could not read microcode: -2
```
iwlist scan sayng "network is down"
```
root@void-laptop:/home/void# iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down

pan0      Interface doesn't support scanning.

```and ifconfig falling to bring wlan0 up
```
root@void-laptop:/home/void# ifconfig wlan0
wlan0     Link encap:Ethernet  HWaddr 00:23:15:06:b1:70  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

root@void-laptop:/home/void# ifconfig wlan0 up
SIOCSIFFLAGS: No such file or directory
```Finally i discover that lspci give me another pcid

```
07:00.0 0280: 8086:0089 (rev 35)
```It was my epic fail - i spend 3 days to track this diff and warn all who fail with broadcom wifi - some models shipped with intel card.



P.S.
and according to this [bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/532451") intel still have no open driver for this card. So be patient.

---

### Post by dbld on 2010-07-09
Same problem following 10.4 upgrade no wifi.

Using Lenovo S10e.
```
05:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
        Subsystem: Broadcom Corporation Device 04b5

```

Followed update procedure as found in broadcom [README.txt]("http://www.broadcom.com/docs/linux_sta/README.txt") file:
[http://www.broadcom.com/docs/linux_sta/README.txt](http://www.broadcom.com/docs/linux_sta/README.txt)
```

Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate

Sometimes the driver does not show up in the Hardware Drivers choices.  In
this case, try reintalling the driver from the GUI or shell like this:

From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the 
Reload button in the upper left corner of Synaptic to refresh your index then 
search for and reinstall the package named bcmwl-kernel-source.

From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source

In either GUI or text case, after reinstalling, reboot your machine.

Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.
```

All working well following reboot.

---

### Post by bobttt on 2010-09-28
Same **BCM4313 chipset** found in the new **HP Mini 210 **with Intel NM10 chipset (1.86GHz Atom N475).

Same instructions to install the wifi driver. Tested working with WPA2 access point.

---

### Post by Bodsda on 2010-11-01
I have a HP Mini 210 also. To get wifi working I ran
```

apt-cache search bcmwl

```

This returned two packages.
```

bcmwl-modaliases
bcmwl-kernel-source

```

After installing the kernel source, and giving it a reboot, wifi worked without any issues.

Thanks,
Bodsda

---

### Post by topbayder on 2010-12-05
just got ubuntu studio and having the same problem on my DELL laptop. i can't hardwire to a router. is there a way i can get the packages required some other way and USB stick them accross to my DELL?

---

### Post by soad6 on 2010-12-27
[SIZE="6"]**FIXED!! FIXES ISSUES WITH BCM 4313 & 4312 if you run Ubuntu 10.10 and are on 2.6.35-24 gen**[/SIZE]

 if you updated to kernel 2.6.35.-24 gen
please revert to any version prior to this... 
then uninstall the bcmwl-kernel-source package
and install the b43-fwcutter package
and install the firmware-b43-lpphy-installer package
then reboot.
confirmed by 5 ppl this works.

command as follows below

sudo apt-get remove bcmwl-kernel-source
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
sudo reboot
...
if this doesn't work for you please let me know... also if this works
with anything other then these two chipsets please let me know... thanx

---

### Post by tetebueno on 2010-12-31
Didn't work for me.

I'm running an HP G42-364LA with a Broadcom 4727 (BCM4313).

Installing b43-fwcutter via apt-get, I get the 012 while firmware-b43-lpphy-installer requires the 013. I got the 013 version from debian.packages.org, but when trying to install again the b43-lpphy-installer I got the following error in the post install script:

```
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--install):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer

```

... according to [this chart]("http://wireless.kernel.org/en/users/Drivers/b43#Known_PCI_devices"), the chip is the appropriate one.

I've already tried installing the open source driver and no luck, the Broadcom driver and I package installer crashes, I've also tried using Ndiswrapper but no luck here either.
If anybody can give me a hint here, you'll be saving a brand new laptop.
Cheers.

---

### Post by tetebueno on 2011-01-01
Forgot to mention, this is on a Lucid (2.6.35-22).

---

### Post by teklife on 2011-01-04
total noob idiot here, but has anyone reported this problem to the kernel maintainers? i sorta know what backports are, but is there an inverse of that? bringing the older drivers or whatever it is that worked fine in the older kernel into the latest? 

i have this same problem on my girl's s10-3t which i couldn't solve except by reverting to the older kernel(2.6.35-23) and deleting 2.6.35-24. how will i know when it's ok to update again? or should i just always stay using this kernel now?

---

### Post by fiacobelli on 2011-01-07
Hi, 
My laptop (HP dm1z) lspci says:
 Network controller: Broadcom Corporation BCM4313 802.11b/g LP-PHY

but the installation of firmware-b43-lpphy-installer fails.

> 
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)



Any ideas?

---

### Post by tetebueno on 2011-01-09
Sorry to disapoint everyone, but I solved my issue starting from scratch on a 10.04 and updating everything.
Cheers.

---

### Post by Chefarov on 2011-01-17
Same problem like tetebueno here. Same output

Card:
BCM4313 LP-PHY

Ubuntu 10.10 - 2.6.35-22-generic


Hava also tried the STA driver , both(compiling the package mentioned above and installing the package from restricted drivers).

---

### Post by ruwens on 2011-01-20
It worked fine for me (on a S10-Netbook without Tablet) by activating the Broadcom-STA-driver on netbook edition of 10.04. version.

---

### Post by buchta on 2011-02-13
hi,
I have asus 1215n, but with Broadcom bcm4313 LP-PHY -it's working fine with the proprietary driver, but only for wi-fi -my issue is that I cannot get the bluetooth part working -anyone know what's going on and how to fix it?

edit: SOLVED: [http://ubuntuforums.org/showthread.php?t=1686980&page=2](http://ubuntuforums.org/showthread.php?t=1686980&page=2)

---

### Post by david.flights on 2011-03-25
Ubuntu 10.10, EEEPC 1015PE, Broadcom 4313 x 4272

After trying:

sudo apt-get install bcmwl-kernel-source


I get:


Building dependency tree       
Reading state information... Done
bcmwl-kernel-source is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by www.rzr.online.fr on 2011-10-16
hi

can you update this status of S103t on oneiric  ?

-- 
[http://rzr.online.fr/q/broadcom](http://rzr.online.fr/q/broadcom)

---

### Post by AllBuntu on 2011-10-16
This worked for me in 11.04. I updated yesterday to 11.10 and it does not work. There are more serious things broken in 11.10, too, so I will file bugs eventually. I think Wi-Fi troubles might be causing a 30 second delay on resume. Here is how an upgrade configures it: 

foxyboy@s10t:~$ lspci -k -d 14e4:4727
07:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
	Subsystem: Broadcom Corporation Device 0510
	Kernel driver in use: bcma-pci-bridge
	Kernel modules: wl, bcma, brcmsmac

---

### Post by AllBuntu on 2011-10-16
ifconfig -a does not list the interface, so driver not work

---

### Post by AllBuntu on 2011-10-16
The driver configuration does not come up right. I filed a bug:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/875892)

fix is:

create a one-line file /etc/modprobe.d/blacklist-bcma
blacklist bcma

then reboot: wi-fi now works
foxyboy@s10t:~$ lspci -k -nn -d 14e4:4727
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
 Subsystem: Broadcom Corporation Device [14e4:0510]
 Kernel driver in use: wl
 Kernel modules: wl, bcma, brcmsmac

---

### Post by demonboy on 2011-10-28
Hi Allbuntu,

I have the same Broadcom card but I'm still struggling, even after creating the blacklist-bcma file. In fact it would be fair to say I am pulling what little hair I have out over this problem! If you would be so kind, could you confirm for me:

1) Do you also have a file in the same modprobe.d folder called 'blacklist-bcm43.conf'?
2) If so, does it look like this?
```

blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx

```
3) In Ubuntu Software Centre, if you type in 'Broadcom', what files do you have installed? Do you have just 'bcmwl-kernel-source' and 'b43-fwcutter'?
4) Are you running the 64bit version of Ubuntu?

I'm hoping the answers to this will help me sort this problem out once and for all. Thanks.

---

### Post by demonboy on 2011-10-28
It's ok, I ended up commenting out ALL drivers relating to the Broadcom card.

---

### Post by knowNothing23 on 2013-02-10
> **Bodsda said:**
> I have a HP Mini 210 also. To get wifi working I ran
```

apt-cache search bcmwl

```

This returned two packages.
```

bcmwl-modaliases
bcmwl-kernel-source

```

After installing the kernel source, and giving it a reboot, wifi worked without any issues. 

Thanks,
Bodsda

After looking for days! You saved me with these sentences. Oddly enough, rebooting disabled all the accomplishments. Now, I am without wireless again. Could it be some hardware conflict? Anyone can help?

---

