---
title: "HP/Compaq nc6000"
date: 2005-05-04
forum: Hardware &amp; Laptops
---

### Post by Kroovy on 2005-05-04
Just wondering if anybody has succeeded/failed at installing Ubuntu on a HP/Compaq nc6000. 
I currently have it installed on my desktop, but was kinda dubious about installing it onto my laptop...
Any help or suggestions appreciated! 
:)

---

### Post by jon_hill987 on 2005-05-04
It mostly works on my HP compaq nx9005, I'm just having trouble with my wifi card.

---

### Post by 23meg on 2005-05-04
i don't know how much this will help but everything except the famous conexant (win)modem, which can only run with proprietary drivers (and which i have no use for) is fine with my compaq evo n800v over here.

---

### Post by phen on 2005-05-05
there is a special hp version available soon. there is a thread about it in the forum. just search for "hp" "laptop" "nc6120"

Thomas Schneller can provide ýou with a prerelease, you have to send him an email. I hope your laptop is  supported, too!

kai

---

### Post by jon_hill987 on 2005-05-05
[QUOTE=phen]there is a special hp version available soon. there is a thread about it in the forum. just search for "hp" "laptop" "nc6120"

Thomas Schneller can provide ýou with a prerelease, you have to send him an email. I hope your laptop is  supported, too!

kai[/QUOTE]

Tryed the search, just got this thread, I was wondering if it might work better than the curent release with my nx9005.

---

### Post by bgrant75 on 2005-05-06
It definitly works on a NC6000. The model I had used the Atheros wireless. Some other NC6000's have the intel wireless.

I however since have just purchased a IBM Thinkpad T43 and now will give it a go.

Good luck.

---

### Post by balazs on 2005-06-18
Hi Guys,

I just installed Hoary on a 1 year old NC6000 (Pentium M 1.4 Ghz). Installation was smooth, no problems at all. I have downloaded the modified version with the HP drivers as suggested by Thomas Schieller on another thread. Everything seems to be OK, but i guess i will need a few days to test everything.

Will get back if after that. Now i am just simply toooo excited to have such a painless linux installation and a healthy running system.

---

### Post by funkenstein on 2005-06-19
another successful nx9005 install. I got Teamspeak server and battlefield2 servers running, Diablo II (old skool) is fine. I don't have a wireless card, so can't comment.
Only thing I'm having trouble with is the zalman usb external soundcard that only works if you plug it in after the system is booted and even then it's a hassle :p .....

---

### Post by balazs on 2005-07-10
Hi everyone,

after a few week of usage i just find one thing annoying:  Startup time is well over 2 minutes (round 2:30). Today i used a stopwatch to measure, and here is what happens (choosing Ubuntu as an operating system in grub is 00:00 seconds):

1: 39 seconds after start we arrive to the network activation
2: It spends 1 minute with this (very annoying when i am not connected): 1:40
3: By 1:55 gnome is loaded
4: By 2:25 i am logged in.

I realize i loose this 1 minute with the network interfaces. Is it possible to speed this up? I use the wireless card as my main network adapter.

Otherwise i am a very happy linux user, this is the first distribution i kept longer than 1 week, and i intend to get rid of windows entirely soon.

So any leads on this startup problem?


Thanx,

Balazs

---

### Post by skippy on 2005-07-24
I didn't use the custom hp iso, (did know about it till now) but got it working.
I have one major problem...pcmcia  
If I have any pcmcia cards in, everything hangs at boot.  
My system does not have built in wireless, so I have tried a pcmcia(belkin) which gave me the above result.
Does anyone know if pcmcia works with the "custom" HP iso Hoary?

---

### Post by iimre on 2005-07-25
[QUOTE=Kroovy]Just wondering if anybody has succeeded/failed at installing Ubuntu on a HP/Compaq nc6000. 
:)[/QUOTE]
I have it installed without any problem on my nc6000 both the "standard" Hoary Hedgehog and Thomas Schneller's custom cdimage.
Otherwise I'm using the Debian SID for regular work on it for a year now. What's not work for me : sdcard reader and infraport, :(  otherwise no problem with it.  :)

---

