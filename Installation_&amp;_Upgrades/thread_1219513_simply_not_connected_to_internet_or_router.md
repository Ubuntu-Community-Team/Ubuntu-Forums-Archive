---
title: "simply not connected to internet or router"
date: 2009-07-21
forum: Installation &amp; Upgrades
---

### Post by mparker1113 on 2009-07-21
Hi,
 
I loaded ubuntu server 9.04, and was pretty sure that i loaded it with all of the software i want (developement, etc.)
 
I am not able to get to the internet.
 
Here are some characteristics of my environment.
 
Opening ifconfig is blank.
 
Interfaces file is blank, too.
 
I can't ping anything, even the router (D-Link 164) that i am connected to by a cable. that is 192.168.0.1. 
 
I am not very experienced at networking machines, can someone please give me some help?

---

### Post by dlmarti on 2009-07-21
If ifconfig is blank, most likely your card was not recognized.

Can you show the output of lspci please.

I assume we are talking of a wired network.

---

### Post by mparker1113 on 2009-07-23
i don't have an lspci file.   /sbin is where my ifconfig file is, and i don't see any lspci file in that folder.
 
Is that where the file should be? 
 
If i get a wireless ethernet card that works for linux, will i just have to install it into the machine for it to be recognized and to work ?
 
I have some encrpytion in my wireless wp security or something like that. I assume that ubuntu can handle this?
 
Thank you for any input. I had thought i responded yesterday, but obviosly my response wasnt' sent.
 
Mike P
 
 
> **dlmarti said:**
> If ifconfig is blank, most likely your card was not recognized.
 
Can you show the output of lspci please.
 
I assume we are talking of a wired network.

---

### Post by dlmarti on 2009-07-23
just type lspci on the command line.

---

### Post by mparker1113 on 2009-07-24
That machine is still off network. I copied it below. where there is a ..., that means there was some more information on that line. If you need more info, please let me know.

thank you.

host bridge: Intel corporation 82845G/GL...
VGA compatible controller: Intel Corpporation 82845G/..
USB Controller: Intel Corporation 828201DB/DBL/DBM ...
PCI bridge: Intel Corporation 82801 PCI Bridge
ISA bridge: Intel Corpporation 82801DB/DBL...
IDE interface: Intel Corporation 82801DB
SMBus: Intel Corporation 82801DB/DBL/DBM
Ethernet Controller: Digital Equipment Corporation DECchip 21142/43 (rev41)
Etherenet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)

> **dlmarti said:**
> just type lspci on the command line.

---

### Post by dlmarti on 2009-07-24
Is this an ASUS motherboard?

If so the BCM4401 driver is not included in the kernel, but ASUS does have a driver for Linux.

It also looks like you have another ethernet cotroller (the DEC one), do you know which one your plugged into?

Can you tell me more about your hardware?

---

### Post by wojox on 2009-07-24
Can you connect to the router from another machine on your LAN?

---

### Post by mparker1113 on 2009-07-25
It is a dell dimension running a celeron processor. 

I have 2 Ethernet cards, only one of which actually works. The one that works is something that i put in from another machine -- it says Kingston 10/100mbs on the outside of the card. I am guessing that it is the Broadcom one identified in the lspci file. 

I am not sure which type of board i am using. I try to get the information using dmidecode, but the screen scrolls and i can't see all of the information.


> **dlmarti said:**
> Is this an ASUS motherboard?

If so the BCM4401 driver is not included in the kernel, but ASUS does have a driver for Linux.

It also looks like you have another ethernet cotroller (the DEC one), do you know which one your plugged into?

Can you tell me more about your hardware?

---

### Post by dlmarti on 2009-07-25
Can you remove the one that doesn't work, and run lspci again, so I know which one to debug?

---

### Post by mparker1113 on 2009-07-25
I don't think i can remove the broken one. It is soldered into the board. 

I am sure that the one we want is the Broadcom...

> **dlmarti said:**
> Can you remove the one that doesn't work, and run lspci again, so I know which one to debug?

---

### Post by dlmarti on 2009-07-25
Go into your bios and disable the non-working network card.

Then try this:
sudo /etc/init.d/networking stop
sudo /sbin/modprobe tg3
sudo /etc/init.d/networking start
ifconfig

Send me the output of the modprobe and the ifconfig

---

### Post by mparker1113 on 2009-07-25
I have been looking around, and am not sure how to change my bios settings so that i take the bad card out. Could you tell me what would be a good way to do this?

> **dlmarti said:**
> Go into your bios and disable the non-working network card.

Then try this:
sudo /etc/init.d/networking stop
sudo /sbin/modprobe tg3
sudo /etc/init.d/networking start
ifconfig

Send me the output of the modprobe and the ifconfig

---

### Post by dlmarti on 2009-07-25
Every bios is different, if you have the tag number of your dell you should be able to download the manual directly from dell support.

Normally its just a matter of looking around till you find it.

We have to be absolutely sure that we are debugging the correct chip, otherwise this is never going to work.

---

