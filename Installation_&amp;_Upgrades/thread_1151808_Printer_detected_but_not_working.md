---
title: "Printer detected but not working"
date: 2009-05-07
forum: Installation &amp; Upgrades
---

### Post by Jayhawker on 2009-05-07
Once plugged in a HP Laserjet 1018, drivers have been downloaded and apparently all was ready to work, but when ordering to print, and after an instruction saying print was in process, another instruction says job is done, but no sheet is printed.

How to solve this problem, please?  :(

---

### Post by wpshooter on 2009-05-07
Did you find the drivers for your Laserjet 1018 included in the Ubuntu O/S or did you download them from somewhere else ?

My suggestion would be to use the drivers that are included in Ubuntu, if there are any, and my "guess" would be that there is.

---

### Post by Jayhawker on 2009-05-07
> **wpshooter said:**
> Did you find the drivers for your Laserjet 1018 included in the Ubuntu O/S or did you download them from somewhere else ?

My suggestion would be to use the drivers that are included in Ubuntu, if there are any, and my "guess" would be that there is.

As soon as I've plugged in the printer, Ubuntu's drivers downloaded themselves. That's why I'm amazed. Any suggestion?   :)

---

### Post by wpshooter on 2009-05-07
> **Jayhawker said:**
> As soon as I've plugged in the printer, Ubuntu's drivers downloaded themselves. That's why I'm amazed. Any suggestion? Maybe when saying where printer's location is (name of computer) there is something wrong?  :)

Are you simply saying that Ubuntu detected the presence of the printer ?  If so, I don't think that necessarily means that the drivers for it have been installed.  You have to go thru the printer setup routine (somewhat similar to M/S windows) and choose how your printer is connected, brand & model of printer from listing and and then choose the proper driver from those in the listing to be associated with/driver for your printer - are you doing all of that ?

---

### Post by shababhsiddique on 2009-05-07
I also have same type of problem not yet fixed..

Do you have any websites who provide such drivers for free will be useful.
Does your error looks somewhat ?-
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112817&stc=1&d=1241717535[/IMG]

---

### Post by Jayhawker on 2009-05-07
> **shababhsiddique said:**
> I also have same type of problem not yet fixed..

Do you have any websites who provide such drivers for free will be useful.
Does your error looks somewhat ?-
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=112817&stc=1&d=1241717535[/IMG]

No. This is not the indication I get. Mine says that print has been done successfully, which is not correct.

---

### Post by Jayhawker on 2009-05-07
> **wpshooter said:**
> Are you simply saying that Ubuntu detected the presence of the printer ?  If so, I don't think that necessarily means that the drivers for it have been installed.  You have to go thru the printer setup routine (somewhat similar to M/S windows) and choose how your printer is connected, brand & model of printer from listing and and then choose the proper driver from those in the listing to be associated with/driver for your printer - are you doing all of that ?

