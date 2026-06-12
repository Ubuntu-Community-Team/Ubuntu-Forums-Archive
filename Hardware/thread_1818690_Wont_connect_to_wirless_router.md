---
title: "Wont connect to wirless router"
date: 2011-08-05
forum: Hardware
---

### Post by mark5656 on 2011-08-05
Hi, today i did a fresh install of ubuntu 11. the only problem i have with it, is that it wont connect or find any wireless router. im using a cable for now, but need to get wireless soon. ive looked around and heard i need to see if my wifi chip is compatible and stuff, but dont have enough info on how to do it. any help would be appreciated.
thanks

---

### Post by dog-soldier on 2011-08-05
i have the same problem when i do a install and what i have to do is reboot the router.
just unplug the router for a minute or so and plug it back in. 
when i do this my wireless works

---

### Post by mark5656 on 2011-08-05
i tried that, but it still doesnt work :confused:
anyways, i tried the iwconfig command in terminal, and it gave me this info:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

i remember someone saying something about the ESSID=, but i dont remember what it was for...

---

### Post by Jeff Morasco on 2011-08-05
I am a neophyte, but had the same problem. I am using 10.04 on an hp netbook. I typed in the name of the router in the Wireless network connections under preferences and the computer found and connected. I have since downloaded wifiradar and it 'sees' other available wireless routers. I haven't tried connecting as they are secured. I have no idea if this will be a solution for you.

---

### Post by mark5656 on 2011-08-06
i tried that too, but it didnt work, i think it cant recognize the wifi chip, or card.
this is the specs of mine:
```
Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

is this even supported?

---

### Post by plucky on 2011-08-08
> **mark5656 said:**
> i tried that too, but it didnt work, i think it cant recognize the wifi chip, or card.
this is the specs of mine:
```
Marvell Technology Group Ltd. 88E8038 PCI-E Fast Ethernet Controller (rev 14)
Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)
```

is this even supported?

Can you get a wired connection?


See [Here](http://ubuntuforums.org/showthread.php?t=1744331&highlight=AR2413)

Good Luck

---

### Post by mark5656 on 2011-08-08
yes, i can get a wired connection. but that didnt work. i think im supposed to install ubuntu 10. that might work someone told me....

---

