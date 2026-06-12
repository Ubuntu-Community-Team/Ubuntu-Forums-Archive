---
title: "Epson 2540 printer / scanner"
date: 2014-10-12
forum: Hardware
---

### Post by Bobby_James on 2014-10-12
I cannot print from my new Epson 2540 printer/scanner even though I have done what I can to solve the problem.

```
dpkg -l | grep epson-inkjet-printer
```

ii  epson-inkjet-printer-201211w                 1.0.0-1lsb3.2                                       Epson WF-2010/WF-2510/WF-2520/WF-2530/WF-2540 - Epson Inkjet Printer Driver

ii  epson-inkjet-printer-escpr                   1.4.3-1lsb3.2                                       Epson Inkjet Printer Driver (ESC/P-R) for Linux

```
localhost:631
```

[TABLE="class: list"]
[TR]
[TD][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series")[/TD]
[TD]HP Deskjet 2540 series[/TD]
[TD]Local Printer[/TD]
[TD]HP DeskJet 2500 - CUPS+Gutenprint v5.2.8-pre1[/TD]
[TD]Idle - "Rendering completed"[/TD]
[/TR]
[/TABLE]

I have connected the USB cable from the laptop to computer. When I print, all appears to work and CUPS shows each time that the print job has completed. However, nothing ever prints.

For example, CUPS shows:

[TABLE="class: list"]
[TR]
[TD][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series")-27[/TD]
[TD]Unknown[/TD]
[TD]Withheld[/TD]
[TD]11k[/TD]
[TD]1[/TD]
[TD]  completed at
Sun 12 Oct 2014 16:48:52 BST[/TD]
[/TR]
[/TABLE]

Yet this print job never printed.

I have downloaded the drivers and I have looked at CUPS. What more can I do?  Thanks.

---

### Post by Bobby_James on 2014-10-14
This is an example where something just works in Windows 8 but does not seem to work in Ubuntu 12.04.

I have an Epson 2540 printer/copier/scanner. It has wireless but, right now, I'm just trying with the USB cable. 

Here are the drivers I've installed:

 
ii  epson-inkjet-printer-201211w                 1.0.0-1lsb3.2                                        Epson  WF-2010/WF-2510/WF-2520/WF-2530/WF-2540 - Epson Inkjet Printer Driver

ii  epson-inkjet-printer-escpr                   1.4.3-1lsb3.2                                        Epson Inkjet Printer Driver (ESC/P-R) for  Linux


This is what localhost:631 shows:

[TABLE="class: cms_table_list"]
[TR]
[TD][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series")[/TD]
[TD]HP Deskjet 2540 series[/TD]
[TD]Local Printer[/TD]
[TD]HP DeskJet 2500 - CUPS+Gutenprint v5.2.8-pre1[/TD]
[TD]Idle - "Rendering completed"[/TD]
[/TR]
[/TABLE]

 
I connect the USB cable from the laptop to the printer. When I  print, CUPS (on localhost) shows each time that the print job  has completed. However, nothing ever prints. The printer does not make any noises to suggest that's it's received any instructions. 

For example, CUPS shows:

[TABLE="class: cms_table_list"]
[TR]
[TD][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series")-27[/TD]
[TD]Unknown[/TD]
[TD]Withheld[/TD]
[TD]11k[/TD]
[TD]1[/TD]
[TD]  completed at
Sun 12 Oct 2014 16:48:52 BST[/TD]
[/TR]
[/TABLE]

 
Yet this print job never printed.

What more can I do? I've installed the drivers and the printer shows in CUPS. But nothing ever prints! Thanks.

---

### Post by JeQhdMD on 2014-10-14
I have this exact printer . . all printer functions including scan work perfectly.   I am running Ubuntu 14.04.

Here are the drivers I have installed:

[IMG]http://i.imgur.com/VRVUdYk.png[/IMG]

[IMG]http://i.imgur.com/iQOY7sg.png[/IMG]

My localhost:631 shows I have CUPS 1.7.2 installed, with printer driver (Epson WF-2540 Series-epson-inkjet-printer 1.0.0-1lsb3.2 Seiko Epson Corporation LSB 3.2).

I don't recall seeing anything referencing "Gutenprint"

So . . . I would uninstall the drivers you've already done - - have USB cable connected and rerun the printer scan routine.   Then, recheck USC and click the down arrow next to "All Software".   You should see a comprehensive listing of dozens of Epson "Series" printers, and you want to install the two I have posted above.

---

### Post by sammiev on 2014-10-14
I go [here]("http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX") for the drivers and do a search on 2540.

---

### Post by JeQhdMD on 2014-10-14
Yes, this is a great site for Epson drivers . . . If I recall correctly, Ubuntu via USC pulled in the two main printer drivers, but I went to this site for the scanner drivers (I installed both).   I recommend using "Simple Scanner" for the easiest and fastest scans.

---

### Post by mörgæs on 2014-10-14
Threads merged. Please stop double-posting.
If you feel you don't get enough answers then bumping after a reasonably long time is tolerated.

---

### Post by Bobby_James on 2014-10-15
> **JeQhdMD said:**
> I have this exact printer . . all printer functions including scan work perfectly.   I am running Ubuntu 14.04.

Here are the drivers I have installed:

[IMG]http://i.imgur.com/VRVUdYk.png[/IMG]

[IMG]http://i.imgur.com/iQOY7sg.png[/IMG]

My localhost:631 shows I have CUPS 1.7.2 installed, with printer driver (Epson WF-2540 Series-epson-inkjet-printer 1.0.0-1lsb3.2 Seiko Epson Corporation LSB 3.2).

I don't recall seeing anything referencing "Gutenprint"

So . . . I would uninstall the drivers you've already done - - have USB cable connected and rerun the printer scan routine.   Then, recheck USC and click the down arrow next to "All Software".   You should see a comprehensive listing of dozens of Epson "Series" printers, and you want to install the two I have posted above.

Some progress, thanks. I uninstalled my drivers with dpkg -P. 

Then I inserted the USB, went to USC, and typed "print drivers". There was no listing of dozens of Epson printers.

In USC, when I click on epson-inkjet-printer-201211w, it shows "There isn&#8217;t a software package called &#8220;epson-inkjet-printer-201211w&#8221; in your current software sources." The same happens with epson-inkjet-printer-escpr.

This is, I guess, the problem. Do I need to place something into souces.list? I searched but could not find anything. 

How do I put the package into the software sources?

---

### Post by JeQhdMD on 2014-10-15
OK, below are my sources - - note the epson source:

Also, I didn't type anything into the search field of USC - - I clicked the down arrow to the right of "All Software", and selected "printdriver" .   That brings up the list of 40 or 50 printer or printer groupings, and their associated drivers.

Hope this helps.   I know I had to uninstall and reinstall two or three times before everything started working.   I also initially got a couple dependency errors upon installing the 2 "scanner" drivers.   I basically ignored those (was using Gdebi mostly vs UBC for scanner) . . . but the command line should be even better and you can use the "force" option.   Good luck.   When you succeed, perhaps a few more "cogent" notes will help others with this or a similar epson printer.

[IMG]http://i.imgur.com/bE2I3MS.png[/IMG]

---

### Post by sammiev on 2014-10-15
This is what I see for your printer/scanner. I notice a lot of ppa's in your source list but that's another thing for a different day.

---

### Post by Bobby_James on 2014-10-16
I have now managed, with your help, to get the printer working.

Here is what I did (with some trial and error).

1. Added deb [http://download.ebz.epson.net/dsc/op/stable/debian/](http://download.ebz.epson.net/dsc/op/stable/debian/) lsb3.2 main into /etc/apt/sources.list via USC / Software Sources / Add.

2. I then had to import the GPG key as, when I tried apt-get update / apt-get upgrade, I received an error telling me the Epson files were unsigned. The solution was sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E5E86C008AA65D56

3. I went to USC All Software and clicked on printer drivers. This led me to a list of Epson printers. I selected epson-inkjet-printer-201211w and epson-inkjet-printer-escpr and installed them.

My dpkg -l | grep epson-inkjet-printer now shows: 

ii  epson-inkjet-printer-201211w   1.0.0-1lsb3.2  Epson WF-2010/WF-2510/WF-2520/WF-2530/WF-2540 - Epson Inkjet Printer Driver

ii  epson-inkjet-printer-escpr   1.4.1-1lsb3.2  Epson Inkjet Printer Driver (ESC/P-R) for Linux

4. However, when I tried to print from Gedit, no printers were shown. To resolve this, I went to localhost:631 / Administration / Find New Printers which found the 2540. One issue is that I could not select the correct model from the list so chose a different model. However, this does not matter because the drivers for the 2540 were already installed by USC.

My CUPS now looks like:
[TABLE="class: list"]
[TR]
[TD][HP_Deskjet_2540_series]("http://localhost:631/printers/HP_Deskjet_2540_series")[/TD]
[TD]HP Deskjet 2540 series[/TD]
[TD]Local Printer[/TD]
[TD]HP Deskjet 2050 j510 Series, hpcups 3.12.2[/TD]
[TD]Paused - "Unplugged or turned off"[/TD]
[/TR]
[/TABLE]

The line which shows 2050 j510 Series is irrelevant. What matters is the first column.

---

### Post by Bobby_James on 2014-10-16
Now I am having problems with the scanner aspect.

I installed along with all dependencies :

iscan-data_1.31.0-1_all.deb
iscan_2.30.0-1~usb0.1.ltdl7_i386.deb
iscan-network-nt_1.1.1-1_i386.deb

However, Simple Scan cannot find the scanner (yes it is plugged in via USB).

Also, the iscan icon says "Could not send commands to scanner. Check scanner status".

Any suggestions?

---

### Post by Mike_Walsh on 2014-10-16
Hallo, Bobby.

Easy stuff first; the iscan icon saying "Could not send....etc.", is a very simple fix. Close iscan, turn your printer off.....wait about 10 seconds or so, then turn the printer back on, and open iscan again. The GUI should now appear.

Don't ask me WHY it does this; a 'glitch' in the coding is my guess! I have an Epson all-in-one myself, an SX218. I run multiple 'Buntu 'flavours', and it does this in every single one of them. It's amazing the number of people who fail to install the data package FIRST.

You have to remember, these drivers were never developed by Epson; they were originally developed by a Japanese company called Avasys, who have since washed their hands of them, and turned the repositories over to Epson. However, if you ever speak to an Epson customer service rep, they will INSIST that they don't 'do' Linux drivers.....and will direct you instead to the Avasys website, where you find a polite notice re-directing you BACK to Epson! It's a real case of 'round the houses'...

However, once it IS set up, you should have the choice of either Image Scan for Linux, OR Simple Scan; they both ought to work.

Hope that helps.

Regards,

Mike.

BTW: I can't for the life of me understand why your CUPS interface is showing your printer as an HP... :confused:

---

### Post by Bobby_James on 2014-10-16
I am officially deluded. I do not have an Epson 2540. I have a HP Deskjet 2540.

But: I installed the Epson drivers from USC. And they worked??? Does this make any sense?

---

### Post by Mike_Walsh on 2014-10-16
Nope! NO sense at all...

I've often thought printers are a bit like 'black magic'. They're the one part of any sytem (with perhaps the exception of the hard drive (more 'black magic'!)), which converts software commands into physical movement.....and thus are necessarily way more complex than many other parts of your system.

Having said that, I can't imagine I'm the ONLY person who wishes for a nice, straight-forward ROTARY volume control on the external case of my 'puter...! :D

Regards,

Mike.

---

### Post by JeQhdMD on 2014-10-16
I believe many aspects of CUPS are common to multiple MFP brands . . . but I have to admit this is one of the "strangest" threads I've ever seen on these forums.   Linux MUST be making progress . .  if you can get hardware to work even when installing the competitors drivers . . . . who'd a thunk??? :?::?:shock::shock::shock:

---

### Post by Bobby_James on 2014-10-29
> **sammiev said:**
> I notice a lot of ppa's in your source list but that's another thing for a different day.

Could you please elaborate on this issue, thanks?

---

### Post by sammiev on 2014-10-29
> **Bobby_James said:**
> Could you please elaborate on this issue, thanks?

I thought JeQhdMD was the op and I was surprised to see so many 3rd party ppa.

You did not post yours and if you do not install 3rd party ppa's your likely good. 3rd party ppa's from untrusted sites may let a hacker into your computer.

---

