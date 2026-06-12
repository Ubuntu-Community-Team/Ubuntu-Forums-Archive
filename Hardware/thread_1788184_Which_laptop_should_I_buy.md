---
title: "Which laptop should I buy?"
date: 2011-06-22
forum: Hardware
---

### Post by nidzo732 on 2011-06-22
I have a dillemma about theese two laptops

MSI CR620-616XEU
CPU: Intel i3-370M 2.4ghz (2 cores)
Intel HM55 Chipset
RAM: 4GB DDR3
GPU: Intel 5700MHD
HDD: 320GB 5400rpm
WIFI: Atheros Wireless LAN (802.11 b/g/n)

 ACER Aspire 5552-N933G50Mnkk (long name, I know)
CPU: AMD Phenom II Quad-Core N930 2ghz(4 cores)
AMD® RS880M Chipset
RAM: 3GB DDR3
GPU: ATI RADEON HD 4250
HDD: 500GB 5400rpm
WIFI: Acer® InviLink Nplify Wireless LAN (802.11b/g/Draft-N)

Prices ar similar ~400euros
Which one is better?
Is it better to have i3 with 2 cores and 4GB ram, or phenom quad core with 3GB ram?
I've heard a lot of complaints about natty and ATI GPUs, should i take intel or ATI?
Will ubuntu and WIFI work on theese laptops?

---

### Post by Jahid65 on 2011-06-22
based on the configuration given above, I would go for the phenom one. Intel core i3 370 is not a sandy-bridge processor. Ati is better than intel HD graphcs. 

I can't say whether WIFI will work with ubuntu? If the laptop is marketed before ubuntu 11.04, then there is a fair amount of chances that it will work. But I can't say you for sure.

---

### Post by mastablasta on 2011-06-22
second one.
 
also it has more disk as for ram you can always expand it later if needed.
 
for test use live CD if you are buying in shop if you will be ordering online then you should be able to return it no questiosn asked (if it doesn't work). unless you still didn't apply this in your laws....

---

### Post by varunendra on 2011-06-23
Important things you can't change in a laptop:

[LIST]
[*]Processor
[*]Chipset
[*]Graphics adapter
[*]Wifi adapter
[*]Screen size
[/LIST]
Assuming screen sizes are same for both, rest seem to be better in the Acer model, except for the Wifi adapter - it is in question as Jahid pointed out.

Since Wifi is a very important feature of a laptop, you should contact the support guys at Acer to make sure it is supported in linux, or they have proprietary drivers available for linux.

If that is okay, or if wifi is not an issue for you, then the Acer model is definitely better.

Otherwise, either go with the MSI one or force the Acer vendor to give you a successful demo with a live ubuntu (or another linux) cd before going with Acer model.

---

### Post by nidzo732 on 2011-06-23
The acer comes with Linpus linux preinstalled, so it should work wit all distros. How will ATI work with unity?

---

### Post by varunendra on 2011-06-23
> **nidzo732 said:**
> The acer comes with Linpus linux preinstalled, so it should work wit all distros. How will ATI work with unity?

That's a good news. Just make sure it works fine and note down the driver it is using:
```
lshw -C network
```
(if lshw is available)
or-
```
lspci -v
```

For ATI support for unity, this suggests it should be fine: [https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
> **Accelerated 3D support**

 All these Radeon(HD) cards and derivatives have good 3D acceleration support 

...
...
RS880                       RadeonHD 4100/4200/4290
...
... 

Again, the only way to confirm all this is a demo if possible:).

---

### Post by mastablasta on 2011-06-23
> **nidzo732 said:**
> The acer comes with Linpus linux preinstalled, so it should work wit all distros. 
 
not if they use special firmware (drivers etc) and Linpus i sort of made by Acer  believe.
 
>  
How will ATI work with unity?
 
 
It will work. If not, then you can use LTS and go with Unity later when the do work. 
 
Or switch to KDE :-P

---

### Post by owiknowi on 2011-06-23
if applicable to your situation:
also take in consideration that warranty may be void if you install something else then the pre installed os.
also there are pretty steep differences in how manufacturers handle guarantee services.

pretty easy to use, in my experience, are asus and compal, but that's just another fools personal opinion.

also you could take a look here: [http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by kleovoulinos on 2011-06-23
I would suggest the second one. Way better hardware! ;)

---

### Post by mikeleonard on 2011-06-23
I only prefer to Dell because My friends bought Sony, Compaq ,Lenovo ,HP and Dell laptop .
But Dell is Still work Properly.
So I thinck Dell is Best.

---

