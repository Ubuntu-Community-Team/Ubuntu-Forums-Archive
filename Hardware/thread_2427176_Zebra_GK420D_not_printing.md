---
title: "Zebra GK420D not printing"
date: 2019-09-18
forum: Hardware
---

### Post by allelopath on 2019-09-18
I now have a Zebra GK420D. It is connected via USB. The status indicator light is solid green. 
I see it:
> ~$ lpstat -t
device for Zebra_Technologies_ZTC_GK420d: usb://Zebra%20Technologies/ZTC%20GK420d?serial=28J130202450
Zebra_Technologies_ZTC_GK420d accepting requests since Wed 18 Sep 2019 09:23:44 PM MDT
printer Zebra_Technologies_ZTC_GK420d is idle.  enabled since Wed 18 Sep 2019 09:23:44 PM MDT


I went to CUPS and added the Zebra printer. There was not an entry for GK240, I see;

Zebra CPCL Label Printer (en)  
Zebra EPL1 Label Printer (en)
Zebra EPL2 Label Printer (en)
Zebra ZPL Label Printer (en)    

With the first 2, this happens when I click Print:
    A popup appears saying "Printing ..."
    The status indicator light flashes, 
    Then a popup appears saying "Printing completed" 
but nothing prints.
With the last 2, something is printed, but it is not right, the label for the package is sideways.

I've tried switching between portrait and landscape ... no difference.

I can print the pdf correcty on my recently installed Brother printer on the ethernet.

What am I missing?

Ubuntu 18.04.3 LTS

---

### Post by oldfred on 2019-09-19
ZPL requires a generic printer that sends no codes, and your software has to embed the ZPL code to control the printer. 

Older thread.
[URL="https://ubuntuforums.org/showthread.php?t=2305103"]https://ubuntuforums.org/showthread.php?t=2305103

[https://www.youtube.com/watch?v=56cHDa9G8mY](https://www.youtube.com/watch?v=56cHDa9G8mY)

[https://askubuntu.com/questions/1132367/driver-for-a-zebra-gk420d-label-printer](https://askubuntu.com/questions/1132367/driver-for-a-zebra-gk420d-label-printer)
[/URL]

---

### Post by allelopath on 2019-09-19
I followed the video. I am much closer.
Now the problem is that there is too much margin on the top and left.

---

