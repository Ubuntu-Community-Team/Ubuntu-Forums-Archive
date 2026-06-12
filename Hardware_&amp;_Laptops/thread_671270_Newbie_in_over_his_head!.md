---
title: "Newbie in over his head!"
date: 2008-01-18
forum: Hardware &amp; Laptops
---

### Post by aprilian bandit on 2008-01-18
Hi guys, I'm absolutely virginal to linux so please be gentle! 

I have an acer aspire 7520 laptop and was reading through the thread regarding installing ubuntu on it, and thought I'd give it a go and get rid of crappy vista. One thing I picked up was the noacpi to add in the boot so it now boots up most of the time, but reading other things - about "install these xp drivers for the wireless" and "simply install the nvidia drivers" are lost on me. It took me about 2 hours just to install ndiswrapper (using the guide at sourceforge).

I would be very grateful of a very basic step by step guide to installing the nvidia drivers, getting ndiswrapper or gtkwifi to recognise my wireless card and driver, and how to install the audio codec. I keep chasing my tail in terminal, getting lost left right and centre!

Also, if anyone could point me in the direction of a reasonably comprehensive idiots guide to linux/terminal/ubuntu I'd appreciate it.

I should have got to learn it on the live cd first I guess, but why have a deep end if you're not going to jump in to it?! :)

---

### Post by jerrykenny on 2008-01-18
Havent you discovered the synaptics package manager ? look in system administartion synaptic.

there you can do searches for things like "restricted drivers"  and "nvidia".

Also read this excellent guide

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)



Cha's documentation is one of the great strengths of Ubuntu !

---

### Post by nick_h on 2008-01-18
> I would be very grateful of a very basic step by step guide to installing the nvidia drivers
System->Administration->Restricted Drivers Manager
You should see the nvidia driver listed.  Select it.

> getting ndiswrapper
From a terminal type:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```
Then to install your Windows driver use:
```
sudo ndiswrapper -i /path/driver.inf
```
To check this use:
```
ndiswrapper -l
iwconfig
```
If this works then you will need to update your /etc/modules.  You may also need to blacklist the original inbuilt driver.  What card are you using?

> and how to install the audio codec
Type:
```
sudo apt-get install ubuntu-restricted-extras
```
for more information look [here](https://help.ubuntu.com/community/RestrictedFormats) and [here](https://help.ubuntu.com/7.10/musicvideophotos/C/index.html).

For a command line reference try - [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by aprilian bandit on 2008-01-20
> System->Administration->Restricted Drivers Manager
You should see the nvidia driver listed.  Select it.
> Havent you discovered the synaptics package manager ? look in system administartion synaptic. there you can do searches for things like "restricted drivers" and "nvidia".
Couldn't see it before because I hadn't been connected to the net to seach and download. nvidia now sorted, cheers guys :)


> From a terminal type:
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```
Then to install your Windows driver use:
```
sudo ndiswrapper -i /path/driver.inf
```
To check this use:
```
ndiswrapper -l
iwconfig
```Currently this isn't going so well... using the list, I get ```
bcmwl6 : invalid driver!
net5211 : driver installed
              device (168C:001C) present (alternate driver: ath-pci)
netathr : invalid driver!
netathrx : invalid driver!
```
However I seem unable to delete the invalid drivers??
When I iwconfig I get
```
lo         no wireless extensions
eth19        no wireless extensions
```All I know of the card is that it's atheros. [http://support.acer-euro.com/drivers/notebook/as_7520.html](http://support.acer-euro.com/drivers/notebook/as_7520.html) is where I got the invalid drivers from!?


> Type:
```
sudo apt-get install ubuntu-restricted-extras
```
I get
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras
```

Thanks for the links by the way, will no doubt prove invaluable when I get chance to read them :) Thanks for your help so far :KS

---

### Post by nick_h on 2008-01-20
First the easy bit.  For the ubuntu-restricted-extras package you need to enable the multiverse repository.

System->Administration->Software Sources

Then under the "Ubuntu Software" tab select "multiverse".  You may wish to also enable "universe" at this point.

The wireless may be more difficult.  You can check the card you have installed with:
```
lspci -v
```

You can try to remove the invalid drivers with:
```
sudo ndiswrapper -r bcmwl6
```
and the same with the other invalid drivers.

Next you can check which drivers are loaded with the *lsmod* command.  The list will be long so it is common to pipe the output to the *grep* command.

```
lsmod | grep ndiswrapper
```
should show this module.

```
lsmod | grep ath-pci
```
will probably not show this one.

---

### Post by aprilian bandit on 2008-01-27
Cheers for that Nick, due to erratic booting I decided to give fedora core a pop, and it's been working much smoother on this crappy laptop than ubuntu was so I'm going to stick with it (no boot issues and audio working once software was upgraded). However, most of the threads I've been finding regarding issues with the Atheros AR5006EG wireless card have been on this forum so I'll stick in here and gain some much appreciated knowledge :)
> 
The wireless may be more difficult.  You can check the card you have installed with:
```
lspci -v
```

```
05:00.0 Ethernet controller: Atheros Communications, Inc. AR5006EG 802.11 b/g Wireless PCI Express Adapter (rev 01)
        Subsystem: AMBIT Microsystem Corp. Unknown device 0428
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at f2200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel modules: ath5k, ath_pci
```

> You can try to remove the invalid drivers with:
```
sudo ndiswrapper -r bcmwl6
```
and the same with the other invalid drivers.
Done, thank you.

> Next you can check which drivers are loaded with the *lsmod* command.  The list will be long so it is common to pipe the output to the *grep* command.

```
lsmod | grep ndiswrapper
```
should show this module.
```
[pete@localhost ~]$ /sbin/lsmod | grep ndiswrapper
ndiswrapper           219520  0 
```


> ```
lsmod | grep ath-pci
```
will probably not show this one.
Nope, nothing shown... I'm of the understanding that I have to remove this ath_pci but I haven't been able to, been trying the rmmod command and it's been getting me nowhere.
```
[pete@localhost ~]$ /sbin/rmmod ath_pci
ERROR: Module ath_pci does not exist in /proc/modules

``` Do I have to put the path to the ath_pci module to remove it?

Cheers again.

---

### Post by nick_h on 2008-01-28
It looks like the modules you need to look for are ath5k and ath_pci (underscore not hyphen).  Do they show up in the lsmod?

---

### Post by aprilian bandit on 2008-01-30
It's (finally) ok now... I found this link in the Fedora forums... [http://home.nyc.rr.com/computertaijutsu/rhwireless.html](http://home.nyc.rr.com/computertaijutsu/rhwireless.html)
there is a section at the bottom that relates to the AR5006EG wireless card (which is most likely actually the AR5007EG).

It's a guide for fedora, but it should still work for ubuntu too if anyone else is having any grief with this card? It involves the use of experimental madwifi drivers.

Thanks a lot for the help though, appreciated :)

---

### Post by nick_h on 2008-01-31
I'm glad you got it sorted out.  I was going to suggest searching on this forum there are quite a few threads on this driver.

---

