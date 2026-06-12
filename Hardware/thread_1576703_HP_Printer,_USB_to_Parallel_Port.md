---
title: "HP Printer, USB to Parallel Port?"
date: 2010-09-17
forum: Hardware
---

### Post by JasonSilver on 2010-09-17
Today I bought a USB to parallel port cable to connect a great old printer to my laptop. It's an HP LaserJet III, remember those? Very nice output. :)

I can't get it working.

Diagnostic Output:
```
Page 1 (Scheduler not running?):
{'cups_connection_failure': False}
Page 2 (Choose printer):
{'cups_dests_available': [], 'cups_queue_listed': False}
Page 3 (Local or remote?):
{'printer_is_remote': False}
Page 4 (Choose device):
{'cups_device_listed': False, 'cups_devices_available': {}}
Page 5 (Locale issues):
{'printer_page_size': None,
 'system_locale_lang': None,
 'user_locale_ctype': 'en_CA',
 'user_locale_messages': 'en_CA'}

```

and 

```

lsusb
Bus 002 Device 005: ID 04fc:0c25 Sunplus Technology Co., Ltd SATALink SPIF225A

```

```

ls -l /dev/usb/lp* /dev/bus/usb/*/*
...snip...
crw-rw-r-- 1 root lp   189, 388 2010-09-17 17:47 /dev/bus/usb/004/005
...snip

```

and 

```

sudo usb_printerid /dev/usb/lp0 
GET_DEVICE_ID string:
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;'&#65533;M&#65533;0D&#65533;'&#65533;&#65533;t&#65533;&#65533;&#65533; &#65533;M&#65533;'&#65533;&#65533;t&#65533;&#65533;&#65533;N|=$&#65533;&#65533;&#65533;f&#65533;M&&#65533;B$@&#65533;&#65533;&#65533;8&#65533;t&#65533;<&#65533;&#65533;NX&#65533;&#65533;&#65533;&#49305;&#65533;&#65533;=&#1816;N&#49305;&#65533;&#65533;YN&#65533;&#65533;&#65533;t&#65533;&#65533;&#65533;&#65533;|$&#65533;N	&#65533;&#65533;t&#65533;X&#65533;t&#65533;&#65533;M&#65533;&#65533;4M&#65533;&#65533;Nx&#65533;&#65533;&#65533;&#65533;&#65533;N&#1795;&#65533;&#65533;&#65533;&#65533;M&#771;&#65533;&#65533;4M&#65533;&#65533;&#65533;&#65533;T&#65533;N&#65533;&#65533;t&#65533;$&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;'&#1667;4&#65533;H&#65533;t&#65533;&#65533;&#65533; &#65533;M4&#65533;&#65533;&#65533;N&#65533;&#65533;N&#65533;;M$&#65533;N&#65533;&#65533;N &#65533;N&#65533;&#65533;N&#65533;&#65533;M&#65533;N&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;N&#65533;&#65533;t&#65533;&#1027;&#65533;&#65533;&#65533;&#65533;N`&#65533;&#65533;&#65533;&#65533;eN&#65533;&#65533;N|&#65533;N$&#65533;N&#65533;M`&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;M4M&#65533;&#65533;ii
                                   &#65533;&#65533;&#65533;f&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;#,}0&#65533;,&#1796;&#65533;&#65533;=&#65533;&#516;&#65533;&#65533;`&#65533;#&#65533;=&#1816;N&#1284;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;t&#65533;.N=&#65533;&#65533;&#65533;NH&#65533;t&#65533;X&#65533;t&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;N&#261;&#65533;&#65533;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;T&#65533;NH&#65533;t&#65533;&#65533;&#65533;N&#65533;_&M!&#65533;&#65533;X&#65533;&#65533;&#65533;&#65533;i&#65533;_&&#65533;&#65533;h&#65533;&#65533;&#65533;&#1796;&#65533;&#65533;M&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;y&#65533;$c&&#65533;_&`&#65533;

```

Any help? What should I do?

Thanks!
Jason

---

### Post by JasonSilver on 2010-09-22
bump

---

### Post by JasonSilver on 2010-09-23
SOLVED!

So here's the trick.

I created a printer with a fake URI, I used lpd://localhost, but anything will work.

Save it, choose the correct printer driver, then exit the printer utility.

Then from a terminal/command window, stop CUPS by typing:
```

$ sudo service cups stop

```

Then edit the printers.conf file:
```

$ sudo gedit /etc/cups/printers.conf

```

Then find the fake LPD line you added, and replace it with:

```

DeviceURI file:///dev/usblp0

```

Restart CUPS:
```

$ sudo service cups restart

```

Thanks to Gentoo forums:
[http://forums.gentoo.org/viewtopic-t-751814.html](http://forums.gentoo.org/viewtopic-t-751814.html)

YAY!

---

### Post by sinjihn on 2011-03-01
Well that almost worked for me, at least I got some kind of response from the printer! however the only output I got was spots all over the page. something for me to work on when I have time.

---

