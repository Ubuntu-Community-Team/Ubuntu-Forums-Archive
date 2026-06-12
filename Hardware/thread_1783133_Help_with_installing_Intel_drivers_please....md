---
title: "Help with installing Intel drivers please..."
date: 2011-06-15
forum: Hardware
---

### Post by ET900 on 2011-06-15
Hey all I'm sorta new to Linux and new to this forum.

I recently bought a Samsung laptop (NP-RV511-A07UK). i'm not actually sure which chipset the motherboard is running so I don't know which drivers to get for that and the onboard graphics but I think I have found the drivers for the i3 processor:

[http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=20050&ProdId=3222&lang=eng&OSVersion=Debian%20Linux*&DownloadType=Firmware]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&DwnldID=20050&ProdId=3222&lang=eng&OSVersion=Debian%20Linux*&DownloadType=Firmware")

The description on this page reads:

 "[FONT=Arial][SIZE=2]Intel releases microcode updates to correct  processor behavior as documented in the respective processor  specification updates. While the regular approach to getting this  microcode update is via a BIOS upgrade, Intel realizes that this can be  an administrative hassle. The Linux Operating System and VMware ESX  products have a mechanism to update the microcode after booting. For  example, this file will be used by the operating system mechanism if the  file is placed in the /etc/firmware directory of the Linux system."

So i unzipped the folder I downloaded from there and it just appeared to be a plain text file with a little bit of a description and a disclamer and then what I guess is the CPU code. Everything seems ok so far but now I don't know where to place the file. It just says to put it in the "[/SIZE][/FONT][FONT=Arial][SIZE=2]/etc/firmware directory". Does anyone know where the "etc" folder is? I found some folders called "etc" but they didn't have another folder inside called "firmware", I also found a folder called "firmware" but it wasn't inside a folder called "etc".

This is a bit frustrating >_< Can anyone give me a hand? Also if anyone knows what other drivers I need to download for my laptop that'd be sweet :)

Thanks all!
[/SIZE][/FONT]

---

### Post by sanderd17 on 2011-06-15
Why do you need that drivers? Aren't you happy with the Intel drivers that are build into the kernel?

I have an i3 processor and I didn't need to add any drivers.

---

### Post by ET900 on 2011-06-15
Well I just thought it'd be better to get the specific drivers from the intel website instead of some generic drivers, or does ubuntu have official intel drivers built into it? Thanks.

---

### Post by sanderd17 on 2011-06-15
Linux has a lot of kernel developers. They make drivers for as much hardware as possible. 

Here is a list of the top 10 contributing firms from 2009. [http://news.cnet.com/8301-13505_3-10288910-16.html](http://news.cnet.com/8301-13505_3-10288910-16.html) And Intel takes the second place. So I guess Intel would put it's own drivers in the kernel.

For nVidea and ATI cards it's another story. nVidea creates linux drivers but doesn't release them as Open source (so you need to install those) and ATI makes no Linux drivers (so you are bound to the drivers included in the kernel).

---

### Post by ET900 on 2011-06-15
Ah right, interesting, thanks :) Maybe I don't need to worry so much about the cpu drivers then. I think I'm still gonna need drivers for the chipset and onboard graphics though right?

---

### Post by Sylslay on 2011-06-15
I agree with post above.

Drivers in kernel are made by Intel.

---

### Post by sanderd17 on 2011-06-15
I wouldn't install any additional drivers unless you feel something is working bad. But I know, for the Intel processors with integrated graphics. The chance is very small that you will find sometoing better.

---

### Post by ET900 on 2011-06-15
> **sanderd17 said:**
> I wouldn't install any additional drivers unless you feel something is working bad. But I know, for the Intel processors with integrated graphics. The chance is very small that you will find sometoing better.

