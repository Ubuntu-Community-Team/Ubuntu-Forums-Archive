---
title: "Trouble with Wireless Networking"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by newbie21 on 2005-11-23
I have 2 wireless cards I can't get to work.  One uses ndiswrapper and one uses orinoco, orinoco_cs, and hermes.  I added those to /etc/modules, and they come up when I do iwconfig.

When I type in iwconfig, it shows wlan0 connected to my access point (unencrypted while i try to get this working), but ping -c 3 [www.google.com](www.google.com) doesn't work.  I tried the following series of commands:

sudo ifup wlan0
#didnt work

sudo ifconfig wlan0 up
#didn't work

sudo ifconfig wlan0 up
sudo dhclient wlan0
#didn't work

sudo iwconfig wlan0 essid any
#didn't work

Then, I tried all of these again with sudo /etc/init.d/networking restart && sudo /etc/init.d/pcmcia restart.

I'm using breezy 5.10 "server" install.

Thanks for any help.

---

### Post by Lambert on 2005-11-23
If you run ifconfig do you have an ip addr assigned to the device?

 Link encap:Ethernet  HWaddr 00:11:95:50:BE:62
          i**net addr:192.168.99.50**  Bcast:192.168.255.255  Mask:255.255.0.0

If yes can you ping an external site using the ip address?

ping 216.239.57.99

---

### Post by newbie21 on 2005-11-23
No, there is no inet addr.

iwconfig shows wlan0 connected to my ap, and ifconfig shows wlan0 has received TX and RX packets, if any of that helps.

There's nothing wrong with the ap or card because it works in SuSE 10.0 and Windows XP Professional.

---

### Post by Lambert on 2005-11-24
Card's working ok. there's a break down somewhere in assigning the ip address to the device.

Go to this thread the 11th post and try the same thing. 

[http://www.ubuntuforums.org/showthread.php?t=93433&page=2](http://www.ubuntuforums.org/showthread.php?t=93433&page=2)

Post back results.

---

### Post by aznboi on 2005-11-24
or you could try the gtkwifi.... i dont kno if it would help but its worth a try.
go here to download it:
```
http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download
```

then open up the terminal, cd to where u downloaded, and type in ```
sudo dpkg -i gtkwifi-1.09.deb
```

right click in the panel click Add to Panel and under teh Internet category there should be something saying Wireless Connection manager. Click that

---

### Post by newbie21 on 2005-11-25
[QUOTE=aznboi]or you could try the gtkwifi.... i dont kno if it would help but its worth a try.
go here to download it:
```
http://prdownloads.sourceforge.net/gtkwifi/gtkwifi-1.09.deb?download
```

then open up the terminal, cd to where u downloaded, and type in ```
sudo dpkg -i gtkwifi-1.09.deb
```

right click in the panel click Add to Panel and under teh Internet category there should be something saying Wireless Connection manager. Click that[/QUOTE]
i'm not running a gui.  The server install is cli only.

Thanks Lambert, that worked!  What's the easiest way to get it to do it every time the computer starts?

---

