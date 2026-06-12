---
title: "Dell Inspiron 6400 WiFi problems"
date: 2006-10-12
forum: Hardware &amp; Laptops
---

### Post by kikkertje on 2006-10-12
Hi,
I recently installed Ubuntu 6.06 as a Dual boot on my Dell Inspiron 6400.
all went well, except some major problem with my Intel Pro Wireless.
The LED on my laptop, labled as "WIFI", is flickering all the time.
and thus i don't know how to use WiFi.
I read on the forum that in should work out of the box, but apparantly, it isn't the case here.
when I enter 'iwconfig' in the terminal, i get this output:
```


kiran@darkloader:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

could someone explain to me how to install the WIFI, because it's really needed to work at school.
And is there a way to work with WEP-Secured WiFi connections :s

tnx alot.

Kikkertje

---

### Post by cnbiz850 on 2006-10-18
I have about the same machine as yours and I am about at the same stage as you on wireless, just a little further.  I managed to use iwconfig to get some parameters set, but still can't get it work yet.  I don't know why.

```


$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:"tp-link"  
          Mode:Ad-Hoc  Frequency:2.437 GHz  Cell: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:39   Missed beacon:0

sit0      no wireless extensions.


```

---

### Post by discord on 2006-10-18
you guys should install network-manager-gnome that should make it easy for you to manage the wireless. iwconfig works but its kind of a hassle and takes getting used to.



> **kikkertje said:**
> Hi,
I recently installed Ubuntu 6.06 as a Dual boot on my Dell Inspiron 6400.
all went well, except some major problem with my Intel Pro Wireless.
The LED on my laptop, labled as "WIFI", is flickering all the time.
and thus i don't know how to use WiFi.
I read on the forum that in should work out of the box, but apparantly, it isn't the case here.
when I enter 'iwconfig' in the terminal, i get this output:
```


kiran@darkloader:~$ iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated
          Bit Rate:0 kb/s   Tx-Power:16 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

could someone explain to me how to install the WIFI, because it's really needed to work at school.
And is there a way to work with WEP-Secured WiFi connections :s

tnx alot.

Kikkertje

---

### Post by cnbiz850 on 2006-10-18
I installed network-manager-gnome, but seems nothing happens.  Nothing even appears.  Can't someone tell me what to do with network-manager-gnome?

---

### Post by kinanti on 2006-10-28
Ubuntu 6.10.
No Wifi.
I've got the Inspiron 6400 with the intel wifi card.

Please help...:(  

K.

---

### Post by Darkwing Duck on 2007-01-09
I used the wireless assistant through the Applications menu, was able to get it connected, at long and painful last. It is a tad annoying that the wireless gets picked up as ¨eth1¨ instead of ¨wlan0¨

---

### Post by nachotronics on 2007-02-17
Did you disabled the wireless hotkey in the BIOS setup?? There are known issues with that...

Also AFTER you get wifi working, for WEP and/or WPA you should use network-manager-gnome

---

