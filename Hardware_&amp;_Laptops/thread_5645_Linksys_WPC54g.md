---
title: "Linksys WPC54g"
date: 2004-11-20
forum: Hardware &amp; Laptops
---

### Post by brdweb on 2004-11-20
I have sucessfully hooked up to my home 54G network with WEP using my Linksys WPC54G pcimia card. I went to the linksys site, downloaded the latest windows driver for the card, and installed it using ndiswrapper. Took a little bit of trial and error plus checking the ndiswrapper site to get my settings correct but now I have a full strength connection.

---

### Post by ramzez on 2004-11-20
can you write step by step guide, please?

cheers.

---

### Post by danpre on 2004-11-21
Yeah - I have the same PCMCIA card - fighting with it for a few weeks now - a can't get it working

Any chances for help from you? 

DANIeL

[QUOTE=brdweb]I have sucessfully hooked up to my home 54G network with WEP using my Linksys WPC54G pcimia card. I went to the linksys site, downloaded the latest windows driver for the card, and installed it using ndiswrapper. Took a little bit of trial and error plus checking the ndiswrapper site to get my settings correct but now I have a full strength connection.[/QUOTE]

---

### Post by ramzez on 2004-11-24
actually it is very simple

install ndiswrapper from synaptic package manager.

then download [ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip)

unzip the downloaded zipfile, find the correct .inf (lsbcmnds.inf in my case) file and run
sudo ndiswrapper -i lsbcmnds.inf 

 load the module and make it reload on reboot:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules 

in gnome, goto networking and put your settings.

hope it helps.

---

### Post by danpre on 2004-11-26
[FONT=Tahoma]ramirez:

thx

but it is too late now 

I was plaing around with linuxant driverloader it was working very fine for almoust one mounth so I have both a license - I spent 20 bucks

well - good thing about it - 20 bucks for a company working for LINUX

thanks anyway


DANIeL

[QUOTE=ramzez]actually it is very simple

install ndiswrapper from synaptic package manager.

then download [ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip)

unzip the downloaded zipfile, find the correct .inf (lsbcmnds.inf in my case) file and run
sudo ndiswrapper -i lsbcmnds.inf 

 load the module and make it reload on reboot:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules 

in gnome, goto networking and put your settings.

hope it helps.[/QUOTE][/FONT]

---

### Post by Joshua on 2005-03-15
It took me quite a while to figure out how to get this working, so I wanted to post something about it and possibly save someone a little time.

I've got an old Gateway Solo 5100 and I bought the WPC54G.  My home network is run on the WRT54G.  My solution might not apply to normal Ubuntu users because of my installation method, so I'll describe it.

My CD-ROM, apparently, doesn't like normal sized CDs.  When I try to install Ubuntu it gets hung up towards the end while installing the system base packages.  It does fine, however, with the Debian netinstall CDs on the smaller 80mm disks.  So I installed a minimal Debian system with the netinstall CD and then changed the APT repositories to the Ubuntu Hoary ones.  Then, I upgraded (it took a little investigation to complete dependencies and stuff).  Once that was done, I installed the linux-686 packages so that I would have the most recent Ubuntu Kernel.

Then, I followed the normal instructions for installing ndiswrapper and the windows drivers.  Ndiswrapper is in the 2.6.10 Kernel so that was easy with "modprobe ndiswrapper".

Anyway, once all that was done, I couldn't get the card to work.  iwlist wlan0 scan said that it couldn't pick anything up.  ifup wlan0 said it couldn't get a dhcp response.  After loads of trying different drivers and reloading modules, etc. I looked at the dmesg output and saw that there was some module called acx_pci that seemd to be trying to operate my card.  There was even a little warning that my card used proprietary drivers and that acx_pci might not work.  So I rmmod ndiswrapper, rmmod acx_pci, modprobe ndiswrapper.  BINGO!  ifup wlan0 and everything is hunky-dory.  Now I need to figure out how to keep acx_pci from loading on boot and how to get ndiswrapper to load on boot.  If anyone knows, please let me know.  I've tried ndiswrapper -m.  It says that it's good, but when I boot - no ndiswrapper...

---

### Post by YorYor on 2005-04-02
Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.

---

### Post by epb613 on 2005-05-02
[QUOTE=YorYor]Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.[/QUOTE]
 Wow thanks so much - this fiixed my wifi after it not working for months!

---

### Post by jon_hill987 on 2005-05-03
[QUOTE=YorYor][http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).[/QUOTE]

I get a 404 from that, i'll try your summary though and see if it works. I havn't got the same wifi card as you but i'm ready to try anything....

---

### Post by Dillius on 2005-05-04
I'm having an infinite ammount of trouble with this card. Using the WPC54G v.2. I've been trying a number of drivers and such. I've found that there are 2 .inf files that have differet effects.

"lsbcmnds.inf" causes no errors, but ndiswrapper -l only shows driver present, and says nothing about the hardware

"lstinds.inf" shows in ndiswrapper as both driver present and hardware present, but whenever i try to add ndiswrapper with modprobe, I have the following error:

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
PCI: Setting latency timer of device 0000:02:00.0 to 64
ndiswrapper (ndis_init_one_pci:95): Windows driver couldn't initialize the device (C0000001)
lstinds: probe of 0000:02:00.0 failed with error -22
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18 ) added

Also, the Device Manager keeps listing this card as some Texas Instruments ACX 100 card.... I had to blacklist some other drivers so they wouldnt load due to hotplug, but I can't be sure that worked correctly(The drivers were acx100 and acx_pci).

---

### Post by danpre on 2005-05-04
[QUOTE=Dillius]I'm having an infinite ammount of trouble with this card. Using the WPC54G v.2. I've been trying a number of drivers and such. I've found that there are 2 .inf files that have differet effects.

"lsbcmnds.inf" causes no errors, but ndiswrapper -l only shows driver present, and says nothing about the hardware

"lstinds.inf" shows in ndiswrapper as both driver present and hardware present, but whenever i try to add ndiswrapper with modprobe, I have the following error:

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
PCI: Setting latency timer of device 0000:02:00.0 to 64
ndiswrapper (ndis_init_one_pci:95): Windows driver couldn't initialize the device (C0000001)
lstinds: probe of 0000:02:00.0 failed with error -22
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18 ) added

Also, the Device Manager keeps listing this card as some Texas Instruments ACX 100 card.... I had to blacklist some other drivers so they wouldnt load due to hotplug, but I can't be sure that worked correctly(The drivers were acx100 and acx_pci).[/QUOTE]

If you want to - I can send you windows drivers I'm using:
net8180.inf
rtl8180.sys

those are older linksys drivers - a new ones don't work with my card

DANIeL

---

### Post by Dillius on 2005-05-04
> If you want to - I can send you windows drivers I'm using:
net8180.inf
rtl8180.sys

those are older linksys drivers - a new ones don't work with my card

That would be excellent

I'm kinda wondering if I've been doing something wonrg the whole time. I have the inf file loaded, but i've never done anything involving any of the .sys files. Do they have to be placed in the /etc/ndiswrapper folder with the inf file? Or are they not important?

I'll be happy whatever it takes to get it to work... i'm just really curious about this error message i'm getting.

---

### Post by Narzuhl on 2005-05-17
Ok So i have been trying this card for about 2 weeks on a Toshiba Portege 3490CT.
I have tried Several big named and some small names Linux Distros and a few BSD distros and look around for one that would work best with this laptop. IT unit has a PCMCIA cd rom and no floppy and as it is older i did not want to buy much for it. So i decided to try Kubuntu 5.04 I have tried KDE in the past and for some reason the newest version i have trouble wiith it, so i switched to ubuntu 5.04 instead. Well Gnome is very nice now (I always thought it was boring) and with the excelent help from this forum (including this thread) i managed to get my WPC54g working and can use the card now.  \\:D/ . So thats to everyone for a great job and way more help than most other distros

---

### Post by kramins on 2005-05-24
I have been banging my head aganst the wall for sometime now, I have read and re-read all the the information i can find, and for the life of me i can not get my card to work or even power up. I know my system see's the card. hell it gets the MAC off the card, but i can not get it to power up. any idea's?

---

### Post by danpre on 2005-05-25
[QUOTE=kramins]I have been banging my head aganst the wall for sometime now, I have read and re-read all the the information i can find, and for the life of me i can not get my card to work or even power up. I know my system see's the card. hell it gets the MAC off the card, but i can not get it to power up. any idea's?[/QUOTE]

Do you have "pcmcia" service stared at system boot?

---

### Post by Zodiac on 2005-05-27
I get this error when I try to modprobe:

root@valhalla:/etc/ndiswrapper # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted


What's the dillio??

---

### Post by Zodiac on 2005-05-27
[QUOTE=Dillius]I'm having an infinite ammount of trouble with this card. Using the WPC54G v.2. I've been trying a number of drivers and such. I've found that there are 2 .inf files that have differet effects.

"lsbcmnds.inf" causes no errors, but ndiswrapper -l only shows driver present, and says nothing about the hardware

"lstinds.inf" shows in ndiswrapper as both driver present and hardware present, but whenever i try to add ndiswrapper with modprobe, I have the following error:

ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
PCI: Setting latency timer of device 0000:02:00.0 to 64
ndiswrapper (ndis_init_one_pci:95): Windows driver couldn't initialize the device (C0000001)
lstinds: probe of 0000:02:00.0 failed with error -22
ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.18 ) added

