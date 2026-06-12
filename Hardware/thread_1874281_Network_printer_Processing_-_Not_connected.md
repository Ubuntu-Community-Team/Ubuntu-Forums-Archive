---
title: "Network printer: Processing - Not connected?"
date: 2011-11-02
forum: Hardware
---

### Post by jfd3220 on 2011-11-02
I have a Brother DCP7065DN attached to the network. Previously I was able to print to it with no problem from my 10.04 desktop.  Suddenly this week everytime I go to print something I get the following message in the print queue: Processing - Not connected? I've also noticed that when I send a print job to the printer a little blue circle with an "i" in it appears over the printer icon in the System>Administration>Printing window.  I've deleted and added the printer a few times and cycled the power to both devices.  I've tried managing it through localhost:631 but nothing seems to fix the problem.  I seem to remember CUPS being updated in the last week but I'm not sure.  Can anyone help me?

---

### Post by SparTacux on 2011-11-02
Try pinging your print server from another computer.

---

### Post by jfd3220 on 2011-11-04
How do I do that?  I have just tried printing from my laptop running 11.04 and have the same problem.  Printing is not a problem from windoze so it's not a hardware problem.

---

### Post by jfd3220 on 2011-11-04
I seem to have found a solution. Previously I was installing the driver via the 'Find Network Printer' option in the 'Select Device' window.  Now I selected the 'Internet Printing Protocol' option and put in the IP address of the printer and cleared the 'Queue' field then clicked verify and selected the driver that I had installed earlier and now everything seems to be working.  It's working in both 10.04 and 11.04.

---

### Post by jfd3220 on 2011-11-09
This problem seems to have returned. I've installed 11.04 on a new machine and installed the printer the way I installed it on the other machines, through the IPP option, and now I'm getting the same message.  The problem has also returned on the other Ubuntu machines on the network.  Windoze machines on the network are still printing fine.

---

### Post by jfd3220 on 2011-11-09
So I've reinstalled the printer several different ways again.  This time I went through the "Find Network Printer" option.  I provided the IP of the printer and at first it returned a JetDirect printer and then about 10 seconds later it returned the Brother printer.  I tried both of these options. The second one seems to be working.  This is exactly the way that I had installed the printer when this whole problem started, so I'm going to give it a few days and see if the problem recurs.

---

### Post by jfd3220 on 2011-11-17
This problem has returned.  I haven't made any changes to the printer configuration.  Any ideas?

---

### Post by SparTacux on 2011-11-17
Are you using static IP or DHCP to get your IP addresses on your network?.
If using DHCP then your print server is possibly going to get a different IP every boot up. It could be something as simple as that.

Test with ping command ( run terminal )

ping 192.168.0.2

If 198.168.02 is your print server. Use ifconfig ( in terminal ) on the print server to get it's IP or right click on network icon ( on the panel  )and select connection information.
Then ping it from another computer.

Also if using a firewall make sure you allow traffic ( in and out ) on port 631 on all machines. Try disabling Firewall on all machines to test.


Also make sure your print server is set to broadcast it's presence on the network. Run print manager on Print Server and select Server from menu and tick publish shared printers. If you do this you will be able to use the Find Network Printer option on the other computers to find your printer.

Hope this helps

---

### Post by jfd3220 on 2011-11-17
It's actually static IP.  That much I am sure of.  The problem must be with CUPS somewhere because the window$ machines have no problem printing.

Both Ubuntu machines can ping each other.

Do the machines with the print servers need to have static IPs?  Rebooting and reinstalling the printer would fix the issue then, wouldn't it? I just ask because I have tried that and it didn't resolve anything.

---

### Post by SparTacux on 2011-11-17
Did you select publish shared printers on the Server menu?

---

### Post by SparTacux on 2011-11-17
Other than that try to get the cups screen up in your browser

Run Firefox and type 192.168.0.2:631 in the URL Bar
If 192.168.0.2 is your IP of the print server

That's about the limit of my vast knowlede on cups ;-)

---

### Post by jfd3220 on 2011-11-17
Yes the printer seems to be shared by default.  The "Shared" box is checked when I check the properties of the printer.

Just reinstalled the printer and it's working again.  I checked the router device list and it turns out that the printer was assigned a static IP but the other machines were not, although I'm pretty sure they've been getting the same IP addresses for quite a while.  Now everything has a static IP. Thanks for your help SparTacux.

---

### Post by SparTacux on 2011-11-17
Is your printer attached to an Ubuntu computer or to the router?

---

