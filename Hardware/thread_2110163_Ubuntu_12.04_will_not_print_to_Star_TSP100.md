---
title: "Ubuntu 12.04 will not print to Star TSP100"
date: 2013-01-29
forum: Hardware
---

### Post by applerock79 on 2013-01-29
I have the 64-bit Ubuntu 12.04 installed.
Can't print to usb Star TSP100 receipt printer.
Print Config sees the printer, drivers installed, just wont print.
Tried going to Star web site and DL the driver there and follow directions to make driver. That failed. No makefile present, was the error. Then tried to get working via CUPS. It "sees" the printer but won't print. Just like trying to install it via the "Print Config" (older version, not the newer one in Ubuntu 12)
Found a 32-bit PPD, but would not work with 64-bit Ubuntu, errored out. This is silly, I must be missing something, esp since Ubuntu recognizes the printer (though it sees it as a TSP113. No matter)

The .deb file that was mentioned out this site fora driver no longer works. Perhaps too old. Errors out.


Any ideas?

---

### Post by applerock79 on 2013-01-30
Ok. I just added: 
```
sudo apt-get install ia32-libs
```

Still no print. Thing is all looks fine, Ubuntu even will communicate with the Star usb printer and correctly identify when it is online, idle or offline.

The only error I saw was in the CUPS 1.52 http front end.
libc.so error

Still need help.

---

### Post by alfangel on 2013-05-10
i did it¡, just need download the driver for linux [http://www.starmicronics.com.mx/Printer/PrinterDesc.aspx?PageId=1&PrinterId=40](http://www.starmicronics.com.mx/Printer/PrinterDesc.aspx?PageId=1&PrinterId=40) , and follow the instructions on the readme, beginin in the step 5, before follow this, just go on the synaptic manager and search cups-dev, and install all the development headers for cups, then open terminal type cd your/directory  into source files of the driver and do sudo make, then a make install and just install the printer as always.

i have a TSP100 and i will try this in a imac G3 with linux mintPPC11, i dont know if the cash drower will work  :/

---