Also, the Device Manager keeps listing this card as some Texas Instruments ACX 100 card.... I had to blacklist some other drivers so they wouldnt load due to hotplug, but I can't be sure that worked correctly(The drivers were acx100 and acx_pci).[/QUOTE]

I am having this exact same problem... doe sanyone have any further insight on this issue?

---

### Post by kramins on 2005-05-28
[QUOTE=danpre]Do you have "pcmcia" service stared at system boot?[/QUOTE]
yep, it's started. but still not power to my pc card.

also modprobe, seems to work but i do not get any msg about it succefuly installing ndiswrapper, ndiswrapper when i install the inf forces RadioState to 1

---

### Post by nickerbocker on 2005-05-30
Hello.  I have this WPC54G ver4 card.  I followed the quoted guide.  When I do:
"sudo echo ndiswrapper >> /etc/modules"
I get an access denied.  When I do "sudo iwlist wlan0 scan" I get a "wlan0: interface not found." I'm trying to install this on an IBM Thinkpad T22.  If anyone has any help they can send my way, I'd really appreciate it!

-nickerbocker


[QUOTE=YorYor]Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.[/QUOTE]

---

### Post by danpre on 2005-05-30
[QUOTE=nickerbocker]Hello.  I have this WPC54G ver4 card.  I followed the quoted guide.  When I do:
"sudo echo ndiswrapper >> /etc/modules"
I get an access denied.  When I do "sudo iwlist wlan0 scan" I get a "wlan0: interface not found." I'm trying to install this on an IBM Thinkpad T22.  If anyone has any help they can send my way, I'd really appreciate it!

-nickerbocker[/QUOTE]
I don't remember how does it work with ndiswrapper, but try to scan eth1 or eth0 - with driverloader drivers I have my wifi card with eth1 symbol.

---

### Post by nickerbocker on 2005-05-30
[QUOTE=danpre]I don't remember how does it work with ndiswrapper, but try to scan eth1 or eth0 - with driverloader drivers I have my wifi card with eth1 symbol.[/QUOTE]

This is what I'm seeing:
nic@nic:~/linksys$ sudo ndiswrapper -l
Installed ndis drivers:
linksys driver present

and when i so a lspci -v, i get
...
0000:02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
        Subsystem: Linksys: Unknown device 0029
        Flags: medium devsel, IRQ 9
        I/O ports at 4000 [disabled] [size=32]
        Memory at 18400800 (32-bit, non-prefetchable) [disabled] [size=32]
        Memory at 18400000 (32-bit, non-prefetchable) [disabled] [size=2K]
        Capabilities: [40] Power Management version 2
...
it looks like the driver isn't picking up my card.
The only network devices I can find are eth0 and lo

Thank you for  replying.
-nickerbocker

---

### Post by oshkar on 2005-06-01
[QUOTE=nickerbocker]
it looks like the driver isn't picking up my card.
The only network devices I can find are eth0 and lo

Thank you for  replying.
-nickerbocker[/QUOTE]

That is exactly what I get after following all the steps given.

---

### Post by Narzuhl on 2005-06-02
[QUOTE=nickerbocker]it looks like the driver isn't picking up my card.
The only network devices I can find are eth0 and lo

Thank you for  replying.
-nickerbocker[/QUOTE]


I had the same problem. I have to fiddle with my Bios, i changed my controller mode in the bios to CardBus/16-bit
See what you have in the bios and if you can change your PCMCIA controller.

---

### Post by Seq on 2005-06-02
Hi there.

Me and Kramins have been sitting down working on his wireless card. It seems there is a native Linux driver for the card, and that is the approach we've been taking.

[acx100 on Sourceforge](http://acx100.sourceforge.net/) 

Your mileage may vary since it looks like the different vendors may use different radios in conjunction with the acx100/acx111 chip.

For reference, Kramins' has a Linksys WPC54GV2, which uses the acx111 chipset and radio type 0x16. The first issue came up when ubuntu managed to find the firmware for the card, *TIACX111.BIN-2.6.10-5-686* (naming will vary depending on kernel), but not for the radio. 

The solution for the radio firmware was to find the driver cd that came with the card, and copy radio16.bin to /lib/hotplug/firmware/RADIO16.BIN , and then symlink that to RADIO16.BIN-2.6.10-5-686 (again, depending on kernel version).

```
cd /lib/hotplug/firmware
sudo cp /media/cdrom/radio16.bin RADIO16.BIN
sudo ln -s RADIO16.BIN RADIO16.BIN-2.6.10-5-686
```

Now, there are no really critical sounding warnings (other than the bunch that the driver throws anyway).

ifconfig -a shows the interface exists, and iwconfig recognizes it as wireless, but despite this we still cannot get the interface to actually work at all, any way, whatsoever. Unable to scan, or associate.

---

### Post by oshkar on 2005-06-04
[QUOTE=Narzuhl]I had the same problem. I have to fiddle with my Bios, i changed my controller mode in the bios to CardBus/16-bit
See what you have in the bios and if you can change your PCMCIA controller.[/QUOTE]

I can't modify my BIOS (I supose it's blocked by COMPAQ -I got a Compaq Presario 1700 Series-) so I don't know what to do right know, and my card is not supported by the generic acx100 Linux Driver given in the [previous message](http://ubuntuforums.org/showthread.php?t=5645&goto=newpost) .

So, I'm hooked to the wire again  [-X

Thanks anyway.

---

### Post by Nad1 on 2005-06-11
Hi,

I try to install my WPC54G and i have some problems :

root@portable:/home/nadir # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

How do ?

Thx

---

### Post by YorYor on 2005-06-11
[QUOTE=Nad1]Hi,

I try to install my WPC54G and i have some problems :

root@portable:/home/nadir # modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

How do ?

Thx[/QUOTE]
 root@portable:/home/nadir #**_sudo_** modprobe ndiswrapper

Try this.

---

### Post by Nad1 on 2005-06-11
>  root@portable:/home/nadir #sudo modprobe ndiswrapper

Try this. 

Same error ...

root@portable:/home/nadir # sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

---

### Post by gordon_06fr on 2005-06-17
[QUOTE=YorYor]
1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.[/QUOTE]

hey there,
This works perfect for me.... BUT how do I get this installed so that it reloads automatically when I start ubuntu? Kinda a pain to go via terminal and enter the commands manually each time...  :|

---

### Post by P235 on 2005-06-25
[QUOTE=YorYor]Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.[/QUOTE]

Hey, I followed Yor Yor's advice and so far it's gone smoothly until the iwlist wlan0 scan step.  I've set up wlan0 under gnome's networking but when I scan I only get the following:

sudo iwlist wlan0 scan
wlan0     No scan results

Also, step 3f. with sudo echo ndiswrapper >> /etc/modules didn't work for me either.  I get a permission denied.

Any suggestions will be most welcome.

---

### Post by P235 on 2005-06-25
I realised that I couldn't connected to the internet because I had two connections active in the same time.  I had a lan and a wireless connection active.  I couldn't use the wireless until I ifdown eth0.  So, that's that.  This post is very helpful

---

### Post by gregbazar on 2005-07-27
Thought I would keep this thread up to date with some more tips on the Linksys 54G card.

I initally tried ndiswrapper with the most recent drivers on Linksys' site, but they did not work.  I suspect they are for the V2 cards, and mine was a V1.2 card (says so on the sticker on the back of the card).

The most recent drivers showed the card, its MAC address etc, but I couldn't scan, or see any wireless activity.

I uninstalled the drivers with "ndiswrapper -e" and then fell back to the next oldest  drivers (also available from the Linksys website).

When I installed via ndiswrapper and did an iwlist (as noted earlier in this thread), it came right up.  Adding ndiswrappers to /etc/modules made it boot right up next time, flawless.

Thanks for the help all.  :D

---

### Post by The_Necromancer on 2005-08-09
Hello, I'm a newbie to Ubuntu and semi-knowledgeable of the Linux. When trying the instructions quoted everything works fine until I try "sudo modprobe ndiswrapper". The terminal gives me this statement:

sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

ndiswrapper is listed within the "/etc/modules" file. Any suggestions... anyone?



[QUOTE=YorYor]Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.[/QUOTE]

---

### Post by XStylus on 2005-08-09
[QUOTE=The_Necromancer]Hello, I'm a newbie to Ubuntu and semi-knowledgeable of the Linux. When trying the instructions quoted everything works fine until I try "sudo modprobe ndiswrapper". The terminal gives me this statement:

sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation not permitted

ndiswrapper is listed within the "/etc/modules" file. Any suggestions... anyone?[/QUOTE]

I'm in the same boat. I see lots of people with this problem, but no solutions anywhere.

I installed the driver okay, and ndiswrapper -l reports "driver present, hardware present", but "sudo modprobe ndiswrapper" keeps spitting back "operation not permitted". This is a fresh install of Ubuntu as well.

I'm working with a Linksys WUSB54AG and a Netgear WG111U. Both have the same problem. Whichever one I get working is the one I keep, the other is going back to the store.

---

### Post by 1337G33K on 2005-08-13
Hi guys, I guess I'm one of those chumps who's stuck with this card...

Anyways, I followed this great walkthrough but I could only get as far as step 3g
```
sudo iwlist wlan0 scan
```

However, when I tried to connect to the router with
```
sudo iwconfig wlan0 channel 6 essid saturn mode Managed
```

