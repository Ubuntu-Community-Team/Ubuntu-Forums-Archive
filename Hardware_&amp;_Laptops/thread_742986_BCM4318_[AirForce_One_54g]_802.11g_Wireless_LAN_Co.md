---
title: "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller"
date: 2008-04-02
forum: Hardware &amp; Laptops
---

### Post by Neo31rex31 on 2008-04-02
I'm completely new to these forums so please bare with me , and i apologize if i posted this in the wrong place. 

As a fairly new linux user i'm having some problems getting my "BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller" in my compaq presario v5000 laptop. After several attempts at installing Kubuntu, Ubuntu, GOS etc etc. I finally got one to install correctly on my system (i had a hardware error and had to pull the cmos battery to correct it) that aside, i currently have ubuntu 7.10 installed and am unable to get this wireless card to work. I have scoured the internet and tried various fixes and nothing has worked so far. I have tried to use the restricted drivers but it says there is a firmware issue, (sorry the laptop isn't in front of me so i could give off the exact error). Does ANYONE have any suggestions.
Thanks
Eric

---

### Post by luisromangz on 2008-04-02
You should try using Ndiswrapper. Look for info in their website, and if you have problems, come back to the forums.

---

### Post by Neo31rex31 on 2008-04-02
ok i'll check it out, thanks

---

### Post by bremedios on 2008-04-02
At least with some of the Broadcomm drivers (I'm not sure if it's all) you'll also have to enable the firmware in the "Restricted Drivers Manager" for the Broadcomm driver to work (mine would be seen by the OS without it, but couldn't connect to anything.)

Also check the state of the wireless power on your laptop, it's possible that on some laptops they use a software-based switch instead of a hardware based-switch.  I know on an Acer laptop that I once worked on, you couldn't change the wifi power without an appropriate driver installed.

---

### Post by Xintron on 2008-05-07
bremedios: I'm on a acer laptop, having the AirForce One wireless card and I know there's a switch (you have to turn it on when using windows for example) and I wonder how I turn this switch on and what driver I need.

---

### Post by fokukac on 2008-05-16
a few tips to ndiswrapper:
**what it is**: lets linux use windows xp hardware drivers
**what do you need to use it**: ndiswrapper, ndiswrapper-common and the win xp driver files (xxx.inf, xxx.sys)
install it by typing: 
```
sudo apt-get install ndiswrapper ndiswrapper-common ndisgtk
```
**how to use it**: if you do not like command line, there is a graphical frontend for ndiswrapper called ndisgtk on the ubuntu repos. you can get it with a simple apt-get. It is pretty intuitive.

good luck and have fun

---

