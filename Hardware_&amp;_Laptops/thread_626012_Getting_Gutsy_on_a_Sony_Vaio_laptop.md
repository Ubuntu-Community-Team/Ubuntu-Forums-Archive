---
title: "Getting Gutsy on a Sony Vaio laptop"
date: 2007-11-28
forum: Hardware &amp; Laptops
---

### Post by daz4126 on 2007-11-28
I've recently bought a new sony vaio vgn-cr22g/w laptop and was a first frustrated because Ubuntu Gutsy wouldn't install at all and when it did, the wi-fi, sound and compiz wouldn't work. After a couple of weeks and lots of much appreciated help on these and other forums, I've got it working and am loving it. I've decided to summarise the steps I took to get everything working so that they are all in one place and hopefully will help anybody else.

**step 1 - getting it to boot**
[LIST=1]
[*]Boot from a live CD
[*]Press F6 for options
[*]delete the last part that refers to 'quiet splash'
[*]The cd should now boot fine
[/LIST]


*Thanks to Lenticular for fixing that.*

**step 2 - getting compiz to work**
Go into synaptic and install the package - xserver-xgl (search for it)
reboot and compiz should now work (enable it by going to system > appearance and then click on the 'visual effects' tab and select the 'extra' radio button)
If you want more advanced effects then install the package 'compizconfig-settings-manager', and you will get Advanced Desktop Effects Settings in the system menu (and also add a "Custom" radio button to your Appearance choices).  There is a great article about these settings here:
[URL="http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion"]http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion[/URL

*thanks and credit to dwasifar for all the help with that.*

**step 3 - get sound working**
There is a fix for this that you have to do. dwasifar put me onto this and it can be found at the following link:
[http://ubuntuforums.org/showthread.php?t=416207]("http://ubuntuforums.org/showthread.php?t=416207")

I've reproduced the instructions here for completeness.

Open terminal.

```
cd /etc/init.d
```

Create a new text file:

```
sudo gedit soundstartfix
```

Text to stick in:

```
#!/bin/bash
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto
```

Save, then close the text editor.

Now you need to make it start with other schtuff, soo...

```
sudo update-rc.d soundstartfix defaults
```

Wait for it to finish, then:

```
sudo chmod +x soundstartfix
```

Reboot, and it should be working perfectly!

**step 4 - get wifi working**
By far the hardest! At the moment I am using windows drivers with ndiswrapper. I am looking into a possible solution using native linux drivers and will post any updates.

Download the windows 32-bit(or 64bit if you need) Wireless_Atheros ZIP  drivers from here.(
[ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/](ftp://ftp.work.acer-euro.com/notebook/aspire_5100/driver/)
(the last link is a zip file)

Download and install the last version of ndiswrapper (it works from 1.45 version)
Follow the instructions on the ndiswrapper site (you will need to install the build-essential package using synaptic in order to compile the latest ndiswrapper from source)

Try to remove the module ath_pci to let ndiswrapper to use the wifi. Type the following 2 commands in to a terminal
     "sudo rmmod ath_pci" and "sudo modprobe -r ath_pci"

also  put that module in the blacklist of modprobe to avoid it
loading on the startup:

```
sudo nano /etc/modprobe.d/blacklist-common
```

Insert this line:
```
blacklist ath_pci
```

Then restart the laptop.

unpackage the window's driver (right-click and select 'extract') and navigate in a terminal to the drivers folder.
 ```
cd Desktop/Wireless_Atheros_V5.3.0.67_XP_XB63_XB62\(WHQL\)/Drivers/XP-x32/
```
(this assumes the extracted folder is on the desktop)

Now type the following into a terminal:

```
sudo ndiswrapper -i net5211.inf
```

 then install to modprobe
```
ndiswrapper -m
```

now you need to get the wifi recognised:
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

Hopefully now the network manager will start to connect to your router!
So that it connects on startup each time, you need to edit the modules file:
```
 sudo gedit /etc/modules
```
add the line
```
ndiswrapper
```
on a new line at the end of the file. Save and exit.

Now it should all work.
*Credit for this solution goes to Ewan Parker on the Open University Linux forums and the Ubuntu wiki page:*
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper?highlight=%28ndiswrapper%29)

Hope this helps,

DAZ

---

### Post by theodore_kh on 2008-01-09
I really appreciate your guide, thanks.

By the way, you might want to add a 'sudo' in front of
> 
ndiswrapper -i net5211.inf

I was stuck there for a while when they give me the permission denied error.

---

### Post by daz4126 on 2008-01-10
cheers, glad it helped. I've edited the instructions to include 'sudo'.

DAZ

---

### Post by daz4126 on 2008-01-10
Update - I've found a few native drivers through the mad-wifi project, but they seem a bit more complicated with patch installs etc...

Sound doesn't actually seem to be working properly for me with that fix. I get a notification at the login prompt screen and I get the 'Ubuntu Welcome' music as I login, but then get no system sounds. All sounds through my browser (e.g. listening to youtube) work fine. Anybody any ideas on this.

Thanks,

DAZ

---

### Post by Daelyn on 2008-01-10
Nice guide.

Why not edit the title to "HOW-TO Gutsy on Sony Vaio CR-Series" so it is quickly identified for our dear Sony friends crossing over to the good side?

There is also a "laptop-testing" section where you can write guides and stuff so it appears as a article. :)

---

### Post by daz4126 on 2008-01-10
Done! Where is the laptop testing section??

---

### Post by daz4126 on 2008-01-10
Wait a sec ... I've only managed to change the title of the origninal message! How do I change the title of the whole post?

DAZ

---

### Post by theodore_kh on 2008-01-13
> **daz4126 said:**
> Update - I've found a few native drivers through the mad-wifi project, but they seem a bit more complicated with patch installs etc...

Sound doesn't actually seem to be working properly for me with that fix. I get a notification at the login prompt screen and I get the 'Ubuntu Welcome' music as I login, but then get no system sounds. All sounds through my browser (e.g. listening to youtube) work fine. Anybody any ideas on this.

Thanks,

DAZ

Are you using the latest madwifi for your AR5006EG ?

I plan to try on madwifi but so far I haven't come across anyone successful using madwifi on a SONY AR5006EG.

Yet madwifi did mention it is supported.

---

### Post by daz4126 on 2008-01-13
> **theodore_kh said:**
> Are you using the latest madwifi for your AR5006EG ?

I plan to try on madwifi but so far I haven't come across anyone successful using madwifi on a SONY AR5006EG.

Yet madwifi did mention it is supported.

I think that it is incorrectly shown as AR5006 and is actually AR5007, which seems to be supported by the ath5k project (completely free version of madwifi from what I can tell). Here are some interesting notes from [http://madwifi.org/wiki/Compatibility/Atheros:](http://madwifi.org/wiki/Compatibility/Atheros:)

[INDENT]Atheros AR5007EG ¶
Chipset:	AR2425 / AR5007EG
URL:	[http://atheros.com/pt/AR5007EG.htm](http://atheros.com/pt/AR5007EG.htm)
Supports:	802.11b 802.11g
Interface:	PCI-Express x1
Device Information:	Ethernet controller: Atheros Communications, Inc. Unknown device 001c (rev 01),Subsystem: AMBIT Microsystem Corp. Unknown device 3065
Notes:	not supported by HAL as of 2007.04.28 - resturns Hal status 13
Notes:	Suported by ndiswrapper with windows driver, but some user reports crash problems
Notes:	Instructions about how to use the windows driver + ndiswrapper
Notes:	works fine with ndiswrapper, using old drivers, search ubuntu forums
Notes:	Sometimes erroneously reported as an AR5006EG by lspci
Notes:	Works perfectly with latest madwifi snapshot and this patch --> [http://madwifi.org/ticket/1679](http://madwifi.org/ticket/1679)
Notes:	This patch was tested on a Acer Aspire 5315 ans he works fine[/INDENT]

As you can see, it could work with a patch, which I haven't got round to trying yet.

DAZ

---

