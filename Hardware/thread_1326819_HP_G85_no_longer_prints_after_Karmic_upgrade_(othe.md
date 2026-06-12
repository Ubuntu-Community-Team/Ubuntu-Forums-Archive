---
title: "HP G85 no longer prints after Karmic upgrade (other printer is fine)"
date: 2009-11-14
forum: Hardware
---

### Post by Digital Magi on 2009-11-14
My system has two printers, an HP OfficeJet G85 and an HP DeskJet 4280. Both worked fine in Jaunty, both would scan and print. Both are connected to my primary desktop via USB.

I did a fresh install of Karmic (saving my /home partition) on this machine.

After the install, the G85 will no longer print. It will scan images. Print jobs sent to this printer just sit in the queue forever.

If I attempt to clean heads or check ink levels I get "maintenance command submitted as job#X" but never get a result.

I get no error messages.

The 4280 has no problems, prints and scans fine, even over the network. The G85 is also visible over the network.

I have power cycled, deleted and reinstalled multiple times, both manually choosing the driver and letting ubuntu choose one for me on detection.

Current driver is hpijs, 3.9.8

Tried to manually update to the 3.9.10 drivers, but the [HP site]("http://hplipopensource.com/hplip-web/index.html") just cycles through the sourceforge mirrors without ever finding it... maybe no Karmic version up yet?

In case it helps, here is the output for tail -f /var/log/messages
during a powercycle then re-installation
```
Nov 14 19:20:41 blue kernel: [15698.568082] usb 2-2: USB disconnect, address 5
Nov 14 19:20:41 blue udev-configure-printer: Disabled printer ipp://localhost:631/printers/OfficeJet-G85 as the corresponding device was unplugged or turned off
Nov 14 19:20:49 blue kernel: [15706.372187] usb 2-2: new full speed USB device using uhci_hcd and address 6
Nov 14 19:20:49 blue kernel: [15706.555331] usb 2-2: configuration #1 chosen from 1 choice
Nov 14 19:20:49 blue kernel: [15706.563305] usblp0: USB Bidirectional printer dev 6 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0211
Nov 14 19:20:52 blue udev-configure-printer: Re-enabled printer ipp://localhost:631/printers/OfficeJet-G85
Nov 14 19:21:34 blue kernel: [15752.136086] usb 2-2: USB disconnect, address 6
Nov 14 19:21:34 blue kernel: [15752.136371] usblp0: removed
Nov 14 19:21:43 blue kernel: [15761.256053] usb 2-2: new full speed USB device using uhci_hcd and address 7
Nov 14 19:21:44 blue kernel: [15761.439333] usb 2-2: configuration #1 chosen from 1 choice
Nov 14 19:21:44 blue kernel: [15761.456284] usblp0: USB Bidirectional printer dev 7 if 0 alt 0 proto 3 vid 0x03F0 pid 0x0211

```

Thanks in advance for any help. These HP printers are normally the easiest to use with linux... I suspect it has something to do with the Cups problems we all have had. I just got network printing back working after the last Cups update.

---

### Post by Digital Magi on 2009-11-14
Did additional testing - G85 prints when connected to a Vista machine.

---

### Post by Digital Magi on 2009-11-21
still working on this. Finally was able to download HPLIP 3.9.10 and got it installed in the top panel. The G85 detected and installed with no error messages.

A little better, at least now I get ink status.

Still won't print. Jobs get sent to the printer, and Ubuntu thinks they have printed, but they don't. No paper feed or head motion at all.

Really frustrating, still no error messages.

Tried to install it on a freshly-formatted clean install of 9.10 on another laptop, same result - so I know it's not a misconfiguration of this particular machine, it's something in the 9.10 setup.

I have confirmed this printer as working from 8.04, 8.10, 9.04, XP and Vista, so it's not the printer itself.

---

### Post by francf on 2009-11-23
where you find the hplip 3.9.10?
I have the same problem.
Thanks

---

### Post by Digital Magi on 2009-11-24
[http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

---

### Post by bagl0312 on 2009-11-30
Hello,
I have the same problem with a HP G55 multifuncion printer.
I did a fresh install of karmic, printer is recognized and everything seem correctly installed, the driver is  hpijs 3.9.8.
If I print something it stays in the printer queue forever, and no error message is sent.

I tried also to change the driver (there are four possible drivers compatible with my printer in the CUPS database), but nothing works.

The same printer connected to a laptop with Jaunty is recognized automatically and works correctly.

---

### Post by AmsterdamMack on 2009-11-30
Hi,

i can confirm that there seems to be something wrong.
The HP Officejet K80 here is also not working, although perfectly recognised... :cry:

While looking at google I found this one: [http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1896463.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1896463.html)

So I guess we have to wait and try later again :popcorn:

McMack

---

### Post by lessmemorelove on 2010-01-18
i have a g55 that also quit working in karmic. any further ideas on this front?

---

### Post by gari on 2010-01-19
I also confirm the problem with my OfficeJet G85, that was on the other hand perfectly working before on Ubuntu 8.04 8.10 9.04 ....
This is a really really anoying bug !!!
Hope that it will be solved soon !!

---

### Post by lessmemorelove on 2010-01-19
ok. installed all the cups, foomatic (except foomatic-gui), and hplip / hpijs entries in synaptic. then i installed the printer. then i ran "sudo hp-plugin -i" to install the hp driver and rebooted. i checked to be sure i was in the lpadmin and saned user groups and after reboot i turned off the printer and turned it back on and ubuntu "magically" installed it in the printers as a second entry. now it works. as far as i can tell every time i reboot my computer i have to turn off then on the printer. it adds another entry but at least i can print and scan with it now.

edit: this is for my g55 using hplip 3.9.8

---

### Post by specialcowboy on 2010-01-21
> **Digital Magi said:**
> [http://hplipopensource.com/hplip-web/index.html](http://hplipopensource.com/hplip-web/index.html)

I was having the same problems: Officejet G85 worked fine on 9.04 Jaunty but stopped working on 9.10 Karmic. Ubuntu detected the printer and jobs could be sent which were reported as having printed but nothing was happening on the printer.

 I went to the website above and input the information for the Officejet G85. It took me to a page to download HPLIP 3.9.12 (Karmic was using 3.9.8 ) even though HP's site said that the printer should work with HPLIP 3.9.8 I thought it couldn't hurt to update the drivers and software. I followed all of the instructions on HP's page and now the Officejet G85 is working just fine under Karmic. Hope this helps others having the same problem.

---

### Post by Digital Magi on 2010-01-23
I had given up on this until I saw the new replies. Turns out that the 3.9.12 driver update has fixed the problem (whatever it was).

All working fine now. Thanks for the help, folks!

---

### Post by De Mille on 2010-01-24
I still have the same problem and after setting up the new driver.
During setup I chose to unplug and replug the printer. In the setup window there was no printer to select.
Than I restarted the system with the printer ON. Did HP setup in the Terminal and now I had a printer to selct and setup was completed. Now I have a bleu HP icon in my system tray to start the device manager The printer is recognized and I can even read the inkt content. But the printer still don't print a test page.
Xsane does not start up and error code " can not find device. Device is occupied"
Wat can I do?
In 9.04 everything worked fine, how can I go back to 9.04?

---

### Post by De Mille on 2010-01-26
For me the thread is NOT SOLVED. See my thread.
After installation 3.9.12 I have two icons, one printer and one bleu HP icon. Switching the printer ON, the printer is detected but when I want to print a test page I get the warning that the printer is probably not connected. What did I do wrong?

> **specialcowboy said:**
> I was having the same problems: Officejet G85 worked fine on 9.04 Jaunty but stopped working on 9.10 Karmic. Ubuntu detected the printer and jobs could be sent which were reported as having printed but nothing was happening on the printer.

 I went to the website above and input the information for the Officejet G85. It took me to a page to download HPLIP 3.9.12 (Karmic was using 3.9.8 ) even though HP's site said that the printer should work with HPLIP 3.9.8 I thought it couldn't hurt to update the drivers and software. I followed all of the instructions on HP's page and now the Officejet G85 is working just fine under Karmic. Hope this helps others having the same problem.

---

### Post by specialcowboy on 2010-02-08
Sorry to hear that it's not working for you.  I also have two icons: one for the printer and one blue HP icon.  I believe that this is normal behavior. Can anyone else confirm this? The blue HP icon is the HP device manager and the print icon is the print administration GUI. (If I'm not mistaken I seem to remember a similar setup on an old Apple PowerBook I had years ago with an HP printer installed.) So I didn't consider this to mean that there was a problem with the install or setup of the newer HPLIP.

Where did you go to print your test page? The blue HP icon or the Printer Administrator (under the System menu -> Printing or using the HP device manager?) I printed my test page using System -> Printing, right-clicking on the OfficeJet-G85, selecting Properties and the clicking on Print Test Page. I also tried using the blue HP icon and using the "Print Test Page option from the main window. Both worked for me.

On closer inspection I have also noticed that I have to printer icons in the Print Administration tool, one is OfficeJet_G85 (notice the underscore) and the other is OfficeJet-G85 (notice the hyphen). Is this the case for you as well?

In any case, when I want to print from an app (like openoffice) I use the one with the hyphen in the printer name. The printer with the underscore produces the error message you mentioned. However, when I am trying to scan it seems that the printer with the underscore in the name works.

I'm sure this sounds a little "half-baked" but I've been able to print documents and scan using Xsane this way.  I'm not sure why there are two printers listed. Can anyone else share their experiences and and comment on whether or not they have two printers listed in the printer administrator?

> **De Mille said:**
> For me the thread is NOT SOLVED. See my thread.
After installation 3.9.12 I have two icons, one printer and one bleu HP icon. Switching the printer ON, the printer is detected but when I want to print a test page I get the warning that the printer is probably not connected. What did I do wrong?

---

### Post by De Mille on 2010-03-04
When I select print from a document the printer do not work. When selecting the Hp icon opening the hp manager and than search for the document and select it , than the printer works. This is not satisfacory.
I made a new installation of 9.10 on ext4 and now i have no printer icon any more. When I print from a document, the icon appeares for a moment. The printer DO NOT print. The printer manager gives task completed;
I tried to install hplip-3.10.2 but during installation with the terminal an error code: error: Package install command failed with error code 255. Installation not possible.
What now?




> **specialcowboy said:**
> Sorry to hear that it's not working for you.  I also have two icons: one for the printer and one blue HP icon.  I believe that this is normal behavior. Can anyone else confirm this? The blue HP icon is the HP device manager and the print icon is the print administration GUI. (If I'm not mistaken I seem to remember a similar setup on an old Apple PowerBook I had years ago with an HP printer installed.) So I didn't consider this to mean that there was a problem with the install or setup of the newer HPLIP.

Where did you go to print your test page? The blue HP icon or the Printer Administrator (under the System menu -> Printing or using the HP device manager?) I printed my test page using System -> Printing, right-clicking on the OfficeJet-G85, selecting Properties and the clicking on Print Test Page. I also tried using the blue HP icon and using the "Print Test Page option from the main window. Both worked for me.

On closer inspection I have also noticed that I have to printer icons in the Print Administration tool, one is OfficeJet_G85 (notice the underscore) and the other is OfficeJet-G85 (notice the hyphen). Is this the case for you as well?

In any case, when I want to print from an app (like openoffice) I use the one with the hyphen in the printer name. The printer with the underscore produces the error message you mentioned. However, when I am trying to scan it seems that the printer with the underscore in the name works.

I'm sure this sounds a little "half-baked" but I've been able to print documents and scan using Xsane this way.  I'm not sure why there are two printers listed. Can anyone else share their experiences and and comment on whether or not they have two printers listed in the printer administrator?

---

### Post by specialcowboy on 2010-03-14
Again, I am sorry to hear that you are still having issues. I know how frustrating that can be.  I am certainly no expert but would like to help as much as I can.  Although your current ability to print (using the HPLIP Manager) is not satisfactory at least we know that it is possible (in general) to print from your computer to the G85.

Your post doesn't tell me enough about certain things.  So a few questions that may help myself or others in understanding and diagnosing your problems. 

When you are in a document and you want to print how many printers do you see?
OR, when you go to System/Admin/Printers how many printers are listed? As I mentioned in my previous post, I have two printer icons available from System/Admin/Printers and from within the apps. However, it seems that only one works while the other displays the behavior you described. 

This one (which works for me): OfficeJet_G85 has the following URI in the printer properties hp:/usb/OfficeJet_G85?serial=SGF0CE086JVL

This one (which does not work for me) Hewlett-Packard OfficeJet G85 (seen as OfficeJet-G85) has this URI in the printer properties usb://HP/OfficeJet%20G85?serial=SGF0CE086JVL

As you can see the two URI's above are different. I'm not sure if this means anything but you may want to check your setup to see if any of this helps you.

Are you using Gnome or KDE or something else? (I'm using Gnome)
I can't comment on using hplip 3.10.2 as I used (and am still using) version 3.9.12
What app or apps are you trying to print from that aren't working?
How is the printer connected? (parallel cable, USB)? Mine is USB.
Are you able to access the printer for scanning? 
I don't recall but am assuming the printer worked previously under a different OS (Windows or Linux)?
Was your system fully updated prior to attempting to install hplip 3.10.2? Can anyone else comment on the error received when trying to install?

Also, as per my previous post - any additional input from the community would be most appreciated. I am only able to share what has worked for me. Perhaps I got lucky?

> **De Mille said:**
> When I select print from a document the printer do not work. When selecting the Hp icon opening the hp manager and than search for the document and select it , than the printer works. This is not satisfacory.
I made a new installation of 9.10 on ext4 and now i have no printer icon any more. When I print from a document, the icon appeares for a moment. The printer DO NOT print. The printer manager gives task completed;
I tried to install hplip-3.10.2 but during installation with the terminal an error code: error: Package install command failed with error code 255. Installation not possible.
What now?

---

### Post by De Mille on 2010-03-23
I use gnome and the printer is connected to USB.

For me the problem is SOLVED now.
I re-installed hplip using synaptic and restarted the computer. Everything was the same. Sane works fine but the printer did not print a document ( printer not connecrted warning). Only one printer visible in printer cofiguration.
In the printer configuration window I selected NEW. I selected my printer and the program could not find it. Than I selected my printer manualy from the list of printers witch is shown and than I could choose the driver 3.9.12. Ater that I had two printers visible. I selected the last installed as standard and everything works fine now.

---

### Post by specialcowboy on 2010-04-02
I am glad to hear that your printer problems are now solved. :)

---

### Post by satyen2a on 2010-07-27
on Lucid:

cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

I installed hplip-cups like this:
[FONT="Courier New"]sudo apt-get install hplip-cups[/FONT]

Re added printer.
And now I can print.

---

