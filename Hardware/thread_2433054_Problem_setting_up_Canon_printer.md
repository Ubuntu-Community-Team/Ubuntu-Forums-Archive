---
title: "Problem setting up Canon printer"
date: 2019-12-12
forum: Hardware
---

### Post by townhill on 2019-12-12
I'm setting up my laptop after converting to Ubuntu 19.10 from windows and having difficulty with the printer.  I have a Canon Pixma 8520.  Trying to set it up through CUPS and the printer is not responding.  The printer and laptop are on  a wireless network.  i installed the driver from a Deb file because I couldn't find one for my printer from the list on the Ubuntu install.

In CUPS I set up the printer and driver, calling it Canonxx, It is set up with the ip address found in the terminal by pinging myprinter.  

The other canonpixma i set up in CUPS with the IP address I found on the printer's screen.

When I searched for network printers in CUPS I did not see any, so I set both up manually using the IP addresses above.

After setting them up I checked in the terminal and got the following: 

```
$ lpstat -a
canonpixma accepting requests since Thu 12 Dec 2019 08:05:50 PM PST
CanonXX accepting requests since Thu 12 Dec 2019 08:08:12 PM PST

```

and 

```
$ ping myprinter
PING myprinter.Home (198.105.244.23) 56(84) bytes of data.

```

when I check the Canonxx printer in CUPS I get