Where can I find brand and model's list? Not easy to find it.
Thank You :(

---

### Post by wpshooter on 2009-05-08
> **Jayhawker said:**
> Where can I find brand and model's list? Not easy to find it.
Thank You :(

I am doing this from memory, but I think it is under SYSTEM/ADMINISTRATION/PRINTER SETUP menu.

When you get into the printer setup menu, then click on add new printer.

---

### Post by staar2 on 2009-05-09
Actually i got same printer and same problem, I have searched many topics and many forums, but i haven't reached to answer. All time i get message printer hp laserjet 1018 may not be connected. Currently i got installed drivers through hp-lib, if i don't get the printer working, ill have to reinstall ubuntu. 
:(
Got this in log
> May  9 18:37:17 ufo-desktop kernel: [  937.380123] usb 1-2: usbfs: USBDEVFS_CONTROL failed cmd hpijs rqt 161 rq 1 len 1 ret -110

also when run lsusb get this
> 
Bus 001 Device 006: ID 03f0:4117 Hewlett-Packard Printing Support <---- Seems like printer is connected.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 045e:00dd Microsoft Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 04e6:5116 SCM Microsystems, Inc. SCR331-LC1 SmartCard Reader
Bus 002 Device 002: ID 04a9:220d Canon, Inc. CanoScan N670U/N676U/LiDE 20
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub



---

### Post by VastOne on 2009-05-09
Having these same issues with a Ubuntu installed USB Brother MFC-8460N

It worked initially, but now all I get is the printer is apparently not connected messages

VastOne

---

### Post by todak on 2009-05-09
You need a specific driver to make it run. See [here]("http://foo2zjs.rkkda.com/"). According to the website, you must follow the install instructions to the letter.

---

### Post by staar2 on 2009-05-09
Now i tryed with foomatics drivers and i printed 1 page out after restart i get same message. This is big bug fix this.

---

### Post by staar2 on 2009-05-10
As i have read the previous post in this forum with similar problem and i haven't seen the answer for this. Has anyone got the printer work normal ? All these similar topics end with giving up.

---

### Post by todak on 2009-05-10
Have you looked at this page?: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/) You must follow the instructions on that page to get it to work. Quoting from the page: *** [B][COLOR="Red"]DON'T USE the foo2zjs package from:
     	Ubuntu, SUSE, Mandrake/Manrivia, Debian, RedHat, Fedora, Gentoo, Xandros, EEE PC, Linpus, MacOSX, or BSD!
*** Download it here and follow the directions below.[/COLOR][/B]

---

### Post by staar2 on 2009-05-12
Wow, superb i got printing to work, only with small problems, no resume when paper*s is out also when printer is not working and you press printer it stucks.

---

### Post by IronArjen on 2009-06-04
This is a problem of the printer that not empties correctly its memory. For this you have to go to windows, no other option.

---

### Post by staar2 on 2009-07-08
What about any manual commands or is there something what could be programmed ?

---

### Post by justloser on 2009-07-10
Would it work if you turned the printer off when not you were not using it? That way any buffer would be clear when you powered it on to print.

Just a thought

---

### Post by staar2 on 2009-07-13
> **justloser said:**
> Would it work if you turned the printer off when not you were not using it? That way any buffer would be clear when you powered it on to print.0
Just a thought 
This trick has been working ill turn printer off and then on again, start printer in CUPS. It's not best solution, so i am looking for some code for to it automaticly, bash, c++ ?

---

### Post by Whydoe on 2009-07-26
I've had similar problems with my HP 1018.  Works fine one day, then I reboot and it seems to have a problem finding the printer on USB port.  When I do: lsusb it takes a long time and printer is not found.  I got it working, but I don't konw how I got it working.  May be possible that USB cable was wrapped around to many other cables?  Seems to work now.  However, I still had issue with the test page sending the request and then saying it's complete without anything being printed.  The only way I've got it to work is to use the hpijs 3.9.2 driver (not foos) and to open terminal and type hp-setup.  Follow instructions to download plugin for printer and bingo.  My file was hplip-3.9.2-plugin.run.  May be different for other HP laserjets, don't know.  Should be in /usr/share/hplip/data/plugin.  Hope that helps, I'm still working out bugs with mine.

---

### Post by LinuxBob on 2009-08-16
I have had this problem on one of three Ubuntu machines and posted this in the General forum here:

 Do not update to latest CUPS!!!

I have been trying all week to get my HP LaserJet 4L connected on my LAN via a DLink DP-301+ printer server set up for my three Ubuntu machines. I can only get it working with two of them 1) a Dell 1505n ubuntu 7.04 Fiesty and 2) an older HP on which I loaded tonight Ubuntu 9.04 but on which I installed all available upgrades EXCEPT anything CUPS-related. I stuck with the CUPS packages in the download iso of 9.04.

My newest desktop is a Zareason ION Breeze on which Zareason installed Ubuntu and which has a notably different System > Administration > Printing interface, so I assume this reflects installation of the latest & "greatest" (Not) CUPS. I can install the printer the same as with the other machines using localhost:631 CUPS web interface but when I try to print a test page Ubuntu reports the job completes yet nothing prints and the data light on the printer never lights up.

Anyone know how to either 1) add this printer using the updated latest CUPS packages, or 2) how can I revert CUPS back to the packages in the latest Ubuntu ISO file ubuntu-9.04-desktop-i386.iso.

---

### Post by LinuxBob on 2009-08-18
The network printing problem is solved.  I bought a new all in one wireless capable printer and it worked first time with the Zareason using the localhost:631 network printer setup.  That led me to believe the Dlink printer server had a permission issue.  That was the case.

The DP-301P+ requires a mac address when the user permission feature is turned on.  The Dlink accepts a mac address with a space between the hexadecimal pair of numbers, not a colon.

---