### Post by jfd3220 on 2011-11-17
To the router through a switch.

---

### Post by arst06d on 2012-09-13
I have the same problem with my Brother MFC-425CN, attached to the router.
The router DHCP is configured to always assign the same ip address to the printer.
Suddenly I can't print from either my desktop or netbook -"processing - not connected" being the status in the print queue.
Odd thing is that I can initiate and print a test page no problem.

I have deleted and recreated the printer definitions but nothing works.

Help, please ...

---

### Post by jfd3220 on 2012-09-13
I have found that sometimes it helps to disable and re-enable the printer.  Also, printing from the browser seems to be more problematic than printing from other applications.

---

### Post by arst06d on 2012-09-13
I've disabled, deleted, disconnected, rebooted, and anything else I can think of to no effect.

I'm having probs from all applications inc browser and LibreOffice.

---

### Post by jfd3220 on 2012-09-13
Which version of Ubuntu are you using?

---

### Post by kurt18947 on 2012-09-13
I've had very good luck with networked brother printers using the following procedure. YMMV as usual.

I get to the printing applet.  I'm using gnome-shell which uses a 'dumbed-down' printer app but  the command <system-config-printer> in terminal brings it up.  Right-click on the printer icon and select "properties".  One of the lines should be "Device URI".  I put the following:  socket://xxx.xxx.xxx.xxx:9100  where x=i.p. address of the printer.  You may want to restart though I don't know if a restart is necessary.  This has been pretty successful for me.  Other printer network connection protocols have been hit-and-miss for me.

---

### Post by arst06d on 2012-09-13
> **jfd3220 said:**
> Which version of Ubuntu are you using?

Using 12.04

Re the solution from kurt18947 - I was set up like that anyway.  Tried a reboot (again) and sent a doc to print.

Same problem as before.

---

### Post by Easy Limits on 2012-09-13
Have you tried "system-config-printer" at the terminal?

---

### Post by arst06d on 2012-09-13
> **Easy Limits said:**
> Have you tried "system-config-printer" at the terminal?

yep, and played about with the properties in various configurations.

---

### Post by Peter Maunder on 2012-09-13
I am not certain whether my experience is directly relevant, but I too have a Brother network attached.

My Brother HL-5250DN is attached as an USB printer to my desktop and as a network printer to the Desktop and Laptop running 12.04 and a Netbook with Linux-Mint (Mate) 13.  
I used to have a problem when the printer was directly addressed  (192.168.0.2 or 192.168.0.5) if I turned the printer on after the computers,  because the router added addresses dynamically. I defined the printer in the Laptop and Netbook twice with different addresses to get around this problem.  USB connection  was no problem. 
 
Since 12.04 the printer was redefined in the properties Device URI: as 
  dnssd://Brother%20HL-5250DN%20series._pdl-datastream._t  after upgrading the systems from Ubuntu 11.04. Now the order for turning on the printer is not important.

---

### Post by arst06d on 2012-09-13
My device is now dnssd://Brother%20MFC-425CN._pdl-datastream._tcp.local/
still the same error.

What a complete bugger - was printing fine until today and can't identify any changes which would have affected this.

---

### Post by Peter Maunder on 2012-09-14
Just a thought, but have you checked the cables and they are correctly seated? Running a test print is a short message compared with activating and downloading print job with its associated fonts.

---

### Post by arst06d on 2012-09-14
Hi - yes disconnected and reconnected both ethernet and power cables at both ends, and still had the problem.

Curiously though, I have managed to print today with no further changes made.  I'm going to leave it a while to monitor.  Maybe 12.10 will fix it completely, or screw it completely.  Maybe the printer's on the way out.  Who knows.

---

### Post by kurt18947 on 2012-09-15
> **arst06d said:**
> My device is now dnssd://Brother%20MFC-425CN._pdl-datastream._tcp.local/
still the same error.

What a complete bugger - was printing fine until today and cahttp://www.pclinuxos.com/forum/n't identify any changes which would have affected this.

I had that type address and like your subsequent post, my connection was intermittent.  When I assigned a static IP address to the printer and used HP JetDirect protcol (Socket://i.p.address) my network printer connection has been rock solid.  Brother printers seem to hew very closely to HP standards.  In fact if I use the Ubuntu install for the MFC-7820N, it shows up as an HP laser printer.

---

### Post by arst06d on 2012-09-16
Like yours, my printer was reliable until this problem occurred.

My router assigns the same ip address to it each time of asking, and it was set up as socket://ip.address.

Hey ho!

---

