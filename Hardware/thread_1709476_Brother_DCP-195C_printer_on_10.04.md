---
title: "Brother DCP-195C printer on 10.04"
date: 2011-03-18
forum: Hardware
---

### Post by Amalka on 2011-03-18
I managed to install drivers for Brother DCP-195C printer from [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-195C](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-195C) site but when I want to print to it, printer displays "Receiving Data" messsage and then... nothing happens.
After this message there should a printed paper come out, but... well, it doesn't.

Did anyone manage to make this printer work?


And, yes, printer itself is ok and prints ok from Windows.

---

### Post by Amalka on 2011-03-21
I managed to solve this problem by re-installing the printer in the following order:

Terminal:
```
sudo aa-complain cupsd
sudo mkdir /usr/share/cups/model
```
After that I installed cupswrapperDCP310CN-1.0.2-3.i386.deb from [http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperDCP310CN-1.0.2-3.i386.deb&lang=English_gpl](http://www.brother.com/cgi-bin/agreement/agreement.cgi?dlfile=http://www.brother.com/pub/bsc/linux/dlf/cupswrapperDCP310CN-1.0.2-3.i386.deb&lang=English_gpl)

and it works just fine.  :D

---

