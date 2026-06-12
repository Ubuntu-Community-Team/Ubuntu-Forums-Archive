---
title: "Canon MX920 won't print; When it does, part of the page is missing."
date: 2018-01-13
forum: Hardware
---

### Post by garrukapex on 2018-01-13
So, I'm loving linux so far. My biggest issue is with my printer, a Canon MX920 Series. The default drivers worked a little, but the printer was... selective with what part of the page it would print. It would normally leave off the first 2-3 inches at the top of the page as white, and then the bottom of the page wouldn't be printed. 

Now, I've been playing with it a bit, trying different drivers to try and get it to work. I've tried the Canon Asia ubuntu driver, to no avail. 
I currently have 3 options:
MX920 series Ver.3.90 ()
MX920 series Ver.3.90 ()
MX920 series, driverless, cups-filters 1.17.9 (en)

That's not a typo, I have the same driver twice for some reason. Now, one printer says it is perpetually in use, but can be accessed by other devices. I've been printing off of my iphone for the past few weeks, but I'm really getting tired of not being able to use my laptop for printing. Let me know if you need any other information. I've been struggling with this since I started using Kubuntu 17.10 about a month ago, and would really like my printer to work. 

Thanks for the help. I really appreciate what you guys do, and any and all help means a lot. 
Thanks.

---

### Post by pdc on 2018-01-13
so if I were installing a driver for the MX920series, I would go here [http://support-asia.canon-asia.com/?personal](http://support-asia.canon-asia.com/?personal) to the Canon Asia site; then navigate to the MX920series and that would take me to here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100517002.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100517002.html) and I would click to download and SAVE what will be [COLOR="#0000FF"]cnijfilter-mx920series-3.90-1-deb.tar.gz[/COLOR]

Then I would open a terminal ...... holding down the control and alt and t buttons together .......... and I would rehearse how to paste into the terminal .... which is right-click at the flashing text prompt ....... and look for PASTE in the menu that appears ......

OK: then one would copy each line of text below; line by line; paste it into the terminal; hit the ENTER key then proceed to the next line so the commands are

```
cd Downloads
```
```
tar -zxvf cnijfilter-mx920series-3.90-1-deb.tar.gz
```
```
cd cnijfilter-mx920series-3.90-1-deb
```

then we run the install script; it will 1) install the drivers and 2) register the printer with lpadmin 

```
sudo ./install.sh
```      and watch the terminal as it runs as it may ask questions 

__________

If you read through the above, and want to give it a go; I would suggest deleting all existing entries in the PRINTERS folder .......... as you say none work ....... and thus start with a clean script 

_______

if whilst reading all this through; before you start the above, ............ if you do ```
cd Downloads
``` and then ```
ls
``` ........ the [COLOR="#FF0000"]ls[/COLOR] command asks the computer to **LIST** what is in the Downloads directory; if either [COLOR="#0000FF"]cnijfilter-mx920series-3.90-1-deb.tar.gz [/COLOR]or [COLOR="#0000FF"]cnijfilter-mx920series-3.90-1-deb[/COLOR] are sitting there, then you can start the sequence from there .. does that make sense?

_________________________
Gosh, aren't things complicated ......... your reference to driverless > MX920 series, driverless, cups-filters 1.17.9 (en) made me think that the MX920 was airprint-compatible [https://support.apple.com/en-nz/HT201311](https://support.apple.com/en-nz/HT201311) and when I check, the 922 to the 928 inclusive are airprint-compatible; which I understand means ...... no driver install is needed ........... airprint does it all for you ....... but if the airprint site is exactly right, then the 920 is NOT compatible; so *maybe* why it does not work .......... I am assuming you tried that driverless cups option ..... am I right?

---

### Post by garrukapex on 2018-01-13
I have tried the driverless, and it didn't work all that well. The printer is airprint compatible. 

Also, I've already tried the drivers from the canon asia site, which is why I think I have two sets of the 3.9 version driver installed. That one doesn't work any better than the one that got installed when I installed the drivers for the first time. Would you happen to have any other suggestions? 

Also, how would I clear out the printers folder? Where is it located exactly?

---

### Post by pdc on 2018-01-14
If you use the Search function on your Desktop; it should find the Printers folder for you; 

So you have looked at the Canon drivers; the open-source Gutenprint is also available; 

If you choose an existing icon in your Printers folder; Right-click on it; look in Properties for MAKE & MODEL and drag the window to the right to enlarge it; click on CHANGE; pause while the database searches; select CANON from the options; then search through for MX920 (as per the enclosed thumbnail); select that; see how it goes