### Post by mparker1113 on 2009-07-25
so are you suggesting that i find the bios through the system when i boot, by doing f2 and getting the bios settings? 

or, is there a way using the linux software to set the bios ?


> **dlmarti said:**
> Every bios is different, if you have the tag number of your dell you should be able to download the manual directly from dell support.

Normally its just a matter of looking around till you find it.

We have to be absolutely sure that we are debugging the correct chip, otherwise this is never going to work.

---

### Post by dlmarti on 2009-07-25
> **mparker1113 said:**
> so are you suggesting that i find the bios through the system when i boot, by doing f2 and getting the bios settings? 

or, is there a way using the linux software to set the bios ?

You can't do it through Linux, you have to do it through your bios method (probably the f2 thing your thinking about"

---

### Post by mparker1113 on 2009-08-01
Hi dlmarti

i hope that you remember me. I have been to busy to get to my machine.

I never figured out how to disable the ethernet card from the bios. But instead, i removed the one that wasn't soldered to the machine and ran lspci again. After doing that, the only ethernet card showing is bhr BroadCom Corporation one -- so with that information, i can tell you that the Ethernet card which works is the Ethernet Controller: Digital Equipment Corporation DECchip 21142/43 (rev41) card. 

Is that enough information for us to debug and fix this ?



> **dlmarti said:**
> Can you remove the one that doesn't work, and run lspci again, so I know which one to debug?

---

### Post by W4l0ck on 2009-08-01
Wow, you gots a problem with your hardware.

---

### Post by mparker1113 on 2009-08-01
I guess, i just want to get cooking with this.

Should i just get a different nic card, one that will work with the O.S. ?

[quote=W4l0ck;7715614]Wow, you gots a problem with your hardware.[/q.uote]

---

### Post by dlmarti on 2009-08-01
First disable the none working nic.  If you need instructions on how to get into the bios, give me the name of your motherboard.  It should be printed directly on the MB.

---

### Post by mparker1113 on 2009-08-02
Okay, i think that i have this ready now. In the bios, went to advanced/peripherals, and disabled the Integrated Network Adapter. 

Now when i do the lspci, I only have one Ethernet controller listed, Digital Equipment Corporation DECchip 21142/43.  But, I think that i am having some other problems with my router not working with cabled connections now. 

I think i am going to buy a wireless NIC card for this ubuntu server. I have WEP 64 bit security turned on for wireless, will ubuntu be compatible with this ?





> **dlmarti said:**
> First disable the none working nic.  If you need instructions on how to get into the bios, give me the name of your motherboard.  It should be printed directly on the MB.

---

### Post by dlmarti on 2009-08-02
ok good, can you re-run lspci and ifconfig so I can see the output now?

---

### Post by mparker1113 on 2009-08-17
> **dlmarti said:**
> ok good, can you re-run lspci and ifconfig so I can see the output now?

I have been away, but would love to get this machine working. Here are the results you asked for:   (copied by hand, let me know what you think or if you need more information. -- thanks for any insight)

lscpi: 

Host Bridge: Intel Corporation 828456/GLI[Brookdale-G]/GE/PE DRam Controller.....

VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics...

USB Controller: Intel Corporation  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHC1 Controller # 1 (rev 02)

USB Controller: Intel Corporation  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHC1 Controller # 2 (rev 02)

USB Controller: Intel Corporation  82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHC1 Controller # 3 (rev 02)

USB Controller: Intel Corporation  82801DB/DBM (ICH4/ICH4-L/ICH4-M) USB2 EHCI Controller (rev 02)

PCI bridge: Intel Corporation 82801 PCI Bridge (rev 82)

ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 02)

IDE Interface: Intel Corpporation 82801DB (ICH4) IDE Controller (rev 02)
SMBus: Intel Corpration 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev02)

Multimedia audio controller ...

Ethernet controller: Digital Equipment Corporation DECchip 21142/43 (rev 41)


OUTPUT of ifconfig :

lo

Link encap: Local Loopback

inet addr: 127.0.0.1  Mask: 255.0.0.0

intet6 addr: ::1/128 Scope: Host

UP LOOPBACK RUNING MTU: 16436 Metric: 1

RXPackets: 3570 errors: 0 dropped: 0 overruns: 0 frame: 0

TX packets: 3570 errors: 0 dropped: 0 overruns: 0 carrier: 0 collisions: 0 txqueuelen: 0

RX bytes: 1769551 (1.7 M) TX bytes: 1769551 (1.7 MB)

virbr0
 
Link encap: Ethernet HWadr 7a:60:83:79:3c:8c

inet addr: 192.168.122.1 Bcast: 192.168.122.255 Mask: 255.255.255.0

inet6 addr: fe0::7860:83ff:fe79:ec8c/64 Scope:Link

UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1

RX packets: 0 errors: 0 dropped: 0 overruns: 0 frame: 0

TX packets: 209 errors: 0 dropped:0  overruns: 0 frame: 0

