---
title: "Please help an ubuntu noob"
date: 2009-07-05
forum: Installation &amp; Upgrades
---

### Post by -Blake- on 2009-07-05
I am coming straight from Windows XP and Vista and just installed Ubuntu 9.04, but I do not know how to configure it correctly. So far I have been trying to follow the steps the posters have been giving this guy but it isn't helping me. [http://www.neowin.net/forum/index.php?showtopic=468431&st=15](http://www.neowin.net/forum/index.php?showtopic=468431&st=15)

The display options give me no other choices but 800 x 600 and 640 x 480. I don't know how to update the drivers for my hadware or even check the status of my desktop to see how it is running. Please help! I installed the AMD64 edition running on an AMD K8 3800+ 2.4Ghz single core, 2 gigs memory, integrated nvidia graphics, 20 gb partition (is that enough?). My computer is an eMachine W5243.

---

### Post by taurus on 2009-07-05
Do you see your graphic card on the list in System -> Administration -> Hardware Drivers?

---

### Post by Sukotto on 2009-07-05
Has there been a notification popup on the top about Restricted Drivers? Check out the last poster post and get back to us. Soon as the correct video driver is installed you can change the resolution.

---

### Post by -Blake- on 2009-07-05
That worked! Thank you so much! Now I can work on my wireless internet, it does not sign on even though I input the SSID and WPA/WPA2 password. It constantly tries to reconnect. Had to fabricate a 20 ft LAN cable to reach this desktop to the router. I have deleted the connection and recreated it but no luck...It keeps popping up about allowing "access to the network secret password" and the "keyring," once I click allow it will wait a few seconds and pop up with a Wireless Network Authorization Required dialog box for the password to the network. If I click on the show password checkbox it does not have the password I input. Is this a security encryption or an error somewhere?

---

### Post by khelben1979 on 2009-07-05
[nVidia drivers from nVidia.com]("http://www.nvidia.com/page/pg_20030521269172.html")

You need to know what integrated graphics you have and then choose the correct choice from the list:
```
sudo lspci
```
gives this information.

The /etc/X11/xorg.conf contains all the information based upon the creation of the X configuration file.

[EnvyNG]("http://en.wikipedia.org/wiki/Envy_%28software%29") is a program which makes installation of graphics drivers easier (check the link).

```
sudo apt-get install envyng
```
installs envyNG in your system using root priviliges.

[EnvyNG Wiki]("http://albertomilone.com/pmwiki/pmwiki.php?n=Main.EnvyNG-InstructionsForUbuntu") if you feel uncertain.

For every other command you feel uncertain about, just use the [man]("http://en.wikipedia.org/wiki/Man_%28Unix%29") command and read the manual. You will learn a lot. Having [patience]("http://en.wikipedia.org/wiki/Patience") is also something you will benefit from.

---

### Post by ajgreeny on 2009-07-05
What wireless adapter do you have as some are not very good with linux or ubuntu, and some will work only with wep and not wpa security.

---

### Post by -Blake- on 2009-07-05
I typed in the sudo lspci and I think it showed all the hardware in my pc. I will post the screenshot. I do not have a wireless NIC but instead a USB peripheral by Belkin to connect wirelessly.

---

### Post by ajgreeny on 2009-07-05
I suppose the Restricted Driver dialog does not offer anything for your realtec card, does it?

---

### Post by -Blake- on 2009-07-05
I don't know, how do I find the restricted drivers?

---

### Post by -Blake- on 2009-07-05
Also [khelben1979]("http://ubuntuforums.org/member.php?u=443262"), I tried the sudo apt-get install EnvyNG and it said:

Reading package lists...done
Building dependency tree
Reading state information...done
E: couldn't find package EnvyNG

---

### Post by Sef on 2009-07-05
> I don't know, how do I find the restricted drivers?


System > Administration > Hardware Drivers

---

### Post by khelben1979 on 2009-07-05
> **-Blake- said:**
> Also [khelben1979]("http://ubuntuforums.org/member.php?u=443262"), I tried the sudo apt-get install EnvyNG and it said:

Reading package lists...done
Building dependency tree
Reading state information...done
E: couldn't find package EnvyNG

Did you try without using capitals:
```
sudo apt-get install envyng
```

and not
```
sudo apt-get install EnvyNG
```

Also, try search for envy in [synaptic]("http://en.wikipedia.org/wiki/Synaptic_Package_Manager") if that fails.

---

