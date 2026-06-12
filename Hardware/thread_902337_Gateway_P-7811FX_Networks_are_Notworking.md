---
title: "Gateway P-7811FX Networks are Notworking"
date: 2008-08-27
forum: Hardware
---

### Post by Giblet5 on 2008-08-27
8.04.1 (Hardy) fresh install.
(2.6.24-19-generic)
Gateway P-7811FX laptop.

Neither network interface works. (Gig & WiFi)

Hardware tests yield the following errors:
Marvell Technology Group Ltd. Unknown device 4380 (rev 10)
Intel Corporation Unknown device 4232

'lspci -n' yields the obvious entries for these interfaces:
11ab:4380
8086:4232

All I have are Vista drivers and ndiswrapper can't use them.

I can't even find out what chips the P-7811FX uses for networking w/o ripping the skins (and warranty) off the thing.

The good news: for a laptop that was released at the middle of this month, only the network interfaces have a problem....although I haven't tried installing an nvidia driver for the 9800M GPU...

"Bleeding Edge": Not just pretty words...

----------

Ibex daily build doesn't detect a network controller either...

----------

I got the wireless network adapter working by using the great instructions provided at this link:
[http://ubuntuforums.org/showthread.php?p=5650315](http://ubuntuforums.org/showthread.php?p=5650315)

I guess I'll have to wait on the Marvell Gb adapter.

---

### Post by Giblet5 on 2008-08-28
To fix the gigabit ether NIC on the P-7811FX:

Download the Marvell driver via:
[http://www.marvell.com/drivers/driverDisplay.do?driverId=153](http://www.marvell.com/drivers/driverDisplay.do?driverId=153)

Make sure you have the build-essential package (you can get it from the install CDROM).

```
sudo bash #easier
cd /tmp
tar xjf ~/install_V10.*.bz2
cd DriverInstall
ln -s /usr/src/linux-headers-2.6.24-19-generic /usr/src/linux
bash install.sh
```

You'll get some prompts about the older sk98lin module. Marvell recommends removal, but it works to just deactivate it via the prompts that the script produces.

When it's done:
```
modprobe sk98lin
```

and watch your ethernet connector light up.


The above worked briefly for the Intel 5100 WiFi chip, but it no longer works and I can't figure out why.

The wlan0 interface gets configured but (perhaps because of the iwlwifi wmaster0 interface to the mac80211 module) stays down. Grr.

---

### Post by davbren on 2008-09-01
hmmm good guide, its the first time I managed to compile the driver finally however the ethernet still doesn't work... I'm not sure why now. Its the most recent driver so it should work... but it doesn't any ideas?

Other than that, its a good guide :)

---

### Post by Giblet5 on 2008-09-03
> **davbren said:**
> hmmm good guide, its the first time I managed to compile the driver finally however the ethernet still doesn't work... I'm not sure why now. Its the most recent driver so it should work... but it doesn't any ideas?

Other than that, its a good guide :)


Heh. A "good guide" dies immediately because there are no further questions.

You did the "modprobe sk98lin" (as superuser) command and the ethernet port didn't wake up?

You DO have a live 10/100/1000 cable plugged in to the RJ45 jack, right?

The hard-lan is 100% reliable for me. It even wakes up from suspend OK.

The Wi-Fi is another matter and I'm considering replacing the P-7811FX's WiFi card with an Intel 4965AGN ($39US at TigerDirect). The 5100AGN card (what ships with the FX) sucks rancid mandrill toejam under Linux OR under Vista.

---

### Post by davbren on 2008-09-03
hehe, I do have the cable in and still nothing... I've contacted Marvel and they are trying to figure it out...

I'll let you know what happens.

---

### Post by Keith12125 on 2008-09-11
I'm getting an error during compilation. I have a fresh install of Ubuntu 8.04.1 amd64. 

```

Check kernel headers (Kernel:2.6.24 == Header:2.6.24)               [   OK   ]
Check kernel functions (Changed: nothing)                           [   OK   ]
Compile the kernel (error)                                          [ failed ]

```

---

### Post by lennartack on 2008-09-12
> **Keith12125 said:**
> I'm getting an error during compilation. I have a fresh install of Ubuntu 8.04.1 amd64. 

```

Check kernel headers (Kernel:2.6.24 == Header:2.6.24)               [   OK   ]
Check kernel functions (Changed: nothing)                           [   OK   ]
Compile the kernel (error)                                          [ failed ]

```

Same for me with x86.

---

### Post by Javaslinger on 2008-09-19
I'm trying to install ubuntu 8.04 on this same laptop and received an error shorty into the installation.

Did you guys have any troubles getting it to install?

I hear the SATA drive may be a problem for Ubuntu.

I'm a total linux newbie, so if you can, stay very simple.

Thanks,

Javaslinger

---

### Post by Keith12125 on 2008-09-20
I installed 8.04.1 amd64 without any problems. Ubuntu doesn't pick up the Marvell Yukon Ethernet or the Intel 5100 wireless on its own. You can compile the drivers yourself... however, from what I've read Ibex (8.10) will support both of these drivers. I'm just waiting for its release.

---