TX packets: 029 errors: 0 dropped: 0 overruns: 0 carrier: 0 colistions: 0 txqueuelen:0

RX bytes:0 (0.0 B) TX bytes: 476908 (46.9KB)

---

### Post by dlmarti on 2009-08-19
What is the virbr0 interface, a virtual bridge?  I'm not familiar with that.

What is the output of lsmod?

In the output of lsmod, do you see a module called tulip?

If you do a sudo insmod tulip, what is the output of ifconfig then?

---

### Post by mparker1113 on 2009-08-19
I am not sure what the virb0 is, bur it is a category in the ifconfig, that and lo.
 
This is the result of lsmod ( i left what was obvious to me as unrelated out):
 
snd_ac97_codec   111-12  1  snd_intel8x0
 
ac97_bus   9856  1 snd_ac97_codec
 
snd_pcm   83076  2  snd_intel8x0,snd_ac97_codec
 
snd_timer   29704  1  snd_pcm
 
snd   62628 4  snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer,snd_pcm,snd_timer
 
iTC0_wdt  19236  0
 
snd_page_allloc   17032  2  snd_intel8x0,snd_pcm
 
itCO_vendor_suport  11652  1  iTCO_wdt
 
shpchp  40340  0
 
parport_pc   40356  1
 
intel_ag0   34500  1
 
parport   42220  3  lp,ppdev,parport_pc
 
agpgart  42696  1   intel_agp
 
tulip   58656  0
 
fbcon  45856  0
 
tileblit  10752  1  fbcon
 
bitblit  18696  1   fbcon
 
 
When i do sudo insmod tulip, i get "can't read 'tulip': No such file or directory....
 
 
---end of response ----
 
> **dlmarti said:**
> What is the virbr0 interface, a virtual bridge? I'm not familiar with that.
 
What is the output of lsmod?
 
In the output of lsmod, do you see a module called tulip?
 
If you do a sudo insmod tulip, what is the output of ifconfig then?

---

### Post by dlmarti on 2009-08-19
It looks to me that tulip is loaded so thats good.

Couple of things:
1. if you do a "sudo ifconfig eth0 192.168.1.1" what does ifconfig look like?
2. check your network setup and see if you can find the virbr0 mentioned.  Its probably nothing, but since I'm not familiar with it I would like to know what its doing.

---

### Post by mparker1113 on 2009-08-19
sudo ifconfig eth0 192.168.1.1 does nothing. 
 
I am not sure where to find virbr0. 
 
Do you think that if i bought a wireless NIC card that is compatible with Ubuntu, that i could use that connection to get to my router ?
 
-- end response.
 
I am not sure where to look for the 
> **dlmarti said:**
> It looks to me that tulip is loaded so thats good.
 
Couple of things:
1. if you do a "sudo ifconfig eth0 192.168.1.1" what does ifconfig look like?
2. check your network setup and see if you can find the virbr0 mentioned. Its probably nothing, but since I'm not familiar with it I would like to know what its doing.

---

### Post by mparker1113 on 2009-08-19
Doing sudo ifconfig eth0 192.168.1.1 produces nothing.
 
I am not sure where virbr0 is. 
 
Do you think that if i got a linux compatible wireless NIC card that my connection issues would be solved ? I really want to get to work using this server..
 
Thanks
 
-- 
 
> **dlmarti said:**
> It looks to me that tulip is loaded so thats good.
 
Couple of things:
1. if you do a "sudo ifconfig eth0 192.168.1.1" what does ifconfig look like?
2. check your network setup and see if you can find the virbr0 mentioned. Its probably nothing, but since I'm not familiar with it I would like to know what its doing.

---

### Post by dlmarti on 2009-08-19
> **mparker1113 said:**
> Doing sudo ifconfig eth0 192.168.1.1 produces nothing.
 
I am not sure where virbr0 is. 
 
Do you think that if i got a linux compatible wireless NIC card that my connection issues would be solved ? I really want to get to work using this server..
 
Thanks
 
--

after you do a "sudo ifconfig eth0 192.168.1.1"  re-run ifconfig and see what it says.

As far as the wireless NIC card goes, if we really can't get this working I would just purchase a cheap wired NIC for a few dollars online.

---

### Post by mparker1113 on 2009-08-20
> **dlmarti said:**
> after you do a "sudo ifconfig eth0 192.168.1.1"  re-run ifconfig and see what it says.

As far as the wireless NIC card goes, if we really can't get this working I would just purchase a cheap wired NIC for a few dollars online.

So, i think that i am going to get a Wireless Nic. I don't want wired, because my router is downstairs, and the server upstairs (wife doesn't like cables throughout the home...)

Do you think i should be okay if i pursue that ?

I just want to get started so that i can use the software, and not all of this troubleshooting of hardware. 

If you think i am better off to keep troubleshooting first, i will do that.

Thanks,
 
Mike

---

### Post by dlmarti on 2009-08-20
If wireless is the way you want to go, I'm not the one to recommend one for you.  I don't use wireless, in fact I spent a lot of time wiring my entire house  :)

---