I get no response what-so-ever.  Just the prompt again.  So then I tried to ping the router (192.168.1.1), and I get "Network cannot be reached"...

What am I missing?  (I already disabled my wired connection with "sudo ifdown eth0")  ](*,)

---

### Post by The_Necromancer on 2005-08-13
Well, I found some useful info at [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

It helped me get to the point where my wireless card now shows up in the GUI "System > Administration > Networking" console. Still no connection, though. Guess I'll continue searching.

---

### Post by The_Necromancer on 2005-08-15
I finally got a connection through my wireless! I just have to figure out how to make my card search for my access point without having to broadcast its SSID, then get WPA working. The solution seemed rather simple, it waqs just a matterof retracing steps and looking at them differently- and a little trial-and-error.

---

### Post by nige on 2005-08-20
If you have having problems with the WPC54G v 1.2 you can get the drivers for it from [http://theweirdone.iwarp.com](http://theweirdone.iwarp.com). I am currently using those drivers and I have managed to get WPA working flawless expect for using '#' inside a pass phrase.

I hopefully this could help those of you with these problems.
I am annoyed at linksys for not producing linux drivers for the WPC54G or for having so many different versions of it.

I hope this helps
Regards

-Nige

---

### Post by DarkDisaster on 2005-08-23
[QUOTE=YorYor]Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0
[/QUOTE]

Why did you change RadioState|1 to 0 ? What for?! I can't understand...
I done that and my wpc54g doen't blink with activity.... 
At the gnome network settings I deactivate eth0 and activate wlan0 and put my wep key. It's necessary to put the ESSID in those settings?!
Where did I fail ?!

is there an wlanassistant for gnome?!
It would help so much!

---

### Post by ISBB on 2005-08-24
Just thought i would sign up and thank you guys for the wonderful help...

I followed those lovely how-to on the first page.. and it worked flawlessly.. :D

Thank you guys very much. \\:D/ 

Thanks again.. :D

btw this is on a dell inspiron 7500 p3 500 w/ 128mb ram.. ubuntu install flawlessly and with that little work around everything works perfect for me... very happy camper with this distro... Mucho props to the guys that put it together.. :D

---

### Post by YorYor on 2005-08-24
[QUOTE=DarkDisaster]Why did you change RadioState|1 to 0 ? What for?! I can't understand...
I done that and my wpc54g doen't blink with activity.... 
At the gnome network settings I deactivate eth0 and activate wlan0 and put my wep key. It's necessary to put the ESSID in those settings?!
Where did I fail ?!

is there an wlanassistant for gnome?!
It would help so much![/QUOTE]
 There was a bug which caused setting RadioState 1 to be interpreted as "Radio Off" instead of the logical Radio On. I'm not sure whether it still exists with the current version of the ndiswrapper-tools package, but it did when I installed it in the past.

There isn't any of those nice Windows wireless GUI that integrates flawlessly yet, but Wifi Radar comes close. You ought to try disabling your WEP and broadcast your SSID first, to see if "iwlist scan" picks it up. If it does, then your card is working. I never use WEP cause it slows things down (a little), so I use MAC address access control. Hard and fast, no breaking in far as I know. They're gonna have to figure out your MAC address before they can even try to spoof it. Not sure how easy it is, but they'd have to be pretty near you to try that!

I also didn't use the gnome network settings, everything was commandline, so I can't advise on that too. And yes, you have to provide your SSID in that network page... it doesn't pick things up itself.

Good luck!

>> ISBB, great to know it worked for you... have fun!

---

### Post by blazerte on 2005-08-30
Whoops! The followng is for ubuntu V5.04 (with all updates), not warty:

The existing acx_pci driver in Hoary didn't work with my Linksys WPC45G V2.0,
so I tried the WinXP drivers with ndiswrapper. I do everything in the root
terminal. To start, just in case: 
ifdown wlan0 
To stop the acx_pci driver from hogging the device, put acx_pci in 
/etc/hotplug/blacklist (use gedit or echo) and: 
rmmod acx_pci 

The Linksys WPC45G V2.0 came with two drivers on the cdrom, LSTINDS.INF and
lsbcmnds.inf. Only LSTINDS.INF provides WinXP drivers, which are required by
ndiswrapper. So use that one. Mine has the same date and Version number as
that on the Linksys website, so I didn't download anything.
Put in the Linksys cdrom, then:
cd /cdrom
ndiswrapper -i LSTINDS.INF
Afterwards, I did not have to edit anything in /etc/ndiswrapper. 
modprobe ndiswrapper
This worked fr me. Not sure why others are having probs. Then: 
tail /var/log/syslog 
should reveal how the LSTINDS driver is being used by ndiswrapper to access
device wlan0. If not, you've got problems to sort out.

I editted /etc/network/interfaces to add a few options to wlan0. Some of 
this can be done with ubuntu's graphical System/Admin/Networking utility, 
especially if you are using DHCP to automatically retrieve the paramters.

Then bring it up:
ifup wlan0

It worked for me. If you also have a wired connection, make sure eth0 is 
not the default and is "down".

---

### Post by KVTL on 2005-09-03
I got the acx_pci to work a little. I got the leds blinking and also viewed [www.vg.no](www.vg.no) with the driver that was shipped with ubuntu. 

What I did was:

sudo rmmod acx_pci
sudo modprobe acx_pci /etc/init.d/networking restart

P.S I have a version 2 with acx111 chipset.

also the acx_pci module is outdated in ubuntu since it ask for RADIO16.BIN, I read this at acx100.sourceforge.org' s mailing list.

I hope it will get better support in breezy.

KVTL \\:D/

---

### Post by PSyMastR on 2005-09-08
Never mind.  It detects it.

---

### Post by Bluefire on 2005-09-11
[QUOTE=blazerte]Whoops! The followng is for ubuntu V5.04 (with all updates), not warty:

The existing acx_pci driver in Hoary didn't work with my Linksys WPC45G V2.0,
so I tried the WinXP drivers with ndiswrapper. I do everything in the root
terminal. To start, just in case: 
ifdown wlan0 
To stop the acx_pci driver from hogging the device, put acx_pci in 
/etc/hotplug/blacklist (use gedit or echo) and: 
rmmod acx_pci 

The Linksys WPC45G V2.0 came with two drivers on the cdrom, LSTINDS.INF and
lsbcmnds.inf. Only LSTINDS.INF provides WinXP drivers, which are required by
ndiswrapper. So use that one. Mine has the same date and Version number as
that on the Linksys website, so I didn't download anything.
Put in the Linksys cdrom, then:
cd /cdrom
It worked for me. If you also have a wired connection, make sure eth0 is 
not the default and is "down".[/QUOTE]


This guide really helped me and got me further then before.  Finally, ndiswrapper recognizes the hardware.

However, I still have no lights on the card, and this is what my log gives:

```
charly@ubuntu:~/sources$ tail /var/log/syslog
Sep 11 14:28:34 localhost loadndisdriver: loadndisdriver: main(462): version 1.0rc2 start ed
Sep 11 14:28:34 localhost udev[8278]: creating device node '/dev/ndiswrapper'
Sep 11 14:28:34 localhost kernel: ACPI: PCI interrupt 0000:03:00.0[A] -> GSI 20 (level, l ow) -> IRQ 20
Sep 11 14:28:34 localhost kernel: ndiswrapper (ndis_init_one_pci:95): Windows driver coul dn't initialize the device (C0000001)
Sep 11 14:28:34 localhost kernel: lstinds: probe of 0000:03:00.0 failed with error -22
Sep 11 14:28:34 localhost kernel: ndiswrapper: driver lstinds (Linksys,03/10/2004,6.0.0.1 8) added
Sep 11 14:29:15 localhost gconfd (root-8310): starting (version 2.10.0), pid 8310 user 'r oot'
Sep 11 14:29:15 localhost gconfd (root-8310): Resolved address "xml:readonly:/etc/gconf/g conf.xml.mandatory" to a read-only configuration source at position 0
Sep 11 14:29:15 localhost gconfd (root-8310): Resolved address "xml:readwrite:/root/.gcon f" to a writable configuration source at position 1
Sep 11 14:29:15 localhost gconfd (root-8310): Resolved address "xml:readonly:/etc/gconf/g conf.xml.defaults" to a read-only configuration source at position 2
```

---

### Post by PSyMastR on 2005-09-17
Ok, I installed ndiswrapper.  I installed the correct drivers for my computer's wireless card:
WPC54g version 1.3
I used this app that decects that both the hardware and driver is present, but it wont connect to my wireless network, and the network name and password are correct.  What am I doing wrong?  This is driving me crazy!

---

### Post by impf0s on 2005-09-24
```
martin@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:0F:66:A3:92:2A
                    ESSID:"Buchmayr"
                    Protocol:IEEE 802.11b
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:0/100  Signal level:-28 dBm  Noise level:-256 dBm
                    Encryption key:off
                    Bit Rate:1 Mb/s
                    Bit Rate:2 Mb/s
                    Bit Rate:5.5 Mb/s
                    Bit Rate:11 Mb/s
                    Bit Rate:6 Mb/s
                    Bit Rate:9 Mb/s
                    Bit Rate:12 Mb/s
                    Bit Rate:18 Mb/s
                    Bit Rate:24 Mb/s
                    Bit Rate:36 Mb/s
                    Bit Rate:48 Mb/s
                    Bit Rate:54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0

martin@ubuntu:~$ sudo iwconfig wlan0 channel 8 essid Buchmayr mode Managed
martin@ubuntu:~$ sudo ifup wlan0
Ignoring unknown interface wlan0=wlan0.
martin@ubuntu:~$

``` 


Whats this Ignoring unknown interface thing?

What shall i do? It won't work! Please help!!


~~UPDATE~~

YEAH I DID IT NOW!

But theres a problem just existing:
How to load wlan0 in the boottime?

When im rebooting i have to do all things in the terminal again....
( sudo modprobe ndiswrapper
sudo iwconfig wlan0 channel 6 essid Buchmayr mode Managed
sudo ifdown eth0
sudo ifuo wlan0 )

---

### Post by Anthem on 2005-09-24
I'm actually using Breezy, but I saw this thread and had to ask.

Has anyone successfully gotten WPA working with this card?

---

### Post by nukedathlonman on 2005-10-04
I got my WPC54G card working on my old PII 266 laptop, and I can connect with out issues provided I do it manualy - I found that when I'm trying to connect to a WEP encrypted access point I have to do it manualy, I have to use iwconfig twice before I can get a DHCP lease because it's dropping the first access point config.  It connects for a second and then "forgets" the wep key and the access point drops the connection.

The AP is configured to not broadcast the ESSID, and is useing a 128-bit encrytions key.

What I do to connect:
iwconfig wlan0 essid awifispot key notarealkey
iwconfig wlan0 essid awifispot key notarealkey
dhclient wlan0

if I do this quickly: 
iwconfig wlan0 essid awifispot key notarealkey
iwconfig
iwconfig
iwconfig

The first iwconfig after I configure the wireless connection shows the connection complete with wep key,  the second shows only everythign but the wep key, and the thrid shows no wireless connection at all.  I have replicated this with 4 access points and a wireless router.

Any ideas on how I can get my card to connect to the access point the first time everytime?

---

### Post by KurtHaegeman on 2005-10-07
After changing WPA security to WEP, it now works for me too. Still interested in a WPA solution, though...

Thanks for the info.

---

### Post by KVTL on 2005-10-26
I got wep to work with ndiswrapper. I cant get the acx100 driver to work (only get the Leds on).

Ypu can enter wep key under network dialog, but there you ned a - for evry five character to get it working. :KS

---

### Post by K2712 on 2005-11-09
I used hoary for months, and my WPC54G card worked fine via ndiswrapper. . . . until I upgraded to breezy.  I went through the re-installation process, but now all of my drivers are invalid.  I installed all of the driver files twice, once from disk, and once from the .zip file from the ndiswrapper list.  No matter what I try, when I ndiswrapper -l, I'm told all of my drivers are invalid.  How can this be when they worked with hoary?

---

### Post by K2712 on 2005-11-09
Ok, I removed ndiswrapper-utils using synaptic then re-installed, and now I have a driver present, but no hardware.  iwlist and iwconfig don't see wlan0, how do I bridge that gap?

---

### Post by elemental666 on 2005-11-28
Better bump an old one than start a new one right?

The quoted instructions below worked perfectly on my WPC54GS, with the following exceptions:
echo ndiswrapper >> /etc/modules 
gave me: 
bash: /etc/modules: Permission denied

but when I went to Network settings, there she was.
configured her with my ssid and dhcp and activated her.
no problem.

However, i have to do the modprobe after every reboot.  I know there is a config file that gets executing during boot where I can put in modprobe command and then it will at least be in the network setting after the boot, which is all I really want since I will be connecting to multiple networks.

However, do I have to use sudo in that config file? If so how do I provide the password?

Thanks for listening.

[QUOTE=ramzez]actually it is very simple

install ndiswrapper from synaptic package manager.

then download [ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip)

unzip the downloaded zipfile, find the correct .inf (lsbcmnds.inf in my case) file and run
sudo ndiswrapper -i lsbcmnds.inf 

 load the module and make it reload on reboot:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules 

in gnome, goto networking and put your settings.

hope it helps.[/QUOTE]

---

### Post by SatanGolga on 2005-11-29
I have a Linksys WPC54G v1.2 and got it to work with the latest drivers downloadable at linksys.com  (WPC54G_driver_utility_v3.1%2C0.zip), using ndiswrapper following the instructions mentioned earlier. The ones that came on the installation CD did not work.
We're online!   Thanks a lot!

---

### Post by checksum on 2005-12-06
[QUOTE=gordon_06fr]hey there,
This works perfect for me.... BUT how do I get this installed so that it reloads automatically when I start ubuntu? Kinda a pain to go via terminal and enter the commands manually each time...  :|[/QUOTE]

Did you get this to work? If not, does somebody know how to automate this process in order to avoid doing all the steps with each boot?

BTW, got it to work also perfectly with the v3 card. Thanks for the steps provided!

---

### Post by ricolarno on 2005-12-28
This so far has been very helpfull, but it's still not working :confused: 

I use the Breezy Badger Ubuntu, my wifi card is a linksys WPC54G (labeled as v1.2 on the card, as a v3 in windows xp). I tried different drivers, without success.

I have the ndiswrapper working properly, and if I type ndiswrapper -l, I get a message saying the driver is present and the hardware is present. 

After typing *modprobe ndiswrapper*, my wifi connexion doesn't appear in the network-admin gui, so I can't configure it, and ifconfig doesn't show a wlan0...

Should I add something in /etc/network/interfaces ?
How do I edit /etc/modules ?

Thanks for your help.

---

### Post by macdo on 2006-02-18
With a lot of trial and error, I got this card working. It appears that the steps by YorYor, above, are not necessarily enough... (although there was no problem under Ubuntu, they didn't cut it under Kubuntu or Xubuntu).

[See here for details.]("http://macdo10.free.fr/wordpress/?p=166")

Basically, after you've completed the steps above, and if ifup doesnt, than you might need to edit /etc/network/interfaces and /etc/network/run/ifstate.
It's not that hard, just look at whats already there and copy the last line, replacing eth0 with wlan0.

So in /etc/network/run/ifstate, add a line 
```
wlan0=wlan0
```
In /etc/network/interfaces, add a line
```
iface wlan0 inet dhcp
```
Then ifdown and ifup wlan0, and hopefully you're sorted...

Good luck!

-- 
macdo

---

### Post by appdx on 2006-02-19
Hmm, ok, so I've been trying to get this working for about 4 months and so far no luck...
I don't even have LEDs blinking on the card, I got "driver present, hardware present"
But when I do 'wlist wlan0 scan' it says interface doesn't support scanning
so i tried 'sudo ifup wlan0' and I got
"appdx@Titan:/etc/ndiswrapper$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
sit0: unknown hardware address type 776
Bind socket to interface: No such device
Failed to bring up wlan0."

Help?!

---

### Post by macdo on 2006-02-19
I take it the card *does* work :p

Try 
```
sudo ifdown wlan0
```
(to end the process that's causing you grief),  then
```
sudo ifup wlan0
```
Then ping something (your router, for example).  
If that doesn't work, I suggest you uninstall the card 
```
sudo ndiswrapper -e lsbcmnds.inf
```
then start again.
Follow YorYor's instructions, near the top of this thread, but you may need to edit /etc/network/interfaces and /etc/network/run/ifstate.

Btw, I am taking it that you are using Breezy - I couldn't get it to work on Hoary...

-- 
macdo

---

### Post by appdx on 2006-02-19
ok, following YorYor's instructions I get to "iwlist wlan0 scan" and it just says no scan results...For step 3b, it says "The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines." I didn't get this...Also, for 3d it says "Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4." I only had 2 .conf files that didn't have the line 'Radiostate|1' in them. (I added that line). For step 3f I get 'permission denied'. And then I went to 3g and it gave 'no scan results'.

I appreciate any help.

---

### Post by macdo on 2006-02-19
Okay, step by step:
* Is your card actually working? Is there any way you can test it?
* Is Ubuntu loading the PCMCIA interface - try dmesg to find out.
* What version is the card? Are you using the right pilots?

If those three steps are ok, I can't see why the LEDs don't come on. 
Try making sure that ndiswrapper is the latest version (in fact, make sure that your system is up to date...).
Then ```
ndiswrapper -e lbscmnds.inf
``` to uninstall the pilot, and then reinstall it.
HTH

By the way, I've just noticed that this thread is in the Warty forums - but what distro are you using?

---

### Post by macdo on 2006-02-19
check [here]("http://ubuntuforums.org/showthread.php?p=751442"): it might help...

---

### Post by derk.d on 2006-03-06
Hi I am new to linux and want to get rid of windows....soo i installed ubuntu breezy! Everything works except my wpc54g v3. i did what you said above with ndiswrapper! and when i type iwlist wlan0 scan I get my router in the list, but it doesn't connect with it! I did this: sudo iwconfig wlan0 essid my network channel 11 mode Managed key mywebkey 

then did: sudo ifup wlan0
he is trying to connect to the dhcp but doesn't do that....I am sure i filled in the correct key etc! I had it worked on a wrt54g router but at home I use a dlink 624+ and for some reason under linux he finds it but can't connect to it! in windows everything works great....

can somebody help me!!!?????

i have the wpc54g v3

---

### Post by nzruss on 2006-04-01
[QUOTE=checksum]Did you get this to work? If not, does somebody know how to automate this process in order to avoid doing all the steps with each boot?

BTW, got it to work also perfectly with the v3 card. Thanks for the steps provided![/QUOTE]

Got it to work with the v3 card also. To answer your question, I think there are two ways:

1. use System->Preferences->Sessions, and select the "Startup Programs" tab, enter ndiswrapper. (i dont know if this actually works- anyone???)

2. sudo gedit /etc/modules

Add ndiswrapper to the end of this, save and close. When your machine reboots, it will find the Wireless Adaptor and start it up. (this is what i used and it works!)

Still waiting for WPA support!! (Using MAC access restrictions at the moment)

Thanks to everyone for all their posts! This forum really really rocks. That was the last step in getting Household to: Ubuntu x 2, Windows x 1.

---

### Post by pherms on 2006-04-07
I finally got it working with WPA support after fiddling and trying for a few hours.

Here's what I found (I'm using the Linksys wpc54g).

Install like mentioned above (ndiswrapper).

Follow this link:
[http://www.vollink.com/gary/deb_wifi.html]("http://www.vollink.com/gary/deb_wifi.html")

On this page it says you have to install the wpasupplicant.

follow the steps mentioned here to get it to work.
Take notice of the following. When you edit the file /etc/default/wpasupplicant, you have to add/edit a line which says:

OPTIONS="-w -i wlan0 -D hostap -c /etc/wpa_supplicant.conf"

This was the line where I had an error. My network card didn't get a DHCP address from my router. I checked it and double checked it. Didn't see any error.
What happens is that "-D hostap" specifies the driver Linux uses to use the network card. After I changed "-D hostap" to "-D ndiswrapper" and did a /etc/init.d/wpasupplicant stop and then a start, everything works like charm.

Finally I can use my wireless network with my Ubuntu installation on my laptop.

Good luck

---

### Post by various artists on 2006-04-10
as this is my first post here, documenting my first steps with linux at all (i'm a mac user at daytime ;) ) i hope to get this done anyway, please bear with me as i'm just getting into linux.
my powerbook G3 wallstreet now runs on ubuntu 5.10, all is fine here but i want to take advantage of my WLAN, using the WPC54G (labeled v1.2) that usually runs ok with the other powerbook.

using said technique by ramzez
```
install ndiswrapper from synaptic package manager.

then download ftp://ftp.linksys.com/pub/network/wp...ility_v2.0.zip

unzip the downloaded zipfile, find the correct .inf (lsbcmnds.inf in my case) file and run
sudo ndiswrapper -i lsbcmnds.inf

load the module and make it reload on reboot:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules

in gnome, goto networking and put your settings.
```
the terminal replies:
```
various@VariousArtists:~$ sudo ndiswrapper -i lsbcmnds.inf
sudo: ndiswrapper: command not found
various@VariousArtists:~$ modprobe ndiswrapper
FATAL: Module ndiswrapper not found.
```
it seems that ndiswrapper-source hasn't been correctly installed or initiated, rebooting doesn't do the job which leaves me stuck here ... i have tried to follow step 2 in nzruss' last post but ndiswrapper doesn't show up in the list. what else seems to be odd is that ndiswrapper showed up as ndiswrapper-source in synaptic. huh? :confused: 

while i'm at it, is WPA supported with this method (according to pherms, see below, yes--anyone else?) and if not, what can i do to have it supported on this machine?

thanks a lot!

---

### Post by macdo on 2006-04-15
It seems from here that ndiswrapper is not properly installed. Try this:
```
sudo apt-get install ndiswrapper-utils
```

Anything that ends in -source is source code, not compiled.

---

### Post by yellow5 on 2006-05-14
I finally got my WPC54Gv2 card working after a few tries. The walkthrough at the start of this thread was very helpful, but it was still failing at the "sudo iwlist wlan0 scan" step. It kept coming back "unable to scan".

Here's what made it work for me: Windows XP is NOT case-sensitive, so I ran gedit on the LSTINDS.INF file and did a find/replace on TNET1130 (I replaced it with the filename with the correct case - tnet1130) and replaced the LSTINDS4 with Lstinds4 (note the capital L).

I suppose you could probably just rename the .sys files to match with what the LSTINDS.INF file stated, but to each his/her own I guess.

After performing these steps, I then walked through the steps at the beginning of the thread, and it finally worked (after a reboot).

Hope this helps!

-y5

---

### Post by scapermoya on 2006-05-23
this thread really helped me getting the card up and running, thanks guys.

however, now that the driver works, etc, i am still having issues actually connecting to the AP.

I had my AP set to not broadcast the ssid, but after reading the ndiswrapper FAQ, i set it to broadcast. here is my trouble:

when i "iwlist scan", it shows the proper ssid, which is good
but then, "sudo iwconfig wlan0 channel 6 essid scotland mode Managed" kicks back with "Error for wireless request "Set Frequency" : SET failed on device wlan0 ; Invalid argument."

so i got rid of the "channel 6" part of the command, just to try, and it goes through without error. except that this makes the "link" light on the card solid indefinitely. "sudo ifup wlan0" kicks back a "Ignoring unknown interface wlan0=wlan0."

if i replace scotland with a non-existant ssid (like moocow for instance), the link light blinks a few times and then goes dark, blinking every once in a while as if its looking for the moocow.

any thoughts?

by the way, ifconfig doesnt show wlan0, if that means anything.

---

### Post by cstran01 on 2006-06-13
[QUOTE=scapermoya]this thread really helped me getting the card up and running, thanks guys.

however, now that the driver works, etc, i am still having issues actually connecting to the AP.

I had my AP set to not broadcast the ssid, but after reading the ndiswrapper FAQ, i set it to broadcast. here is my trouble:

when i "iwlist scan", it shows the proper ssid, which is good
but then, "sudo iwconfig wlan0 channel 6 essid scotland mode Managed" kicks back with "Error for wireless request "Set Frequency" : SET failed on device wlan0 ; Invalid argument."

so i got rid of the "channel 6" part of the command, just to try, and it goes through without error. except that this makes the "link" light on the card solid indefinitely. "sudo ifup wlan0" kicks back a "Ignoring unknown interface wlan0=wlan0."

if i replace scotland with a non-existant ssid (like moocow for instance), the link light blinks a few times and then goes dark, blinking every once in a while as if its looking for the moocow.

any thoughts?

by the way, ifconfig doesnt show wlan0, if that means anything.[/QUOTE]
Thanks for the great tutorial in getting this card to work. It really made the process very easy and a whole lot less frustrating that my trying for abotu 16 hours to get the D-LINK DWL-650+ AIRPLUS card to work with any distribution on this old laptop. I am relatively new to Linux as well, but I must again state that this made it all worth removing the windows installation from teh old Pavillion ze1250 (AthlonXP 256MB Ram soon to be upped and a lowly 20 gig hard drive). This means that everything now works. Thanks again.

---

### Post by dmizer on 2006-06-17
wpc54g ver2 with the texas instrument chipset.

i finally got some lights on my card by doing the following.

to load the ndiswrapper driver, i had to edit the .sys file name so they matched what was in the ini file according to post number 68 above (thanks yellow5)

so now when i do ndiswrapper -l, it shows "lstinds driver present, hardware present"
but i still got no lights.

this is apparently because it's tring to load some acx_pci module noted in post 41 (thanks blazerte)

apparently there were other modules that were trying to load for this card, so i got fed up with blacklisting and created my own entry in /etc/pcmcia/config.opts.  here's how i did that:

first you need to give the card a name.  it already has one.  lspci should show output of something similar to this:
```
0000:06:00.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
```
then you need to find the manfid.  to do that, just type "cardctl ident" and you should get output of something like this:
```
$ cardctl ident
Socket 0:
  no product info available
Socket 1:
  no product info available
  manfid: 0xf7ff, 0xfe5b
```
now ... edit your config options for your pcmcia cards:
```
sudo nano /etc/pcmcia/config.opts
```
and create a new entry at the end of the file using the information you have from lspci and cardctl ident so it looks like this:
```
card "Texas Instruments ACX 111 54Mbps Wireless Interface"
  manfid 0xf7ff, 0xfe5b
  bind "ndiswrapper"
```
save by doing ctrl+x, type Y to accept the change, and enter.

now, when you restart your network, your machine is forced to use the ndiswrapper module for this card and you should get the power light to come on.

i just have to get it to link and all will be well.

edit: got it to link up.  i tried again and again to get this thing to get a dhcp lease by typing in the commands by yoryor, but it could never pick up a dhcp lease.  i got sick of typing everything over and over again, so i just did the following to expediate the process:
```
$ sudo iwlist wlan0 scan&& sudo iwconfig wlan0 channel 1 essid youressid mode Managed&& sudo ifup wlan0
```
shezam ... dhcp lease.  **note: the link light did not come on, but i do have a connection**

i had given up on this card.  thanks everyone who put so much effort into this.

---

### Post by jowood on 2006-07-02
I did this for my WPC54G v 1.2 in Ubuntu Dapper Drake 6.06:

```

$ wget http://download.berlios.de/bcm43xx/bcm43xx-fwcutter-004.tar.bz2
$ tar jxvf bcm43xx-fwcutter-004.tar.bz2
$ cd bcm43xx-fwcutter-004
$ make
$ wget http://gaesi.org/~jowood/wl_apsta.o
$ ./bcm43xx-fwcutter wl_apsta.o
$ sudo make installfw

```

and it worked for me;)

---

### Post by Raadbull on 2006-07-11
My WPC54G is working now yeeehaaaa.

I used the ndiswrapper way shown in the 4th or 5th post in this thread.
But had no link.
The Problem was the old Broadcom driver it was running too on the card.
I kicked it into the Blacklist as written in the following link and everything  was fine.
[http://ubuntuforums.org/archive/index.php/t-190967.html](http://ubuntuforums.org/archive/index.php/t-190967.html)

Have a nice day..:-)

---

### Post by akorai on 2006-07-16
okay here we go...
I am new to Linux, I went through this thread line by line and I am still dead in the water.
I have the WPC54G V2.0

I got ndiswrapper installed, got the nstinds.inf file case problem fixed.  installed it and when i do ndiswrapper -l it shows the driver, but says that it is invalid

So I figured I would uninstall it, but when i do ndiswrapper -e it says the driver is not installed.

Okay got them to uninstall now my -l says no drivers installed

So I think I ran across the problem...when I tried to reinstall lstinds.inf I get counldn't copy lstinds.inf at /usr/sbin/ndiswrapper line 135

any ideas? ](*,) 

Edit:  So now I finally got the driver installed, but it will not locate my AP.  I am broadcasting my SSID and it will not pick it up with the iwlist scan...this is getting really irritating...:evil: 

Edit:  Okay this is the last thing i have managed to do, loosing hope, ran a dmesg 2 things stuck out to me
1st.  17179610.124000 wlan0 (WE) : Driver using old /proc/net/wireless support, please fix driver !
2nd.  17180462.328000 acx:  firmware 'Rev 2.3.1.31' does not work well with this driver

Now i d/l'd the newest driver from linksys, so i dunno why it would say this...
Any help here would be great:-|

---

### Post by The Road Below on 2006-08-11
Linux n00b using wpc54g.  Using free trial linuxant driver and it works great.  Will probably buy.

---

### Post by skeeve on 2006-10-18
I have the WPC54G ver 4 PCMCIA. I get to the point where the card actually connects to the router. However, it won't get an IP via DHCP and specifying a static IP doesn't work either.

The strange thing is that encryption is set to "Off", even though I specified the WEP key. No matter what I do, I can't get the encryption to switch to "On".

If anyone is successfully running the ver 4 card with WEP enabled, I'd appreciate if you could send me your windows driver. I downloaded the latest one from Linksys. Maybe that is the problem.

---

### Post by Achetar on 2006-12-25
BAAAAAAAAAAAAAAAHHHHHHHH!!!!!!!!!!!!!!!!!!!!!!!](*,) ](*,) ](*,) 
None of the above ideas work!
I have the linksys WPC45G v3.
It seemed to work at 1st, but i couldnt get it. It always says no hardware present.
I followed all the steps.
plz help!
also, i would like it written so that an almost complete Ubuntu n00b (i know somwhat how to use the terminal) could do it. I would appreciate any and all help. I am running Ubuntu 6.10. I have ndiswrapper and ndisgtk installed.
I can boot into WinXP. I can also connect directly to the WiFi router (that is how i am writing this ;)) Thnx in advance.
Also, the following error appears when i use 'ndiswrapper -i lsbcmnds.inf' when i am logged in as the root:
Installing lsbcmnds
couldn't copy lsbcmnds.inf at /usr/sbin/ndiswrapper-1.8 line 144

