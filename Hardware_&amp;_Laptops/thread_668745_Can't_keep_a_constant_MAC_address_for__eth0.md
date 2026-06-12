---
title: "Can't keep a constant MAC address for  eth0"
date: 2008-01-15
forum: Hardware &amp; Laptops
---

### Post by jgoguen on 2008-01-15
I have a HP Pavilion dv2622 with Ubuntu Gutsy, and I can't seem to get the MAC address for eth0 to stay constant.  At this time, I have eth10 displayed, with 11 entries in /etc/udev/rules.d/70-persistent-net.rules all similar to the following:
```

# PCI device 0x10de:0x054c (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:28:81:2f", NAME="eth0"

```The only difference is the MAC address, which always starts with "00:00:6c" but has the last 3 pairs different for each instance, and the name, which seems to be incrementing every time I reboot or wake the laptop.  None of the entries have anything close to the real MAC address though, which is 00:16:D3:F2:08:8D.  It doesn't matter to me if that's the MAC address actually assigned to the card, I just need a MAC address that stays constant so I can get my laptop onto my university's network.  The wireless interface isn't affected by this, so that gives me something on campus, but there's plenty of places where it's faster to just break out an ethernet cable.

So my question is, how can I force the usage of the real MAC address, or force udev to pick one MAC address and stick with it?

---

### Post by jgoguen on 2008-01-18
I just noticed in /var/log/kern.log this pair of entries:
```
Jan 18 18:09:50 hermes kernel: [64594.332000] 0000:00:0a.0: Invalid Mac address detected: 8d:08:f2:d3:16:00
Jan 18 18:09:50 hermes kernel: [64594.332000] Please complain to your hardware vendor. Switching to a random MAC.
```

The detected hardware address is the reverse of the real MAC address.  How can I either tell udev to reverse it, or disable creation of new ethX devices and force eth0 to use the real MAC address?

---

### Post by dubs990 on 2008-01-21
i've been having the same problem on bcm4321 card, I found a thread which at least explains what is happening (backwards MAC address plays a key role), 
the problem doesn't seem to have a real solution... but hey knowing is half the battle

[http://ubuntuforums.org/showthread.php?t=627114]("http://ubuntuforums.org/showthread.php?t=627114")

---

### Post by ice60 on 2008-01-21
you can change your MAC address with these commands -
```
ifconfig eth0 down hw ether xx:xx:xx:xx:xx:xx
ifconfig eth0 up
```

i've never done it so i don't know if it will remember the new MAC, or if you have to run it everytime you bootup. but, i'm sure the MAC is hardcoded so the new MAC address won't permanently stick.

this is where i got that from i think -
[http://www.irongeek.com/i.php?page=security/changemac](http://www.irongeek.com/i.php?page=security/changemac)

it has this way too, run it as root, or sudo i mean :| -
```

1) Bring down the interface: "ifconfig eth0 down"

2) Enter new MAC address: "ifconfig eth0 hw ether 00:00:00:AA:AA:AA"

3) Bring up the interface: "ifconfig eth0 up"
```

---

### Post by Daelyn on 2008-01-22
I'm unsure if the ifconfig lines in terminal changes permanently, or just until you reboot. So, I always do following on mine.

```
 sudo gedit /etc/network/interfaces 
```
Look for 

```
 auto eth0
iface <your interface> inet dhcp 
```

add following line just below the above
```
 hwaddress ether <MAC adress of your choise>
```
dont forget to remove these <><> :)

after you've changed in the network config, do following.

```
 sudo /etc/init.d/networking restart 
``` and see if it goes through without complaining/errors.


Best of luck!

---

### Post by flabdablet on 2008-03-12
Just encountered this annoying bug in Gutsy on a customer's shiny new computer.  Grrr.

The problem seems to be that some of the kernel's network drivers mess up the process of reading and/or storing the MAC address for the network cards they're working with, and end up with a byte-reversed version: instead of valid address op:qr:st:uv:wx:yz, the driver sees yz:wx:uv:st:qr:op.  This will generally be an invalid address, and a random but valid MAC address gets used instead (along with the complaint that jgoguen noted in the kernel log).

Every time this happens, udev sees what its rules say is a new network card, and assigns it a new interface ID.  To stop this from happening, I modified two files: in /etc/udev/rules.d/70-persistent-net.rules, I got rid of all seventeen of the stanzas that followed this pattern:
```
# PCI device 0x10de:0x0450 (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:28:81:2f", NAME="eth13"
```
and replaced them with a single stanza that looks like this:
```
# PCI device 0x10de:0x0450 (forcedeth)
# This rule modified by hand, as a bug in the forcedeth driver makes the generated
# ATTRS{address} rule unworkable (card wakes up with a different, random MAC address
# assigned on every boot).  ST 12-Mar-2008.
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{vendor}="0x10de", ATTRS{device}=="0x0450", NAME="eth0"
```
To make that change stick, I also had to add an extra stanza to /etc/udev/rules.d/75-persistent-net-generator.rules, making the first part look like this:
```
# Rule added 12-Mar-2008 ST, working around forcedeth MAC bug
ACTION=="add", SUBSYSTEM=="net", KERNEL=="eth*|ath*|wlan*|ra*|sta*" \
        ATTRS{vendor}=="0x10de", ATTRS{device}=="0x0450", GOTO="persistent_net_generator_end"

ACTION=="add", SUBSYSTEM=="net", KERNEL=="eth*|ath*|wlan*|ra*|sta*" \
        NAME!="?*", DRIVERS=="?*", GOTO="persistent_net_generator_do"
```
If you do this yourself, make sure the ATTRS{vendor} and ATTRS{device} strings match those originally listed in original "PCI device" comments you removed from 70-persistent-net.rules.  Don't blindly use mine, since your hardware will probably not be the same.

Finally, I used daelyn's tip to fix the MAC address for eth0 in /etc/network/interfaces, which now looks like this:
```
auto lo eth0

iface lo inet loopback

iface eth0 inet dhcp
hwaddress ether op:qr:st:uv:wx:yz
```
Use the correctly-ordered version of the backwards MAC complained about in the kernel log instead of op:qr:st:uv:wx:yz, and you should be good to go.

Hope this helps somebody.

---