### Post by viedzma on 2007-05-09
Have NC6000 with Ubuntu and wireless, bluetooth, IrDa working, only the sd card reader doesn't work... but I have it for a few hours and maybe it will work if I find out how :)
Looks like this :D
[[IMG]http://img91.imageshack.us/img91/766/ubuntu20070508ak3.th.png[/IMG]](http://img91.imageshack.us/my.php?image=ubuntu20070508ak3.png)

---

### Post by locutus42 on 2007-05-09
> **viedzma said:**
> Have NC6000 with Ubuntu and wireless, bluetooth, IrDa working, only the sd card reader doesn't work... but I have it for a few hours and maybe it will work if I find out how

NOTE:  This is for the Texas Instrument SD chips. It works for my HP/Compaq R4000/ZV6000 with the "Texas Instruments PCI6411/6421/6611/6621/7411/7421/7611/7621 Secure Digital Controller"(copied from lspci output). See the script below for a URL to where the  information for the script was obtained.

Save this to a file named "sdhci",  use ( chmod +x sdhci ) to make it executable, and run it with sudo to see if it works( sudo sdhci ):


```

#!/bin/sh

# from:
#http://ubuntuforums.org/showthread.php?p=1614392#post1614392
#
# Get lsb functions
. /lib/lsb/init-functions
LSPCI_ADDRESS=`lspci | grep "FlashMedia" | cut -d " " -f 1`

case "$1" in

start)
        log_begin_msg "Configuring card reader"

        modprobe fakephp || return 1
        setpci -s ${LSPCI_ADDRESS} 86.b=90
        setpci -s ${LSPCI_ADDRESS} 4c.b=02 # FlashMedia SD disable
        setpci -s ${LSPCI_ADDRESS} 04.b=06 # SDHCI Mem+ BusMaster+
        setpci -s ${LSPCI_ADDRESS} 88.b=01 # SDHCI DMA enable
        modprobe sdhci || return 1

        log_end_msg $?
	;;

stop)
        log_begin_msg "Shutting down card reader"

        modprobe -r sdhci
        lsmod | grep -q sdhci && return 1
        setpci -s ${LSPCI_ADDRESS} 88.b=00 # SDHCI DMA disable
        setpci -s ${LSPCI_ADDRESS} 04.b=07 # SDHCI Mem- BusMaster-
        setpci -s ${LSPCI_ADDRESS} 4c.b=00 # FlashMedia SD enable
        setpci -s ${LSPCI_ADDRESS} 86.b=d0
        modprobe -r fakephp

        log_end_msg $?
	;;


*)
    log_success_msg "Usage: /etc/init.d/sdhci start|stop"
    exit 1
    ;;
esac

exit 0

```

If it works, move the file to the /etc/init.d directory( sudo mv sdhci /etc/init.d ) and then add it to the boot sequence( sudo update-rc.d sdhci defaults ).

---

### Post by viedzma on 2007-05-11
If I run this it looks like that:
```

root@anilap:/etc/init.d# /etc/init.d/sdhci start
 * Configuring card reader   
setpci: -s: Invalid slot number
setpci: -s: Invalid slot number
setpci: -s: Invalid function number
setpci: -s: Invalid slot number

```

If you could tell me where from did you get numbers from these lines:
```

setpci -s ${LSPCI_ADDRESS} 86.b=90
setpci -s ${LSPCI_ADDRESS} 4c.b=02 # FlashMedia SD disable
setpci -s ${LSPCI_ADDRESS} 04.b=06 # SDHCI Mem+ BusMaster+
setpci -s ${LSPCI_ADDRESS} 88.b=01 # SDHCI DMA enable

```

i think that would help me. The problem is that I don't have the Texas instrumantals SD Chip. It looks like this:
```
root@anilap:/etc/init.d# lspci | grep CardBus
02:06.0 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.1 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller
02:06.2 System peripheral: O2 Micro, Inc. OZ711Mx 4-in-1 MemoryCardBus Accelerator
02:06.3 CardBus bridge: O2 Micro, Inc. OZ711M3/MC3 4-in-1 MemoryCardBus Controller

```

---

### Post by locutus42 on 2007-05-11
Sorry but as noted in my entry, the script only works with the TI SD chip and it also lists where I got the information.  So the reason it's failing with that error is because the "lspci" line in the script is not finding anything with the "FlashMedia" string in it.

I will move that line stating that the script only works for the TI SD FlashMedia chip to the top of the entry.  I was hopeful that the nc6000 also used the TI SD chip since the zv6000 and R4000 use it.

---

### Post by billWalker on 2007-05-19
Thanks, locutus42, that script worked perfectly for me (zv6000).  First time in the year I've been using Ubuntu that I've been able to write to my SD cards.

---

### Post by tcpkid_82 on 2008-02-26
Hello,

Ubuntu runs fine on a HP NC6000 for me (7.04) with XGL the only problem u might encounter is the driver for the wireless card. But its easy to find. Video & Sound work 100%. Ubuntu 7.10 is crap... i mean i have not gotten XGL to work on it it keeps giving me an error "Could Not Enable Desktop Effects" or something like that.. but every thing else works fine.. I bought this NEW NC6000 in 2007 (less than 6 months actually) u might wonder how i got a new one well its a long story.. :)

try the live cd before u install it.. then ull know what works.. if u know how to make XGL work on ubuntu7.10 then pls post.. because if i use live cd and update graphic driver it wants me to restart that way XGL will work. without installing ubuntu how will XGL work? thanks...

---

### Post by locutus42 on 2008-02-26
> **tcpkid_82 said:**
> Hello,
try the live cd before u install it.. then ull know what works.. if u know how to make XGL work on ubuntu7.10 then pls post.. because if i use live cd and update graphic driver it wants me to restart that way XGL will work. without installing ubuntu how will XGL work? thanks...

I spent an hour or so trying to get the LiveCD of Kubuntu 7.10 going with 3D desktop effects and finally gave up since, IIRC, it required kernel updates and you can't do that in a LiveCD. Otherwise, as long as I copy my bcm43xx_* files into the /lib/firmware directory then wireless works and everything else. Even installed the restricted ATI driver and got 3D performance working for Java3D stuff. Ubuntu/Kubuntu is really coming along nicely on HP/Compaq laptops.

---

