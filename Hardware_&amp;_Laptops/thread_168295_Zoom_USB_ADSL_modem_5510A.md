---
title: "Zoom USB ADSL modem 5510A"
date: 2006-04-30
forum: Hardware &amp; Laptops
---

### Post by mesh2005 on 2006-04-30
I use Zoom USB ADSL modem 5510A, I want to install the Ubuntu linux. Will it detect my modem?
Thanks:-k :

---

### Post by Malac on 2006-04-30
Hi,
Newbie myself but I have got the same modem and I can see it in Device Manager so Ubuntu is seeing the Modem as "connected" to the system but I have yet to figure out anyway to get it connected to the internet.
I have tried eagle, eciadsl, connexant cxacru, and I have trawled through countless pages on the internet(dual-boot with XP) trying to get this sorted to no avail.

Most of the guides or drivers are for other linux systems so the install instructions don't tally up with what I am seeing in Ubuntu screens/menus/options or I'm unable to compile things using downloaded scripts/packages because they are for different systems and Ubuntu doesn't have a particular app or enviroment variable set.

My reading tells me the general consensus with USB modems is throw them away and get an ethernet one. Not very helpful when (in the UK at least) I found most of the broadband providers(about 80%) gave out USB modems with their deals. I feel this is therefore a glaring hole in Ubuntu, or Linux systems generally, that in an internet access world there is no easy way to get USB modems up/running/configured without re-compiling this and that.

Sorry if this turned into any sort of flame it was not intended to be. Ubuntu is a lovely system which installed first time on both occasions I have installed it but, as I am unable to connect to the internet, it will ultimately probably be removed from my PC.

Anybody want to take this one on?

---

### Post by Malac on 2006-05-15
:DOkay I finally managed to extract the firmware from the cnxetu.sys file and get the firmware to load into the Zoom modem.:D

At last I have a Green:mrgreen: link light but now what do I do.

The device is still not appearing in the network list with eth0 and ppp0.
Or, if it's supposed to be mapped as ppp0 it isn't being detected.:confused: ](*,)

Oh well keep plugging away at it.
"Brute Force and Ignorance" may win the day yet.

---

### Post by mips on 2006-05-15
[QUOTE=Malac]:DOkay I finally managed to extract the firmware from the cnxetu.sys file and get the firmware to load into the Zoom modem.:D

At last I have a Green:mrgreen: link light but now what do I do.

The device is still not appearing in the network list with eth0 and ppp0.
Or, if it's supposed to be mapped as ppp0 it isn't being detected.:confused: ](*,)

Oh well keep plugging away at it.
"Brute Force and Ignorance" may win the day yet.[/QUOTE]

**sudo pppoeconf** maybe ?

---

### Post by Malac on 2006-05-15
Nope, tried that and all I get is the eth0 card showing up that's it.:-k

---

### Post by Malac on 2006-05-16
Okay I'm really stuck now.

Need some help to unscramble cryptic errors.

As previous posts state I managed to get the modem light to stay on and firmware loaded using the cxacru drivers and recompiling the kernel.

But, when I run ./cxstart.sh I get :
```
>>> Inits Conexant AccessRunner <<<
>>> Loading firmware...
...........
I found ADSL modem with VendorID = 1803 & ProductID = 5510
Loading and sending /usr/local/lib/cxacru/cxfirm5.bin...
Firmware is sent!
Setting configuration...
Waiting ADSL line is up (until 90 seconds)...
...........
ADSL line is up (Downstream 576 Kbits/s, Upstream 288 Kbits/s)
/usr/sbin/cxload.sh: line 65: /tmp/cxacru.params: No such file or directory
>>> Loading driver...
FATAL: Module crc32 not found.
Launching driver in normal mode...
FATAL: Error inserting cxacru (/lib/modules/2.6.12-adslusb/kernel/drivers/usb/atm/cxacru.ko): Unknown symbol in module, or unknown parameter (see dmesg)
``` 

Then when I dmesg I see :

```
[4294754.035000] cxacru 1-2:1.0: poll status: error -5
[4294759.039000] cxacru 1-2:1.0: poll status: error -5
[4294759.267000] eth0: no IPv6 routers present
[4294764.042000] cxacru 1-2:1.0: poll status: error -5

There are then Loads of these : "cxacru 1-2:1.0: poll status: error -5"

[4295329.034000] cxacru 1-2:1.0: poll status: error -5
[4295333.052000] usbcore: deregistering driver cxacru
[4295373.296000] cxacru: Unknown parameter `speed'
[4295787.978000] cxacru: Unknown parameter `speed'
[4295823.048000] cxacru: Unknown parameter `speed'
[4295977.368000] cxacru: Unknown parameter `speed'
[4296009.240000] cxacru: Unknown parameter `speed'
``` 
I don't know what should be in /tmp/cxacru.params as this wasn't mentioned in the setup instructions or what the crc32 module does or where it is getting the speed parameter reported in dmesg from.

I thought maybe it was because I was trying to restart the modem so I rebooted and just did;

```
 pppd call [provider name]
