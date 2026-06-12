---
title: "set up epson wp-4020 printer"
date: 2014-12-17
forum: Hardware
---

### Post by Mike_Alt on 2014-12-17
I am a newbie to Ubuntu and recently bought the printer listed above. The version is 14.04 LTS.

I tried to install using the GUI system setting icon for printers but was not successful in finding the correct driver - when I tried to print a test page all the device did was to eject all the paper in the tray without printing any characters or graphics.

I looked at the epson web site ([www.epson.com](www.epson.com)) but didn't see any support for Linux. Any suggestions would be appreciated other than buy another printer.

Printer description; inkjet, 4 color (bk, y, m, c), 2 paper sources (3rd optional), able to double side print without handling paper.

Thanks.

---

### Post by ajgreeny on 2014-12-17
Try the epson download site at [http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

---

### Post by sammiev on 2014-12-17
> **ajgreeny said:**
> Try the epson download site at [http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

+1 but you may want to get rid of the others you first.

---

### Post by pdc on 2014-12-19
so Mike you need to know if you have a 32bit (or 64bit) system; as Epson make both; 

you need a debian package so from here [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19445&DSCCHK=f19be7033a2aa451249ee62d3c088d4cb5985f47](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=19445&DSCCHK=f19be7033a2aa451249ee62d3c088d4cb5985f47)

you need either the [COLOR="#2F4F4F"]epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb[/COLOR] or the [COLOR="#2F4F4F"]epson-inkjet-printer-201113w_1.0.2-1lsb3.2_amd64.deb[/COLOR]

---

### Post by Mike_Alt on 2014-12-20
Thanks people.

I downloaded 'epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb' for a 32 bit system.

All I have to do is figure out how to install it. If anyone is willing to provide plain language instructions on how to install - that's great.

---

### Post by pdc on 2014-12-20
well if it is saved in your Downloads directory; (where downloaded files end up by default)

then from a terminal (hit the control and alt and t keys together to open the terminal) ........the commands to **copy** from here and **paste** into the terminal are

[COLOR="#FF0000"]cd Downloads[/COLOR] (hit the ENTER key)

[COLOR="#FF0000"]sudo dpkg -i epson-inkjet-printer-201113w_1.0.2-1lsb3.2_i386.deb[/COLOR]  (hit the ENTER key)

................use your mouse and the menu at the top of the terminal to do the pasting .................

_________________________

or right-click from the GUI and select "install with gdebi installer" or Ubuntu software centre or whatever option is offered ..................

---

### Post by Mike_Alt on 2014-12-23
Well the epson supplied driver doesn't work - all that happens when attempting to print is output blank pages (no characters or graphics). I contacted epson and was told they don't support linux drivers:(  Also when configuring the driver the 'test page button' is greyed out and the 2-sided checkbox is greyed out.

what are my options to resolve this?

As a FYI the printer works fine with windows xp sp3 (i'm trying to switch to ubuntu).

---

### Post by Mike_Walsh on 2014-12-23
Hallo, Mike.

I see you were told the exact same thing that I was by the Customer Service people at Epson! They insist they 'don't do Linux drivers', and will usually refer you onto Avasys, a Japanese company who used to develop the Linux printers for them. 

What they don't tell you, is that 2 years ago, Avavsys shut up shop, and passed responsibility for the repositories back to Epson.....but Epson will still insist that they 'don't do Linux drivers'..... Epson don't make life easy for Linux users!

I was going to refer you to openprinting.org, but I see that their driver for the WP-4020 is the same as that recommended by pdc in post#4, so..... If you still can't install your printer by the usual methods, then I don't really know what to suggest.

The only other way you COULD do it, which is a wee bit cumbersome, is to go into your browser, enter 'localhost:631', and this will take you to the CUPS (Common Unix Printing System) web interface itself, and attempt to install your printer direct from here. All 'buntu -based distros, and in fact most Linux distros, DO use CUPS, but you don't normally see it.....it's hidden from you, in the interests of simplifying matters. However, you still need to have the 'driver' (it's actually a filter program for CUPS) installed on the system before you try this step.

The Puppy Linux distros are about the only ones I know of that use CUPS directly.

Regards,

Mike. ;)

BTW: Unfortunately, it's no use complaining to Epson about the fact that their supplied 'driver' for Linux won't work, as Linux is such a small part of their business, still. As I understand it, ANY printer will work with ANY Linux distro, so long as you have a 'filter' program (or 'driver') that will allow your hardware to work with CUPS.....but I'm willing to be corrected on this one!

---

### Post by QIII on 2014-12-23
The next time a smug Epson techie tells you they "don't do Linux", refer them [here]("http://www.linuxfoundation.org/about/members") (under "Silver Members") and let them know you are sure that upper management would be happy if you were to call to let them know that they don't support Linux.

---

### Post by Mike_Walsh on 2014-12-23
+1 !!!!! I MAY just do that...

Regards,

Mike.

Merry Xmas, QIII.....have a good one.

---

### Post by Mike_Alt on 2014-12-24
Thanks QIII for the suggestion.

I just faxed The president of Epson Americas at;

Mr. John Lang, President and Chief Executive Officer, Epson America, Inc.
Epson America, Inc.
3840 Kilroy Airport Way
Long Beach, CA 90806
(P) 562-981-3840
(F) 562-290-5220

If / when I get a response, I'll post it here.

---

### Post by sammiev on 2014-12-24
> **Mike_Alt said:**
> Thanks QIII for the suggestion.

I just faxed The president of Epson Americas at;

Mr. John Lang, President and Chief Executive Officer, Epson America, Inc.
Epson America, Inc.
3840 Kilroy Airport Way
Long Beach, CA 90806
(P) 562-981-3840
(F) 562-290-5220

If / when I get a response, I'll post it here.

+1 good one!

---

### Post by pdc on 2014-12-24
OK Mike Alt

........can we see how the driver install went please? If you can copy this command ```
dpkg -l | grep epson-inkjet-printer
```   ........please copy as it contains the pipe symbol .........and if you could paste it into a terminal; (control alt t) [http://www.howtogeek.com/howto/22283/four-ways-to-get-instant-access-to-a-terminal-in-linux/](http://www.howtogeek.com/howto/22283/four-ways-to-get-instant-access-to-a-terminal-in-linux/)            easiest to use your mouse and the top line of the terminal? ........................   the paste shortcut is three simultaneous keys: control and shift and p 

if you could copy any results you get please; and post them back here; and if you get no result please tell us that;

could you also click on this link [http://localhost:631/printers/](http://localhost:631/printers/) which opens CUPS for your system: printer admin; and tell us what is in Column 4 entitled: Make and Model: you may be able to select it all and paste it back here; 

just feel it could be helpful to clarify if the Epson driver installed ok for you;

---

### Post by Mike_Alt on 2014-12-25
PDC, Thanks for the additional checks.

The results:

From the code "dpkg -l | grep epson-inkjet-printer" - my results  ii  epson-inkjet-printer-201113w                          1.0.2-1lsb3.2                                       i386         EPSON WP-4015/4525 Series - Epson Inkjet Printer Driver

From "http://localhost:631/printers/" - my results  
Queue Name,                Description,                     Location,       Make and Model,                                                     Status
EPSON-WP-4020-Series  EPSON WP-4020 Series   mike-ubuntu      Epson WorkForce 40 - CUPS+Gutenprint v5.2.10-pre2     Idle

i included all from localhost.

I believe what these results mean is that driver installed correctly - let me know if I'm off-base.

---

### Post by pdc on 2014-12-25
yes, it appears the driver is correctly installed; 

but then one must make a registry entry telling the computer: for an entry that one could call: MY_EPSON ...........please use the Epson drivers;  ([COLOR="#EE82EE"]epson-inkjet-printer-201113w 1.0.2-1lsb3.2 i386[/COLOR])

.................in contrast one could create another entry called MIKE's_EPSON and you could tell it to use the [COLOR="#FFA07A"]gutenprint[/COLOR] (Open Source) driver; ................as you have in this case ..................................

__________________________

have a look at that column 4: the Epson setting you are using; has used the [COLOR="#FFA07A"]gutenprint[/COLOR] Open Source driver; [http://gimp-print.sourceforge.net/](http://gimp-print.sourceforge.net/)

............ so possibly unfair to blame Epson; when you are not actually pointing your computer at the Epson driver?

_________________________

If you paste the command ```
system-config-printer
``` into a terminal ........... you seem very fluent at that .............. it opens a GUI box; I would suggest deleting the existing entry; (or renaming it something like [COLOR="#0000FF"]Epson_Gutenprint[/COLOR] so you can recognise it ...)

and there should be an [COLOR="#0000FF"]ADD A NEW PRINTER[/COLOR] button top left; it you get that going, it should then look to see what is available; our 410 Epson uses the EPSON_XP-410.ppd file and I see it is in [COLOR="#008000"]/etc/cups/ppd[/COLOR] so the install may well have put yours in a similar folder; you can usually point the GUI that is creating a printer entry to a ppd if it is slow to find the epson drivers .................

.........is this enough to be getting on with?

---

### Post by Mike_Alt on 2014-12-27
Hi pdc,

i appreciate your help but I am unaware of Linux having a registry - how do I access it.

"system-config-printer" entered into a terminal opens printers-localhost and clicking on 'add'open  anoither window with a list of printers - see 'add-printer-select'.

After getting 'printers-local host', turned on device and additional info appeared in the terminal see 'termail-screenshot.png'

---

### Post by pdc on 2014-12-27
"i appreciate your help but I am unaware of Linux having a registry - how do I access it."

what I meant was > Register the printer to the spooler eg when Canon advise how to register a LAN connection for one of their printers, the lpadmin format is > /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v cnijnet:/[MAC_address] -E

........cnijet pertains only to Canon ................but just showing this is one step on from installing the printer drivers ..................

so they say if" the MAC address is "00:00:85:AB:C1:23" and if you specify "MG3100LAN" as the [printer_name]:"

then > sudo /usr/sbin/lpadmin -p MG3100LAN -m canonmg3100.ppd -v cnijnet:/00-00-85-AB-C1-23 -E

________________

often the install scripts that automate the installs; do this; the Canon ones do .....

-_______________________________

......... beyond that, I could only google on the error messages you are getting on your terminal; to try to make head or tail of them;

---

### Post by Mike_Alt on 2015-01-10
Hi people,

I finally got back to work on this - SUCCESS! The printer seems to work - judging by printing a test page and printing as double sided 2 pages from a large document.

I found additional information  [http://www.linuxfoundation.org/collaborate/workgroups/openprinting](http://www.linuxfoundation.org/collaborate/workgroups/openprinting) and 
[https://wiki.linuxfoundation.org/index.php?title=OpenPrinting/Database/DriverPackages&oldid=23386](https://wiki.linuxfoundation.org/index.php?title=OpenPrinting/Database/DriverPackages&oldid=23386)

1st I installed lsb 3.2 using the command from epson [http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule) , clicked download for the more recent driver, clicked accept, and entered [Ubunbu]:
# apt-get install lsb into a terminal window. Then installed epson-inkjet-printer-escpr_1.4.4-1lsb3.2_i386.deb - see term-results-ok.doc for commands entered and results in terminal window.

---

### Post by pdc on 2015-01-10
well done Mike; enjoy!

---