> CanonXX (Processing, Accepting Jobs, Not Shared)
Driver:	Canon TR8500 series Ver.5.50 (color, 2-sided printing)
Connection:	[http://198.105.244.23](http://198.105.244.23)


But I cant print anything.  Nothing on the canonpixma and with the CanonXX, first I get a message  that I am connected to the printer and then that the printer is not responding.

I'm just getting started in Linux so am probably missing a simple step.   Can anyone point me in the direction of how to correctly set up my printer?

---

### Post by brian_p on 2019-12-13
> **townhill said:**
> I'm setting up my laptop after converting to Ubuntu 19.10 from windows and having difficulty with the printer.  I have a Canon Pixma 8520.  Trying to set it up through CUPS and the printer is not responding.  The printer and laptop are on  a wireless network.  i installed the driver from a Deb file because I couldn't find one for my printer from the list on the Ubuntu install.

The first problem here is your expectations. You expect to have to use a driver but, because the Pixma 8520 is an AirPrint device, no drivers, from Ubuntu or from Canon, are needed.

Please give what you get with

```
driverless
```

> 
In CUPS I set up the printer and driver, calling it Canonxx, It is set up with the ip address found in the terminal by pinging myprinter.  

The other canonpixma i set up in CUPS with the IP address I found on the printer's screen.

What model is canonpixma?

The second problem is this:
> Connection: [http://198.105.244.23](http://198.105.244.23)
That URI is not correct.

---

### Post by townhill on 2019-12-13
The driverless command returns nothing.  I think it should have returned the URI of the printer. Does that mean that my printer is not visible on the network?  Maybe it's a printer issue?

The printer model is Canon TR8520 and identifies its Product Name as TR8500 series.

---

### Post by brian_p on 2019-12-13
Let's try

```
lpinfo -v
```

and

```
avahi-browse -rt _ipp._tcp
```

---

### Post by townhill on 2019-12-13
So 

```
$ lpinfo -v
network ipp
network http
network lpd
file cups-brf:/
network beh
network socket
direct hp
serial serial:/dev/ttyS4?baud=115200
network https
network ipps
direct hpfax

```

and 

```
$ avahi-browse -rt _ipp._tcp
+   wlo1 IPv6 Canon TR8500 @ MSI                            Internet Printer     local
+   wlo1 IPv4 Canon TR8500 @ MSI                            Internet Printer     local
+     lo IPv4 Canon TR8500 @ MSI                            Internet Printer     local
=   wlo1 IPv6 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [MSI.local]
   address = [fe80::bd47:7a34:b476:ef53]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]
=   wlo1 IPv4 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [MSI.local]
   address = [192.168.0.3]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]
=     lo IPv4 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]



```

---

### Post by brian_p on 2019-12-13
> **townhill said:**
> So 

```
$ lpinfo -v
network ipp
network http
network lpd
file cups-brf:/
network beh
network socket
direct hp
serial serial:/dev/ttyS4?baud=115200
network https
network ipps
direct hpfax

```

The command you used is a CUPS command. It does not show any discovered network printers, as did the *driverless* command also. At this point I would normally say you do not have any printer on the network. However, I cannot claim this because the *avahi-browse* command does show the printer. I am mystified as to why *lpinfo -v* gives the output it does.

Does ```
ippfind -T 5
``` give you anything?

> 
```
$ avahi-browse -rt _ipp._tcp
+   wlo1 IPv6 Canon TR8500 @ MSI                            Internet Printer     local
+   wlo1 IPv4 Canon TR8500 @ MSI                            Internet Printer     local
+     lo IPv4 Canon TR8500 @ MSI                            Internet Printer     local
=   wlo1 IPv6 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [MSI.local]
   address = [fe80::bd47:7a34:b476:ef53]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]
=   wlo1 IPv4 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [MSI.local]
   address = [192.168.0.3]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]
=     lo IPv4 Canon TR8500 @ MSI                            Internet Printer     local
   hostname = [localhost]
   address = [127.0.0.1]
   port = [631]
   txt = ["printer-type=0x80101E" "printer-state=3" "Duplex=T" "Color=T" "TLS=1.2" "UUID=7ba84bca-3d37-36fd-6202-e190f4fec622" "URF=DM3" "pdl=application/octet-stream,application/pdf,application/postscript,image/jpeg,image/png,image/pwg-raster,image/urf" "product=(tr8500)" "priority=0" "note=" "adminurl=https://MSI.local.:631/printers/Canon-TR8500" "ty=Canon TR8500 series Ver.5.50" "rp=printers/Canon-TR8500" "qtotal=1" "txtvers=1"]

```

The *txt =* line contains *URF=DM3*. This confirms that the device is an AirPrint printer. It has an IP address *192.168.0.3* and a hostname *MSI.local*.

A print queue can be set up with either

```
lpadmin -p tr8500 -v ipp://MSI.local/printers/Canon-TR8500 -E -m everywhere
``` 

or

```
lpadmin -p tr8500 -v ipp://192.168.0.3/printers/Canon-TR8500 -E -m everywhere
```

Does

```
lp -d tr8500 /etc/nsswitch.conf
``` print?

What is also puzzling is the line > =     lo IPv4 Canon TR8500 @ MSI

Have you got the device also connected by USB?

---

### Post by townhill on 2019-12-13
Yes, ippfind gives me

```

$ ippfind -T 5ipp://MSI.local:631/printers/Canon-TR8500

```

and 
```

$ lp -d tr8500 /etc/nsswitch.conf
request id is tr8500-26 (1 file(s))


```
pops up a window saying that a file is printing but CUPS says printer not responding

The printer is on the wireless network but there is no usb connection, wireless only.

---

### Post by townhill on 2019-12-13
i set up the print queue as you showed me.

---

### Post by townhill on 2019-12-13
Actually, i ran the [COLOR=#000000][FONT=&amp]$ lp -d tr8500 /etc/nsswitch.conf command again and now the document is sitting in the print queue showing as pending for the last 14 minutes. 

 I'm trying to see how to move it from pending to print. 

 I saw an o[lder post on Stack Exchange]("https://askubuntu.com/questions/519401/printer-in-pending-mode-only-not-printing") that mentioned that this happened because a *print policies* setting was disabled, but that related to 14.04 and I don't see the option in Settings on 19.10[/FONT][/COLOR]

---

### Post by brian_p on 2019-12-13
> **townhill said:**
> Yes, ippfind gives me

```

$ ippfind -T 5ipp://MSI.local:631/printers/Canon-TR8500

```

That is exactly what I expected. Considering *driverless* uses *ippfind*, its failure to give an output looks like a bug.

> 
and 
```

$ lp -d tr8500 /etc/nsswitch.conf
request id is tr8500-26 (1 file(s))


```
pops up a window saying that a file is printing but CUPS says printer not responding

The printer is on the wireless network but there is no usb connection, wireless only.

It looks like a possible failure of the filtering system. Please do

```
sudo cupsfilter -p /etc/cups/ppd/tr8500.ppd -m printer/foo -e nsswitch.conf > out.dat 2>log
```

All the output goes in the file *log*; nothing is shown on the screen. You can use ```
less log
``` to see what is in the file. Post *log* here; as an attachment is probably best.

---

### Post by townhill on 2019-12-13
This looks like it might be the problem.  The log file looks basically empty 

```

cupsfilter: Unable to determine MIME type of "nsswitch.conf".
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)

```

On another note, i did find that I could right click on the printer icon in the printer settings and in the policies tab I see that the *enabled* check box is unticked.  i can check it to enable policies but it goes back to disabled as soon as I click off it.  Maybe a configuration file is overriding the setting?

---

### Post by townhill on 2019-12-13
Sorry, thought I had replied.  So the log looks pretty much empty, 

```

cupsfilter: Unable to determine MIME type of "nsswitch.conf".
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END)

```

Also I was able to see the printer policies checkbox by right clicking on the printer icon in settings and going to *policies*, but I cant make it stay enabled.  It goes back to unchecked right away.  Problem with a configuration file overiding?

---

### Post by brian_p on 2019-12-14
> **townhill said:**
> This looks like it might be the problem.  The log file looks basically empty.

The biggest problem we have at present is me. :( In the sixth post I took a wrong turning because I misinterpreted what the the two commands were telling us. *avahi-browse* shows  printers **and** queues on the network. It is showing queues. *driverless* shows **only** printers. It gives an empty output, so it doesn't discover any printers.

You have not got the TR8500 on the network. I wonder whether you have confused getting a wireless connection with Wireless Direct. Using Wireless Direct  disables connection with a router.

---

### Post by townhill on 2019-12-14
I am at a loss.  I reset the printer and connected to the wireless network again.  From the printers control panel I see the network info so I'm pretty sure the printer is on the network but still no luck.  When I try to print  I get a message that the printer has stopped, the configuration file is incorrect or the printer is offline.  :confused:    When I ping the printer at the ip address shown on the printers screen (192.168.0.8) I cant connect. Maybe my best bet would be to hookup the printer directly with a usb cable.  

I have a second laptop here running Zorin and it discovered the printer but said it was offline when I tried to print to it.  I tried pinging the printer with no luck.  If the usb connection works at least I will be able to print while poking around trying to get the wireless to work. It doesn't seem likely, but maybe it just boils down to something wrong with the printer setup.

Thank you for your patience and perseverance helping me with this.

---

### Post by brian_p on 2019-12-15
> **townhill said:**
> I am at a loss.  I reset the printer and connected to the wireless network again.  From the printers control panel I see the network info so I'm pretty sure the printer is on the network but still no luck.  When I try to print  I get a message that the printer has stopped, the configuration file is incorrect or the printer is offline.  :confused:    When I ping the printer at the ip address shown on the printers screen (192.168.0.8) I cant connect. Maybe my best bet would be to hookup the printer directly with a usb cable.  


Page 166 of the printer's manual is worth looking at. Can you ping the router from the laptop? The printer also has a web server that should be accessible with ```
http://192.168.0.8
``` (but probably isn't if ping and *driverless* do not work). This really looks like a network problem to me.

---

### Post by townhill on 2019-12-16
Yes. I think your right.  Thanks for your help, I have learned quite a bit poking around as I followed your suggestions.  This forum is so helpful, especially for new Linux users like me.  It makes me even happier that I
made the switch from Windows.   

i'll concentrate on figuring out whatever network problem I'm having.  Meanwhile I have set up the printer with a usb connection. Not the long term fix but ok for now. Not sure if i should mark this post as solved.  Is that the right way to close it out?

---