```

This resulted in the following output:
```
Plugin /usr/lib/pppd/2.4.3/pppoatm.so loaded.
pppd: The remote system is required to authenticate itself
pppd: but I couldn't find any suitable secret (password) for it to use to do so.
pppd: (None of the available passwords would let it use an IP address.)

``` 
I am now totally out of ideas as I know little enough about Linux let alone protocols and so on. I'm hoping one step will fix the others and it's maybe a cascading problem.

Anyone any ideas please, it would be much appreciated.

---

### Post by Malac on 2006-05-16
:DHurrah Hurrah,:D
:DHAHAHAHA:D

:DFinally I am on the Internet in UBUNTU over my ZOOM ADSL USB MODEM.
Many thanks to all the people who helped on this forum and the other linux forums I tried. I couldn't have done it without you.
:D
I'm So Happy:D:D


Okay now on to connection sharing with my girlfriends XP machine.

---

### Post by mips on 2006-05-16
[QUOTE=Malac]
/usr/sbin/cxload.sh: line 65: /tmp/cxacru.params: No such file or directory
>>> Loading driver...
FATAL: Module crc32 not found.
Launching driver in normal mode...
FATAL: Error inserting cxacru (/lib/modules/2.6.12-adslusb/kernel/drivers/usb/atm/cxacru.ko): Unknown symbol in module, or unknown parameter (see dmesg)[/code] 
[/QUOTE]

Do you have a /tmp/cxacru.params file or something close ???


Are you using the correct username & password. A few people make the mistake of not entering the full userid. ie. [email]userid@ispdomain.net[/email]  Some people just enter the userid part and not the rest.

---

### Post by mips on 2006-05-16
[QUOTE=Malac]:DHurrah Hurrah,:D
:DHAHAHAHA:D

:DFinally I am on the Internet in UBUNTU over my ZOOM ADSL USB MODEM.
Many thanks to all the people who helped on this forum and the other linux forums I tried. I couldn't have done it without you.
:D
I'm So Happy:D:D


Okay now on to connection sharing with my girlfriends XP machine.[/QUOTE]

Malac,

Please tell us what you did to fix the problem. This will help other people in future is they encounter the same issue.

Just use firestarter for sharing.

---

### Post by Malac on 2006-05-16
Okay Sorry mips I just was so pleased to be finally online.
 I've been upgrading since I got on so apologise for the delay.
 
 The problem seems to be that I was re-loading the driver when I ran  ./cxstart.sh
 I did in fact not reboot when I said I had I only logged out so the driver was still loaded hence the problem.

I did actually do a reboot and then only ran ```
pppd call [provider name]
```
This worked perfectly this time, I haven't dared reboot until I have run Synaptic Updates.

I think the problem may have been my provider script in /etc/peers also.
I have included it here in case it helps anyone.
```
user "MyUserName@MyProvider.com"

# VP and VC must match the ones used by your ISP.
plugin pppoatm.so
#0.38 #UK

noipdefault
usepeerdns
defaultroute
persist
noauth
nopcomp
noccp
novj
#connect "/usr/sbin/chat -v -f /etc/chatscripts/supanet"

```

Note I commented out the VP and VC numbers as I kept getting an error.(Though this error may be unconnected to this.)
And the same with the connect line as again I got errors.
If some one can explain why I may need to put them back and also what the chat thing is for. IRC?

Anyway hope this helps, now I have had it working once I will start to experiment and reboot with other options and stuff.

One Happy Ubuntu User.

---

### Post by Malac on 2006-05-16
Okay it is definitely working now as I have just done a shutdown and boot from scratch and it connected first time.

Will try to get some sort of "walk-through" sorted and post as soon as I can in case it is of use to anyone.

---

### Post by mips on 2006-05-16
[QUOTE=Malac]Okay Sorry mips I just was so pleased to be finally online.
 I've been upgrading since I got on so apologise for the delay.
 [/QUOTE]

Please, no need to apologise. Understood, the happiness part ;)

Thanks 4 the feedback !

---

### Post by Malac on 2006-05-24
In the interests of tidyness the "walkthrough" for a complete install of the ZOOM ADSLUSB MODEM is now here:

[http://www.ubuntuforums.org/showthread.php?t=182567](http://www.ubuntuforums.org/showthread.php?t=182567)

---

### Post by Malac on 2006-05-25
Have Fun

---

### Post by mips on 2006-05-31
Thanks!  Been away for 10days and only read this now.

---

### Post by Malac on 2006-06-11
[B]Okay I have posted a full "walkthrough" for 6.06 "Dapper" install of Zoom 5510-72 USB Modem in the General Howto Section of the Forums for "Dapper".

The link is here:
[http://www.ubuntuforums.org/showthread.php?t=194237]("http://www.ubuntuforums.org/showthread.php?t=194237")

 Hope this helps any problems let me know.[/B]

---

