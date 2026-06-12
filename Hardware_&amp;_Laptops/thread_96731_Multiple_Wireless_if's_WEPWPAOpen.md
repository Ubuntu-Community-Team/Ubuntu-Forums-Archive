---
title: "Multiple Wireless if's WEP/WPA/Open"
date: 2005-11-29
forum: Hardware &amp; Laptops
---

### Post by mfreeze on 2005-11-29
Does anyone have any experience in configuring /etc/network/interfaces for multiple wireless interfaces? Specifically for Ubuntu - Kubuntu Breezy.  I want to edit the interfaces file to allow my pcmcia nic to 'see' my WEP-enabled home network when I am at home, my WPA-enabled network when I am at work, and open networks when I am at places like Internet Cafe's, hotspots, etc...

Also, I also have a problem when eth0 and ath0 are up at the same time.  I get no access unless ifdown one of the interfaces

I have read the wpa howto, the  wifi howto, and others, but I just can't seem to be able to do what I need.

Maybe I've looked at it too long...  Who knows?

Any help is appreciated.

Thanks,

---

### Post by Lambert on 2005-11-29
Have you looked at a connection manager like network manager or gtkwifi?

But to answer your question is yes, there is a way to set up your interfaces file to do this.

You would create interfaces like this

iface home inet dhcp


iface work inet static

iface hotspot inet dhcp




Of course with correct data and all the other data below it.

Then to bring up a particular interface it would be something like this from the CLI.

ifup eth0=home

You can read [here]("http://www.debian.org/doc/manuals/reference/ch-gateway.en.html") for more information. Section 10.6 is where you want to read.

---

### Post by jwolf on 2005-11-29
I wrote 3 scripts that I execute depending on where I am. This assumes that you are only connecting to one WPA network and wpa-supplicant is already configured. I use these on a daily basis (mainly the first two) with great success. For reference my wifi card is eth1. If this helps, feel free to use them:

Home (WPA)
```

#!/bin/bash
# wifi connection script for home wireless network
echo "Configuring Connection..."

echo "Bringing interface down..."
sudo ifconfig eth1 down
echo "Terminating related processes..."
sudo killall -w -q dhclient
sudo rm -f /var/run/dhclient.pid
sudo killall -q wpa_supplicant
echo "Starting required processes"
sudo /etc/init.d/wifi_wpa.sh
echo "Bringing interface up..."
sudo ifconfig eth1 up
sudo dhclient -q eth1


while [ -n "$(ping -c 1 google.com|grep unknown)" ]
do
    echo "Connecting..."
done

echo "Connection Established"

```

Work (WEP) - You'd need to change the essid and wep key
```
#!/bin/bash
#Wifi config for work


echo "Bringing interface down..."
sudo ifconfig eth1 down
echo "Terminating related processes..."
sudo killall -w -q dhclient
sudo rm -f /var/run/dhclient.pid
sudo killall -q wpa_supplicant
echo "Bringing interface up..."
sudo ifconfig eth1 up
sudo iwconfig eth1 essid "WorkWifi" key MYWEPKEY123123123123
sudo dhclient -q eth1

while [ -n "$(ping -c 1 google.com|grep unknown)" ]
do
    echo "Connecting..."
done


echo "Connection established"

```

And any open WiFi
```

#!/bin/bash
#Wifi config script for open networks

echo "Bringing interface down..."
sudo ifconfig eth1 down
echo "Terminating related processes..."
sudo killall -w -q dhclient
sudo rm -f /var/run/dhclient.pid
sudo killall -q wpa_supplicant
echo "Bringing interface up..."
sudo ifconfig eth1 up
sudo iwconfig eth1 essid any
sudo dhclient -q eth1

while [ -n "$(ping -c 1 google.com|grep unknown)" ]
do
    echo "Connecting..."
done


echo "Connection established"


```

I have these saved in my home folder as homewifi.sh, workwifi.sh and openwifi.sh. If you connect to multiple WEP networks just clone that script and run the appropriate one depending on what network you are connecting to.

---

### Post by mfreeze on 2005-11-29
Thanks for the scripts.  I'll check them out but I'm pretty sure that they will do. ;->

For the first reply:  I didn't think that NetworkManager would work with WPA?

Also: I'm really looking for a script that will 'see' the wireless networks, allow you to manually connect, and then  save the configuration information and connect to that wireless network automatically the next time it encounters it on boot.  Kind of like (and I hate to say it...) my M$ laptop does.  It seems that this ought to be already working somewhere but I just can't get my hands on  the goods.

Thanks,
Mark.

---

