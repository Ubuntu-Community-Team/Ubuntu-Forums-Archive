---
title: "I need BandLuxe c270 work in Ubuntu 9.04"
date: 2009-04-26
forum: Hardware
---

### Post by lonely man on 2009-04-26
hi...

first of all I love to say the best version I ever use is Ubuntu 9.04
it's work great with my laptop HP dv6880ee

but the problem now is I want my modem BandLuxe c270 with it, and I need "How to" steps or other "Utilities"

and I have other issue that when I plug the modem in my laptop the NetworkManager is stop working and I can't connect via wireless 

it's work only after I restart the system

---

### Post by ishansasanka on 2009-07-27
Any one have the drivers for Bandluxe C270 HSDPA USB MODEM ??????

---

### Post by djmaxmalta on 2009-08-17
hi guys i have a bandluxe C270 to with go mobile (post paid) Country malta

how ever if you eject the green icon from desktop then network manager will pick it up, how ever! trouble is to connect if some one knows how to fix that thanks,

ubuntu networkmanager finds it +

connects -

though go mobile contacted me they told me to try and follow the fedora manual from bandrich.com ... seems like we may need some extra software and compiling :(

i will keep on researching when i do find an answer i will post it here, to my OP and on my linux and oss websites

---

### Post by felixdzerzhinsky on 2009-08-18
> **ishansasanka said:**
> Any one have the drivers for Bandluxe C270 HSDPA USB MODEM ??????

I am using it in Cambodia. When you plug it in the "CDROM" loads. Unmount that. (Right Click Unmount or Eject)

Then I connect using wvdial. If you don't have get connected somehow or bring wvdial and its dependancies on a USB Stick. The easy way is in a shell:

```
sudo aptitude install wvdial
```

Setup your wvdial.conf with 

```
sudo gedit /etc/wvdial.conf
```

Paste in wvdial.conf (you will need to edit this according to your ISP  That Modem is ttyUSB"Zero" not the letter "o")

[Dialer Defaults] 

Modem = /dev/ttyUSB0 

Baud = 230400 

Init1 = ATZ 

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 

ISDN = 0 

Modem Type = Analog Modem 

Phone = *99***1# 

Username = "aa" 

Password = "aa" 

Stupid Mode = 1 


Good Luck

---

### Post by Harshana on 2009-11-10
> **felixdzerzhinsky said:**
> I am using it in Cambodia. When you plug it in the "CDROM" loads. Unmount that. (Right Click Unmount or Eject)

Then I connect using wvdial. If you don't have get connected somehow or bring wvdial and its dependancies on a USB Stick. The easy way is in a shell:

```
sudo aptitude install wvdial
```

Setup your wvdial.conf with 

```
sudo gedit /etc/wvdial.conf
```

Paste in wvdial.conf (you will need to edit this according to your ISP  That Modem is ttyUSB"Zero" not the letter "o")

[Dialer Defaults] 

Modem = /dev/ttyUSB0 

Baud = 230400 

Init1 = ATZ 

Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0 

ISDN = 0 

Modem Type = Analog Modem 

Phone = *99***1# 

Username = "aa" 

Password = "aa" 

Stupid Mode = 1 


Good Luck

This also didn't work with me.
What else to do?
It tring to connect.But not.

---

### Post by ddreamer on 2010-08-19
You may try this one: [http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2](http://swiss.ubuntuforums.org/showthread.php?t=886942&page=2)
My C120 works fine with Ubuntu 10.04

---

### Post by djmaxmalta on 2010-08-19
in 9.10 it worked for me, just had to conect as a dail up modem, chose my country operator, then other plan, then gave it my APN

---

