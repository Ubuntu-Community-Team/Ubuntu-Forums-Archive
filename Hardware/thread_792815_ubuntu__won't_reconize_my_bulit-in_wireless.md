---
title: "ubuntu  won't reconize my bulit-in wireless"
date: 2008-05-13
forum: Hardware
---

### Post by new2linux2008 on 2008-05-13
I have a hp dv9727cl. I've downloaded multiple windows drivers and ran then "Windows wireless Drivers" thing, but still no go. 



HP Pavilion Entertainment PC dv9727cl

lspci -v

03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
	Subsystem: Hewlett-Packard Company Unknown device 137a
	Flags: bus master, fast devsel, latency 0, IRQ 10
	Memory at f6000000 (64-bit, non-prefetchable) [size=64K]
	Capabilities: <access denied>

please help. really want to be able to run ubunt & I need my wireless.

---

### Post by he4Ler on 2008-05-13
Did you use the inf file from the windows driver?
you can type

sudo ndiswrapper -i name.inf
sudo depmod -a
sudo modprobe ndiswrapper

that should do it if it is the right drivers.. try another driver for win2k or something.. any of them should work :)'

---

### Post by new2linux2008 on 2008-05-14
I tried that and it didn't work. I tried all the drivers and none worked. I did find one that said it worked, that I installed via: Admin -> Windows Network Driver. But under Admin -> Network. it doesn't show anywireless at all. Even though the Windows Network Driver states it's the correct driver.

Side Note:
I'm running ubuntu amd64 version Hardy Heron 8.04

---

### Post by he4Ler on 2008-05-15
If you have AMD64 version, try this guide, that should do it:

[http://ubuntuforums.org/showthread.php?t=512828](http://ubuntuforums.org/showthread.php?t=512828)

---

### Post by new2linux2008 on 2008-05-15
THANKS, that worked. well kinda. it now shows the driver and I can see my network, but not sure on how to connect. It even tells me how good my connection to my router is, but won't actully probably a linux noob thing.

---

### Post by new2linux2008 on 2008-05-16
Thought this may help
Did iwconfig = 

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID: off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Power Management: off
          Link Quality: 0  Signal level: 0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

---

### Post by new2linux2008 on 2008-05-16
also if i type this into the terminal:
 sudo iwlist scan = well i got alot of other networks but here is the results for mine


          Cell 02 - Address: 00: 1C: 10: B0: BF: DE
                    ESSID:"linksys"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.462 GHz (Channel 11)
                    Quality:100/100  Signal level:-20 dBm  Noise level:-96 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

---

### Post by mattiast on 2008-05-16
Are you using the networktool in gnome?
Make sure you choose wep or wpa, and hex or ascii that must be right when you type in your key to the network.

if you can't get it to work, try another tool, like wifi-radar

```

sudo apt-get install wifi-radar

```

it's very easy to use..

I'm new to this so I'm not sure that I be to any help,
hope this works!

---

### Post by new2linux2008 on 2008-05-16
Thanks for the info. I installed the radar. I saw my network, I saw the signal strength, but wouldn't get a ip.

---

### Post by clb137 on 2008-05-27
> **new2linux2008 said:**
> Thanks for the info. I installed the radar. I saw my network, I saw the signal strength, but wouldn't get a ip.

use dhcp


clint

---

### Post by beornharris on 2008-06-08
Hi,

I am really hoping for a solution to this as well.  Im not such a noob, but have still spent many fruitless hours trying to get this to work.
Setup is the same (Hardy Heron 8.04 on HP Pavilion dv9727cl).  I have tried both using ndiswrapper and madwifi (with a 32 bit install) with no joy for either.  In both cases, I can get the card recognised and drivers loaded.  I can see my home network and everything looks good up until actually trying to communicate.
DHCP fails to obtain a lease.  I have tried setting a static address, again with no joy.  The router etc is fine, as I have another laptop connecting without issue.
The only thing I can think of (given that everything looks ok) is that it is the wireless "hard" switch (front-left).  Switching this seems to have no effect but I am wondering if it is preventing the wireless from connecting properly (light also stays orange).

Any thoughts?  or other experiences?

Cheers

Beorn

---

### Post by clb137 on 2008-06-09
Hi Beorn,

With the light on orange i suggest to me that you are trying to connect using WEP, are you sure that the card is reconized by ubuntu? what is the output of your lspci?

clint

---

### Post by beornharris on 2008-06-10
Hi clint

Been there, done that.  lspci shows its an Atheros, as per the post that started this thread (03:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01))
I have since opened the laptop to look at the card, but cant see any detailed markings (I dont want to rip the card apart).  You are correct that I am using WEP...I might investigate WPA (Just been lazy).
I now have a workaround for this problem ([http://ubuntuforums.org/showthread.php?t=824626](http://ubuntuforums.org/showthread.php?t=824626)) ...but will solve it (hopefully) by buying a card that works out of the box.

Thanks for your reply.

---

### Post by Bartender on 2008-06-10
My Dad has a new HP/Compaq with one of those pesky Atheros cards.  I dropped my 4965 card into his notebook and it worked like a champ.  The Vista side had to get new drivers, but the Ubuntu side saw the card and immediately put it to use.
I bought the card at Amazon (about $38 with tax).  It certainly appeared to be brand new.  Be very careful with those tiny wires and the fragile ring-and-pin connectors on the card, and be very careful about not dropping either of the two tiny screws inside the machine!!

---

### Post by dinub1 on 2008-06-10
> **he4Ler said:**
> Did you use the inf file from the windows driver?
you can type

sudo ndiswrapper -i name.inf
sudo depmod -a
sudo modprobe ndiswrapper

that should do it if it is the right drivers.. try another driver for win2k or something.. any of them should work :)'

That may be fine only that it may need ndiswrapper re compilation, like it needed on mine. After that it should work fine with native Windows driver.

---

