---
title: "3G network issue,"
date: 2008-08-23
forum: General Help
---

### Post by dragon2611 on 2008-08-23
I have Ubuntu-eee 8.04 installed on my Asus EEE 900, Works fine with wi-fi and wired lans. (afiak its the same as Ubuntu 8.04 just with some eee related hacks/optimisations predone)

The only problem I do seem to be having is with my E170 HSDPA modem.

I downloaded UMTSMON and use it setup the APN and enter the PIN or the simcard.

It accepts the pin finds the network, can hit connect and a PPP session successfully establishes and Indeed the internet works

Only problem i'm having is with the system detecting there is an active Network connection, it doesn't seem to be doing so

For instance I will start firefox and it will start in offline mode, Pidgin will sit on "Waiting for network" and I know it can work over the Mobile modem (for Aim at least, MSN is a bit iffy via the mobile network)

Is there something I need to change to make Ubuntu see there is a network connection available, the apps do actually work if they try to talk to the internet it's just some aren't bothering becuase they think there isnt a network connection.

---

### Post by Alaric on 2008-08-23
You might want to try posting this in the networking/wireless section instead of General Help.  

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

P.S., You might want to add a 'cat /etc/network/interfaces' to your post.

---

### Post by dragon2611 on 2008-08-23
> **Alaric said:**
> You might want to try posting this in the networking/wireless section instead of General Help.  

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

P.S., You might want to add a 'cat /etc/network/interfaces' to your post.

Posted...

But I think that might be the problem but i'm not sure of the syntax to add ppp0

```
dragon@dragon-eee:/dev$ sudo cat /etc/network/interfaces 
auto lo
iface lo inet loopback 

```

---

### Post by Alaric on 2008-08-23
Try running the 'network-admin' command.  If your modem shows up in there, then I'm stumped, and won't be any help.  If it doesn't (as I assume it won't), then chances are good that the third party software for your network card is handling the internet connection through the card instead of the OS default programs.  In that case, you may be able to find a work around, such as adding a dummy device to network-admin that will appear always on, or by finding better software that utilizes Ubuntu's default network-admin application.  You could try setting your Ethernet port to a static IP address (as opposed to a default DHCP automatic address) so it appears always connected... but that could override your third party software and keep you from connecting to the internet at all.  It's worth a shot though; it should be easily reversible.

---

### Post by dragon2611 on 2008-08-23
Shows as not configured, I did try configuring it but didn't get anywhere.

I think UMTSMON uses WVdial as its backend.

---

### Post by Alaric on 2008-08-23
Sorry man, I have no experience with WVDial.

---

### Post by dragon2611 on 2008-08-23
Threw the Wired NIC to DHCP instead of "Roaming Mode" ubuntu now seems to think theres an active network interface all the time.

I would ideally like proper detection of network interface status but oh well it works.

---

