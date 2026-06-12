---
title: "unassigned ipw3945 wireless card"
date: 2006-07-26
forum: Hardware &amp; Laptops
---

### Post by smolko on 2006-07-26
Hello,
I'm a not-very-happy user of a new UMAX 6200 notebook. The problem is, that I can't persuade my wifi card to work. It is detected by the system and I can also configure it in System-->Administration-->Network settings. But It can't find any wireless network.

lspci:
```
[17181450.068000] ipw3945: Detected Intel PRO/Wireless 3945ABG Network Connectio n
[17181450.968000] ipw3945: Detected geography ABG (13 802.11bg channels, 23 802. 11a channels)

```

The problem occured when I tried the iwconfig:
```
smolko@smolko-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I have no idea why is it unassociated (there should be something like IEEE802...). I installed all kernel packages needed and tried both 686 and 386 kernels.
Neither wheelspin's script [http://www.ubuntuforums.org/showthread.php?t=140085&page=6]("http://www.ubuntuforums.org/showthread.php?t=140085&page=6") helped... everything went fine until the output message, that the eth1 device was not found.
I'll be very thankfull for any help.

---

### Post by ahallubuntu on 2006-07-26
What I did:

- Installed Network Manager

- Edited /etc/network/interfaces to remove all lines but the "auto" and "iface" lines.

- restarted networking:

sudo /etc/init.d/networking restart

- restarted Network Manager:

sudo /etc/init.d/dbus restart

and then my card 3945 was detected by Network Manager and worked fine.

---

### Post by smolko on 2006-07-26
I've altered the file as you recommended but I've got an error message. Could you please paste your interfaces file here? I've done some changes in that file before, so probably that's why it doesn't work out fine.

---

### Post by ahallubuntu on 2006-07-26
What error are you getting?  At what point do you get it?

My Dell E1505 has an Ethernet card (eth0) as well as the 3945 (eth1).  My interfaces file, as I said, has only  iface and auto directives in it.  If you have anything else, Network Manager won't work - or so I've been told.  Try taking everything but those lines.

Here's my interfaces file - very basic:

```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by smolko on 2006-07-28
Thank's for your help!
I finnaly figured it out. I just changed my ip to static, changed the mode to Ad-Hoc (I wanted to connect two computers) and **chose a random channel number**
```
sudo iwconfig eth1 channel 5
```
Now my iwconfig output looks like this:
```
eth1      IEEE 802.11g  ESSID:"test"
          Mode:Ad-Hoc  Frequency:2.432 GHz  Cell: 02:13:02:12:31:2B
          Bit Rate:54 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:99  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
And as you said the network manager applet works only with dhcp but using dhcp for ad-hoc connections is a bit weird.

---

