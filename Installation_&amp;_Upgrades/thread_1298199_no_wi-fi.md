---
title: "no wi-fi ?"
date: 2009-10-22
forum: Installation &amp; Upgrades
---

### Post by toolmanpaul on 2009-10-22
been using xubuntu for a month or so but can't seem to get wi-fi working....loaded some kind of wi-fi helper from the apt's but it just briefly flashes something to fast to read then disappears..so no help there....acer laptop with vista from store...wi-fi works fine in windows....any ideas Thanks to all who respond...  Paul

---

### Post by dstew on 2009-10-23
What version of Ubuntu do you have? And what is your WiFi card (you should be able to list it with the **lspci** command).

---

### Post by toolmanpaul on 2009-10-23
> **dstew said:**
> What version of Ubuntu do you have? And what is your WiFi card (you should be able to list it with the **lspci** command).

Wow...that kicked out some goodies...have no clue what i'm looking at...xubuntu 9.8 jaunty ?

2)
07:00.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)

---

### Post by Chi The Designer on 2009-10-23
> 06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)That's the one you're looking for, really.
Maybe you should google it's name and see if anything particular might be occuring with 9.10 on that particular part.

Other than that, I can do you no good. :(
Best of luck..

**Edit:**
Google is my best friend.

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

Hope this helps!

---

### Post by dstew on 2009-10-24
This [Troubleshooting How-To]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide") may be of some help. It is based on command-line tools, so it should work in Xubunut as well as Ubuntu.

Since your card is seen in the lspci command, it is in there, and the hardware is seen by the system. The command **lshw** should list your card under a network heading. There you can see what driver, if any, has claimed the card. If there is a driver listed in the configuration: line, then probably we only need to alter a configuration setting to get the card to work. To see the configuration settings, use the **iwconfig** command.

---

### Post by toolmanpaul on 2009-10-24
capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by toolmanpaul on 2009-10-24
:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

what's next??  is there any thing that a dishonest person could use to hack me?

---

### Post by dstew on 2009-10-26
Are you sure you are looking at the correct lshw output? That configuration line is probably for a Personal Area Network (like Bluetooth). Post the whole output of ```
sudo lshw -C network
```and let us look at it.> is there any thing that a dishonest person could use to hack me?No. If and when we get your wireless interface working, you will need to configure it with encryption like WPA, and use a password or pass phrase. We are not at that point yet.

---

