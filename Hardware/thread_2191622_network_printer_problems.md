---
title: "network printer problems"
date: 2013-12-03
forum: Hardware
---

### Post by wt-pm66 on 2013-12-03
This may get complicated, I'll try to be as clear as possible. I have a HP DeskJet 1051 all-in one printer. I did have it plugged straight into a pc, if it sat without being used for a day or two it would disappear from the hardware list. I would have to unplug the usb for a short time then plug it back in so it would be recognized again. I've had other printers that did the same thing, so it's not anything unusual. However now I have installed a networking wireless router with usb ports so you can network printers and whatever. I hooked it all up last night, and even printed with it, no problem. Now this morning it has disappeared, I did get up and go back to where it is and unplugged it for about 10 seconds plugged it back in with no luck. Last night I got the router up and going, then plugged the printer in, and my computer immediately picked up the printer. I'm thinking I'm going to have to get the IP address, or system location address, and put that in as a static printer, I'm guessing. Problem is I've got to get it recognized first so I can write down the address, that it shows. 

How do I get it recognized again, then make sure it stays recognized across all of the computers in the house?

---

### Post by philinux on 2013-12-03
Have a look at your network with  nmap.
My networked printer and phone show up when on.

[http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/](http://www.cyberciti.biz/networking/nmap-command-examples-tutorials/)

---

### Post by ajgreeny on 2013-12-03
Forgive me for asking, but are you aware that in order for the printer to be seen on the network the computer it is directly attached to must be running, and not switched off, nor in hibernation or suspension.  You also need to have the drivers for the printer installed on all machines that wish to use it.

It is also much easier, though I am not certain if it is totally necessary, to use a static IP either for the printer itself, if it is directly attached to a router, or the computer to which the printer is attached if it is indirectly attached to the network.  How you do that will depend on your network setup and your hardware router etc etc.

---

### Post by wt-pm66 on 2013-12-03
@Philinux, I tried to install nmap, it was already installed. So then I try the commands to check the network, and it just sat there. I put in the command, a new prompt popped up and that was that. What did I do wrong. I couldn't get it to upgrade either. 

@ajgreeny, Yes I am aware the computer has to be on. Matter of fact the computer the printer was attached to was the one I was trying to print from. Drivers are installed on all computers. I felt a static IP would be needed, I just need to know how to find it to start with so I can assign an IP. 

I put the IP of the router in my browser and opened the control panel, it shows the external hard drive connected by usb to router, but does not show printer. Well there is a media sharing section that finds music and pictures that's why the harddrive shows up, but there is not a section for printers or other  hardware. I'm going to try the Belkin support website, but I don't know if it's in Linux (booted into Windows 7 and the printer showed up, but I have the HP Monitor and preferences software installed in windows), or if it's in the router, so I'm checking both places until I find an answer.

---

### Post by philinux on 2013-12-04
@wt-pm66 with the printer connected to a networked machine do this.

```
sudo nmap -sP 192.168.1.0/24
```

---

### Post by ajgreeny on 2013-12-04
As the printer is attached to a computer you will need the IP address of the computer for the printer IP address; it will not have its own IP.
Therefore you will need to set a static IP for that computer.

---

### Post by wt-pm66 on 2013-12-04
> **philinux said:**
> @wt-pm66 with the printer connected to a networked machine do this.

```
sudo nmap -sP 192.168.1.0/24
```

Output is:
nmap: option '-sp' is ambiguous; possibilities: '--spoof_mac' '--spoof-mac'
Nmap 6.00 ( [http://nmap.org](http://nmap.org) )
Usage: nmap [Scan Type(s)] [Options] {target specification}
 
Then about 8 pages of instructions on how to use nmap. 

Currently when I click on the menu button, and type in HP, and click on HPLIP Toolbox, nothing at all happens.                                                                               When going to System Settings>Printers> Sorry the printing service does not seem to be available
When opening the HPLIP Status Service from the taskbar, nothing happens
When opening the HP Device Manager, it says there is no printer installed. I go through the process of installing the printer, which is detected (connected directly to computer), get to the end and it says the correct pdd file is not installed, Choose pdd file>yes> a folder opens with 5 pdd files, numbered from 0-4, it doesn't matter which one I click on, it's not the correct one. 

So how bad have I screwed it up? I've tried uninstalling cups multiple times, and reinstalling, I've tried upgrading hplip to current version several times, and it will not install, terminal says the latest version is installed, cups says it needs to be upgraded. 

Also a problem I ran into in the beginning when things actually worked halfway, is when going to localhost:631 and attempting other changes, it requires root username & password, but my username & password do not work. I found on internet that ubuntu doesn't use root passwords, so how do I manage this?

---

