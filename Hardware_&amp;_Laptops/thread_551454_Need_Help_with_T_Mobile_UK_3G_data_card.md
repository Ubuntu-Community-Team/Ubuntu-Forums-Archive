---
title: "Need Help with T Mobile UK 3G data card"
date: 2007-09-15
forum: Hardware &amp; Laptops
---

### Post by Sn1per on 2007-09-15
hi, 

I am new to Linux ( I am running Ubuntu 7.04), I have a 3G T-Mobile Datacard, I read alot of tutorials  but i seem to not be able to solve this problem out so i came here seeking help.

My Data Card is made by Option 
SNR: NF2369B...
Model: GT Fusion+EMEA

there is also something on the side like:
NZ1L....

So according to  the front page of Pharscape site my datacard should be this:
```



GlobeTrotter Fusion+

GlobeTrotter Fusion HSDPA
   NB or NF
   HSDPA 1.8, UMTS,EDGE, GPRS and WiFi 802.11g   Yes
   Cardbus - Nozomi interface
```

I followed the tutorial by Net42:
[http://www.net42.co.uk/os/linux/tmobile_datacard.html](http://www.net42.co.uk/os/linux/tmobile_datacard.html)

So, I downloaded the 2.21alpha driver version on pharscapse site extracted the Driver file.

I typed in terminal "make" it gave me this:

```
sniper@Home-Laptop:~/Desktop/nozomi_2.21alpha_060917$ make

Warning: Compiling for 2.6: 

make -C /lib/modules/2.6.20-15-generic/build SUBDIRS=/home/sniper/Desktop/nozomi_2.21alpha_060917 modules

make[1]: Entering directory `/usr/src/linux-headers-2.6.20-15-generic'
  
  CC [M]  /home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.o

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c: In function ‘nozomi_setup_interrupt’:

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1517: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1736:64: error: macro "INIT_WORK" passed 3 arguments, but takes just 2

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c: In function ‘nozomi_card_init’:

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1736: error: ‘INIT_WORK’ undeclared (first use in this function)

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1736: error: (Each undeclared identifier is reported only once

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1736: error: for each function it appears in.)

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:1742: warning: overflow in implicit constant conversion

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c: At top level:

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:2326: warning: initialization from incompatible pointer type

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c: In function ‘ntty_tty_init’:

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:2361: warning: assignment from incompatible pointer type

/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.c:2362: warning: assignment from incompatible pointer type

make[2]: *** [/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.o] Error 1

make[1]: *** [_module_/home/sniper/Desktop/nozomi_2.21alpha_060917] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2
```

and then i decided to go ahead and did "make install"


```
sniper@Home-Laptop:~/Desktop/nozomi_2.21alpha_060917$ make install

modprobe -r nozomi

cp -f nozomi.ko /lib/modules/2.6.20-15-generic/kernel/drivers/pci/hotplug

cp: cannot stat `nozomi.ko': No such file or directory
make: *** [install] Error 1

sniper@Home-Laptop:~/Desktop/nozomi_2.21alpha_060917$ 

```

At this stage I assumed the driver got installed and carried on with the tutorial.


So now i am at the stage of the tutorial where it says:
**Using the Nozomi Linux Driver with KPPP**

1- 

[img]http://img265.imageshack.us/img265/5675/1screenshotkpppconfigurwy5.png[/img]

2- 

[img]http://img236.imageshack.us/img236/5361/2screenshoteditaccount3uc9.png[/img]

3- 

[img]http://img96.imageshack.us/img96/7854/3screenshotcustomizepppoe2.png[/img]

4- 

[img]http://img292.imageshack.us/img292/9343/4screenshoteditmodem3gdzr1.png[/img]

5-

> Under 'Modems', add a new modem. In the modem Device tab, set the port to be /dev/modem from the drop-down menu. Make a symlink from /dev/modem to /dev/noz0.

I couldnt find **/dev/noz0** in the list so instead i put **/dev/ttyS0**.


6- 

[img]http://img170.imageshack.us/img170/4649/5screenshoteditmodemcombi9.png[/img]

When i try to connect it says "**The Modem is Busy**"

I wanted to see if the driver is installed, i figured out that its when i typed "lspci" in the terminal.

i got this back:

Command lspci

```
sniper@Home-Laptop:~$ lspci
...
...
03:00.0 Ethernet controller: Marvell Technology Group Ltd. 88w8335 [Libertas] 802.11b/g Wireless (rev 43)
03:00.1 Ethernet controller: Marvell Technology Group Ltd. Unknown device 1fb7 (rev 43)
03:00.2 Network controller: Option N.V. Qualcomm MSM6275 UMTS chip
sniper@Home-Laptop:~$ 

```

here is copy of my system log when i try to connect:

```
Sep 14 23:07:42 Home-Laptop NetworkManager: <information>^IUpdating allowed wireless network lists. 
Sep 14 23:11:39 Home-Laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Sep 14 23:11:44 Home-Laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Sep 14 23:11:52 Home-Laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
Sep 14 23:12:06 Home-Laptop dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
Sep 14 23:12:09 Home-Laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 14 23:12:10 Home-Laptop dhclient: No DHCPOFFERS received.
Sep 14 23:12:10 Home-Laptop dhclient: No working leases in persistent database - sleeping.
Sep 14 23:12:12 Home-Laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
Sep 14 23:12:15 Home-Laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 7
Sep 14 23:12:22 Home-Laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
Sep 14 23:12:30 Home-Laptop dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
Sep 14 23:12:40 Home-Laptop dhclient: No DHCPOFFERS received.
Sep 14 23:12:40 Home-Laptop dhclient: No working leases in persistent database - sleeping.

```

I desperately need help guys, i would be ever so grateful for any sort of help.

---

### Post by MrHippocampus on 2007-09-15
```

make[2]: *** [/home/sniper/Desktop/nozomi_2.21alpha_060917/nozomi.o] Error 1

make[1]: *** [_module_/home/sniper/Desktop/nozomi_2.21alpha_060917] Error 2

make[1]: Leaving directory `/usr/src/linux-headers-2.6.20-15-generic'
make: *** [default] Error 2

```

Seeing that at the end of "make" (and the Error lines in the other make output) means the make failed and the driver didnt compile, and therefore didn't get installed (which is why you don't have a /dev/noz0 etc...). So it seems you should concentrate on getting it compiling properly in the first place.

Have you tried asking about this at the pharscape forums? they will probably have more people there who would know what to do.

---

### Post by Sn1per on 2007-09-15
> **MrHippocampus said:**
> 

Seeing that at the end of "make" (and the Error lines in the other make output) means the make failed and the driver didnt compile, and therefore didn't get installed (which is why you don't have a /dev/noz0 etc...). So it seems you should concentrate on getting it compiling properly in the first place.

Have you tried asking about this at the pharscape forums? they will probably have more people there who would know what to do.

I have made the same post there, have had no replies. So, i thought i may come and seek some advice here. 

Thanks for the reply, but from looking at it here is there anything else wrong? 

ill try to compile the drivers again see if i get anything...

---

### Post by Sn1per on 2007-09-18
I had to reinstall Ubuntu because i had deleted something by mistake, and when i did and attempted to install the driver again. It worked. 

so just to let you know i got it sorted.

---

### Post by rulsky on 2007-10-25
There is an easy way to do this, if you go to this website you can download the vodafone application.

[https://forge.vodafonebetavine.net/frs/download.php/55/vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb](https://forge.vodafonebetavine.net/frs/download.php/55/vodafone-mobile-connect-card-driver-for-linux_1.0_gutsy_i386.deb)

The default is vodafone Spain...but change it to T-mobile UK 

Open  - Applications>Internet>Vodafone Mobile

Tools > Preferences

Username - user
Password - wap
preferred connection  - 3G
APN - general.t-mobile.uk

Just click connect and you are in.....

If you have anyother network card can also work just change the above info to whatever this site mentions....
[http://www.filesaveas.com/gprs.html](http://www.filesaveas.com/gprs.html)

---

