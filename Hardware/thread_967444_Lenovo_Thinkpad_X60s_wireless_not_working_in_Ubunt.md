---
title: "Lenovo Thinkpad X60s: wireless not working in Ubuntu, working in Windows"
date: 2008-11-02
forum: Hardware
---

### Post by zee on 2008-11-02
Hi.
  I have a Lenovo X60s laptop that ran Ubuntu 8.04 just fine with all the hardware working perfectly. 

  Now, yesterday I tried to set up a completely encrypted system so I booted up the system with the Intrepid Ibex (Desktop) CD. While in the live environment I was able to connect to my wireless network (uses WPA-PSK for authentication) but only for a few minutes, because all of a sudden the connection was dropped and I was unable to connect to my wireless network ever since. I tried also with 7.04 and 8.04.1 but nothing seems to help.

  I booted in Windows XP only to find that the laptop can connect to the very same wireless network without any problem.

  The wireless card in question is an Intel PRO/Wireless 3945ABG. The Radio frequency switch is OFF (Bluetooth and wireless card ON).

What could be the explanation? A failing wireless card?

---

### Post by Kredit on 2008-11-02
I have same problem with my X61s. I think, if you turn on the wifi switch, then the bluetoth led burns. So 
1) Switch on the wifi
2) open a terminal and type  *sudo ifconfig wlan0 up*
 And works...

---

### Post by zee on 2008-11-02
will try when I return home. Thanks for the tip.

Best regards,
Zee

---

### Post by zee on 2008-11-03
It works! Thank you.

EDIT:
 I switched OFF both radios with the switch on the laptop. Now I'm again unable to connect to wireless networks. The trick mentioned in the second post does not work.

 It seems the wlan0 interface doesn't get an IP address, so the NetworkManager app just deactivates the wlan0 device.
 
zee

---

### Post by jimmy the saint on 2008-11-03
if you have an intel wireless card, once you hit the wireless kill switch, it really is killed!!  this is mentioned in the release notes for intrepid.
the workaround is to purge the driver, then reenable it thusly:

```
sudo rmmod iwl3945
```
then
```
sudo modprobe iwl3945
```

you need to do this anytime you use the kill switch.  They say that a fix in coming, but the bug is marked medium urgency, which means you may as well get used to it.

---

### Post by zee on 2008-11-04
I tried: modprobe -r iwl3945 && modprobe iwl3945, but it didn't seem to help, so I simply reinstalled the Windows system from a disk image I have, enabled the wireless cad and then installed Ubuntu on a separate partition.

so far so good.

---

