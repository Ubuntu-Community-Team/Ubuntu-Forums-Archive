---
title: "Dlink Wireless Card Not Connecting"
date: 2008-01-13
forum: Hardware &amp; Laptops
---

### Post by Xsabre on 2008-01-13
Clean install of Xubuntu 7.10 on Dell Inspirion 8100. Everything seems to be good other than I don't have on board NIC working. Please keep this in mind as I have no way to connect to the net.  I have an old [Dlink (DWL-650) Rev:1A]("http://support.dlink.com/products/view.asp?productid=DWL%2D650") that would work out better. [This states that it should work.]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink") It is the first 650 on the list. Stated driver is orinoco_cs.

I tried following the instructions on [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)
but the PCMCIA card can't connected to the network.

Checked iwconfig. It is showing wifi0 and wlan0. But I only have one PCMCIA card connected.

Dmesg shows that PCMCIA, wfi0 and wlano registered without a problem.

From WiFi Howto:
"Sometimes there are two devices that appear: wlan0 and wifi0, even if there is one card. This causes errors sometimes, like a tendency to not detect wireless access points. In certain configurations, this is caused by hostap_cs and hostap kernel modules. Check your dmesg output for errors around "wlan0". Place the appropriate excludes into /etc/modprobe.d/blacklist and reboot."

Could any of these things be presenting a problem?

I would greatly appreciate it if someone would help me try to resolve this.

Thanks in advance...

---

### Post by Xsabre on 2008-01-14
Ok, folks... thanks to help of the these postings I was able to resolve my issues with wireless setup.

How To: Troubleshoot your Wireless Network Connection - Connecting at Command Line
[http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

and

NetworkManager with hidden ESSID
[http://ubuntuforums.org/showthread.php?t=290334&page=4](http://ubuntuforums.org/showthread.php?t=290334&page=4)

I hope this will help someone else out...

---

