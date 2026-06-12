---
title: "One step from getting wireless working on my Acer Aspire"
date: 2006-05-29
forum: Hardware &amp; Laptops
---

### Post by houshier on 2006-05-29
Hi,

I am so close to getting wireless working on my laptop, probably just missing something very simple, any suggestions would be appreciated!

Ok. I have an Acer Aspire 3609. I've been through the forums and found lots of info/instructions on setting up Acer notebooks with Broadcom wireless (thanks everbody!). 

What I've done so far:
[LIST]
[*]installed the ndiswrapper-utils using apt-get (i also compiled v1.16 and used that but that didn't work either) 
[*]got the correct drivers bcmwl5 from the acer website
[*]ndiswrapper -i bcmwl5.inf
[*]ndiswrapper -l shows it's installed
[/LIST]
bcmwl5	driver present, hardware present 

[LIST]
[*]Installed ndis drivers:
[*]ndiswrapper -m
[*]modprobe ndiswrapper
[*]dmesg shows that it's installed ok
[/LIST]
```

[  653.978224] ndiswrapper version 1.1 loaded (preempt=no,smp=no)
[  653.990552] ndiswrapper: driver bcmwl5 (Broadcom,12/22/2004, 3.100.46.0) loaded
[  653.998248] ndiswrapper: using irq 11
[  654.504816] wlan0: ndiswrapper ethernet device 00:14:a4:65:3f:62 using driver bcmwl5, configuration file 14E4:4318:1468:0311.5.conf

```
now when I try iwconfig it shows:

```
wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00   
          Bit Rate:54 Mb/s   Tx-Power:25 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```



when I scan for the networks:

wlan0     No scan results

I've tried to ifup wlan0 and that works but I don't get assigned an ip address

```
wlan0     Link encap:Ethernet  HWaddr 00:14:A4:65:3F:62  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Memory:bc000000-bc001fff 
```

I'm guessing that this is all down to getting the wireless button 'pressed'. Have tried acerhk, but it didn't seem to help. Was going to try acer_acpi but I don't have a 64-bit system (Actually I downloaded and compiled installed anyway, but it didn't help)

So, now I'm lost I don't know what else to try. Can anybody spot what I'm missing?

Oh and this is all on Breezy Badger 5.10 that I just downloaded recently.

Thanks you!

---

### Post by houshier on 2006-05-30
I finally found the answer!

I had been starting the laptop with the acpi=off option(without it would just hang) I changed it to noapic and the wireless light came on and it all works! Such a great feeling when I saw that light come on!

In some ways it's been good to have the problem... being new to linux/ubuntu I've learnt a lot.

Cheers!

---

### Post by fernandocordes on 2006-05-30
Hey there, housier!

I have the same problem with my wireless button as you had. Earlier i solved this with the program called acer_acpi which you mentioned above. But now I can't install  it. Even if I could, acer_acpi is not so good.
It would be very kind of you to explain a little more detailed how you managed to get your wifi turned on upon boot. (don't know how to activate noapic :-| )

---

### Post by houshier on 2006-05-30
Hey Fernando

When you start your laptop it comes up with the GRUB loader? Then there is a menu option for starting Ubuntu right? If you select the menu option and press 'e' you can see the startup parameters and also edit them. On the same line at the end add noapic (make sure you delete the apci=off if it's there). Once you've edited press b to boot.

Editing the line at boot up is just temporary. If it works then to make it permanent, edit the file /boot/grub/menu.lst

Good luck!

---

### Post by waggotamp on 2006-05-30
Hi, 

I have an Acer Aspire 1800 - 

Can you take me through all the steps to help get my laptop working on wifi

You help would be great!

---

### Post by houshier on 2006-05-31
Hi Waggotamp,

Sorry, I don't know anything about that model. But the general steps you will need to take are:

find the correct windows drivers for the wireless card
install ndiswrapper (there's a package on the cd)
install the driver ndiswrapper -i <drivername>.inf
check that it's ok: ndiswrapper -l
get things going: modprobe ndiswrapper

if you can do all of this without any errors than just check that the card is working: iwconfig and scan for your wireless network: iwlist wlan0 scan

There's a lot of info on the forums (more detailed than mine!) such search for "acer ndiswrapper". It took me a few days to go through all the info and eventually after a lot of trial and error get it working!

---

### Post by eckmann on 2006-06-05
[QUOTE=houshier]I finally found the answer!

I had been starting the laptop with the acpi=off option(without it would just hang) I changed it to noapic and the wireless light came on and it all works! Such a great feeling when I saw that light come on!

In some ways it's been good to have the problem... being new to linux/ubuntu I've learnt a lot.

Cheers![/QUOTE]

I was having the same problem -- I couldn't get that button to work no matter what I did (wireless had been working before I pressed that darn button.)  Anyway, I tried your solution of adding noapic as a boot parameter (I didn't have acpi=off in my options) and it worked!!

Thanks so much for posting your solution as I was then able to search for it and find your post (I searched Acer Aspire wireless button.)

Mike

---

