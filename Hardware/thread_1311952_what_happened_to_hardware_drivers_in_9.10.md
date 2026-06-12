---
title: "what happened to hardware drivers in 9.10?"
date: 2009-11-02
forum: Hardware
---

### Post by cliffk on 2009-11-02
i cannot get my wireless modem to work. a system test finds it:
E: ID_VENDOR_FROM_DATABASE=Broadcom Corporation[FONT=monospace]
[/FONT]E: ID_MODEL_FROM_DATABASE=BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller

but it is not in the hardware drivers list. i ran a live copy of 9.04 and drivers were listed in hardware drivers. what happened? 

or is there a new way to get wireless to work in 9.10?

---

### Post by unamanic on 2009-11-02
Yes, Connect wired, update and do Administration->Hardware Drivers.

---

### Post by hansdown on 2009-11-02
Hi cliffk.

Try running update manager, then check hardware drivers again.

Edit:

unamanic beat me to it.

---

### Post by unamanic on 2009-11-02
The need to connect to the net to install wireless drivers that are redistributed free (gratis) from Ubuntu repositories really gets me.  Ubuntu gave up it's free (libre) roots along time ago, why try to go back to them now?

---

### Post by cliffk on 2009-11-03
this is not working. update downloaded a number of unrelated things (eg python, firefox) which i let through, but afterwards, i went to hardware drivers and it is still blank. 

do i have to reboot?

i think i did this (update manager) with 9.04 and it showed hardware drivers, but i didn't pursue it because at the time i was running off a usb boot. i chose to install at 9.10, but now the hardwire drivers won't fill out. is there anything else i can try?

---

### Post by cliffk on 2009-11-03
rebooting has fwcutter showing up in hardware drivers and i activated it, but it doesn't seem to make any difference. i rebooted again and nothing. 

do i need to do something with fwcutter besides activating it in the hardware drivers?

there should be nothing wrong with my wireless hardware; it's never been a problem when i ran it under windows, so i don't think i have a hardware problem.

thanks for any help

---

### Post by unamanic on 2009-11-03
try a:
```

 sudo dpkg-reconfigure b43-fwcutter 

```
and tell it yes when it asks you if you want to download the firmware

ref: [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)

---

### Post by Hakkatuka on 2009-11-03
Try editing /etc/modules and adding "wl" at the last line, then reboot.

---

### Post by sandsjh on 2009-11-03
I have not seen the Dell Latitude e6500 supported on the netbook remix, but everything worked in 9.04. The wireless definitely does not work and it will "install" when connected to ethernet for a couple hours. I tried this twice. Rebooted. Etc.

The wireless driver hung up the update software on my Lenovo S10 twice. Seems like this release is buggy.

---

### Post by stevenw66 on 2009-11-03
I've tried it all. Drivers are initialized but no wireless device detected oh HP1000. I'm prettyy frustrated with Ubuntu regressing eith in multimedia or wireless with every release.

---

### Post by cliffk on 2009-11-03
ok, unamanic, i did the dpkg-reconfigure you suggested. when i go to menu/preferences/network connections/wireless there is nothing listed (eth0 is listed under wired devices). is there a more appropriate way to determine if i have wireless and if so, how do i configure it?


(i did do the lspci|grep command from the link reference and indeed a 4318 wireless was returned on my system)

next i tried removing driver in hardware drivers before dpkg-reconfigure (bad idea, "package broken" but i just reactivated it and i think it's ok), i tried rebooting, and i tried apt-get install b43-fwcutter ("up to date"), which was listed in the reference link you gave. 

obviously i don't know what i'm doing, or what to do next. before i mess something up, maybe you can tell me what to do next, or how i am meant to verify that the wireless device is functioning properly.

---

### Post by JunRamoneda on 2009-11-08
> **stevenw66 said:**
> I've tried it all. Drivers are initialized but no wireless device detected oh HP1000. I'm prettyy frustrated with Ubuntu regressing eith in multimedia or wireless with every release.

I have the same frustrations with Ubuntu.  My Lenovo S10 wifi was working perfectly with 9.04 and when I upgraded to 9.10 I can't get wireless networking to work.

Also tried the sudo dpkg-reconfigure suggestion but no luck

---

### Post by cliffk on 2009-11-08
i've gotten my broadcom working, but i reported it in a new thread because at the time the presenting problem had changed significantly. that thread is [here]("http://ubuntuforums.org/showthread.php?p=8246512#post8246512"). i'm not entirely sure how the problem got solved, but i found a few tools that were useful. can you try a few things on your Lenovo S10? this goes for the other laptops mentioned in this thread... maybe we can get enough information here to solve this....

i think the lenovo has a broadcom wireless in it?[INDENT]lspci | grep ireless    
[/INDENT]grep was case sensitive for me, so i left off the 'w'/'W' ...
then try[INDENT]iwconfig
[/INDENT]and[INDENT]nm-tool

[/INDENT]cut and paste relevant information here. particularly which wireless router you have.

i can't be sure if it made a difference, but i ran something called sudo NetworkManager. that might have helped.

as noted in the separate thread, the first sign of life out of my wireless was the Tx-Power setting in iwconfig, which i was able to turn on and off at will by enabling/disabling my wireless from the keyboard (my particular laptop used Fn-F2, but i have another laptop that has it as a dedicated button) and running iwconfig afterward to see the new settings.

at some point, the wep settings i entered in a gui magically showed up in iwconfig. this happened after some sequence of reboots and running NetworkManager. i may be wrong, maybe NetworkManager is already running on 9.10, i'm just not clear how or when it started working.

i have rebooted several times since, and my wireless reliably comes up, so whatever i did stuck. if you don't have NetworkManager on your system, let me know. i'm still trying to collect information on what i did to get this to work!  fyi, NetworkManager is in the network-manager package if you need to install it (apt-get install network-manager)

anyone else on this thread with laptops that don't work, try pasting the information from the commands listed above... maybe we can figure something out!

btw, recall the link unamanic listed:  [http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
this seems the best source of information on getting wireless to run on linux. if you aren't broadcom wireless, back out of the b43 page.
[I]
btw, the network gui i mentioned above was from the menu System/Administration/Network, click to make changes, then select properties of the Wireless. I turned off "roaming" and entered the ESSID and WEP settings here (i'm afraid to turn back on roaming since i don't want to jinx it :)).

two other network gui's that come with ubuntu: System/Administration/Network Tools doesn't even realize there is a wlan0 (when i try to set properties from this gui it says wlan0 "interface does not exist" (well done, he said sarcastically). the other one is under System/Preferences/Network Connections where a "wireless connection 1" magically showed up when things started working. So there are 3 separate guis pertinent to wireless networking, which is very confusing, hence this additional "btw"[/I]. 
[I]my recommendation: use "System/Administration/Network" and pray to the gods of your choice that it shows up in iwconfig :)
[/I]

---

