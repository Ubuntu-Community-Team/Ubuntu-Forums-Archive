---
title: "NetworkManager and Madwifi"
date: 2007-04-04
forum: Hardware &amp; Laptops
---

### Post by fettuohi on 2007-04-04
I have just installed Ubuntu 7.04 on my DELL Inspiron 8200 laptop and I can get my wifi card (Netgear WAG511) working. I plug it in (it's an external card) and set the ip address etc. with the networkmanager then I try to connect to my wireless network (WPA secured). I set up the ESSID and password and then nothing happens :(. It simply just tries to connect and then it fails. I tried then to set it up with wpasupplicant instead and worked fine but I still can't get on the internet for some reason my laptop insists on using my wired card instead and I can't figure out how to make it use my wifi card which is connected to my network. I got this working under Edgy just fine with KDE. Here I just turned off the eth0 complete but since I'm using gnome now I can't find anyplace where to do that. Any suggestions on what I am missing here and how get it working with NetworkManager maybe?

Regards

André

---

### Post by fettuohi on 2007-04-04
Anybody?

---

### Post by kerry_s on 2007-04-04
To disable wired, right click the network icon and uncheck enable wired.
Wireless sucks in feisty, for me anyway, try installing ndisgtk, it's in the repo, it's front end to ndiswrapper, look for it under administrator> install windows driver. I played with mine for about 2 weeks, i'm just going to by a different card that's more linux compatible.

---

### Post by fettuohi on 2007-04-05
Well, I got it working now with the NetworkManager but only if my AP is broadcasting its ESSID. I normally have set so that the AP doesn't broadcast the ESSID. Can someone explain to me why it works when the AP is broadcasting and doesn't work when it's not. Am I missing some option I need to enter?

Regards

André

---

### Post by liquidalien on 2007-04-06
Same problem for me... It may be related to the madwifi version... The new 0.9.3 corrects lots of bugs. I'll try to compile it tomorrow and i'll post my comments in this thread.

Today, I don't use networkmanager but wpasupplicant and it works well, exept for DHCP... Sometimes I have to use dhclient manueally.

---

### Post by fettuohi on 2007-04-06
That may be because when I log in only the IP address has been set but not the gatway etc. and I use static IP.

Regards

André

---

### Post by fettuohi on 2007-04-06
> **liquidalien said:**
> Same problem for me... It may be related to the madwifi version... The new 0.9.3 corrects lots of bugs. I'll try to compile it tomorrow and i'll post my comments in this thread.

Today, I don't use networkmanager but wpasupplicant and it works well, exept for DHCP... Sometimes I have to use dhclient manueally.

I normally also just use wpasupplicant (under edgy) but under feisty that doesn't even work. I do get the connection to the AP but I still don't have any internet connection for some reason the DNS addresses aren't being set :(. I tried to turn off NM and eth0 but nothing helps. But when I broadcast the ESSID I can connect without any issues. Clearly there is a bug somewhere... :( :confused: 

Looking forward to your post.

Regards

André

---

### Post by fettuohi on 2007-04-09
> **liquidalien said:**
> Same problem for me... It may be related to the madwifi version... The new 0.9.3 corrects lots of bugs. I'll try to compile it tomorrow and i'll post my comments in this thread.

Today, I don't use networkmanager but wpasupplicant and it works well, exept for DHCP... Sometimes I have to use dhclient manueally.

Any luck with recompiling madwifi?

Regards

André

---

### Post by liquidalien on 2007-04-10
I've tried yesterday, but with some errors... The atheros device didn't work anymore. I've had to reinstall the ubuntu madwifi version because I'v completely lost the network.

After that, networkmanager worked one time, and now the problems are back.

I'll try a new install of Kubuntu 7.04 this week-end with the new RC (if it's out).

Regards,

/Fabien

---

### Post by fettuohi on 2007-04-10
> **liquidalien said:**
> I've tried yesterday, but with some errors... The atheros device didn't work anymore. I've had to reinstall the ubuntu madwifi version because I'v completely lost the network.

After that, networkmanager worked one time, and now the problems are back.

I'll try a new install of Kubuntu 7.04 this week-end with the new RC (if it's out).

Regards,

/Fabien

I uninstalled the network manager and installed the wicd manager and then I got it to work. I had to shut off my eth0 first but after that I had wireless networking :).

Regards

André

---

### Post by liquidalien on 2007-04-10
Thanx. I'll try...

---

### Post by sabi on 2007-04-10
This link may/may not help ....

[http://ubuntuforums.org/showthread.php?t=405344](http://ubuntuforums.org/showthread.php?t=405344)

Sabi

---

### Post by stchman on 2007-04-10
> **fettuohi said:**
> I have just installed Ubuntu 7.04 on my DELL Inspiron 8200 laptop and I can get my wifi card (Netgear WAG511) working. I plug it in (it's an external card) and set the ip address etc. with the networkmanager then I try to connect to my wireless network (WPA secured). I set up the ESSID and password and then nothing happens :(. It simply just tries to connect and then it fails. I tried then to set it up with wpasupplicant instead and worked fine but I still can't get on the internet for some reason my laptop insists on using my wired card instead and I can't figure out how to make it use my wifi card which is connected to my network. I got this working under Edgy just fine with KDE. Here I just turned off the eth0 complete but since I'm using gnome now I can't find anyplace where to do that. Any suggestions on what I am missing here and how get it working with NetworkManager maybe?

Regards

André

Do an lspci at the terminal.  If you see Atheros then Feisty should support it.  If not try installing the madwifi drivers.  I have a procedure to install madwifi.

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

This should work well.

---

### Post by liquidalien on 2007-04-11
I've removed network-manager and now all is ok ! It connects very fast. I use knemo to monitor the connection.

@schtman : I'll try you tuto this week-end. Thank you.

Thanx to all.

---

