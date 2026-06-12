---
title: "Network help"
date: 2008-11-16
forum: Hardware
---

### Post by RP64 on 2008-11-16
Hey  guys, I am totally sick of Windows and its crap, I only use windows on another computer for playing PC games, but for regular internet, email, messenger use etc. Im totally into switching to Linux, and I picked Ubuntu cus of its ease of use involving its interface, and its similarities but many advantages over the well made Redhat distro, and anyways so I burnt the ISO of Ubuntu 8.10 to a DVD disk, and I put it in my drive, and I tried to live CD "demo" of it. everything is totally GREAT its just for one thing.... it can't recognize my wireless network. I found out its because companies dont always release all of their drivers publicly, so the open source projects have no way of including those drivers in their programs. Thing is, its working with all other drivers of my laptop, which BTW is an HP Pavillion DV6500 laptop. It has quicklaunch buttons, volume controll quicklaunch controls etc. and a touchpad mouse pad and ALL of this works perfect with the Ubuntu install. The one thing is my wireless connection not showing up which I think is cus of drivers. So anyways, I tried doing stuff with this "ndiswrapper" program, and its gui ndisgtk, and the synaptics installer tool with the ubuntu, but none of it is allowing Linux to recognize my wireless card cus it wont connect to my wireless network. ANYWAYS I've already made a short story long, so could you just... well It may be annoying and time consuming for someone to do this but I would really appreciate it if someone could do some things to help me, basically I'd love it if one of you experienced users could please get a list of all programs I need, give me links to those programs/files (to download), and then step by step detailed instructions on how to make my Ubuntu 8.10 Linux recognize my damn wireless network! I'm too NOOB to do this on my own but hate Microsoft love Linux Please help, THANKS

---

### Post by melojo on 2008-11-16
Try here

[http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops](http://aldeby.org/blog/index.php/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops)

---

### Post by RP64 on 2008-11-16
well the part on that link u showed me talking about the wireless card sort of helps me, but I dont know how to install ndiswrapper so full step by step would like totally help me

---

### Post by RP64 on 2008-11-16
also how do you open the command prompt to enter those manual commands? lol and I know its not called command prompt in linux but I dont know the real name T__T

---

### Post by melojo on 2008-11-16
Below is from the link, Did you read through it?  If not I would read through the whole thing before proceeding.

> HP Pavilion Laptops with AMD Turion platform ship with a Broadcom wireless card. Unfortunately Broadcom is one of the least Linux friendly companies and in fact it does not provide any support for linux OSs (differently from e.g. Intel). Given this, support for linux is provided via ndiswrapper hack.

You can download the windows drivers here (these are for a Broadcom BCM 4328 but should work for all the series) then extract the archive in a folder you call broadcom in your home directory.

Install ndiswrapper and follow the procedure:

sudo apt-get install ndiswrapper-utils

sudo ndiswrapper -i $HOME/broadcom/DRIVER_EN/bcmwl5.inf

sudo ndiswrapper -l

sudo modprobe ndiswrapper

To make ndiswrapper automatically run at each startup:

sudo ndiswrapper -m

OR we can add ndiswrapper module to boot modprobed drivers

gksu cat ndiswrapper >> /etc/modules

At next bootup your Broadcom wireless card will be recognized!


---

### Post by melojo on 2008-11-16
> **RP64 said:**
> also how do you open the command prompt to enter those manual commands? lol and I know its not called command prompt in linux but I dont know the real name T__T


Click menu button>accessories>terminal

---

### Post by RP64 on 2008-11-16
no thats the part (your quote) I read but I meant how the first part said "install ndiswrapper" I don't know how to do that part, is that part of the package he had posted for download in that quote?

---

### Post by melojo on 2008-11-16
Type or copy and paste this in a terminal and hit enter.  This should install ndiswrapper.
```
sudo apt-get install ndiswrapper-utils-1.9* ndiswrapper-common
```

---

### Post by RP64 on 2008-12-22
oh just as an update this was only a problem on the LiveCD when I fully installed the Ubuntu onto my harddrive, it detected the network instantly lol but thx for trying to help

---