### Post by azuro on 2006-01-19
Is there any software that detects and connect to wireless connection (WEP/WPA/Open) automatically, instead of running these scripts everytime?

---

### Post by jml on 2006-01-19
mfreeze, you may not want to have your laptop emulate the Windows ability to remember wireless settings.  This article from C/net yesterday describes a rather serious security flaw that this feature opens.

[http://news.com.com/2102-1002_3-6028275.html?tag=st.util.print](http://news.com.com/2102-1002_3-6028275.html?tag=st.util.print)

Joe

---

### Post by mpvano on 2006-01-19
There are several approaches to automating wireless connectivity, and they've been adequately discussed elsewhere, but I'd like to inform you of a problem that can make their use quite impossible with some wireless adapters at this time.

You should find out whether your card and driver support scanning before you try to use any solution that claims to make a list or menu. Nearly all these solutions break completely if the scan function is not supported. You can waste a lot of time playing with these solutions if your card just doesn't support them.

Try the command "sudo iwlist wlan0 scan" (substitute the name of your card for wlan0 if needed) and see if you get an error message indicating your card doesn't support scanning. if it doesn't, I'd suggest looking for a solution that doesn't rely on scanning (or on automatically connecting to the first open network it finds, for that matter).

It appears that these functions are being modified by card vendors in their firmware because of concerns about security. New firmware releases are built into recent shipments of these cards, and many drivers for Windows force firmware upgrades to remove the old functionality from cards when they update them.

There are obscure workarounds for the problem (that's why many vendors still implement the functionality in windows!), but in many cases they're not in the current drivers yet.

The stupid thing about the current changes is that as soon as they're implemented in a card, all the driver writers (even for windows) start figuring out a way around the "security by obscurity" feature - since nobody can function without finding a list of ESSIDs to select from.

The whole situation reminds me of the recent  "secret" drives by licensing organizations to eliminate stereo audio inputs and to degrade the NTSC video output quality provided by notebook computers to help make piracy more difficult. Whenever things mysteriously stop working I get suspicious - now that we live in a world where anything you buy or install can be "downgraded" secretly by the vendor at any time.

In some cases you can find alternative or older drivers for your interface that DO support scanning, but most of them are currently pretty arcane due to lack of documentation and hard to install and use.

Another solution is to flash the card with an older version of the firmware - unfortunately most older versions are buggy, and if you don't know what you are doing you are likely to end up with a card with no firmware at all that can't be fixed. I'd avoid this.

This problem appears to be quite widespread and the cause of a lot of confusion in this forum. It affects many of the most common chip sets, like the orinoco and prism family.

In some cases, (like my IBM's built in prism2 interface), wireless manager solutions that used to work well are now broken under Windows XP as well - especially if more than one access point is visible to the interface. In my case, this happened after the last driver update from IBM under XP.

The only reliable way I've found to deal with this problem at the moment is to use a solution where you present an essid to the interface for it to find (like the ones suggested using multiple "interfaces" files). Even the old trick of putting a wildcard name like "any" in seems to fail if more than one wireless network is in range. I've taken to finding out the essid of each access point I visit and making custom interface files for them. It's a nuisance, but nothing else seems to work reliably.

I'm hoping this situation will get resolved over the course of the year - the kernel driver developers seem to be working on something, but it's not ready for prime time yet.

This whole situation has turned into a crisis here over the holidays - it appears everyone in my part of the country got a new access point for Christmas. Overlapped access points used to be something pretty rare here, but now I'm encountering them everywhere, In many cases the users have set them up without realizing they're all on the same channel and this REALLY confuses cards trying to scan for networks.

Hope this information helps save some frustration - If you're lucky enough to have cards/drivers that scan properly you should be good to go, but be careful about following every lead given here about network managers. If the card doesn't scan, I think you'll find they're just not going to work properly at the moment. 

Mario

---

### Post by azuro on 2006-01-20
I got the open and wep working now.  But not sure how to configure the WPA connection.  I got wpasupplicant installed and i've configure /etc/default/wpasupplicant

```

# /etc/default/wpasupplicant

ENABLED=1
OPTIONS="-D ipw -i eth1 -c /etc/wpa_supplicant.conf -w"

```

and file /etc/wpa_supplicant.conf
```

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=1
fast_reauth=1

network={
        ssid="some_ssid"
        psk=xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx

```

what else i need??

Thanks.

---

### Post by azuro on 2006-01-30
somebody help please.....

---

### Post by macbuff on 2006-01-30
I followed the WPA help from the Ubuntu wiki pages and it worked first time.

John

---