---

### Post by Achetar on 2006-12-29
Nvr mind i got it working

---

### Post by Achetar on 2006-12-29
Make sure that u have the .sys file that came with the driver in the same directory as the driver.

---

### Post by tical2756 on 2007-02-02
@ jowood

That only works if you have a working wired internet connection, can someone post a how-to using that method if you are not able to connect?

---

### Post by tical2756 on 2007-02-11
jowood - you're a genius.  I got my internet going and your post worked like a charm.  

p.s. it looks like  [http://gaesi.org/~jowood/wl_apsta.o](http://gaesi.org/~jowood/wl_apsta.o) is dead, so i replaced it with boredklink.googlepages.com/wl_apsta.o

thanks

---

### Post by Bart Ellebaut on 2007-05-03
this worked, but now I've started my pc again, and nothing. I did it all again, and still nothing, wlan0 doesn't exist.
what did I do wrong, even made ndiswrapper start at boot

---

### Post by ChazB on 2007-05-11
I just wanted to say thanks to everyone that has participated in this discussion. Using [the post by YorYor]("http://ubuntuforums.org/showpost.php?p=113584&postcount=7") I managed to get my WPC54G ver 4 card working with Ubuntu 7.04, and [the post by nzruss]("http://ubuntuforums.org/showpost.php?p=882859&postcount=64") got it loading at boot. Not every step in YorYor's post worked the same for me, but I chalk that up to newer versions of both the OS, ndiswrapper, and a different version of the wireless card.

---

### Post by cajmoj on 2007-05-31
Finally I am able use my WPC54g card.  I tried all the different options available in this post.  However, I found one that did work and its the first time I have been able to use my wireless card.  I followed these instructions hope they work for someone else.

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist
sudo rmmod bcm43xx
sudo rmmod ndiswrapper
sudo apt-get remove ndiswrapper-utils
sudo rm -r /etc/ndiswrapper/
sudo rm -r /etc/modprobe.d/ndiswrapper
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/dave/Desktop/bcmwl5.inf
sudo ndiswrapper -m
sed -e 's/RadioState|1/RadioState|0/' /etc/ndiswrapper/bcmwl5/*.conf
sudo modprobe ndiswrapper

---

### Post by h0me5k1n on 2007-06-07
I got my WPC54G version 4 working using the guide [COLOR="Blue"][here]("http://www.debianadmin.com/enable-wpa-wireless-access-point-in-ubuntu-linux.html")[/COLOR], with ndiswrapper installed through automatix and the driver from the cd (filename is WLIPNDS.INF).

It doesn't seem to work properly after a reboot though - I have to remove and reload the driver through the "System", "Admininstration" - "Windows Wireless Drivers" application each time I reboot and enter the keyring password as shown in the above link.

I can't work out how to get the network-manager to recognise that the ndiswrapper driver is loaded each time I reboot though otherwise this way of doing it would be perfect.

---

### Post by opengovtv on 2007-06-08
> **YorYor said:**
> Hi all, recently got myself stuck to Ubuntu Hoary after I sorta trialed 10+ distributions over a week. One of the immediate hurdles was to get this WPC54G working, and after hours of searching, I managed to find another solution which worked for me ([http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)](http://tiefighter.et.tudelft.nl/~arthur/wpc54g/)).

In summary,

1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.

over 2 years since yo posted this and it works perfectly, thank you so very much

---

### Post by VelocityBoy2112 on 2007-08-02
as long as you have a Netgear  wireless card with a broadcom chipset, it should work automatically with Ubuntu 7.4.... Model numbers wg511u (older) or wg511t (newer) work best (I only use netgear anyhow - linksys isnt that great...)

---

### Post by hghtn on 2007-08-10
> **Joshua said:**
> It took me quite a while to figure out how to get this working, so I wanted to post something about it and possibly save someone a little time.

I've got an old Gateway Solo 5100 and I bought the WPC54G.  My home network is run on the WRT54G.  My solution might not apply to normal Ubuntu users because of my installation method, so I'll describe it.

My CD-ROM, apparently, doesn't like normal sized CDs.  When I try to install Ubuntu it gets hung up towards the end while installing the system base packages.  It does fine, however, with the Debian netinstall CDs on the smaller 80mm disks.  So I installed a minimal Debian system with the netinstall CD and then changed the APT repositories to the Ubuntu Hoary ones.  Then, I upgraded (it took a little investigation to complete dependencies and stuff).  Once that was done, I installed the linux-686 packages so that I would have the most recent Ubuntu Kernel.

Then, I followed the normal instructions for installing ndiswrapper and the windows drivers.  Ndiswrapper is in the 2.6.10 Kernel so that was easy with "modprobe ndiswrapper"
.[COLOR="Red"]How do install the ndiswrapper?[/COLOR]

Anyway, once all that was done, I couldn't get the card to work.  iwlist wlan0 scan said that it couldn't pick anything up.  ifup wlan0 said it couldn't get a dhcp response.  After loads of trying different drivers and reloading modules, etc. I looked at the dmesg output and saw that there was some module called acx_pci that seemd to be trying to operate my card.  There was even a little warning that my card used proprietary drivers and that acx_pci might not work.  So I rmmod ndiswrapper, rmmod acx_pci, modprobe ndiswrapper.  BINGO!  ifup wlan0 and everything is hunky-dory.  Now I need to figure out how to keep acx_pci from loading on boot and how to get ndiswrapper to load on boot.  If anyone knows, please let me know.  I've tried ndiswrapper -m.  It says that it's good, but when I boot - no ndiswrapper...

See above in red

---

### Post by jnbptst on 2007-08-21
Hi folks,

I'm having following installing the driver for the WPC54g on my Compaq Evo N410c (using Ubuntu 7.04)

I tried to follow the procedure, but here is what I get:


dominique@dominique-laptop:~/Driver$ sudo ndiswrapper -i LSBCMNDS.inf
installing lsbcmnds ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
dominique@dominique-laptop:~/Driver$ sudo ndiswrapper -l
lsbcmnds : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)
dominique@dominique-laptop:~/Driver$ sudo ndiswrapper -a 14e4:4318 lsbcmnds
couldn't create symlink for "14E4:4318:0048:1737.5.conf": Le fichier existe. -
installation may be incomplete
couldn't create symlink for "14E4:4318.5.conf": Le fichier existe. -
installation may be incomplete
couldn't create symlink for "14E4:4320:0049:1737.5.conf": Le fichier existe. -
installation may be incomplete
couldn't create symlink for "14E4:4320:4320:1737.5.conf": Le fichier existe. -
installation may be incomplete
couldn't create symlink for "14E4:4320.5.conf": Le fichier existe. -
installation may be incomplete
driver 'lsbcmnds' is not installed (properly)!


If you have any idea of how to resolve it, please let me know!


thanks in advance,

JB

---

### Post by jnbptst on 2007-08-22
So I eventually managed to make it work (don't ask me how, i tried a bunch of stuff from all over the web, then rebooted, and eventually it worked).

However, the current bitrate is 11M instead of the 54M theoretical capability of my card. I'd like to improve the speed, so I typed

sudo iwconfig wlan0 rate 54M

it does not return any message and the speed remains at 11M...

any suggestion?

thanks

jb

---

### Post by boomcat on 2007-08-22
jnbptst, 
There are only two ways to install this card: 
bcm43xx-cutter - limits range and limits speed to 11.
ndiswrapper - longer range and speeds of 54.

You may have installed it the first way.

---

### Post by jnbptst on 2007-08-22
Hi,

I installed it using ndiswrapper because after a bit of search I had found that bcm43 doesn't work with my version of the card (v3).

By the way not only is the rate 11M, but my connectivity is nonexistent (I can't access any internet service).

The AP is open and without a password.

Any idea?

Thanks

---

### Post by eric87m on 2007-08-23
Im using a WPC54G v3 and need help too. I've been using Linux for a total of 15 minutes so go easy on me.

I managed to the get "Windows Wireless Drivers" application, which is located in system>administration. I downloaded the windows driver for the wireless card from linksys' website. I selected the .inf file from the driver and loaded it in the Windows Wireless Driver program. Nothing happened. Nothing was listed in the window.

So next I followed Achetar's pdf guide. Everything seemed to go fine. I installed the driver via the terminal, and added ndiswrapper to startup. But still no wireless card is listed as a network device. So I tried loading the inf file in Window Wireless Drivers again, and this time it says "driver already installed" but no devices listed in the window.

What to do next?

---

### Post by jnbptst on 2007-08-23
Forgot to mention, I'm using Xubuntu, not ubuntu... Thought it didn't make a difference but it looks like it may

---

### Post by bobo99 on 2007-09-07
I'm trying to get hte same card to work on my version of Ubuntu. (6.06). The problem is I can't install ndiswrapper because I dont think I have any of the compiling tools installed. I can't get any kind of internet connectivity. I managed to d/l ndiswrapper and transfer it to the Linux machine with a USB stick, but I cant make, make install because it says it doesn't recognize the command, how should I proceed?


bojan

---

### Post by haleychin on 2007-09-18
This is  the lastest step for getting ndiswrapper work on ubuntu 7.04

1. Use Synaptic to get ndiswrapper-utils and ndiswrapper-common
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/). If you have installation cd, then go to folder
driver/NT and copy all the file and paste to Linksys.
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something 
like below
dominique@dominique-laptop:~/Driver$ sudo ndiswrapper -i LSBCMNDS.inf
installing lsbcmnds ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

but never mind, it did not cause any problem

3c. sudo modprobe ndiswrapper
3d. sudo nano /etc/modules
3f.  append a line of text : ndiswrapper
3g. save it.
4. blacklist the bcm43xx module by following step
4a. sudo nano /etc/modprobe.d/blacklist-bcm43xx
4b: type in following line of text in to the file:
blacklist bcm43xx
4c: save the file

5 you should have the gnome network manager installed 
the installation for this will not cover here

6 restart the computer then your can connect to the wireless network already
this work fine for me

---

### Post by Fearghal on 2007-10-06
I really am impressed the amount of time and effort that has gone into researching, documenting and posting these forums.  The information supplied by YorYor was tremendous help.  In no small way he has given my old Toshiba with the linksys card a new lease on life.  I can now get rid of the Windows OS.  Up and running now in wireless mode on Feisty.
Thanx YorYor...

Fearghal

---

### Post by kemp_samurai on 2007-10-15
> Forcing Parameter IBSSGMode|0 to IBSSGMode|2

I got this 5 times when i installed the LSBCMNDS.inf file using ndiswrapper to install said driver. Anyone know what this means and what I should do?

Thank you in advance.

---

### Post by jnbptst on 2007-10-15
I got the same as you can see... (still doesn't work)

---

### Post by kemp_samurai on 2007-10-15
so, after some experimentation, and about three uninstall/reinstall cycles, the card finally works. and i did the blacklist section. that appears to have made a bit of a difference.

---

### Post by metalwraith on 2007-10-16
I tried various things in this thread to get my wireless modem up and running.. Couldn't do it.. So used that Linuxant thing I saw mentioned elsewhere... worked perfectly with a little trial and error. But so far still somewhat new to Linux, but have a vague Unix background from my old tech support job where we had to cover alot of things Windows, some Unix,etc.

---

### Post by MartenH on 2007-10-22
I tried this guide on Gutsy Gibbon and now ubuntu shuts down the computer on bootup. Luckily I hadn't started using it yet Good guide, just want to warn everyone to do a backup!

---

### Post by jnbptst on 2007-10-22
I updated to Gutsy and now it's working. It's a bit slow though

---

### Post by MightyVikingJim on 2007-10-23
Howdy.  I installed Ubuntu onto my dad's Thinkpad T20 a month or so back and got a Linksys wireless card for him. Unfortunately, every time I plug the card into the laptop - whether it's at start up, before start up or during operation - the system freezes and won't resume operations. I've left it for a few hours and there was no change. I've already installed the drivers as per the suggestions of several others in this thread, but the system still freezes.

Any help would be most appreciated, and if I need to give any more info, don't hesitate to ask.

Thanks

-Jim

---

### Post by CDiablo on 2007-10-23
I just got on of these and I have versio 1.2. I have tried almost everything here and it does ot work. WHen I plug in the card my hardware manager sees it. By the way I am on xubuntu with gutsy. Tell me where to start cause Im not sure where to.
 I tried the ndis method and it says there it does not support scanning when I want to scan. I have also tried the bcm43xx restricted driver and it does not work either.....does anyone know where I should start. Thanks all.

---

### Post by Firefighter1428 on 2007-10-24
I have followed the directions and have gotten to the bottem. My problem is my card shows up as eth1 not wlan0. How can I fix this??? I am really new at this so any help would be great.

---

### Post by Firefighter1428 on 2007-10-24
> **Firefighter1428 said:**
> I have followed the directions and have gotten to the bottem. My problem is my card shows up as eth1 not wlan0. How can I fix this??? I am really new at this so any help would be great.
Well after blacklisting the ubuntu driver and flipping thorugh I got it to work. I still set at eth1 not wlan0 but it works so I dont care. When I get time I will sit down and put it all in order for what worked for me. I have a IBM R51 laptop. Thanks again and contuine to hate windows!!!

---

### Post by gnomungus on 2007-10-24
a small note on my experience:

1) I had a hell of a time with this, till I read this thread. Thanks everyone for the information!

2) one of the key steps for me was blacklisting the bcm43xx module

3) for some reason once I finally got the hardware recognized, the card would not connect to anything (even an unsecured network) until I installed the KDE network manager (KNetworkManager)

4) even after that, the card simply would not work with WEP until I changed the encryption on my access point from WEP open to WEP shared.

This is not an ideal solution, since WEP shared is less secure, but I'm not particularly concerned about the security of this particular network. Still, if someone knows what might be causing this, I would be grateful for any advice on how to get it working with WEP open for the rare occasion that I might bother moving this old hunk of junk to someone else's network.

---

### Post by pro107 on 2007-10-28
> **ramzez said:**
> actually it is very simple

install ndiswrapper from synaptic package manager.

then download [ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip](ftp://ftp.linksys.com/pub/network/wpc54g_v2_driver_utility_v2.0.zip)

unzip the downloaded zipfile, find the correct .inf (lsbcmnds.inf in my case) file and run
sudo ndiswrapper -i lsbcmnds.inf 

 load the module and make it reload on reboot:
modprobe ndiswrapper
echo ndiswrapper >> /etc/modules 

in gnome, goto networking and put your settings.

hope it helps.
^ This is what I have just done and it works. Just make sure to reboot after everything. I don't know if it's normal, but, my laptop boots quicker without the card in. After it's up, slide card in and your on.

---

### Post by djducky on 2007-12-30
Thanks so much man! I've been trying for a long time to get my adapter working and now its fully working!
Cheers

---

### Post by P235 on 2008-01-01
To Firefighter and anyone else who is interested:

If you wish to change the label from eth1 to wlan0, edit the /etc/iftab file accordingly.

---

### Post by murtaza on 2008-01-12
with freespire the wireless card should work automatically....it worked automatically for me...but i prefer ubuntu....i knew how to install the drivers after some research however, it still does't work even folloing these instructions....


1. Use Synaptic to get ndiswrapper-tools
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something about Forcing parameter RadioState|0 to RadioState|1... mine had 4 lines.
3c. cd /etc/ndiswrapper/
3d. Edit all the .conf files, look for the line RadioState|1 and change it to RadioState|0 (to do this, I had to type sudo gedit and open the files from the GUI... gedit didn't quite like opening files with \: from the command line, not sure why) I'm not sure if just changing one or two files will work, but I just changed all 4.
3e. sudo modprobe ndiswrapper
3f. (optional) sudo echo ndiswrapper >> /etc/modules
3g. sudo iwlist wlan0 scan (look for your access point in the list)
3h. sudo iwconfig wlan0 channel <X> essid <ESSID> mode Managed (the X and ESSID should come from the iwlist)
3i. sudo ifup wlan0

I think that should do it really. Hope that will be useful for someone else.


-step 3d for me wasn't necessary because Radiostat|0 is already configured for all .conf files
- sudo echo ndiswrapper won't work... permission denied
- couldn't scan wlan0
- my linksys card is detected as eth0..

any suggestions please let me know or send me a pm

---

### Post by Wtrz on 2008-03-13
same problems here:

> wtr@ubuntu:~$ sudo lspci
[sudo] password for wtr:
00:00.0 Host bridge: Intel Corporation 430TX - 82439TX MTXC (rev 01)
00:01.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 01)
00:01.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:01.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:01.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 01)
00:02.0 VGA compatible controller: Neomagic Corporation NM2160 [MagicGraph 128XD] (rev 01)
00:03.0 CardBus bridge: Texas Instruments PCI1131 (rev 01)
00:03.1 CardBus bridge: Texas Instruments PCI1131 (rev 01)
05:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)

> wtr@ubuntu:~$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.
any help is appreciated! :)

---

### Post by Bart Ellebaut on 2008-03-13
try sudo iwlist wlan1 scan or sudo iwlist eth0 scan (or eth1)
maybe that works.

otherwise, download wifi-radar with synaptics. I have installed this, and now everything works fine, no matter where I go.

---

### Post by Wtrz on 2008-03-14
hmm, that didn't work for me. Back to yoryor's guide:

1. Use Synaptic to get ndiswrapper-tools
> done
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/)
> done
3. Open terminal, and enter the following commands:
3a. cd Linksys
> wtr@ubuntu:~$ cd linksys3
wtr@ubuntu:~/linksys3$ ls
AUTORUN      I2220NTX.SYS  LSBCMNDS.CAT  WLIPNDS.CAT
AUTORUN.INF  I2220.SYS     SETUP.EXE     WLIPNDS.INF
BCMWL5.SYS   linksys3.INF  UTILITY       WPC54G v4 driver rev 1.22.1.2004
wtr@ubuntu:~/linksys3$ sudo ndiswrapper -i linksys3.INF
installing linksys3 ...
wtr@ubuntu:~/linksys3$ sudo modprobe ndiswrapper
wtr@ubuntu:~/linksys3$ sudo echo ndiswrapper >> /etc/modules
wtr@ubuntu:~/linksys3$ sudo iwlist wlan0 scan
wlan0     Interface doesn't support scanning.

wtr@ubuntu:~/linksys3$ sudo iwlist eth0 scan
eth0      Interface doesn't support scanning.

wtr@ubuntu:~/linksys3$ sudo iwlist wlan1 scan
wlan1     Interface doesn't support scanning.

tried this with every driver i could find, same results

---

### Post by dimiro on 2008-03-19
> **haleychin said:**
> This is  the lastest step for getting ndiswrapper work on ubuntu 7.04

1. Use Synaptic to get ndiswrapper-utils and ndiswrapper-common
2. Get the windows drivers, and copy the .sys and .inf to somewhere (say /home/<yourusername>/Linksys/). If you have installation cd, then go to folder
driver/NT and copy all the file and paste to Linksys.
3. Open terminal, and enter the following commands:
3a. cd Linksys
3b. sudo ndiswrapper -i <name>.inf (mine was lsb something, but I just renamed it to linksys.inf as it makes it easier). The screen should show something 
like below
dominique@dominique-laptop:~/Driver$ sudo ndiswrapper -i LSBCMNDS.inf
installing lsbcmnds ...
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2
forcing parameter IBSSGMode from 0 to 2

but never mind, it did not cause any problem

3c. sudo modprobe ndiswrapper
3d. sudo nano /etc/modules
3f.  append a line of text : ndiswrapper
3g. save it.
4. blacklist the bcm43xx module by following step
4a. sudo nano /etc/modprobe.d/blacklist-bcm43xx
4b: type in following line of text in to the file:
blacklist bcm43xx
4c: save the file

5 you should have the gnome network manager installed 
the installation for this will not cover here

6 restart the computer then your can connect to the wireless network already
this work fine for me

On an old Toshiba Series 4300 (4340), using the same card v3 on Ubuntu Gutsy, the same steps worked for me like a charm and the messages I got in the terminal were the same too. Thank you very much haleychin! :)

---

### Post by poltr1 on 2008-03-21
I followed ramrez's instructions and the wireless network card is detected.  It also finds local wireless networks.  But when I try to connect to one, it tries for about 60 seconds and then gives up.  :confused:  Should I try uninstalling and reinstalling the drivers?  (If so, how's it done?)

Also, I seem to be missing the cardctl command, which identifies mounted PCMCIA cards.  It's not in /sbin or /bin.  What am I missing?

---

### Post by poltr1 on 2008-03-29
Even after trying murtaza's fixes above, I'm still unable to connect to a network with my wireless card.

To recap: I typically use my wireless card in roaming mode as I don't have a wireless conenction at home.  I can detect networks, and can attempt to connect to one.  I get the blue swirl for about 60 seconds, and then it disppears.  :(

Should the network card be detected by pccardctl (the replacement for cardctl)?  Also, is there anything in the config files I should be looking for?

---

### Post by murtaza on 2008-04-02
i used the ndisgtk GUI to install the drivers...find it in synaptic....then i restarted the laptop with the wireless card plugged out....I opened terminal and typed the following....

1. sudo modprobe ndiswrapper
Then, plug in the wireless card
2. dmesg

Wait for a few seconds and you'll notice that your wireless card will find some nearby wireless signals.

I have to do this all the time I use my laptop and it works for me. My wireless network settings is always in roaming mode. If you dont make sure your wireless card is unplugged before you turn on your laptop "dmesg" won't work properly.

---

### Post by poltr1 on 2008-04-10
I installed ndisgtk and noticed that it doesn't report the network card as installed/mounted, even though it's inserted and a green LED is showing on the card.

I am able to see other wireless networks around me; I just can't connect to them.  :(  I try, but it times out after about 60 seconds.

What should I be looking for in the dmesg output?

---

### Post by murtaza on 2008-04-10
when u type dmesg....it''l just change eth0 or eth1 to wlan0 or wlan1  because my wireless card was detected as eth1 i think....but, before typing dmesg, your able to see other wireless networks and that means typing dmesg is not necessary. I have my own wireless network so I just type in the encryption key and then connect to the net...I am not sure why you can't cannot online. I am still new to this as well..

---

### Post by Bart Ellebaut on 2008-04-11
Hey, the green led just means that it is plugged in to the pc, not that it is connected.
Ndisgtk is just a program to install you windows driver for the wireless card. have you done this?
Then click the configure netwerk and make sure everything is ok.
I use the same card, but I have never been able to find it with the networkmanager of KDE.
So I installed 'Wifi-radar'. You have to configure the network again, but this one does the trick for me. maybe you should try this ones.

or try this ones in terminal.this did the trick on my other laptop, same card

start with```
 iwconfig -a
``` to see if it uses wlan or eth ( I had the problem where i was trying wlan and when i changed it to eth, everything was fine)

```
sudo rm -rf /etc/ndiswrapper/lsbcmnds
sudo ndiswrapper -i lsbcmnds.inf
cd /etc/ndiswrapper/
in the directory ndiswrapper: sudo gedit ==> radiostation|1back to 0
                           : sudo modprobe ndiswrapper
                           : sudo iwlist wlan0 scan
                           : sudo iwconfig channel X essid (naam netwerk) mode Managed
                           : ifup wlan0 (eth0)
```

---

### Post by lambdacore on 2008-06-24
hey guys.

i just installed Hardy Heron and it's not going well.
i easily got the card running on Gutsy and used it for a couple of months.
now i installed it with ndiswrapper as usual.
i see the wireless networks and their strenght, but i can't connect to any of them.
i tried changing to WEP and WAP and everything, but nothing does.
i type in the password or hexadecimal thingy, it tries connecting for about a minute, then comes back to the password dialog.
im a bit annoyed right now.

---

### Post by dmizer on 2008-06-25
> **lambdacore said:**
> hey guys.

i just installed Hardy Heron and it's not going well.
i easily got the card running on Gutsy and used it for a couple of months.
now i installed it with ndiswrapper as usual.
i see the wireless networks and their strenght, but i can't connect to any of them.
i tried changing to WEP and WAP and everything, but nothing does.
i type in the password or hexadecimal thingy, it tries connecting for about a minute, then comes back to the password dialog.
im a bit annoyed right now.

what version of the card do you have?

please post the output of:
```
lshw -C network
```

btw, this is an ancient thread.  you probably would have gotten a more speedy reply if you had posted a new thread.

---

