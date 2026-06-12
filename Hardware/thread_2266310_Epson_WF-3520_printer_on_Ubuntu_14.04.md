---
title: "Epson WF-3520 printer on Ubuntu 14.04"
date: 2015-02-21
forum: Hardware
---

### Post by MintPrint on 2015-02-21
Hello,

I'm tying to add my Epson WF-3520 printer in the printer settings and I'm having problems getting Ubuntu 14.04 64 bit to recognise my driver. I've installed the correct driver from the Epson website, and the printer is connected wirelessly to the network. It's even recongised on the list of printers when I try to add it. As soon as I try to continue however, the "searching for drivers" box disappears, reappears, and then I'm given a list of manufacturers and drivers.

Clearly, Ubuntu is not recognising the driver - I'm just not sure why. Any help would be appreciated.

Thank you

---

### Post by MintPrint2 on 2015-02-21
Sorry I lost my original account, I will reply with this one from now on.

---

### Post by weatherman2 on 2015-02-21
How did you attempt to install the driver?  I've never used an Epson printer in Linux.  Each manufacturer has different approaches to do it.  For Canon printers, I've had to type a terminal command (not really the most friendly way to setup a printer in 2015).  

Did you do a web search for your printer and "linux" or "ubuntu" to see if others have had experience with it?  I always do that when I get stuck on something like that.

---

### Post by MintPrint2 on 2015-02-21
I went to the Epson website, and searched for the Linux page of the WF-3520 series here (EDIT: search WF-3520 in the box):

