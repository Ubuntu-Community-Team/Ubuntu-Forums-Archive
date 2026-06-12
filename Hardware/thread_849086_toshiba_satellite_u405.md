---
title: "toshiba satellite u405"
date: 2008-07-04
forum: Hardware
---

### Post by ms.shams on 2008-07-04
Hi everyone.

i bought a toshiba satellite u405-s2830.
this is good. top config and lower price. when i bought this laptop, install ubuntu on it before booting vista :)
but i have a little problem with this:

1- this model has a Marvell Ethernet card that i must run a script after new kernel compilation for works.

2- u405 has a intel wireless network card. that ubuntu detects it. and i can see our network settings and link quality from iwconfig output every time. but i can't connect to detected network with 70/100 percent link quality. when i run "iwlist wlan0 scan" sometimes it says no scan result and sometimes it can scan my network!

can you help me for resolve these major problems please?

---

### Post by Mikecore on 2008-07-04
I have a toshiba laptop with the intel adapter. I have had some issues with connecting to some wireless networks. Try setting your  essid, channel and rate manually with "iwconfig" then either use the gui to connect or try 
dhclient. It might already be running so you might have to kill it. second when your setting it up manually make sure it is not up" by using the "ifconfig" command if it is you need to take it down. 

```

ifconfig wlan0 down"


```

that usually works for me. Once you do get it to connect to a wireless network it will usually do it again without all the typing. good luck and BTW thats a nice computer you just got.

---

### Post by alebu on 2008-07-07
> **ms.shams said:**
> 
1- this model has a Marvell Ethernet card that i must run a script after new kernel compilation for works.

Can you point on some sources of information where I can find such a script? I bought Toshiba satellite pro u400 (u400v i think) and have no LAN or wireless connection at all. Thanks in advance

---

### Post by stchman on 2008-07-07
> **ms.shams said:**
> Hi everyone.

i bought a toshiba satellite u405-s2830.
this is good. top config and lower price. when i bought this laptop, install ubuntu on it before booting vista :)
but i have a little problem with this:

1- this model has a Marvell Ethernet card that i must run a script after new kernel compilation for works.

2- u405 has a intel wireless network card. that ubuntu detects it. and i can see our network settings and link quality from iwconfig output every time. but i can't connect to detected network with 70/100 percent link quality. when i run "iwlist wlan0 scan" sometimes it says no scan result and sometimes it can scan my network!

can you help me for resolve these major problems please?

I have a Toshiba laptop with a 4965AGN and the wireless works perfectly.

As far as the wired ethernet the laptop has a Realtek 8139 which works OOB, but I have never used it.

That laptop also has an x3100 video which works OOB with Hardy.

Give us an lspci output there in this thread.

---

### Post by timrichardson on 2008-07-08
I have a Satellite u400 bought two days ago. It works very well; I even got the bluetooth module working (see my post [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374))

The only real problem I have remaining is the wifi kill switch.
If I use it to turn the wifi off, then I can not reenable wifi. I have to reboot. I am using hardy, all updates and backported kernel modules (which have updates to the intel wireless drivers).

It's something to do with Hal I guess.

---

### Post by alebu on 2008-07-09
> **timrichardson said:**
> I have a Satellite u400 bought two days ago. It works very well; I even got the bluetooth module working (see my post [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374))

The only real problem I have remaining is the wifi kill switch.
If I use it to turn the wifi off, then I can not reenable wifi. I have to reboot. I am using hardy, all updates and backported kernel modules (which have updates to the intel wireless drivers).

It's something to do with Hal I guess.

Hmm, strange, I can't get LAN on U400. I saw that there is a problem with Marvel Gib LAN chipset. Did uyo do anything to enable LAN or it worked out-of-the-box?

---

### Post by wlan0 on 2008-07-28
I got problems with the LAN too... any help to make it work.... and the other problem is the fingerprint reader the multimedia btns work fine with amarok

---

### Post by Zer0Nin3r on 2008-08-16
Just bought a Toshiba Satellite U405D-S2852 to replace my old Compaq Presario R3000.

Was able to install from the live CD with no problems.  I just cannot get both the Ethernet and WiFi to work.  Under restricted devices the Atheros wifi shows up and has a check in the box showing that it is in use but no luck.

Performing a 'lspci' tells me that I'm running a Marvell for Ethernet and an Atheros AR242x chip for wireless.

Any tips for getting the networking to work?

---

### Post by olavjunior on 2008-08-18
> **timrichardson said:**
> I have a Satellite u400 bought two days ago. It works very well; I even got the bluetooth module working (see my post [https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374](https://bugs.launchpad.net/ubuntu/+source/toshset/+bug/181374))

The only real problem I have remaining is the wifi kill switch.
If I use it to turn the wifi off, then I can not reenable wifi. I have to reboot. I am using hardy, all updates and backported kernel modules (which have updates to the intel wireless drivers).

It's something to do with Hal I guess.

I've followed your instructions, and it works! So thank you very much for that! But sometimes after suspension, the bluetooth has disappeared. So, do you know a way to restart the bluetooth without restarting the whole machine?

EDIT: If you ever wonder, go to system -> adm -> services -> turn off whatever you want :)

---

### Post by olavjunior on 2008-08-24
I can't get hdmi to work on my Toshiba (intel graphics). It seems that the hdmi isn't currently supported by the driver in Hardy, and that this is fixed in the 2.4.0 driver. Does anyone know when this dirver will be implemented into Ubuntu? Or a way of updating it?

---

