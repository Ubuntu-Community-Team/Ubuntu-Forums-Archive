---
title: "Getting Vista to talk to your Ubuntu CUPS printer"
date: 2008-10-14
forum: General Help
---

### Post by conorgriffin on 2008-10-14
In an effort to get Vista and Ubuntu to share a printer using CUPS where Ubuntu was the server I came across this article.  It solved the problem for me so hopefully it can help others.



Taken from searchenterpriselinux.techtarget.com ([link]("http://searchenterpriselinux.techtarget.com/tip/0,289483,sid39_gci1250451,00.html"))

> The less you need to rely on any proprietary protocol to get work done, the better off you are overall. Some of those protocols have been real stumbling blocks -- such as SMB, Microsoft's proprietary protocol for file and printer sharing. Linux implementations of SMB exist, but you're probably better off without it in the long run whenever you can manage it.

I recently set up a Linux workstation that shared out a Hewlett-Packard printer to the rest of my network -- a network that otherwise consisted entirely of Windows machines. I didn't like the idea of setting up SMB support on the Linux box, and instead, explored the possibility of having the Windows machines connect directly to the shared printer as a network printing device.

To my surprise, this turned out to be pretty easy. Here are the steps to connect your Windows machines to the shared printer:

Set up the printer on your Linux machine and share it using CUPS via port 631. The exact method for doing this varies between distributions, so check with your distro's documentation. The end result should be a working printer, and a running CUPS service which you can access through your Web browser at [http://localhost:631](http://localhost:631) from the Linux system.

Using the CUPS Web interface, go to the Printers tab and make a note of the printer name, which is typically the Description: line). You can do this from the Windows machine where you plan to set up printer support.

In Windows, go to Control Panel | Printers and click onAdd a printer.

When prompted for a printer location, select Network printer, in the Add Printer Wizard.

When prompted for the network location, select URL and use the followingURL format: http://<hostname>:631/printers/<printername>. 

For instance, if the Linux host has a DNS name of linuxbox and the printer is named LaserJet-5, you'd use [http://linuxbox:631/printers/LaserJet-5](http://linuxbox:631/printers/LaserJet-5) as the URL.

When asked for a printer driver, select Generic as the manufacturer andMS Publisher Imagesetter as the driver. In truth, any generic PostScript driver will do, but this works as well as any.

When finished with the wizard, print a test page to make sure everything is set up correctly.

In Windows Vista, the steps are almost exactly the same, but the nomenclature for some of the steps is a little different. In the first step of the wizard, Vista will attempt to search for a printer (via SMB, which it won't find). Click Stop to halt the search and then click The printer that I want wasn't listed to add a printer manually.

In the next step of the wizard, use Select a shared printer by name when you want to supply the printer's URL. The rest should unfold exactly as before. Adding a printer by TCP/IP address or hostname will not work. Finally, if you're using a firewall product, make sure that port 631 is not being blocked. The Microsoft firewall on the Windows machine will usually know automatically what to do, but some third-party products may not.

---

