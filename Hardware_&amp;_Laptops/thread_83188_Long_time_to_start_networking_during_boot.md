---
title: "Long time to start networking during boot"
date: 2005-10-28
forum: Hardware &amp; Laptops
---

### Post by wakeboarder on 2005-10-28
After enabling ath0 (WLAN) the boot seems to wait for networking to start. I can abort it with crtl-c and it will still work but it takes 1-2 minutes if I just leave it.
It's a HP Compaq NC6000 laptop with Breezy. The WLAN is atheros.
I will try and disable it again to see if I get my normal fast boottime back or not.
Any hints? :confused:

---

### Post by 23meg on 2005-10-28
If you can set yourself a static IP on your router, disable DHCP in Network Settings and enter your IP instead.

---

### Post by tombeharrell on 2005-10-28
It bugs me that networking takes so long to start, because I use my laptop in the office or elsewhere I have two network cards, and I don't want to have to reconfigure to turn the one I'm not using off every time I change. If I leave them both on it takes ages to boot up, I guess the one I'm not using times out eventually.

This must be getting to be more of a problem for people as laptops typically come with wired and wireless LAN these days.

It would be much better if DHCP happened in the background during bootup.

---

### Post by wakeboarder on 2005-10-28
Yes, if I disable ath0 (wireless) the boot doesn't wait.
But on the other hand if both cards are enabled it seems as if both cards are working however I don't know which one will be the default gateway.
At home I have a router with both cable and wireless.

What I trying to say is that I can't see why anything would need to timeout, since both wireless and cable should work, DNS should deliver addresses and so on.

---

### Post by Neovalis on 2005-11-19
I'm having the same problem

---

### Post by ubunny on 2005-11-28
yes i have the delay.  Any way to log these delays?  I'd like to know what else is slowing me down.

So I have the bootup delay from the finding network connections [ok] section, the connection itself isn't there.  Can always reboot to windows here and get online though....ar  

I've edited the hotplug file to comment out eth0 and set the flag settings NET something in another setting to auto but still it hangs on setup.

I get the double same beeps at boot for my orinoco gold G wireless card, but it then decides not to find a dhcp ip address.  dhclient reports nobody giving IPs.  I have an internal 11b card but this is switched off.  Chipset on atho is atheos (sp) so it's the right card I think, orinoco.

iwconfig has the ath0 there with the right connection and wep key but no IP.  

I really just want to use linux....ar

sudo ifup ath0 reports that it's already up but no ip and dhclient just goes on forever listening until ctrl-c ends my networking attempts for the session.

any suggestions are welcome

---

### Post by Heavenly Evil on 2005-11-28
Even though this was for the last version, it still works. See [this thread]("http://www.ubuntuforums.org/showthread.php?t=59420").

---

### Post by ubunny on 2005-11-28
sit0: unkown hardware address type 776
sit0: unkown hardware address type 776
Listening on LPF/ath0/00:0f:1f:00:0f:14
sending on  LPF/ath0/00:0f:1f:00:0f:14
sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
no DHCPOFFERS recieved
no working leases in persistent database - sleeping.

edited from another post but this is the same as my issue with ath0.  

since this isn't going, should I be looking at rebuilding the driver for the pcmcia card itself?  atheros chipset orinoco card.  Maybe this version running can't work with 5.10 .  Any thoughts on that.  Am I barking up the wrong tree?

I bought this card explicitly because it is known to have a high compatability rate with linux, yet here we are, no networking naturally....ar

thanks
u

---

### Post by finni on 2005-11-30
[QUOTE=ubunny]sit0: unkown hardware address type 776
sit0: unkown hardware address type 776
Listening on LPF/ath0/00:0f:1f:00:0f:14
sending on  LPF/ath0/00:0f:1f:00:0f:14
sending on Socket/fallback
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on ath0 to 255.255.255.255 port 67 interval 5
no DHCPOFFERS recieved
no working leases in persistent database - sleeping.

edited from another post but this is the same as my issue with ath0.  

since this isn't going, should I be looking at rebuilding the driver for the pcmcia card itself?  atheros chipset orinoco card.  Maybe this version running can't work with 5.10 .  Any thoughts on that.  Am I barking up the wrong tree?

I bought this card explicitly because it is known to have a high compatability rate with linux, yet here we are, no networking naturally....ar

thanks
u[/QUOTE]

Hello,

I've got nc6000 with atheros wireless working on ubuntu 5.10. I use selfmade scripts. 
Have you updated your wpa_supplicant lately? It helped me with getting dhclient to work.

---

