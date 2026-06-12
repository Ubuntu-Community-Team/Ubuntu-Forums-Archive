---
title: "terminal start up?? aid me please"
date: 2008-09-21
forum: General Help
---

### Post by lahp on 2008-09-21
this is different from most questions asked in some ways i know i installed a server ubuntu.. but i want to view it graphicly or if some one can tell me how to correctly use it to host my website with the terminal then fine lol but i find it easyer to work through things if i have graphics any aid? 

p.s.
would a desktop version work as a server as well i just need the apache server and ubuntu so i can host my own website

---

### Post by bingoUV on 2008-09-21
I think this will work just fine for you. It should install a GUI and should boot graphically the next time
```

sudo apt-get install ubuntu-desktop

```

---

### Post by lahp on 2008-09-21
i tried that it couldnt find anything i am not connected to the internet and i tried to mount the disc it mouted read it said everything is ok and dis mounted 
i am reinstalling hopfully with a internet connection if not what should i do :(

---

### Post by Ryadt on 2008-09-21
You can install LAMP server on the desktop version. Go in synaptic > edit and select 'Mark pakages by task' and then choose LAMP server.

---

### Post by lahp on 2008-09-21
cool,
i will give this a try nothing else on the server fron then?

---

### Post by Ryadt on 2008-09-21
The server edition does not have a gui. You can install the gui with the command that bingoUV gave you. 
Here is a guide about the server: [https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

---

### Post by lahp on 2008-09-21
ok cool... but with out any connection to the internet how will i get the gui? can i download the desktop version and mount the desk and get it from that? i dont wana install the desktop version really

---

### Post by Ryadt on 2008-09-21
Try this guide: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by Ryadt on 2008-09-21
Sorry but why don't you install the gui with ```
sudo apt-get install ubuntu-desktop
```

---

### Post by lahp on 2008-09-21
wont allow me to use that command... it keeps saying can not find

---

### Post by Ryadt on 2008-09-21
> **lahp said:**
> wont allow me to use that command... it keeps saying can not find

Have you got internet connection then?

---

### Post by lswest on 2008-09-21
how are you connecting to the internet?  With ethernet and DHCP try running ```
sudo dhclient *adaptername*
``` where adaptername is the name of your card (eth0, eth1, wlan0, etc.)

Ah, it seems I was too slow to reply (got distracted by the you know you're a geek when thread)

---

### Post by lahp on 2008-09-21
ok like i said not connectted to the internet i have a wirless card installed in the laptop and the screen i am using is a tv because the origanal broke (a hdtv if u must know =P ) and i cnt get to the router with any cables so its this or nothing...
unless i can manually bring the file to the laptop ?

---

### Post by lswest on 2008-09-21
> **lahp said:**
> ok like i said not connectted to the internet i have a wirless card installed in the laptop and the screen i am using is a tv because the origanal broke (a hdtv if u must know =P ) and i cnt get to the router with any cables so its this or nothing...
unless i can manually bring the file to the laptop ?

Could you give us info about the wireless card, and the encryption your network uses (don't need the passphrase, just if it's WEP or WPA2, etc.)

Honestly, it might be easiest to install the desktop edition to the PC to get your wireless working, then install the LAMP server (if you have a fairly large hdd in the thing).

---

### Post by lahp on 2008-09-21
ok as far as i aware its a 802.11 g (it deffo isnt a A or B) 
my wirless is channel 6 with a wep

---

### Post by lswest on 2008-09-21
> **lahp said:**
> ok as far as i aware its a 802.11 g (it deffo isnt a A or B) 
my wirless is channel 6 with a wep

okay, 2 things:
Step 1: type in ```
lshw -C network
``` in the terminal, and check the entry for the network controller.  If it says driver=[something] in the configuration line, then continue, otherwise reply back here with the name of the card.

Step 2: type in ```
sudo iwconfig eth1 essid *name of network* key *passphrase* && sudo dhclient eth1
```
Exchange the name of the network with the actual name. and the passphrase will be your WEP key (if it's the passphrase and not the actual key, add an s: before it (no space, so it would read s:key) and change eth1 with the actual name of your card (run just iwconfig to see which it is, it shouldn't be eth0).

Good luck,
Lswest

---

### Post by lahp on 2008-09-21
driver=8139too

---

### Post by lswest on 2008-09-21
Should be fine, try the second command now.

---

### Post by lahp on 2008-09-21
says logical name= eht0 ? should i enter eth1 anyway

---

### Post by lswest on 2008-09-21
> **lahp said:**
> says logical name= eht0 ? should i enter eth1 anyway

does it have an ethernet card and a wireless card?  If so, that would be the ethernet card...lshw -C network should bring output for two devices, one the wireless and one the ethernet.  Please double check the output to make sure that you didn't miss the second device.

---

### Post by lahp on 2008-09-21
everything it says:
description enthernet controller
product: AR2413 802.11bg NIC
vendor: atheros communications inc.
physical id: 5
bus info: pci@0000:06:05.0
version:01
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list
configuration: latency=80 maxlatency=28 mingnt=10 x-network:1
description: ethernet interface
product: RTL-8139/8139C/8139C+
vendor: realtek semiconductor co. ltd.
physical id:7
bus info: pci@0000:06:07.0
logical name: eth0
version:10
serial: 00:0a:e4:f6:e7:63
width: 32bits
clock: 33MHz
capatibilities: bus_master cap_list ehternet physical
configurations: broadcast=yes driver=8139too driverversion=0.9.28 ip=192.168.0.104(i put this so ignore it) latency 32 maxlatancy=64 mign=32 module=8139too multicast=yes

---

### Post by lswest on 2008-09-21
This seems to be an ethernet card.  Do you know if you have both and ethernet card and wireless card in the computer?  If so, it seems the wireless card isn't being recognized by the server.  You may have more luck with the desktop install (since it may have more drivers pre-installed, I don't know for sure).

Also, it can't hurt to try the command I posted earlier using the eth0 interface, I might be wrong about the ethernet).

---

### Post by lahp on 2008-09-21
it has both installed i will give the command a try thou i trying to get a link for a gui any way... i really dont want to give up my sever one as i need it for hosting my website as im sick of my current host(and i cheap)

---

### Post by lswest on 2008-09-21
installing the Desktop doesn't impede your server at all, you can uninstall it (GUI or the programs you don't need) after setting up wireless and the LAMP server.

---

### Post by lahp on 2008-09-21
hmm ok i will look into this

---

### Post by lswest on 2008-09-21
Seems to be the best option I can come up with.  Maybe someone will post a different solution here.

---

### Post by lswb on 2008-09-21
I'm not sure what your goal or problem is exactly, but it appears you want to enable wireless on the server?

Anyway, try these commands to identify your interfaces:

ifconfig -a|more

You'll see a few paragraphs of output, the first line of each paragraph will indicate what type of interface it is. Ethernet interfaces could be either wired or wifi. Usually the 1st wired interface gets the etho name.

Now type

iwconfig|more

In the output this time you'll see most interfaces are reported with "no wireless extensions" The wireless interface will be clearly recognizable by the information provided. It may be something like eth1, wlan0, ath0, or a similar name. Now use that name instead of eth1 with the iwconfig command line that lswest posted.

From the info you have already posted it looks like you have an atheros wireless adapter so you probably should install the madwifi-tools package, which has tools specific to this make of adapter.

---

