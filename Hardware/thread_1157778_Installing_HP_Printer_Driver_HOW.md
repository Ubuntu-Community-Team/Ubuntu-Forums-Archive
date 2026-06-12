---
title: "Installing HP Printer Driver HOW?"
date: 2009-05-13
forum: Hardware
---

### Post by gnulab on 2009-05-13
Hi,

I'm trying to install printer drivers, my printer is HP LaserJet P2015d.

It's supported by HPLIP and the package is installed by default and checked out alright from System -> Administration -> Synaptic Package Manager.

Now, I would like to install the printer myself instead of having ubuntu detect the printer and install the driver automatically, because the way the printer is connected is via the Linksys print server (WPS-54G) and under Windows, it says LPR (the print job will be directed to a specific IP)

So what do I do now? Do I call up the program HPLIP, choose the driver and install it or I have to do it via the terminal? And if via the terminal, could someone direct me step by step in order to accomplish this?

thank you in advance.
Henry

---

### Post by shadowlemon on 2009-05-13
can you tell us the version of (k)ubntu you are running? As for using servers im not sure how this works but HPLIP has some problems with the newest version Jaunty.

---

### Post by coffeecat on 2009-05-13
> **gnulab said:**
> Now, I would like to install the printer myself instead of having ubuntu detect the printer and install the driver automatically, because the way the printer is connected is via the Linksys print server (WPS-54G) and under Windows, it says LPR (the print job will be directed to a specific IP)

I'm not quite sure what you mean. Have you connected the printer to the print server and switched both the printer and server on and then gone to System > Administration > Printing? That way Ubuntu will pick up and autoinstall a printer on the network, which works just fine for me with my network HP multifunction machine. But as you are using a print server, I don't know whether that will be the same.

If that does work for you, beware of one gotcha that I'm surprised not more people complain about. When I first did this, my printer was getting its LAN IP address from the DHCP server in the router. Another day the printer was assigned a different address and I had to reinstall it in Ubuntu all over again with the new IP address. Ubuntu was using the IP address, not the hostname of the printer. Which is ridiculous - My Apple Mac was fine with the shifting address. I solved this by going into the printer control settings and setting a static IP address for it. I just pass this tip on in case you need to do the same with the print server.

The other thing you might find useful is the hplip-gui package, a nice GUI frontend for hplip and the HP Toolbox. It's in the repositories, but it won't help you with installing a printer.

---

### Post by coffeecat on 2009-05-13
> **shadowlemon said:**
> HPLIP has some problems with the newest version Jaunty.

Really? I haven't encountered any problems - yet. Can you elaborate?

---

### Post by gnulab on 2009-05-14
@ shadowlemon: I am using ubuntu 9.04

When I say print server, it's not the traditional print server.

Here's the link to the print server product I'm currently using.
[http://www.linksysbycisco.com/ANZ/en/products/WPS54G](http://www.linksysbycisco.com/ANZ/en/products/WPS54G)
or
[http://www.dlink.com/products/?sec=2&pid=165](http://www.dlink.com/products/?sec=2&pid=165)


Brief summary of the print server I'm referring to.
The printer itself doesn't have a network card. What happen is, the printer (usb) is plugged into the device (the link above) and this device will be assigned an IP. Each pc will send their print jobs to this device and this device will relay it to the printer. So the printer could be the normal printer (USB), instead of a built-in network card printer. It's a cheaper solution for SOHO.

Now, I've tried System -> Administration -> Printing method. That method automatically searches for printers connected to the pc physically (I'm guessing probing usb & parallel ports), while searching for the printer manually will cause it to search via specified IP. Problem is because the print server is not the traditional type, thus it wouldn't be able to detect the attached printer.

Is there a way that I could choose the printer driver that I want to install manually, instead of relying the system to locate the model of the printer? How do I do that?

Thanks!
Henry

---

### Post by 11hjpphty76lkjj on 2009-05-25
HPLIP only supports HP Jetdirect devices.  Other network print sharing device are not supported because in most cases (all that I'm aware) do not allow the correct communication with the printer for HPLIP to work.

---

### Post by steveneddy on 2009-05-25
As an avid HP printer user for years and recently set up a new HP all in one printer at the house, I recommend downloading the HPLIP software directly from HP here:

[http://hplipopensource.com/hplip-web/gethplip.html](http://hplipopensource.com/hplip-web/gethplip.html)

and let the HPLIP software locate and install the proper driver for you.

If you have any printers installed via the Ubuntu Printer management app, uninstall the printer and restart then run the HPLIP software that you just downloaded.

The HPLIP from HP has updated drivers and better functionality most of the time than the version offered in the repos.

Just my .02

:)

---

