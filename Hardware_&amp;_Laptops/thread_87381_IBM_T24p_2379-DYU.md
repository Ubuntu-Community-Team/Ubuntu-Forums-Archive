---
title: "IBM T24p 2379-DYU"
date: 2005-11-07
forum: Hardware &amp; Laptops
---

### Post by pacman on 2005-11-07
Ok... I have installed various flavors of linux over the years, and I must say I am very impressed with Ubuntu. Having said that, I would like to ask for some help... which seems to be something of a stupid thing to do for most linux users. :rolleyes: 

My system sports the IBM/Atheros A,B/G card, and I seem to be having some problems setting it up. The first thing I find interesting is the output from the ifconfig command... all of the ip seetings seem to be represented in IPv6 format... is this normal? Everything in the iwconfig command looks ok, but I am not 100% sure what I am looking for in the first place.

Any help with this particular system would be greatly appreciated...

---

### Post by lorenco on 2005-11-08
I have an IBM T41 Same card...

I recall that I used the Wireless card during setup.  It works out of the box.
I am using KDE (Kubuntu) and the control center has everthing I need to setup the wireless.

A couple of pointers though:  make sure you are connected to the wireless network:
Check you Access Point... use iwconfig and check the access point mac, is this connected?  Is you Wireless light flashing ?

You should use "sudo modprobe ath_pci"

Here is my module list :
sudo lsmod | grep ath
ath_pci                78908  0
ath_rate_sample        17000  1 ath_pci
wlan                  141692  3 ath_pci,ath_rate_sample
ath_hal               148432  3 ath_pci,ath_rate_sample

---

### Post by benplaut on 2005-11-08
i have the A/B/G II, i don't think there's much of a diff :P

wifi-radar works very well with it, install and try

---

### Post by pacman on 2005-11-08
Thanks guys... 

One thing paramount to me is the ability to roam in and out of multiple networks... at the moment I am using IBMs access manager to accomplish this. Any suggestions with Ubuntu?

Yes the radio light is blinking, but it is blinking very slowly. I will try the commands below and see what I get.

---

### Post by lorenco on 2005-11-08
I remember that there is some cool tools in KDE ? but I recall gnome also having these...

In the Network configuration of kcontrol you find "Profiles"  I roam between work and home and it is transparent BUT it is DHCP between ath0 and eth0 (E1000 card)

Not sure how these profiles work but at least they are there....

---

### Post by pacman on 2005-11-09
Update...

WIFI-Radar work very well...

I can connect to an unprotected wireless network at this point, but I am having trouble connecting to WEP protected network at home and our LEAP protected network at the house. 

Anything I should know about the modes... keys... or anything like that? 

TIA

---

### Post by strawman on 2005-11-09
have you tried the reset button on your router; that worked for me with my initial install of ubuntu.

---