yeah i feel the laptop is running ok tbh, i can tell linux is a bit lighter than windows 7 which i was running until i just wiped it n started using ubuntu studio. i just feel that the graphics performance is lacking though. i know i dont have a very powerful graphics chip but it did perform noticeably better in windows. im really hoping i can find a proper driver for it to see what difference it makes and hopefully boost performance a bit. i know that in windows graphics drivers made such a huge difference to performance, probably way more than any other driver. im assuming its the same with linux. thanks for the help so far guys :)

---

### Post by sanderd17 on 2011-06-15
Ubuntu studio? They use XFCE right?

Because in the default Ubuntu, Unity asks a lot of your graphical card, so that could make your experience slower.

---

### Post by ET900 on 2011-06-15
> **sanderd17 said:**
> Ubuntu studio? They use XFCE right?

Because in the default Ubuntu, Unity asks a lot of your graphical card, so that could make your experience slower.

Erm im not sure, whats that? I am new to linux really, ive played with it a little on random ocassions over the last couple years but ive only been running it properly as my main os for the last couple of days. i got ubuntu studio because i like to record and program music and edit videos so it was recommended to me on the linux forum. i thought it was just ubuntu but with a different default program set and a few codecs pre-installed.

also i was hoping for some power saving/underclocking features for the cpu, kinda like what amd cool n quiet does. is that possible in ubuntu?

Thanks again for all the help! i love this linux community :)

---

### Post by sanderd17 on 2011-06-15
> **ET900 said:**
> Erm im not sure, whats that? I am new to linux really, ive played with it a little on random ocassions over the last couple years but ive only been running it properly as my main os for the last couple of days. i got ubuntu studio because i like to record and program music and edit videos so it was recommended to me on the linux forum. i thought it was just ubuntu but with a different default program set and a few codecs pre-installed.

also i was hoping for some power saving/underclocking features for the cpu, kinda like what amd cool n quiet does. is that possible in ubuntu?

Thanks again for all the help! i love this linux community :)

XFCE is one of the desktop environments (the libraries that are used to create the windows, the menus and most other graphical things). XFCE is quite light. Unity is a DE that canonical created themselves and uses Gnome (another DE) as a base. Unity uses a lot of graphical 3D effects and so is quite heavy (and still a bit buggy). 

This is a list of the most common DEs from heavy to light:

[LIST]
[*]Unity: only for Ubuntu, quite heavy, based on Gnome
[*]KDE: used with Kubuntu, very windows like and a lot of bling
[*]Gnome-shell: shell on top of the third generation of Gnome, very simplistic and not like anything you have seen before.
[*]Gnome: very configurable, you can use it without effects or with a lot of crazy effects
[*]XFCE: quite light on system resources, but still quite customizable
[*]LXDE: extreme light (the L stands for light) and not very customizable
[/LIST]

Normally I use gnome-shell. I really like the interface, but almost all users have a love or hate relationship with it. Nobody is neutral. If I want to use my laptop on battery, than I use LXDE.

For the overclocking, you will have to ask someone else or search the internet. I've never overclocked my computer (since the major speed limiting factor is the HDD anyway) but all I did was overclocking my phone.

Maybe I should look into overclocking my computer. Since I began rendering OSM maps with tilemill my CPU gets used a lot more :D.

---

### Post by Yellow Pasque on 2011-06-15
Firmware files go in /lib/firmware, but I wouldn't do that. (Just keep your BIOS updated).
I'd suggest trying the latest video drivers if you feel your graphics are sluggish: [https://launchpad.net/~xorg-edgers/+archive/ppa](https://launchpad.net/~xorg-edgers/+archive/ppa)

For your info:
CPU: Core i3-380M [http://ark.intel.com/Product.aspx?id=50178](http://ark.intel.com/Product.aspx?id=50178)
Chipset: Intel HM55
GPU: Arrandale-based Intel HD

Good commands to get info on your hardware:
```
sudo lspci -v
sudo lshw
sudo dmidecode
cat /proc/cpuinfo
glxinfo
```

---

