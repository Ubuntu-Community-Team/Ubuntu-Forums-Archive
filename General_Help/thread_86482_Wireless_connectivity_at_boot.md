---
title: "Wireless connectivity at boot"
date: 2005-11-05
forum: General Help
---

### Post by cavaughan on 2005-11-05
Have been using Ubuntu now for several months, but there's one thing with my wireless connectivity that is getting on my nerves. Everytime I reboot I have to go through a series of precedures just to get my wireless card to connect to my wireless router. Unfortunately, I have never been able to pin down what exact procedure I need to follow. But here are a few things I can say for sure.

At boot up there is 0 connectivity with my wireless router. However, eth1 (the wireless card) is active (enabled). I have to manually issue the command:

iwconfig eth1 key restricted **************

And then I seem to have connectivity to the router. I judge that I have connectivity by the fact that the network icon turns from 1 red diamond to several blue ones. However, I never get an ip address from the router. Then I just go through a series of ifconfigs and ifups and ifdowns, etc., sometimes even /etc/init.d/network restart before finally I get an ip address. Kind of a hassel. How can I make this more automatic?

Here is my interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
name Wireless LAN card
wireless-essid CCCP
wireless-key **************************

---

### Post by rado_london on 2005-11-08
Hi 
I had the same problem, but I found a bit strange solution.
First, enable root access via GDM, using System>Administarion settings>login screen>security and tick on "allow root to login with GDM"
Second log out from your user account and login as root using GDM.
Third, go to System>Administration>Network and enable your wireless card. Also at the bottom of the windows says "default interface".Select your wireless card.Click ok and exit.
Restart and if it is working post back!
Best Regards

---

### Post by cavaughan on 2005-11-09
No that didn't change anything. However, I have noticed that I need to be more patient. After issuing the command: 

iwconfig eth1 key restricted *********************

I walk away for awhile and then lo and behold I have an IP address. I'm not sure what's up one with why I have to issue this command and why I have to wait.

Curtis

---

### Post by ngms27 on 2005-11-10
This depends on the drivers.

Even under Windows some Wireless nics won't initialise until after logon by default.

JonnyT

---

### Post by Tunnelrat81 on 2005-11-10
I had a similar problem after both of my initial installs of ubuntu.  The only way I was able to solve the problem was to make the /etc/network/interfaces file immutable by "sudo chattr +i /etc/network/interfaces" I believe.  Before this I would setup my interfaces file and it would work, but after a reboot, my WEP key would have been changed in that file.  So I'd go back and change it again to get it to work.  Making the file immutable means that the file maintains it's proper WEP key entry.  In gnome 'networking' the wep key is "*'d" out in the properties, and mine was indicating that my key was only four digits long, when in reality it's longer.  This must be a security measure, but for some reason I think it may have been setting the interfaces file to match the device properties as listed in gnome.

I currently still have only four digits "****" listed in gnome as my wep key, but my interfaces file remains accurate and I'm able to connect on startup.  hope this helps.

-J

---

### Post by mad_pheonix on 2005-11-10
Once you issue that iwconfig command to give the proper key, you can instantly get an ip/activate the interface by running:

```
sudo /sbin/ifup [interface]
```

That's how I normally activate my wireless after I boot.  I wish there was some way of storing local profiles though, so that I could just activate a profile and it would know the right essid and key.

---

### Post by Maverick911 on 2005-11-10
[QUOTE=cavaughan]No that didn't change anything. However, I have noticed that I need to be more patient. After issuing the command: 

iwconfig eth1 key restricted *********************

I walk away for awhile and then lo and behold I have an IP address. I'm not sure what's up one with why I have to issue this command and why I have to wait.

Curtis[/QUOTE]

Hi, 

I've been having the exact same problem.
You might try this in your interface file and see if it works.

```
auto lo
iface lo inet loopback


# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

auto eth1
iface eth1 inet dhcp
name Wireless LAN card
wireless-key ************************** 
wireless-essid CCCP **(reverse the order of these this and your key command)**

# auto eth0 **(comment this out so your wired interface isn't looking for a connection)**
iface eth0 inet dhcp
```

Good Luck. Let me know if this helps.

---

### Post by Maverick911 on 2005-11-11
Hello All, 

Ignore my previous post (for the most part). The real problem had something to do with my upgrade to 2.6.14-ck1 kernel or ndiswrapper version 1.5.

My wireless is working perfectly at boot now.\\:D/ What I did was reinstall ubuntu, downloaded the stock 686 kernel, and used the ndiswrapper version 1.1 that's included with ubuntu.

After three weeks of fighting with trying to get my Broadcom wireless working at boot without having to ifconfig wlan0 up, ifconfig wlan0 down, iwconfig key.... etc, etc, etc, I'm a really happy camper right now. AND, I learned a good lesson about the pitfalls of living on the bleeding edge.

The only changes I made after reinstall were to my /etc/network/interfaces file so that my wireless (wlan0) would be the default network connection and my wired (eth0) would not be activated until I need it. (No more delay on bootup while it looks for a connection!)

I'll post the changes I made later when I've got more time, but until then the best advice I can offer is stick with the stock kernel and the ndiswrapper version 1.1 module that's included in the distro.

Happy Computing Everyone :D

Hmmm..Now I think I'll see if I can get my printer to work :wink:

---

