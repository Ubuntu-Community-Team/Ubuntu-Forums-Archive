---
title: "IBM t42 + ipw2200 + wpa_supplicant"
date: 2005-09-13
forum: Hardware &amp; Laptops
---

### Post by bysse on 2005-09-13
Im starting to freakout on my new laptop, an IBM t42. The wireless network only works with a LOT of hacking and booting with a network-cable inserted into the laptop.

I've followed this thread when I installed wpa_supplicant:
[http://www.ubuntuforums.org/printthread.php?t=26623](http://www.ubuntuforums.org/printthread.php?t=26623)

and method B of this thread, when trying to start it:
[https://wiki.ubuntu.com/WPAHowto](https://wiki.ubuntu.com/WPAHowto)  

At the moment I'm using ifplugd for configuring the network when a cable is inserted. The config looks like this:
```

INTERFACES="eth0"
HOTPLUG_INTERFACES="eth0"
ARGS="-q -f -u0 -d10 -w -I -b"
SUSPEND_ACTION="stop"
AUTO="yes"
```

And my /etc/network/interfaces 
```
auto lo
iface lo inet loopback

mapping hotplug
        script grep
        map eth0
        map eth1

auto eth0
iface eth0 inet static
        address 192.168.0.5
        netmask 255.255.255.0

iface eth1 inet dhcp
        wireless-wpa foo

```

my wpa_supplicant.conf looks like this:
```
ctrl_interface=/var/run/wpa_supplicant

network={
   ssid="barnhemmet"
   proto=WPA
   key_mgmt=WPA-PSK
   psk="secretpass"
   priority=100
}
```


When I boot without a network cable, the laptop thinks that eth0 is the wireless card interface, but it can't initialize it because it doesn't support any wireless commands. 
I'm really confused here. All guides are just assuming that you only have one interface.... 
Can someone please sort this mess out for me, thanks.

---

### Post by mlomker on 2005-09-22
> 
I'm really confused here. All guides are just assuming that you only have one interface.... 
Can someone please sort this mess out for me, thanks.

This is an older post, so let me know if you still need a hand with this.  I came up with a combination of ifplugd, resolvconf, and whereami that works pretty well.  If you want to use the combo that you've got there then I see some issues with your configs.

---

### Post by bysse on 2005-09-24
I'm currently using a hack that i run after every reboot so i would very much like some easier way.

Either combo is fine with me as long as it works. Altough i think i need to use wpa_supplicant cause my drivers don't support WPA.

thanks

---

### Post by mlomker on 2005-09-24
> 
Altough i think i need to use wpa_supplicant cause my drivers don't support WPA.


True.  I don't like wpa_supplicant because I've seen it take over a minute to associate to an *open* access point.  It's a necessary evil for a lot of people, though.

In this example I'm renaming your wireless interface wlan0, which I think makes more sense but that's up to you.  You could also add whereami and resolvconf to your config if you want to customize further.  Resolvconf works with whereami to let you tweak your DNS server entries even when using DHCP, and whereami allows you to run commands based upon your location or network status.  

For example: if my network is plugged in then I have the system unload the wireless drivers, if I'm at work then mount smb shares, if I'm at home then mount my external hard disk, etc.

-----------

Disable hotplug (tends to confuse ifplugd):
```

sudo chmod 600 /etc/hotplug/net.ifup

```


/etc/default/ifplugd:
```

INTERFACES="eth0"
HOTPLUG_INTERFACES=""
ARGS_eth0="-qfwI -u0 -d10"
SUSPEND_ACTION="stop"

```

/etc/network/interfaces: 
```

auto lo wlan0
iface lo inet loopback

iface eth0 inet static
        address 192.168.0.5
        netmask 255.255.255.0

iface wlan0 inet dhcp
        wireless-wpa foo  #Does this do anything?  I couldn't find it documented.

```

Edit the /etc/iftab file.  Replace the 0's with the HWaddr (aka MAC address) for your wireless interface, which you can get from **ifconfig**:

```

wlan0 mac 00:00:00:00:00:00

```

---

### Post by bysse on 2005-09-27
Ah great now it works like it's supposed to work :)
thanks alot

---

### Post by vyruss on 2005-10-08
Thank you, thank you, thank you **mlomker**! *ifplugd* was driving me crazy by not working from rc5.d but worked when I ran it manually. Your options did the trick though!

---

### Post by mlomker on 2005-10-08
> by not working from rc5.d but worked when I ran it manually.

Ubuntu's normal runlevel is 2, so you can ignore anything other than rcS.d and rc2.d.

---

### Post by vyruss on 2005-10-08
[QUOTE=mlomker]Ubuntu's normal runlevel is 2, so you can ignore anything other than rcS.d and rc2.d.[/QUOTE]

Wait, do you mean that the multiuser X runlevel with networking is 2 and not 5, or that it passes from S to 2 and then to 5 when booting?

---

### Post by mlomker on 2005-10-08
[QUOTE=vyruss]Wait, do you mean that the multiuser X runlevel with networking is 2 and not 5, or that it passes from S to 2 and then to 5 when booting?[/QUOTE]

It goes from S to 2...Ubuntu doesn't use 5.  You can verify for yourself:

```

mlomker@mlomkernote:/var/log$ runlevel
N 2

```

---

### Post by vyruss on 2005-10-09
[QUOTE=mlomker]It goes from S to 2...Ubuntu doesn't use 5.  You can verify for yourself:[/QUOTE]

You're right... wow... you learn something new every day :)

I used to think that runlevel 5 was a "standard" convention :)

---

