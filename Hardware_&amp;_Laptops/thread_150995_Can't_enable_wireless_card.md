---
title: "Can't enable wireless card"
date: 2006-03-27
forum: Hardware &amp; Laptops
---

### Post by Klefgodofbalance on 2006-03-27
Here is a fun one for you all.  I just installed Kubuntu onto my Alienware A51 m7700.  The problem i can't get pass is I am unable to enable my wireless card.

the command lspci displays my wireless as

0000:0a:05.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rec 01)

iwconfig lists this card as device ath0

When i go into System Settings > Network Settings that device is listed, but even with my eth0 disabled I can not enable the wireless card.  When I select enable Interface the green arrow flashes up for an instant and then goes back to the red circle with the x in it.  I receive no error messages when this happens.  

Can anyone point me in the right direction?

---

### Post by gurlyburlyman on 2006-04-03
I was having a similar problem and the posting on this site: [http://www.mepislovers.org/modules/n...14487&start=10](http://www.mepislovers.org/modules/n...14487&start=10)
worked for me.

Here's what I did:

```

sudo ifconfig wlan0 up
sudo ifup wlan0

```

This enabled the interface, but for some reason I still couldn't connect. So the next suggestion on the link above is:

```

sudo ifdown wlan0
sudo ifconfig wlan0 up
sudo ifup wlan0
sudo pump -i wlan0

```

The 'pump' command isn't on my computer, but the first three commands apparently did the trick. After rebooting I can just use the "sudo ifup wlan0" and that seems to do the trick.

---

