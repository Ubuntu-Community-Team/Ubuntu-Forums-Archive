---
title: "Brother HL-6050DN says &quot;ignore data&quot; then prints nothing"
date: 2012-03-21
forum: Hardware
---

### Post by xigen on 2012-03-21
Hi,

It worked before - really well.

Ubuntu 11.10 

1) Unplugged/plugged router
2) Unplugged/plugged hub
3) Made sure printer is attached and seen by network.  Reserved 192.168.2.2 for printer
4)  reinstalled all CUPS stuff via Synaptic

When I print a 'test page' I get a blank sheet of paper
When I attempt to print an email (gmail/firefox) the printer says "Ignore Data".

Suggestions?

MW

---

### Post by plucky on 2012-03-22
> **xigen said:**
> Hi,

It worked before - really well.

Ubuntu 11.10 

1) Unplugged/plugged router
2) Unplugged/plugged hub
3) Made sure printer is attached and seen by network.  Reserved 192.168.2.2 for printer
4)  reinstalled all CUPS stuff via Synaptic

When I print a 'test page' I get a blank sheet of paper
When I attempt to print an email (gmail/firefox) the printer says "Ignore Data".

Suggestions?

MW

Have you installed the drivers?

The drivers for your printer are packaged in the Ubuntu repositories.Open synaptic and search for your printer and install the cupswrapper and lpr driver packages.

Open a terminal and post output of ```
dpkg -l | grep -i brother
```

Good Luck

---

### Post by xigen on 2012-03-22
meow@meow-System:~$ dpkg -l | grep -i brother

ii  brother-cups-wrapper-laser1            1.0.2-1-0ubuntu7                        Cups Wrapper drivers for laser1 brother printers
ii  brother-lpr-drivers-common             1.0.0-4-0ubuntu1                        Common files for brother-lpr-drivers packages
ii  brother-lpr-drivers-laser1             1.0.0-3-0ubuntu5                        LPR drivers for laser1 brother printers
ii  ptouch-driver                          1.3-0ubuntu11                           CUPS/Foomatic driver for Brother P-touch label printers


I tried to print after installing the brother 6050dn drivers.  Unfortunately, it still says "ignore data".

Suggestions?

Best - MW

---

### Post by plucky on 2012-03-22
Does your printer have a USB connection?

If it does,I would connect it to the USB and see if it works that way.Once it works,you will know the drivers are installed correctly and you can then try the network connection.

Good Luck

---

### Post by imachavel on 2012-03-22
this is mine

dpkg -l | grep -i brother
ii  ptouch-driver                          1.3-0ubuntu11                              CUPS/Foomatic driver for Brother P-touch label printers

no idea why you disconnected the router and modem etc. makes no sense as the i.p. configuration protocol is meant to look for i.p. addresses, or possibly your .net framework will search for url addresses translated by d.n.s. or dhcp or whatever on a server domain with the web server back end services running from an i.p. address. Basically put, no ports should effect your printing services. Unless you have it set up as a network printer. Now if it's a host based printer, do me a favor and run

lprm from the terminal, I'd like to see if it cancels the que, if the que is sent at all, which I'm sure it is

now try sudo apt-get install update

maybe it'll fix the drivers

also lspci also from a terminal and post syntax output

now please type:

getlibs -i libstdc++5_3.3.6-17ubuntu1_i386.deb

and post output

and let's try:

ping 10.7.102.65

and tell me if you got a good ping

and last but not least try reinstalling the printer with:

[B]sudo apt-get install cups

and

follow the instructions then:

start cups services

or try and follow this guide:

[http://www.liberiangeek.net/2010/07/installadd-printers-ubuntu-10-04-lucid-lynx/](http://www.liberiangeek.net/2010/07/installadd-printers-ubuntu-10-04-lucid-lynx/)

[http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-an-hp-printer-on-ubuntu-79.htm](http://www.icelab.eu/en/blog/ubuntu-and-linux-12/how-to-install-an-hp-printer-on-ubuntu-79.htm)

[http://www.ehow.com/how_8749065_install-brother-mfc-printer-ubuntu.html](http://www.ehow.com/how_8749065_install-brother-mfc-printer-ubuntu.html)
[/B]

---

### Post by imachavel on 2012-03-22
> **plucky said:**
> Does your printer have a USB connection?

If it does,I would connect it to the USB and see if it works that way.Once it works,you will know the drivers are installed correctly and you can then try the network connection.

Good Luck

you are asking in case he is trying wirelessly? In which case that would explain why he'd disable the router and modem I guess then he'd need a wireless interface card installed in a usb and would use a configuration cd in the disk drive with steps on how to install the printer wirelessly to print wirelessly? It'd probably be made for windows I'd wonder if wine could open it. Otherwise searching for an install method for the exact model of printer for Ubuntu might reveal interesting results as there are DOZENS of hits on google and bing on different printers and ways to install them in Ubuntu. I would try the usb method recommended though

---

### Post by xigen on 2012-03-27
hmmm... I will try the USB connection next.  The printer is 10 ft from my computer and my USB chord is about 3-4 ft. (rut.ro)

...

I was about to try to install the printer as a network printer and try a few IP addresses beginning w/ 192.168.2.2  - just to see if I have a mis-configured rounter table.

When I attempted to install the printer I got a message:
[INDENT]FirewallD is not running. Network printer detection needs services mdns, ipp, ipp-client and samba-client enabled on firewall.[/INDENT]

Is this relevant? (and) how do I enable that on the firewall?

---

### Post by xigen on 2012-03-27
hmmm ... here is a picture of my config.    It does not show the printer as a network printer - and gives (*to my viewing) no way to change the settings to make it a network printer.

---

### Post by mörgæs on 2012-03-27
Moved to the hardware forum.

---

