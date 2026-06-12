---
title: "HP Deskjet 3050 install as network"
date: 2012-01-08
forum: Hardware
---

### Post by Sallée on 2012-01-08
New printer having lots of trouble getting going.  A new HP Deskjet 3050 All-in-One J610a.  The printer requires a usb connection and software to connect to connect to a wireless network.  installation cd is only for MS/Mac, so that is no go.  I have tried hp-setup and have had bizarre results.  Here are my steps and results:
[LIST=1]
[*]hp-setup
[*]Click "Wireless/802.11 (requires a temporary USB connection and is only available for select devices)" then "Next"
[*]Wireless (Wifi/802.11) Configuration, Click "Next"
[*]Select from Discovered Wireless Capable Devices: My device is listed and highlighted.  I click "Next"
[*]New window: An I/O error ocurred.  Please check the USB connection to the printer and try again. (Device I/O error)
[/LIST]

I saw somewhere to add my user to group lp, which I did.  Any ideas out there?

---

### Post by Mark Phelps on 2012-01-09
Two things ...

I have a networked HP printer (8510) and it does NOT allow BOTH network printing and USB connection.  I found that out because when it was USB connected, I went to the touch panel to set up networking and I got a message saying I had to disconnect the USB cable first.  Need to check to see if yours has the same limitation.

Second, I set up mine using CUPS.  Open a browser and enter "localhost:631"  Then use the option to Add a printer -- and you should get a page showing detected network printers.  If yours in on that page, just follow through the menus and install it.

---

### Post by Sallée on 2012-01-09
Mark, thanks for your help.

Looking back at my original post, I was not entirely clear.  The issue is that the printer does not have the capability to set up the wireless connection on its own.  You have to connect a computer to it and set network id and passwords from there.  There is no touchscreen or 10-key.  I can connect using the USB in order to print, but not to set up the wireless connection.  

I tried localhost:631 and got into the CUPS server, which allowed me to set up the USB printing, but not the wireless.  I have also now installed hplip from the website, which corrected some issues and made it so I can get into the device manager, but I am still getting a Device I/O error when I try to set up the wireless, be it from the Device Manager or a new hp-setup instance.

---

