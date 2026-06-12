---
title: "Configuring Sound and Wireless on my IBM Thinkpad 600E"
date: 2008-12-26
forum: Hardware
---

### Post by rioguia on 2008-12-26
It was quite a trial but I got Xubuntu working on my IBM Thinkpad 600E, Model 2646-AAU.  There were three big problems.  
1. The install locked up if the Netgear MA401 wireless card was inserted during install. I just removed the card and reinstalled with no further trouble.  
2.  The wireless Netgear card didn't work (another lockup).  I had to blacklist hostap_cs drivers in order to allow the orinoco_cs drivers to load. (additional configurations were required--see below). 
3.  The sound requires quite a few module and blacklist incantations.  For example, you have to load the snd-cs4232 module in /etc/modules but your configuration in /etc/modprobe.d/alsa-base refers to the snd-cs4236 module.  I don't know why but it works.  

To add to the drama, when I got the sound working, my wireless card stopped working.  I had to exclude IRQ 3 in /etc/pcmcia/config.opts. I kept my notes at this [link]("http://www.substantis.com/blog/") and would be happy to hear any comments or questions posted here.

---

### Post by held7over on 2009-01-08
Sorry, didn't see your link. Great write up!

---

### Post by ralphaustin on 2009-03-28
Nice write up.
I just wanted to note some things I found enabling my old faithful IBM R31 with a ma401 - actually ma401ra card with WPA authentication. I'm on ubuntu 8.10. 

I used the hostap drivers. You'll find many references regarding blacklisting the orinoco drivers in your /etc/modprobe.d/blacklist if you use hostap. It's the converse of the original poster's process. You have to blacklist one of the other. My understanding is the hostap is more WPA friendly. 

If you get ioctl errors on trying to access the card do the irq 3 thing as noted in the substantis link above. 

>7. I am using a Netgear MA401 wireless card.  To get mine >working I had to tell pcmcia not to use IRQ 3:
>a.  sudo vi /etc/pcmcia/config.opts
>Add the line as exactly as written below:

exclude irq 3

I used the Network Manager to manage the networks, and that saves you ALL that stupid /etc/network/interface work. My 
/etc/network/interfaces only has the following in it:

auto lo
iface ip inet loopback

If you manage to get to the point where the network manager applet finds your ssid and you try to set up the authentication but WPA isn't showing up you may need to flash your card. This link helped me with that:

[http://sssg1.whoi.edu/swap_ftp/prism/flash_prism.html](http://sssg1.whoi.edu/swap_ftp/prism/flash_prism.html)

I used the command 
prism2_srec -v -f wlan0 PK010101.HEX SF010802.HEX
When I first did that, I hit the ioctl error. 

ioctl[PRISM2_IOCTL_HOSTAPD]: Connection timed out
Missing wlan component info
Could not read wlan RIDs

In my case it was needing to exclude the irq 3. Then I rebooted.
cat /proc/interrupts then showed pcmcia0.0 on irq 4
Seems there's some problem with sharing of irq 3. 

The weirdest thing was the last thing I did to get things working. When doing the prism2_srec flash I got the message saying that hostap_utils wasn't compiled to allow flashing.
That's something like "This requires PRISM2_DOWNLOAD_SUPPORT definition in driver/module/hostap_config.h."

Sighing deeply I downloaded the source from 
[http://hostap.epitest.fi/releases/](http://hostap.epitest.fi/releases/)
I downloaded hostap-utils-0.4.7.tar.gz and unrolled it in 
/usr/src

Then I went to run the prism2_srec command again to get the file name where I needed to make the change to enable flashing and when I ran it that time it worked. Go figure. I don't know if the software just got broken in at that point or if it picked up something from the /usr/src/hostap-utils-0.4.7 dir. But after the flashing and YAR (yet another reboot) my ssid popped up in the network manager applet with WPA enabled as an authentication option. 

Sorry for the sketchy description, but if you start from scratch trying to configure an old pcmcia wireless card with WPA in an old laptop just these general ideas might save you some time. I spent two or three weeks fooling with this off and on to get it to work. I went through different cards and drivers, madwifi, orinoco, downloading windows drivers and lots of different configs in /etc/network/interfaces before getting this to work. 
My advice:
Use Network Manager and strip /etc/network/interfaces to lo
Use hostap drivers if you want to use WPA
Make sure your card firmware supports WPA

My ma401ra works great now with the Thinkpad r31 and Ubuntu 8.10, logging me into the wireless on reboot with no manual BS. If the wire's in for eth0 it goes with that instead. 

One last thing. I see two things in ifconfig, both wifi0 and wlan0. If you see that and wonder if it's right, I guess it is. Works for me. 

Good Ubuntuing...
Ralph

---

