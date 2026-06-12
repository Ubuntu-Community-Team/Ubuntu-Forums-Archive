---
title: "Netgear Wireless USB WPN111 Adapter"
date: 2005-12-13
forum: Hardware &amp; Laptops
---

### Post by neolev on 2005-12-13
Greetings,

I am having trouble configuring the WPN111 usb adapter with ubuntu. It seems to detect the device when its plugged in via the device manager....i have tried to establish a wireless connection using ndiswrapper...but it doesnt seem to even notice that i have a wireless adapter installed...it currently doesnt show the device in networking.....or the iwconfig is empty with no wireless devices found.... 

If anyone could aid in the setup and installation of this device it would be greatly appreciated...

Neolev

---

### Post by Lambert on 2005-12-13
If nothing is showing in network-admin or using the iwconfig command then you don't have a working driver.

When you installed the driver via ndiswrapper, did you include all file fromthe winxp driver file on the cd? should be a .sys .inf and .bin file. All these need to be in a directory on your harddrive.

---

### Post by neolev on 2005-12-13
That is correct i have all of those files included... this is the return i get on it.

ndiswrapper -l
netwpn11                driver present, hardware present


This is some interesting information i retrieved from a site....

Card: Netgear WPN111 108Mbps RangeMAX USB (with super G/MIMO) 
Chipset: Atheros USB 
pciid: 1358:5f01 
Driver: Windows XP driver available on the Netgear CD: netwpn11.inf + wpn111.sys + ar5523.bin 
Other:Works with latest cvs 1.6(29/11/05) you must run 'load_fw_ar5523 /etc/ndiswrapper/netwpn11/ar5523.bin' before running modprobe 

I am currently running ndiswrapper 1.7 so it should work.....i dont understand what i am supposed to do to "load_fw_ar5523" so that might be the problem i am having....not sure tho....

Neolev

---

### Post by neolev on 2005-12-13
ar5523.bin  netwpn11.inf  WPN111.sys

I forgot here are the drivers i am currently using right off the Win install disc...

iwconfig........returns

lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Neolev

---

### Post by neolev on 2005-12-14
I also tried configuring the /etc/networks/interfaces  file to setup all the wireless information like wep key and hostname etc.... still no luck....probably the key feature is that the wiress adapater doesn't light up again after its initial plug in so obviously its not broadcasting anything....seems like a driver issue in my opinon but i am certainly stumped....still

Hmm it seems like the device doesnt like the windows drivers...

Neolev

---

### Post by neolev on 2005-12-16
*-usb UNCLAIMED
                   description: Generic USB device
                   product: WPN111
                   vendor: Atheros Communications Inc
                   physical id: 1
                   bus info: usb@1:1
                   version: 0.01
                   serial: 1.0
                   capabilities: usb-2.00
                   configuration: maxpower=500mA speed=12.0MB/s

current output for driver information

it seems like i need to load the driver and it should function....anyone able to offer some insight??

---

### Post by Lambert on 2005-12-16
Check to make sure ndiswrapper is loaded.

lsmod | grep ndis

If it is then unload it

sudo modprobe -r ndiswrapper

and try the command from the ndiswrapper site.

load_fw_ar5523 /etc/ndiswrapper/netwpn11/ar5523.bin

then reload the module

sudo modprobe ndiswrapper

---

### Post by neolev on 2005-12-16
returns

bash: load_fw_ar5523: command not found

Neolev

---

### Post by Mordak on 2006-06-19
hey guys, im bringing this topic back. im trying to install the same network device, and i get the same error.

trying the command from the ndiswrapper site.

load_fw_ar5523 /etc/ndiswrapper/netwpn11/ar5523.bin

returns

bash: load_fw_ar5523: command not found

what do i do?

fyi im using ubuntu 6.06

---

### Post by braaivleis on 2006-09-21
neolev,

Well, as a newcomer to Ubuntu I have the enthusiasm and some beginners luck. I had the same problem as you did but got suspicious when Windows XP did activate the WPN111. Why then not Ubuntu?

Somehow I wondered if there is not perhaps an internal memory in the card that remembers the last settings. What I did was to start windows XP and install the drivers from the CD. After the installation, the blue light on the WPN111 started flashing - a sure sign of life!

Since the WPN111 seemed to be happy, I shut down windows XP and started Ubuntu again with all the settings given in this thread. (In other words, do not remove the WPN111 until Windows has shut down completely!)

Eureka, problem solved! (Now I am able to respond to this thread using Ubuntu and Fire fox.) This seems to prove that there is some sort of internal factor involved with the WPN111.

Good luck and I hope that this works for you as well.

Braaivleis...

---

### Post by simyn on 2006-12-07
I also get this error when I try all of the above recommendations:

[FONT="Courier New"]bash: load_fw_ar5523: command not found[/FONT]

Why is this occurring?

I would appreciate any help or advice.

---

### Post by finferflu on 2007-01-23
I've got a different problem. On Edgy, after installing the WPN111 (using the drivers provided in the card installation CD), I got the message:

```
netwpn11 driver present, hardware present
```

But, as mentioned above, I couldn't see any wlan0 with iwconfig. The after rebooting, when I plug the card in, the machine freezes, either at boot time, or when I plug it in after the boot. 

Any ideas?

Thanks!

---

### Post by capaci on 2007-04-26
> **simyn said:**
> I also get this error when I try all of the above recommendations:

[FONT="Courier New"]bash: load_fw_ar5523: command not found[/FONT]

Why is this occurring?

I would appreciate any help or advice.

i get this same error...does anyone know how to get this "load_fw_ar5523" tool?

---

### Post by opes on 2007-05-07
I've been working on this issue the past few days, and was getting the same error.

I tried the version from apt-get, was experiencing the issue.  (7.04)
Now, I removed ndiswrapper, and went and d/l'ed the tar for the newest version of ndiswrapper. (1.43)
Because 1.42 was the one pulled by apt-get and does not have the load_fw_ar5523 file.

ndiswrapper version 1.43 makes the load_fw_ar5523 file obsolute.

I made headway yesterday with compliing version 1.43.

I got it to recognize wpn111, now I just have to configure it.

It can be done, stick with it.

---

### Post by stinger30au on 2008-07-07
im about to tackle this myself, and this thread looks like it hold the keys

[http://ubuntuforums.org/showthread.php?t=844856](http://ubuntuforums.org/showthread.php?t=844856)

---

