---
title: "Network Printer Problem"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by mgaskell on 2007-01-31
I still can print using my Edgy box.

My Laserjet 4Plus is connected to my network via a D-Link print server attached to the parallel port.

I can ping the print server at 192.168.1.110

The connection on the printer properties shows connection (URI) [http://192.168.1.110/](http://192.168.1.110/)

I used CUPS to install since I'm not using the HP JetDirect adapter.

I used the Laserjet 4Plus driver preinstalled with Edgy.

The system shows my printer installed and ready.

Nothing prints. When I send a job to the print server is says that it is printing but it is not.

It kills me to say it but if I can't print using Edgy I have to go back to WinDoze.

Thanks again in advance!

---

### Post by mgaskell on 2007-01-31
First line correction:

I still CAN'T print using Edgy.

Sorry

---

### Post by mgaskell on 2007-01-31
Also:

Forgot to mention that my Ubuntu Edgy box is my laptop communicating wirelessly with my network.

---

### Post by mgaskell on 2007-01-31
I may be going over the top here but I'm trying to provide as much info to get this problem fixed.

Here are the contents of my printers.conf file:

# Printer configuration file for CUPS v1.2.4
# Written by cupsd on 2007-01-29 09:42
<Printer Laserjet>
Info Laserjet 4 Plus
Location bedroom
DeviceURI [http://192.168.1.110/](http://192.168.1.110/)
State Idle
StateTime 1170092483
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
</Printer>

---

### Post by mgaskell on 2007-01-31
Success!!

After weeks of trial and error I finally got this thing to print. I hope this might save someone else the headaches I went through.

I used the localhost:631 address in Firefox to get to the CUPS setup page rather than use the <system> <administration> <printing> option.

I selected Add Printer from the Home page.

I filled in the fields for Name, Location and Description.

Under Device I selected internet printing protocol (http).

Here was my first hang up - Since I am using a D-Link print server attached to the parallel port of my HP LaserJet 4Plus printer, under Device URI I had to use the format socket://*address*. In my case socket://192.168.1.110/. You can find the correct format for your print server by using the "Network Printers" link on the Device URI page of the setup menu.

The only thing left was to select the printer, model and driver. The recommended driver for my printer, Foomatic/Postscript did not work. I had to use Foomatic/hpijs (en).

I printed a test page and everything is working great now.

I can stay with Ubuntu - sorry Bill.

---

### Post by tesseract420 on 2007-02-06
I typed "http://localhost:631" and got:

"ERROR
The requested URL could not be retrieved

While trying to retrieve the URL: [http://localhost:631/](http://localhost:631/)

The following error was encountered:

    * Connection Failed 

The system returned:

    (61) Connection refused

The remote host or network may be down. Please try the request again. "

Any suggestions?

---

