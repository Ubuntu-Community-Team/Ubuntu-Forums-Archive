---
title: "Cannot Connect wirelessly to HP Photosmart 5520 Printer"
date: 2013-06-29
forum: Hardware
---

### Post by Gster4 on 2013-06-29
I got said printer, got HPLIP (version 3.12.6) drivers instead of the older ones in the 12.04 repos.
Drivers were from debian repos, min requred version is [3.12.6 for the model ]("http://hplipopensource.com/hplip-web/models/photosmart/photosmart_5520_series.html")
The wireless network exists:
```

#iwlist scan
     ...
Cell 03 - Address: 2C:59:E5:B1:B5:58
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:off
                    ESSID:"HP-Print-58-Photosmart 5520"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
   ...

```
so thats ok.  
I can connect to it with 
```

# iwconfig wlan0 essid "HP-Print-58-Photosmart 5520"

```
now hp-setup does not recognise the printer when I choose "Network/ethernet/wireless setup"  

suggestions?

---

