---
title: "Canon PIXMA iP4500 support in Gutsy"
date: 2007-10-26
forum: Hardware &amp; Laptops
---

### Post by Djembe on 2007-10-26
I recently purchased Canon's latest PIXMA iP4xxx series printer, the iP4500.  While it is recognized instantly in Gutsy as "Canon iP4500", neither the driver for the iP4000 (what Gutsy tried by default) nor the driver for the iP4300 (the previously most recent in the series) succeeds in making my printer actually print.  Both incur paper movement as if the printer was actually printing (including duplex), however not a drop of ink is on the sheets when they come out onto the output tray.  I made an attempt to configure a custom driver for it, but I could not find a .ppd file (needed to make the driver) either on the driver CD or in my Windows directory.  The printer works wonderfully in Windows, so I was wondering if, since there appears to be no current Linux driver for it, someone could advise me on the possibility of setting it up using the Windows driver through Wine or preferably determining how to find or extract the .ppd file so I can use CUPS to manage printing in Linux.  Any ideas?

---

### Post by wingedpower on 2007-11-01
I too have the IP4500 PIXMA from Canon. The system recognizes the printer, from USB, but cannot print to it.

I have successfully printed to it, through through a hacky method:

1) create a Windows VM
2) install the IP4500 drivers as well as the loopback port drivers in the Windows VM
3) Create a generic HP LaserJet PS printer port
4) Install Ghostscript
5) Link the HP LaserJet PS port via the port loopback through Ghost Script, to print to the IP4500.
6) Bind the IP4500's USB device to the Windows VM
7) In Ubuntu's Cups management, create a new network printer device, of the HP LaserJet PS persuasion and point it at the Windows VM.

While this lets you print, it is NOT photoquality. Think something on par with color newsprint. :/ You're also limited to 600dpi due to the HP Laserjet limitations.

I current print to the IP4500 with my iBook.

Would LOVE to see IP4500 CUPSD support.

Wing.

---

### Post by Djembe on 2007-11-26
Thanks for the guide.  I'm also hoping CUPS support will happen soon.

edit:  Hey, I just found a driver that works!  It's called TurboPrint, and it works in higher resolution, although they'll insert their logo into stuff you print using the free version.

---

### Post by Fanaz on 2007-12-30
Drivers:

[http://cweb.canon.jp/drv-upd/bj/bjlinux280.html](http://cweb.canon.jp/drv-upd/bj/bjlinux280.html)

Works great!

---

### Post by puzzledinmn on 2008-01-09
I found the following Canon IP4500 driver website a little easier to read-

[http://software.canon-europe.com/software/0028476.asp](http://software.canon-europe.com/software/0028476.asp)

Now if I can find a simpler procedure to use the files.  I wouldn't have been so quick to install Ubuntu if I'd have known I couldn't use full screen resolution with my Dell Inspiron 530/SE198WFP combination or even be able to print.

[https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview](https://help.ubuntu.com/community/HardwareSupportComponentsPrinters/CanonPrinters/CanonPixmaIP4200#preview)

---

### Post by puzzledinmn on 2008-01-21
I did a lot of unnecessary steps I think but I am printing with high quality and with color using the Canon 2.80 driver and my Canon iP4500 printer.  I think the relatively simple procedure that Canon gives in their tar file (for 7.04) does work for 7.10 if you make the following changes.  

1. use  sudo dpkg -i *.deb  instead of the common .deb package first.  I got an error trying to individually install but *.deb worked for some reason.
2. their command to change the default printer did not work.  I had to go to System-Preferences-Default Printer and select IP4500 instead of ip4500_series.  That was under GNOME.

I installed the stuff starting with alien in the above link after I got the deb package failure so I can't prove the Canon procedure and the two changes are sufficient.  I don't understand what Canon means by "If the Driver UI does not start even when the --gui option is specified in the cif command", so I may be missing a user interface but at least I can print now!

---

### Post by puzzledinmn on 2008-01-26
After you install the Canon 2.80 iP4500 driver, you will have the following files-

/usr/bin/cifip4500        /usr/bin/lgmonip4500
/usr/bin/cngpijmonip4500  /usr/bin/printuiip4500

printuiip4500 selects paper type and size, and for maintenance.  But it seems dead. But 
cngpij -P IP4500 Sample.png brings the interface to life.
cngpijmonip4500 IP4500 gives status but says Ready when idle or even turned off and no ink level like the driver guide says.  Perhaps someone else can figure out how to get the status to work right. The guide seems incomplete.

---

### Post by cnschulz on 2008-02-18
the drivers i got installed fine un gutsy headless

i used cups to install and configure (after installing .debs)

it prints with no margin but im sure ill figure that out later

:)

---

### Post by karesz on 2008-02-19
The driver works fine, only its really slow (and i mean it), and it works in 600dpi resolution. Unfortunatelly, just a few moments after i've downloaded almost everything, instead of the last one, the site went away, saying error, not available.
Anyway, it helped me out.

edit: The site is available again. Maybe it was maintenance...

---

### Post by dpope on 2008-04-09
I've tried installing the driver using the supplied deb files from canon and the instructions provided in their guide but I still get the blinking lights when I try to print from gutsy to my ip4500.  One potential issue is that I am running 64-bit version of gutsy so I had to use dpkg --force-architecture to get the packages to install.  I do have libia32 installed so I presumed this would be okay but maybe not. 

I tried printing with the IP4500 printer canon's instructions told me  to create and that didn't work.  I also tried deleting the Canon4500_series printer Ubuntu automatically creates but when I next plugged in the printer Ubuntu re-created this driver and then the my cpu usage went up to 100% with a process cifip4500 eating it all up.  I'm not sure if this is because I installed a 32 bit driver on a 64 installation or if its just because the two drivers (the one canon asked you to create in its instructions and the one ubuntu automatically creates) started fighting with each other.

Any help would be appreciated.

---

### Post by karesz on 2008-04-15
Hi! I've found something, but i haven't tried it yet. Maybe if i'll have some more time ... The possible solution: On the canon download site there's an option to download mac osx drivers, cups and non-cups and others. Download the _CUPS_ version, you'll get a dmg file. I've opened it with ultraiso windaz trial version, and inside i've found the "CanonIJiP4500series.ppd" file. This was, when i gave it up, due to lack of time. University is not a friend of tweaking your system... But, this is a file wich cups can handle. Try making a driver with this file...  Write me if you were succesful! Good  luck!

---

### Post by eltimbalino on 2008-04-19
Thanks people for working on this. I have just installed an ip4500 and have the same issue, but I don't even know what "cups", "debs" or "ppd files" are so I am really grateful for the time you have spent learning linux and helping resolve issues like this.

I will keep following this thread as you get closer to a solution that works well and I can use. Thanks.

---

