---
title: "3Com OfficeConnect Wireless 11g card - any luck?"
date: 2005-11-25
forum: General Help
---

### Post by Randy Sparks on 2005-11-25
Has anybody had any luck getting the 3Com OfficeConnect Wireless 11g PCMCIA card working under Ubuntu? According to the Ndiswrapper site it should work fine, although it seems there was an issue about a firmware update causing problems.

The card is recognised within Ubuntu but DHCP autoconfig won't work (the network applet just pauses for a few minutes before claiming the card is activated when in fact it isn't). 

If I assign a static IP, I get told by the network applet that I've misconfigured the card and am told to try again. 

I've tried updating to the latest Ubuntu kernel release but no luck.

---

### Post by ofek on 2005-11-25
I got one please give its name (its written on it something like 3crwe...) and its ver.

---

### Post by Zotova on 2005-11-25
Ok, I had one of these little pests and had loads of problems with it.

First off the card is based on prism54, however check on your card, if it says version 2 then it won't work with the native linux driver. (Something to do with the cards being macless).

In ndiswrapper I got the card working however I found that every two weeks or so the card would simply stop working. The only way to get the darn thing working again was to recompile ndiswrapper and install fresh drivers. I never found an explanation to why.

From your post it sounds like the prism module is the problem. I'm presuming you have ndiswrapper setup with the windows 3com driver installed?

Open a terminal and firstly remove the prism54 module.

```
sudo rmmod prism54
```

That will free up the card and should allow ndiswrapper to take control.

```
modprobe ndiswrapper
```

Your lights should now light up and you should be able to connect to your network using the gnome network settings. Do you have a 3com router as well? I do and I've found that wpa is simply a no go, with both windows and linux. So if you do have a 3com router which you are trying to setup as wpa I'd switch to wep and save yourself a lot of hassle.

---

### Post by ofek on 2005-11-25
You need to add prism54 to the hotplug blacklist so it won't load on startup (or just delete it if u sure u dont need it, like I did).

---

### Post by Randy Sparks on 2005-11-25
It's a 3CRWE154G72 and it's Version 2.0.

I removed the Prism module and modprobed ndiswrapper. But then the card was no longer present in the network applet list. 

I lsmodded and saw that ndiswrapper was present and correct. I also restarted the PCMCIA service. But nothing seemed to make it work. The lights didn't light up on it. :confused:

EDIT: Turns out I haven't installed the Windows drivers, as mentioned by Zotova above. I'm following the instructions in this guide right now: [www.tuxmagazine.com/node/1000167](www.tuxmagazine.com/node/1000167)

---

### Post by Randy Sparks on 2005-11-25
OK. Got it sorted now. For the benefit of others, here's how I got it to work:

1- use Synaptic to get and install the ndiswrapper-utils package
2- go to 3Com's site and download the WinXP drivers for the card 
3- unzip the drivers (if it's an exe file you might have to use Windows to do this but you can try using the unzip command with the file)
4- locate the .inf file for the WinXP driver - usually the XP driver is in its own directory, although in the case of the 3Com drivers I used it was in a folder called "Driver". 
5- open a terminal window (Applications - Accessories - Terminal) and type 

sudo /etc/init.d/pcmcia stop
sudo rmmod prism54
sudo ndiswrapper -i *filename*.inf
sudo modprobe ndiswrapper

6- use the Network applet (System - Administration - Network) to setup your card and then test it by visiting a website etc. 
7- go back to the terminal window and type ndiswrapper -m 
8- type sudo gedit /etc/modules; this will open the modules list in a text editor. Add ndiswrapper to the bottom (won't work otherwise, despite the above step!)
9- type sudo gedit /etc/hotplug/blacklist; again, add prism54 to the bottom of the file
10- Reboot
11- Use the network applet under System - Admnistration to configure the network card (again)

After this it should work fine. :smile: The only bad part is that any wifi cards you might use in the future that use the prism54 module won't work unless you remove the prism54 entry from /etc/hotplug/blacklist.

---

### Post by Samy_Merchi on 2006-02-16
Well I must say I am having no joy with my Officeconnect card (3CRSHPW196). Your instructions were great and clear, Randy, but for some reason, ndiswrapper just isn't accepting the drivers I downloaded from the 3com site.

samy@seija:~$ sudo ndiswrapper -l
No drivers installed
samy@seija:~$ sudo ndiswrapper -i /media/usbdisk/3Com/3CRSHPW_96/Drivers/netwpx96.inf
Installing netwpx96
samy@seija:~$ sudo ndiswrapper -l
Installed ndis drivers:
netwpx96        invalid driver!
samy@seija:~$ sudo ndiswrapper -e netwpx96
samy@seija:~$ sudo ndiswrapper -l
No drivers installed

Why does it keep saying invalid driver and what should I do?

---

### Post by Samy_Merchi on 2006-06-03
I'm ready to scream. :)

Under Breezy, the card didn't work.

I upgraded to one of the Dapper Betas back in March or April or so, and it "just worked".

Now that the machine upgraded itself to the Dapper final release, it stopped working again. ARGH.

---

### Post by cblanquer on 2006-07-13
Little add-on regarding other 3Com cards: 
=> card PCMCIA 3Com 3CRXJK10075 (Office Connect Wireless 108Mbps 11g XJACK) works nearly out-of-the-box with Dapper, only ath0 needed to be activated with network-tools.

Remarks:
- it required setting ndiswrapper under Breezy.
- I have not been able to activate yet WPA encryption

---

