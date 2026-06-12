---
title: "Wifi-radar"
date: 2007-05-04
forum: Hardware &amp; Laptops
---

### Post by ricardovich on 2007-05-04
After upgrading to Feisty and configuring my wifi, I noticed that sometimes my wireless would act flaky. Specifically, it wouldn't always restart after suspend or hibernation which is crucial to my laptop experience. At first I thought that this was do to my wifi being configured with the bcm43xx-fwcutter driver as oppose to ndiswrapper as I had used in Edgy. However I have not had any problems sense I switched to wifi-radar as opposed to the default network-manager. This however required some configuration.

To fully switch to wifi-radar, first install it.
```
sudo apt-get install wifi-radar
```

Then remove network manager.
```
 sudo aptitude remove network-manager network-manager-gnome
```

Then open wifi-radar and and connect to your wireless.

Now allow wifi-radar to start at boot.
Open System -> Preferences -> Sessions and click new under Startup Programs.
Name it wifi-radar and insert the command: wifi-radar -d
This will let wifi-radar open in the background on startup and connect to preferred wireless networks.
Also unclick Network Manager if it isn't already.

Now we have to get wifi-radar to restart after suspend or hibernate.

```
sudo gedit /etc/acpi/resume.d/97-wifistart.sh
```
Insert:
```
wifi-radar -d
```
and save and exit.
No make the script executable:
```
sudo chmod +x /etc/acpi/resume.d/97-wifistart.sh
```

Reboot and test.

Note this has worked on my laptop and may not transfer to yours!
```

lspci | grep Wireless
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
```

My specs:
Presario V2000 w/AMD Sempron (Not Pentium M, and not the Intel wireless chipset that also ships w/V2000)

---

### Post by noisebeard on 2007-05-11
I did a fresh install of 7.04 and couldn't get the nm-applet to connect to my router at all.  It showed the SSIDs in the dropdown list but never obtained an IP or synced with the router.

I used your instructions and installed wifi-radar and now my wireless works effortlessly.  Maybe it's just a bug in the new nm-applet, but yeah, didn't work at all.  And apparently, I'm not the only one with this problem.  

Thanks for the advice on the switch to wifi-radar.

---

### Post by Rescue9 on 2007-05-12
This is great information. I've made the changes... now it's just a matter of days to test it. Thanks

---

### Post by iAMbigFISH on 2007-05-12
I tried this but the results are the same :(


I get the error: Could not get IP address
and this too: SET failed on devcie ath0 ; Invalid argument


Any ideas?

---

### Post by bakermiller on 2007-05-12
i tried this, and i lost my network-manager applet icon and i can't get it back.

I tried reinstalling the g-n-m, the connection is OK, but there is still no icon in the panel to show me the APs and my wired status,
it's not in the 'add to panel' window, and 
When i try nm-applet in the terminal, the prompt just seems to look around without really doing much. 

stuck...

anyone know how to get teh nm icon back to the panel??

---

### Post by bakermiller on 2007-05-12
fine.

it was in:  panel > add to panel >  utilities> notification area(?!)

and i thought it would be called network manager. 
my error

---

