---
title: "[SOLVED] Spoofing a MAC address"
date: 2008-09-09
forum: General Help
---

### Post by malfist on 2008-09-09
How can I spoof my mac address in ubuntu?

---

### Post by iaculallad on 2008-09-09
Open your interfaces file:

```
gksudo gedit /etc/network/interfaces
```

and try adding the line:

> hwaddress ether 01:02:03:04:05:06

w/c is just a example. Try replacing it with what you want to use.

    auto eth0
    iface eth0 inet dhcp
**    hwaddress ether 01:02:03:04:05:06**

Save and Close and try restarting your network.

```
sudo /etc/init.d/networking restart
```

---

### Post by lswb on 2008-09-09
I think you can also 

```
sudo ifconfig eth0 hw ether 01:23:45:67:89:ab
```

substituting for eth0 and the mac address as needed.

---

### Post by diobrando on 2008-09-09
> **lswb said:**
> I think you can also 

```
sudo ifconfig eth0 hw ether 01:23:45:67:89:ab
```

substituting for eth0 and the mac address as needed.

This should work as long as you are not using ndiswrapper. You will need to take the interface down with "sudo ifconfig eth0 down" first, then bring it back up with "sudo ifconfig eth0 up" afterwards.

---

### Post by malfist on 2008-09-09
This is out of complete and total curiosity. Should I be able to run a scripted and randomize my MAC address on boot up?

---

### Post by iaculallad on 2008-09-09
> **malfist said:**
> This is out of complete and total curiosity. Should I be able to run a scripted and randomize my MAC address on boot up?

Try doing that task with [MACCHANGER]("https://help.ubuntu.com/community/AnonymizingNetworkMACAddresses") as discussed here on Ubuntu Community page.

---

### Post by malfist on 2008-09-10
Awesome, thank you!

---

### Post by kooldino on 2008-09-15
> **lswb said:**
> I think you can also 

```
sudo ifconfig eth0 hw ether 01:23:45:67:89:ab
```

substituting for eth0 and the mac address as needed.

Will this make the change permanently?  If so, what file does it write this change to?

---

### Post by lswb on 2008-09-15
> **kooldino said:**
> Will this make the change permanently?  If so, what file does it write this change to?

No, it will be reset to the real address at reboot. But the /etc/network/interface method in an earlier post would make it persistent, or a script could be used with ifconfig.

---

### Post by kooldino on 2008-09-18
> **lswb said:**
> No, it will be reset to the real address at reboot. But the /etc/network/interface method in an earlier post would make it persistent, or a script could be used with ifconfig.


```

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0


auto eth0
iface eth0 inet dhcp
hwaddress ether 00:08:A1:22:D7:30

```

The inline command works for me, however the above in my intefaces file does not.  I tried moving the hwaddress line around, but it didn't help, and gave me some odd error message about the placement of the line.

---

### Post by lswb on 2008-09-18
Try it like this:

iface eth0 inet dhcp hwaddress ether 00:08:A1:22:D7:30

and if that doesn't work try google.

---

### Post by kooldino on 2008-09-29
> **lswb said:**
> Try it like this:

iface eth0 inet dhcp hwaddress ether 00:08:A1:22:D7:30

No dice.

```
tc/network/interfaces:8: too many parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"

```

---

### Post by lswb on 2008-09-29
> **kooldino said:**
> No dice.

```
tc/network/interfaces:8: too many parameters for iface line
ifdown: couldn't read interfaces file "/etc/network/interfaces"

```

OK, from what I have read my suggestion was wrong anyway, the 2 line format is the correct one, like this:

iface eth0 inet dhcp
    hwaddress ether 00:01:02:03:04:05

but you have already said that doesn't work either. I have seen some posts claiming the ifup/ifdown/interfaces scripts are somewhat broken in hardy. I don't know how much truth there is to that, but here is another method you could try in the interfaces file:

iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:01:02:03:04:05

Good luck this time!

---

### Post by bionnaki on 2008-10-15
how would I spoof my mac when using wifi0/ath0 instead of eth0?

would it be:

pre-up ifconfig ath0 hw ether 00:01:02:03:04:05

---

### Post by kooldino on 2009-02-06
> **lswb said:**
> OK, from what I have read my suggestion was wrong anyway, the 2 line format is the correct one, like this:

iface eth0 inet dhcp
    hwaddress ether 00:01:02:03:04:05

but you have already said that doesn't work either. I have seen some posts claiming the ifup/ifdown/interfaces scripts are somewhat broken in hardy. I don't know how much truth there is to that, but here is another method you could try in the interfaces file:

iface eth0 inet dhcp
pre-up ifconfig eth0 hw ether 00:01:02:03:04:05

Good luck this time!

I think that worked...but for some reason it's not picking up the correct IP...which is probably unrelated.

Once I'm logged in, it shows the spoofed MAC listed in ifconfig eth0.

---

### Post by linuxhongkong on 2009-02-14
Using wifi0/ath0 instead of eth0, it should be atheros hardware with MadWifi driver.
spoofing mac addresses with atheros hardware is simple:
it support "wlanconfig" and "macchanger"
My "ASUS Eee PC 900" is OK as following

wlanconfig ath0 destroy
macchanger --another wifi0
wlanconfig ath0 create wlandev wifi0 wlanmode sta

---

