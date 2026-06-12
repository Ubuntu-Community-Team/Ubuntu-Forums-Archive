---
title: "*sigh* WLAN card not recognized"
date: 2006-04-18
forum: Hardware &amp; Laptops
---

### Post by Minyaliel on 2006-04-18
Hi guys,
I'm running Kubuntu on a HP Pavilion ze2000 and have a wireless LAN Pc card from Topcom (skyracer pro card 3054). I *think* I have installed the windows wireless drivers - it does at least show up in my menu, admittedly I have no idea whether it's actually installed, and I can't make much out of the readme's/ install texts. Well, my laptop doesn't recognize the card, the "link" light is flashing but nothing else. What's strange is that the card worked out of the box earlier, before I did a very stupid experiment with Dapper and the system broke down. After I reinstalled the wretched thing, it wouldn't work. Any help is highly appreciated!

---

### Post by Minyaliel on 2006-04-21
Please?

---

### Post by amp_man on 2006-04-22
okay, first of all, you shouldn't be using ndiswrapper, this card is atheros based and supported by madwifi (see [this](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards) page, scroll down to TopCom). so, unload the windows driver (ndiswrapper -e drivername, no extension), remove ndiswrapper from /etc/modules, run "sudo rmmod ndiswrapper", and that should get you back to square one. as far as getting atheros/madwifi going, I have no idea, but at least now you don't have ndiswrapper conflicting with them. you can try "sudo ifconfig ath0 up", it might do the trick for you. If not, and noone else posts here, check out [http://madwifi.org](http://madwifi.org)

edit: [http://www.ubuntuforums.org/showthread.php?t=75451](http://www.ubuntuforums.org/showthread.php?t=75451)

---

### Post by Minyaliel on 2006-04-24
I tried it, didn't work :P

---

### Post by Minyaliel on 2006-04-24
[QUOTE=Minyaliel]I tried it, didn't work :P[/QUOTE]

Aww man, forget what I said, it's WORKING!!! *jumps up and down in glee* I'd just not tried the last command.... thankyouthankyouthankyou!!!

---

### Post by Minyaliel on 2006-04-25
Actually, it didn't work after all. That is, it worked that one evening (or so I thought) and now it doesn't recognize the device again.

niah@Cherceros:~$ sudo ifconfig ath0 up
Password:
ath0: ERROR while getting interface flags: Kein passendes Gerät gefunden (transl: No fitting device found)
niah@Cherceros:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
niah@Cherceros:~$ modprobe ath_pci
niah@Cherceros:~$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: Kein passendes Gerät gefunden
niah@Cherceros:~$

---

### Post by shamrock_uk on 2006-04-25
[QUOTE=Minyaliel]Actually, it didn't work after all. That is, it worked that one evening (or so I thought) and now it doesn't recognize the device again.

niah@Cherceros:~$ sudo ifconfig ath0 up
Password:
ath0: ERROR while getting interface flags: Kein passendes Gerät gefunden (transl: No fitting device found)
niah@Cherceros:~$ sudo rmmod ndiswrapper
ERROR: Module ndiswrapper does not exist in /proc/modules
niah@Cherceros:~$ modprobe ath_pci
niah@Cherceros:~$ sudo ifconfig ath0 up
ath0: ERROR while getting interface flags: Kein passendes Gerät gefunden
niah@Cherceros:~$[/QUOTE]

Sorry, I'm not sure if you've done this, but you need to install the relevent linux-restricted-modules for your kernel in order to get the madwifi drivers. 

After doing that and rebooting, running iwconfig should show your card there under ath0. 

Then ifup ath0 should do the job, assuming it's configured (but this last part can be done from the gnome network dialogue)

---

### Post by Minyaliel on 2006-04-25
Right, so how do I get those?

---

### Post by shamrock_uk on 2006-04-25
[QUOTE=Minyaliel]Right, so how do I get those?[/QUOTE]

You can either search in synaptic (but make sure you match the kernel number with the drivers), or try

*sudo apt-get install linux-restricted-modules-`uname -r` *

which should do it automatically.

Ubuntu is particularly good with wireless cards because it ships with this on the cd.

---

### Post by Minyaliel on 2006-04-25
Gonna try that and get back to you :)

---

### Post by Minyaliel on 2006-04-25
Still doesn't recognize the card :P

---

### Post by shamrock_uk on 2006-04-25
[QUOTE=Minyaliel]Still doesn't recognize the card :P[/QUOTE]

Sorry, just realised I'm being forgetful. 

After rebooting into the new system, you need to do the following at a console:

*sudo modprobe ath_pci*

That should load the atheros driver. (Installing the restricted modules simply makes it available, this command actually loads it)

Then try iwconfig and see if its listed. Apologies, it's been a long day at work ;)

---

### Post by Minyaliel on 2006-05-01
[QUOTE=shamrock_uk]Sorry, just realised I'm being forgetful. 

After rebooting into the new system, you need to do the following at a console:

*sudo modprobe ath_pci*

That should load the atheros driver. (Installing the restricted modules simply makes it available, this command actually loads it)

Then try iwconfig and see if its listed. Apologies, it's been a long day at work ;)[/QUOTE]

I'm going to try that... thanks :)

---

### Post by Minyaliel on 2006-05-02
It works now... can't say how grateful I am for the help :)

---

### Post by shamrock_uk on 2006-05-03
[QUOTE=Minyaliel]It works now... can't say how grateful I am for the help :)[/QUOTE]

Not a problem, glad its working now :)

---