[http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult](http://download.ebz.epson.net/dsc/search/01/search/searchModuleFromResult)

I selected the latest full feature driver, and then installed it through the software centre.

I tried but I found nothing quite like the problem I'm having. It's strange because I've got the driver, I've got Ubuntu to recognise the printer, but I can't get Ubuntu to recognise that the driver is already installed.

I've also made sure that lsb and dpkg are installed, restarted cups, did an update and upgrade. Everything seems to be in order apart from the fact that it isn't working.

---

### Post by weatherman2 on 2015-02-21
In attempting to download the generic driver given on Epson's website, I read this:

[COLOR=#333333][FONT=Tahoma][Notice][/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]In order to install these drivers, you need to install LSB package (version 3.2 or later) beforehand.[/FONT][/COLOR]

[COLOR=#333333][FONT=Tahoma]Ubunbu:[/FONT][/COLOR]
[COLOR=#333333][FONT=Tahoma]# apt-get install lsb

[/FONT][/COLOR]Did you do that?[COLOR=#333333][FONT=Tahoma]

EDIT: never mind, I see that you did.[/FONT][/COLOR]

---

### Post by pdc on 2015-02-21
hi MintPrint; sorry to hear of your problems;

if we could just check a couple of things:

if you can copy and paste these commands into a terminal; line by line; and copy and paste the results back to us here please

____________________

```
dpkg -l | grep epson-inkjet-printer
```

```
/usr/sbin/lpinfo -v
```

```
dpkg -l | grep lsb
```

---

### Post by MintPrint2 on 2015-02-22
Hi pdc,

Output for dpkg -l | grep epson-inkjet-printer

> ii  epson-inkjet-printer-201212w                          1.0.0-1lsb3.2
                                       amd64        WF-3010/WF-3520/WF-3530/WF-3540 Serie
s - Epson Inkjet Printer Driver

Output for /usr/sbin/lpinfo -v:

> network ipp
network ipps
network smb
network lpd
network socket
network http
network https
serial serial:/dev/ttyS0?baud=115200
direct parallel:/dev/lp0
network ipp14
direct hp
direct hpfax

Output for dpkg -l | grep lsb:

> ii  epson-inkjet-printer-201212w                          1.0.0-1lsb3.2                                       amd64        WF-3010/WF-3520/WF-3530/WF-3540 Series - Epson Inkjet Printer Driver
ii  lsb                                                   4.1+Debian11ubuntu6                                 all          Linux Standard Base 4.1 support package
ii  lsb-base                                              4.1+Debian11ubuntu6                                 all          Linux Standard Base 4.1 init script functionality
ii  lsb-core                                              4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 core support package
ii  lsb-cxx                                               4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 C++ support package
ii  lsb-desktop                                           4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Desktop support package
ii  lsb-graphics                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 graphics support package
ii  lsb-invalid-mta                                       4.1+Debian11ubuntu6                                 all          Linux Standard Base sendmail dummy
ii  lsb-languages                                         4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Runtime Languages package
ii  lsb-multimedia                                        4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Multimedia package
ii  lsb-printing                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Printing package
ii  lsb-release                                           4.1+Debian11ubuntu6                                 all          Linux Standard Base version reporting utility
ii  lsb-security                                          4.1+Debian11ubuntu6                                 amd64        Linux Standard Base 4.1 Security package


Should I also give you the output that is dumped in the terminal when I run system-config-printer?

---

### Post by pdc on 2015-02-22
> epson-inkjet-printer-201212w 1.0.0-1lsb3.2 amd64 WF-3010/WF-3520/WF-3530/WF-3540 Series - Epson Inkjet Printer Driver 

.........that looks fine, doesn't it?

___________________________

> Should I also give you the output that is dumped in the terminal when I run system-config-printer?  yes please

_____________________________________

> the printer is connected wirelessly to the network   

 ......... you are sure of this? 

....... you did some of this ?? [http://www.epson.co.uk/gb/en/viewcon/corporatesite/store/products/mainunits/faq/11536/1766](http://www.epson.co.uk/gb/en/viewcon/corporatesite/store/products/mainunits/faq/11536/1766)

---

### Post by MintPrint2 on 2015-02-23
Yes, the only other alternative is the 32 bit version which definitely doesn't work.

The output that is dumped in the terminal when I run system-config-printer:

> 
No ID match for device dnssd://EPSON%20WF-3520%20Series._ipp._tcp.local/:
MFG:EPSON;MDL:WF-3520 Series;CMD:URF,JPEG;
No ID match for device dnssd://EPSON%20WF-3520%20Series._ipp._tcp.local/:
MFG:EPSON;MDL:WF-3520 Series;CMD:URF,JPEG;
HTTP Status 1
(<class 'pycurl.error'>, error(51, 'gnutls_handshake() warning: The server name sent was not recognized'), <traceback object at 0x7fd8dad17830>)
[('/usr/lib/python2.7/dist-packages/cupshelpers/openprinting.py', 78, 'run', 'status = curl.perform()')]

Definitely, I added it a few times just to be sure. I printed out a network status sheet and everything looks fine. The wireless signal is at its best as well, both on the LCD screen and on the status sheet.

---

### Post by MintPrint2 on 2015-02-23
Maybe this is of interest?:
[URL="https://bugs.launchpad.net/ubuntu/+source/pycurl/+bug/1394244"]
https://bugs.launchpad.net/ubuntu/+source/pycurl/+bug/1394244[/URL]

I'm no expert, but it seems pycurl is trying to verify the printer driver from Epson, but it doesn't like it. Something to do with the gnutls package perhaps?

---

### Post by pdc on 2015-02-23
thanks; 

when it says > No ID match for device dnssd://EPSON%20WF-3520%20Series._ipp._tcp.local/: can you paste the command ```
sudo lpinfo -l -v
``` into a terminal and paste back what you get please

______________________________

you seem to be running standard 64bit 14.04 ubuntu?

---

### Post by MintPrint2 on 2015-02-23
Output for sudo lpinfo -l -v:

```
Device: uri = ipp
        class = network
        info = Internet Printing Protocol (ipp)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = ipp14
        class = network
        info = Internet Printing Protocol (ipp14)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = http
        class = network
        info = Internet Printing Protocol (http)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = lpd
        class = network
        info = LPD/LPR Host or Printer
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = socket
        class = network
        info = AppSocket/HP JetDirect
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = ipps
        class = network
        info = Internet Printing Protocol (ipps)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = https
        class = network
        info = Internet Printing Protocol (https)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = serial:/dev/ttyS0?baud=115200
        class = serial
        info = Serial Port #1
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = smb
        class = network
        info = Windows Printer via SAMBA
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = parallel:/dev/lp0
        class = direct
        info = LPT #1
        make-and-model = unknown
        device-id = 
        location = 

```

---

### Post by pdc on 2015-02-23
sorry I missed your excellent detective work on the bug in post #11; reading the bug report, 

seems like this bug was fixed and the package you need to have installed is >  system-config-printer - 1.4.3+20140219-0ubuntu2.5 ........if you check in synaptic which version you have?

__________--

the printout from ```
sudo lpinfo -l -v
``` looks seriously ......... awry ................... you seem to have pined down where the error has been occurring

---

### Post by MintPrint2 on 2015-02-24
Thanks for all your help, given how frustrating adding this printer has been I really do appreciate the assistance!

Okay I went into Synaptic and found that the system-config-printer (gnome version) was at 2.2. I updated it to 2.6 and that installed two extra python packages. I also did a sudo apt-get update and sudo apt-get upgrade, which I noticed updated cups as well. It had some effect, because now when I add the printer the GUI states that there are drivers available for download - specifically the epson-inkjet-printer amd64 one we discussed earlier.

I tried installing it, and then the "searching for drivers" box comes up again, and then a list of manufacturers comes up again.

I'd paste here what was dumped in the terminal, but the license agreement took up the whole box. From what I can see though the "No ID Match" output appeared once again.

Awry in what sense?

---

### Post by pdc on 2015-02-24
> Awry in what sense?  ..........awry .............polite for.............it doesn't seem to recognise anything whatsoever at all ........

_________________

can you run that command ```
sudo lpinfo -l -v
``` again? 

There should be a [COLOR="#0000FF"]ppd[/COLOR] folder that is in /etc/cups ...........and inside that ppd folder should be a EPSON_WF-3520.ppd             from a terminal, if you type ```
cd /etc/cups/ppd
``` and hit enter that gets you into the ppd folder and ```
ls
``` asks for a list of what is in there, and is there an Epson ppd ?

---

### Post by MintPrint2 on 2015-02-27
Sorry for the late reply pdc,

Output for sudo lpinfo -l -v:

> Device: uri = ipp
        class = network
        info = Internet Printing Protocol (ipp)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = ipps
        class = network
        info = Internet Printing Protocol (ipps)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = https
        class = network
        info = Internet Printing Protocol (https)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = ipp14
        class = network
        info = Internet Printing Protocol (ipp14)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = http
        class = network
        info = Internet Printing Protocol (http)
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = smb
        class = network
        info = Windows Printer via SAMBA
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = serial:/dev/ttyS0?baud=115200
        class = serial
        info = Serial Port #1
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = lpd
        class = network
        info = LPD/LPR Host or Printer
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = socket
        class = network
        info = AppSocket/HP JetDirect
        make-and-model = Unknown
        device-id = 
        location = 
Device: uri = dnssd://EPSON%20WF-3520%20Series._ipp._tcp.local/
        class = network
        info = EPSON WF-3520 Series
        make-and-model = EPSON EPSON WF-3520 Series
        device-id = MFG:EPSON;MDL:WF-3520 Series;CMD:URF,JPEG;
        location = 

I tried searching for the ppd with the commands you provided - there's nothing there, nothing comes up on the terminal.

On that note I noticed when I tried to add the printer manually through cups I would get a "Not Found" error when I head to the "Find printer drivers" page.

---

### Post by pdc on 2015-02-27
> I tried searching for the ppd with the commands you provided - there's nothing there, nothing comes up on the terminal.

if you use the Files box on your desktop.............. that allows you to look for files using the GUI (graphic user interface) ......... so you click on FILE SYSTEM then open the folder/directory called [COLOR="#0000FF"]etc[/COLOR] and then inside that open the [COLOR="#0000FF"]cups[/COLOR] directory; and inside that is a [COLOR="#0000FF"]ppd[/COLOR] directory: are there no files in there that are labelled .ppd ............specifically an Epson one?

_____________

there has been a recent cups update in the last day or so: if your system has taken those updates on board, I wonder if it is finding the printer yet?

____________

I have been asking about .ppd files as one can do a command line registration of a printer ......... which is what CUPS would do "behind the scenes" ..............

its format is ```
sudo  /usr/sbin/lpadmin -p [printer_name] -m [PPD_filename] -v [device-uri] -E
```

so that would be ***something like*** ```
sudo  /usr/sbin/lpadmin -p WF-3520 -m EPSON_WF-3520.ppd -v dnssd://EPSON%20WF-3520%20Series._ipp._tcp.local -E
```

---

### Post by MintPrint2 on 2015-02-28
I did a sudo apt-get update and a sudo apt-get upgrade to get cups updated, rebooted, I still can't add the printer.

Yes, I checked the directories through the GUI and there is nothing at all in the ppd folder.

Would I be correct in thinking that the dpkg for the printer I downloaded from Epson's website might be lacking its corresponding ppd?

---

### Post by Mike_Walsh on 2015-02-28
Hi, MintPrint2.

I certainly don't want to derail pdc's excellent line of trouble-shooting (a very conscientious, patient, and methodical individual....all credit to him), but there's one thing you ought to know about the Epson set-up; a 'quirk', if you like, that seems to be unique to them.

You say you've installed the the driver. OK. Via the Software Centre, or Synaptic? (Not that it matters; both will do the job just as well). You then get the 'searching for drivers' box come up, and then the list of manufacturers again? Silly question, perhaps, but have you actually followed the process through to its conclusion?

I agree, you would think that once you've installed the 'driver' (in fact, it's a 'filter'; that's what CUPS calls it), that** that** would be** that**.....but that's OK, because this is the 'quirk' I was talking about; having 'installed' it, you now need to 'add' it. If you **now** select 'Epson' in the manufacturer list, you'll get the entire list of models come up (several hundreds of them!).....you SHOULD see your model appear, together with the driver you've just installed, listed alongside it. Click on 'Add', or 'Done' (I forget which; I've not been in Ubuntu for a few weeks!) You should then get the details box, about giving the printer a name, and adding a user, etc. After this, you ought to be able to print off a test page, to verify it's all working.

Failing that, you could always install it directly, via CUPS, in the browser (simply enter 'http://localhost:631'). Don't however, use the 'Search for printers' option! Use the 'Add new printers' option instead; I've always found this to work better, for some strange reason... When you run 'Puppy' Linux as your 'other' distro (as I do), you very quickly learn **all** about CUPS. Puppy is 'lean & mean', and **very **lightweight; no extraneous or unnecessary apps AT ALL. If you want to add a printer in Puppy, you HAVE to use CUPS; there simply **is **no other option!

It's a very useful bookmark to add to your browser.

Hope that helps.


Regards,

Mike. :)

---

### Post by pdc on 2015-02-28
Hi MintPrint2

you surely need an Epson ppd file in the ppd folder.................. 

so I think you need to run the driver install again.........start from here .............. [http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX) and if you type in WF-3520 you get to [http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71](http://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=18777&DSCCHK=8f035f217059c5d9fa3cff68230cf71c41e74b71)

and you need either the epson-inkjet-printer-201212w_1.0.0-1lsb3.2_i386.deb or epson-inkjet-printer-201212w_1.0.0-1lsb3.2_amd64.deb and clicking to download the appropriate one should initiate Ubuntu software center to ask if you want it installed............that surely should generate a ppd file that you can check exists after the install is run .....................

---

### Post by MintPrint2 on 2015-03-01
Hi Mike,

Yes, I downlaoded the deb package, the amd64 one that pdc mentioned in his/her latest post. Clicking on the deb package takes me to the Software Centre and I install it from there.

I followed pdc's advice and updated the system-config-printer (gnome version) to 2.6. Now I get a page detailing that there is a driver available for download. I find this weird that it would say that but like you said I followed the process anyway, then I get a "searching for drivers" box again with a list of manufacturers. Nowhere in the Epson or Seiko sections do I see a driver for the WF-3520. Other Workforce printers are there, but nothing for the 3520.

I think I will do a series of screenshots to show what I mean - first though I want to ask pdc something...

---

### Post by MintPrint2 on 2015-03-01
Hi pdc,

Sure, no problem - it'll have to be the amd64 one because the 32 bit one I know from previous experience throws up an error.

Before I do that should I use the purge command to remove the driver I have installed now? That's what I always used to do with dpkg's.

---

### Post by pdc on 2015-03-02
> it'll have to be the amd64 one because the 32 bit one I know from previous experience throws up an error.

.............. you need to use the right one appropriate for your system.................. is yours a 64bit ubuntu install?

_________

I confess these posts are so long now I need to go back and see what it is all about; ..............I have seen threads like this where the operator gets fed up; installs things anew; and magically reports all is well ............. this is just me musing ................

what does ```
dpkg -l | grep cups
``` give please?

---

### Post by Mike_Walsh on 2015-03-04
Hi again, MintPrint2.

I find this curious, actually. You say that nowhere does it show a driver (or 'filter') for your machine? From my research, you actually want the same driver that I use myself.....and I've used this same driver on many, many distros, during my 'distro-hopping' days.

Do this experiment for me, would you? 

Go to the Epson Download page ([http://download.ebz.epson.net/dsc/search/01/search/searchModule](http://download.ebz.epson.net/dsc/search/01/search/searchModule)), and type in 'Stylus SX218' (this is MY printer), 'Linux', and hit the search button. The next page shows three options. Select the middle option, the 1.4.5 ESCP/R generic driver (I know this isn't the one you want, but I'm trying to make an illustration here), and select 'Download'. On the next page, there's an enormous long list of Epson printers..! Scroll down till you find the WorkForce printers. Do you see what I see?

The way I read things is that Epson seem to have a GENERIC driver that will give a degree of basic functionality to ALL their printers, which in itself tends to suggest that the software on their machines is basically similar. However, if you want to take advantage of features SPECIFIC to your particular model, you then have to start 'hunting' for them... Strange way of doing things.

------------------------------------------------------------------------------------------------------------------------------------------

@pdc:- I wonder if we can do a bit of collabaration on this one? It's a bit of an oddity, and no mistake. You clearly know a lot more about using the command-line than I do; let me pose a question, if I may. Is it possible that although MintPrint's got the correct driver, or filter installed, for some as yet unknown reason, the system, & CUPS, just isn't 'seeing' it? What could cause that to happen? My guess is that perhaps something else that CUPS relies on maybe isn't configured properly; what do you think? I'm GUESSING that's what was being figured out in posts #12-15, yes?

I've followed a lot of these Epson threads for several months now, helping out where I can.....but I've never seen one give this much trouble before. Epson have a slightly odd way of doing things ( the 'installing' THEN 'adding' spring to mind!), but by & large they're pretty straight-forward machines to work with.

A LOT of the hassle people get with them is solely down to Epson themselves, HAVING the drivers for these machines (they 'inherited' the whole batch from Avasys, when the latter shut up shop in early 2013), but refusing to release them for public usage; at least, that's how the situation has always appeared to me! And they pretend to be members of The Linux Foundation?

That's why I'm thinking about dependencies, perhaps, not being set-up properly. I'm beginning to understand some of the terminal basics, although I've got a LONG way to go; if you are in fact attempting to suss this out, please let me know.....and I'll 'butt out', if you like. Just thinking that two heads might be better than one.....

I don't give a monkeys about who gets credit for solving the problem (!!), but this one's starting to 'niggle' me...! :lol:


Regards,

Mike. :)

---

### Post by MintPrint2 on 2015-03-05
Hi pdc, hi Mike,

Thanks again for all your help - I'm a little busy in real life at the moment but bear with me, I do appreciate your advice and I will try Mike's idea as soon as I get a chance.

The output for dpkg -l | grep cups:

> ii  bluez-cups                                            4.101-0ubuntu13.1                                   amd64        Bluetooth printer driver for CUPS
ii  cups                                                  1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD/driver support, web interface
ii  cups-browsed                                          1.0.52-0ubuntu1.2                                   amd64        OpenPrinting CUPS Filters - cups-browsed
ii  cups-bsd                                              1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - BSD commands
ii  cups-client                                           1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - client programs (SysV)
ii  cups-common                                           1.7.2-0ubuntu1.5                                    all          Common UNIX Printing System(tm) - common files
ii  cups-core-drivers                                     1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD-less printing
ii  cups-daemon                                           1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - daemon
ii  cups-filters                                          1.0.52-0ubuntu1.2                                   amd64        OpenPrinting CUPS Filters - Main Package
ii  cups-filters-core-drivers                             1.0.52-0ubuntu1.2                                   amd64        OpenPrinting CUPS Filters - PPD-less printing
ii  cups-pk-helper                                        0.2.5-0ubuntu1                                      amd64        PolicyKit helper to configure cups with fine-grained privileges
ii  cups-ppdc                                             1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD manipulation utilities
ii  cups-server-common                                    1.7.2-0ubuntu1.5                                    all          Common UNIX Printing System(tm) - server common files
ii  libcups2:amd64                                        1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - Core library
ii  libcups2:i386                                         1.7.2-0ubuntu1.5                                    i386         Common UNIX Printing System(tm) - Core library
ii  libcupscgi1:amd64                                     1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - CGI library
ii  libcupsfilters1:amd64                                 1.0.52-0ubuntu1.2                                   amd64        OpenPrinting CUPS Filters - Shared library
ii  libcupsimage2:amd64                                   1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - Raster image library
ii  libcupsmime1:amd64                                    1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - MIME library
ii  libcupsppdc1:amd64                                    1.7.2-0ubuntu1.5                                    amd64        Common UNIX Printing System(tm) - PPD manipulation library
ii  printer-driver-hpcups                                 3.14.3-0ubuntu3.2                                   amd64        HP Linux Printing and Imaging - CUPS Raster driver (hpcups)
ii  python-cups                                           1.9.66-0ubuntu2                                     amd64        Python bindings for CUPS
ii  python-cupshelpers                                    1.4.3+20140219-0ubuntu2.6                           all          Python modules for printer configuration with CUPS

To answer your question pdc, my Ubuntu is 64 bit.

---

### Post by MintPrint2 on 2015-03-07
Hi Mike,

I gave your suggestion a try tonight and looking at the list of printers I noticed that WF-3520 is there like you said. Unfortunately I have the same problem still and I checked the list of Epson printers in the list of manufacturers when trying to add the printer, the WF-3520 still isn't there.

I also had another look at the ppd folder associated with cups to see if the generic driver added anything, and there wasn't anything there.

---