---

### Post by garrukapex on 2018-01-14
First off, I can't seem to find the printers folder. Could you give a specific folder location (like /usr/bin/~) I'm trying the gutenprint drivers, but like all my other drivers, the printer is not responding. Do you know of any case where it just says "in use" and nothing happens? This seems to happen to every driver I try, which makes me think it might be an ubuntu problem and not a printer problem. 

I also have a second printer. It's a Dell 1355. This worked initially over usb, but now also says "In use" indefinitely both over usb and over the network. I'm beyond confused. 

Thanks for all your help.

---

### Post by pdc on 2018-01-14
> I also have a second printer. It's a Dell 1355.      ........ I wonder if that is an ahhhhhhhhh moment ....... wondering if the Dell is usb connected also ? ...... I ask because linux calls the first-born lp0 (ie lpzero) and second-born is lp1 ........ so one needs to power up the first-born first of all each time; and then the second-born after ........... otherwise the system assumes that the first printer to power up .......... is the first-born 

do you have what used to be called DASH ...... the search function on the Ubuntu desktop ............ type printers in that and it should ........ find you the folder ........ I see you have kubuntu .. do you have an admin folder .. could it be lurking in there????  ........

____________

can you run this command in a terminal please; and paste the result back here; ```
/usr/sbin/lpinfo -v
```       and with both printers turned on, ```
lsusb
```

__________

when you "register" a printer, the command is ```
sudo /usr/sbin/lpadmin -p [Printer Name] -P [PPD file path] -v usb:// [device &#65350;ile path] -E
```            so that might be ```
sudo /usr/sbin/lpadmin -p MX920 -P [PPD file path] -v lp0 -E
```  so you can see the system relies on the lp0 or lp1 designation that one gives it ........ this last section is just an attempt to illustrate ...... don't!! copy and attempt to paste it at all !!

______________________-

I wonder if all your cups files are installed . ...... if I do```
dpkg -l cups*
```

then I get > ii  cups                                                  2.1.3-4ubuntu0.3                amd64                           Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                                          1.8.3-2ubuntu3.1                amd64                           OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                              2.1.3-4ubuntu0.3                amd64                           Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                           2.1.3-4ubuntu0.3                amd64                           Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                           2.1.3-4ubuntu0.3                all                             Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                                     2.1.3-4ubuntu0.3                amd64                           Common UNIX Printing System(tm) - PPD-less printing
ii  cups-daemon                                           2.1.3-4ubuntu0.3                amd64                           Common UNIX Printing System(tm) - daemon
ii  cups-filters                                          1.8.3-2ubuntu3.1                amd64                           OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                             1.8.3-2ubuntu3.1                amd64                           OpenPrinting CUPS Filters - PPD-less printing


do you get similar?

---

### Post by garrukapex on 2018-01-14
I don't connect to the canon over usb, so lsusb won't help us there. The output when I connect to the dell is :

...a bunch of stuff...
Bus 001 Device 009: ID 413c:5406 Dell Computer Corp.


The output of /usr/sbin/lipinfo -v is :

```
[FONT=monospace][COLOR=#000000]network http[/COLOR]
network ipps
network https
network ipp
network lpd
network socket
file cups-pdf:/
network beh
file cups-brf:/
direct hp
direct hpfax
network dnssd://Canon%20MX920%20series._ipp._tcp.local/?uuid=00000000-0000-1000-8000-60128B90895C
network dnssd://Dell%201355cnw%20Color%20MFP%20%40%20Name%E2%80%99s%20iMac._ipp._tcp.local/cups?uuid=ded18e23-0487-3532-46dc-f04c941289be
network dnssd://Dell%201355cnw%20Color%20MFP%20Fax%20%40%20NAME%E2%80%99s%20iMac._ipp._tcp.local/cups?uuid=677b09ed-28b8-34d9-731e-ec5707dbe61f
network ipp://90895C000000.local:631/ipp/print
network cnijnet:/60-12-8B-90-89-5C

[/FONT]
```

Thanks.

---

### Post by garrukapex on 2018-01-14
So I switched to the gutenprint drivers, and then I restarted the printer. That seemed to solve my problem with the Canon Printer. I'd still love to have your help with the Dell, but I'm going to mark this thread as solved because my original issue is solved at this point. It just created another issue that is not yet solved. Thanks for all your help. 

We can use the same thread though, as it is still very related to the issue I originally had.

---

