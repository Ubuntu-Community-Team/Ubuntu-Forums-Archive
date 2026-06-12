---
title: "network-admin fails to see my wireless card"
date: 2007-11-19
forum: Hardware &amp; Laptops
---

### Post by Haluci on 2007-11-19
I have a 0c:00.0 Network controller: Broadcom Corporation BCM4328 802.11a/b/g/n (rev 01)  I've followed every tutorial to install the drivers for this card and they seem to have worked: ndiswrapper says that the driver is installed and the little green light on my wifi card is on.  However, network-admin does not show a wireless connection at all, and the gnome network manager isn't giving me an option to connect to a wireless network.  Is there anything else I need to do to get ubuntu to see my wireless card?

---

### Post by angryfirelord on 2007-11-20
Post the output of **iwconfig**. IF nothing shows up, then post the output of **ifconfig**.

---

### Post by Haluci on 2007-11-20
iwconfig gives me this:

```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Bit Rate:130 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```

Sorry for posting so late, I had to get some sleep.

---

### Post by Haluci on 2007-11-20
bumping after 5 hours of inactivity.

---

### Post by angryfirelord on 2007-11-20
Can you configure your card through network-manager at all? If not, then try using wicd: [http://wicd.sourceforge.net/download.php]("http://wicd.sourceforge.net/download.php")

---

### Post by Haluci on 2007-11-20
My wireless connection simply doesn't show up in network-manager at all.  I see my wired connection, my modem connection, then nothing.

Thanks for the link to wicd, I'll try that.  I'll also post a screenshot later.

---

### Post by Haluci on 2007-11-20
Thanks for your help, wicd works just fine. :)

---

