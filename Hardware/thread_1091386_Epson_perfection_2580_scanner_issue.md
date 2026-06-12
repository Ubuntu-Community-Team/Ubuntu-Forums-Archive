---
title: "Epson perfection 2580 scanner issue"
date: 2009-03-09
forum: Hardware
---

### Post by dionp2 on 2009-03-09
Hi,

My Epson 2580 scanner worked perfectly first time with Ubuntu Intrepid with Xsane.

Now to my dismay it brings up this error when I try to start Xsane..

Failed to open device 'snapscan:libusb:001:003': invalid argument

I used synaptic Package Manager to uninstall and reinstall Xsane and Sane (NB : I added Sane after installing Xsane)

When I type lsusb as root I get:-

Bus 004 Device 002: ID 05fe:0202 Chic Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

I am running Ubuntu 8.10 on a Toshiba A50 Notebook.

I also found some forum hints which lead to this page

[http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/](http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/)

which I installed but had no success with either.

Please help?

Cheers,

Dion

---

### Post by absgtr on 2009-04-19
I also have the exact same issue as described by **dionp2**.

I installed Ubuntu 8.10,  11-Apr-09 and verified that all of my hardware and peripherals were working correctly under Ubuntu. All was A-OK then with my overall system. Very Cool !

I actually scanned several photos using XSane Image Scanner with no trouble at all.

Since then, I did a number of the automatic system upgrades and other package installs and now XSane now throws an error when scanning for devices; 
Failed to open device 'snapscan:libusb:001:008':invalid argument.

Maybe this is related to my scanner interface problem. Also after system upgrades and other package installs I am getting numerous USB error messages at bootup.
"USB 1-2: device description Read/64 error -110. Unable to enumerate USB device on port?

When I figure it out, or find a posted solution I will reply back with the solution.

---

### Post by dionp2 on 2009-04-19
Strange because about a week ago after a few more upgrades I tried the scanner again and now it works perfectly. Although this makes me kind of scared about doing new upgrades if it kills my scanner. It is a pain to have to boot into a windows virtual machine just to do scans.

Although now when I do an lsusb at the command line it says that I have an Epson 2480 even though the actual scanner is a 2580

lsusb
Bus 004 Device 006: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo
Bus 004 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 05fe:0202 Chic Technology Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Not sure about this one and don't have the time to look into it.

---

### Post by absgtr on 2009-04-19
I resolved it, but the solution was time consuming to find on the web and time consuming to implement.
After several, try this, try that, try it again attempts from various web pages, I found the ONE that did the trick.
I am a total newbie to Linux and Ubuntu, but am pretty experienced on the Windows side of the world. So I am struggling a bit to learn terminal commands and the "inards" of the file system / OS.

**Here was my fix;**
I found a web page;  [http://www.arakhne.org/epson/index.html](http://www.arakhne.org/epson/index.html)
This web page instructs you get a copy the driver file "esfw41.bin" from the Windows Installation of the Epson Perfection 2580 Scanner. 

This driver file is encryted into the CAB file on the Epson Scanner Windows installer CD-Rom, but luckily I use the scanner on a different Windows XP PC and did a Windows search for esfw41.bin.  

*[SIZE="1"]Side Note:  I had to run sudo commands in a terminal in order to authorize the creation of the new epson-perfection folder and the editing of the snapscan.conf file.[/SIZE]*

I created an "epson-perfection" folder in the system files under /usr/lib/epson-perfection/
I copied the esfw41.bin file into the /usr/lib/epson-perfection/ folder.
I then edited a file snapscan.conf in the system files under /etc/sane.d/
/etc/sane.d/snapscan.conf to add the specific driver needed for the Epson 2580 Scanner.

**Snippet in the snapscan.conf file:**
#Change to the fully qualified filename of your firmware file, if
# firmware upload is needed by the scanner
***[COLOR="Red"]I COMMENTED OUT THIS LINE[/COLOR]***
#firmware /usr/share/sane/snapscan/your-firmwarefile.bin
***[COLOR="Red"]I ADDED THIS LINE[/COLOR]***
firmware /usr/lib/epson-perfection/esfw41.bin


I then ran the Xsane Image Scanner and it was then happy, found my scanner and I was able to scan a photo.

---

### Post by dionp2 on 2009-04-19
Mate that's orsm.

Admittedly painful and a lot of work but orsm none the less.

I wonder if we can get Xsane or Ubntu to add it to their archives for automatic updates etc.

The universe thing in the sources file.

Cheers,

D

---

### Post by dionp2 on 2009-09-01
Finally got around to installing that scanner driver. Had to unplug/ plugin the scanners USB cable and turn the scanner on and off but it works a treat. 

It also looks like arkane has added sources for ubuntu although I tried that and it didn't work. 

If anyone needs the esfw41.bin file I have zipped it up and attached it to this post. So no need to go looking for it now.

Cheers.

D

---

### Post by dionp2 on 2009-09-01
Actually the sources did update XSane but not the driver for my specific scanner.

---

### Post by dennymallow on 2009-12-28
> **dionp2 said:**
> Finally got around to installing that scanner driver. Had to unplug/ plugin the scanners USB cable and turn the scanner on and off but it works a treat. 

It also looks like arkane has added sources for ubuntu although I tried that and it didn't work. 

If anyone needs the esfw41.bin file I have zipped it up and attached it to this post. So no need to go looking for it now.

Cheers.

D

I have Karmic and Epson Perfection 2580 Photo, and I dowloaded the "libsane-epson-perfection-2580_3.0-21arakhne1_all.deb" package from arakhne:
[http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/]("http://download.tuxfamily.org/arakhne/pool/l/libsane-epson-perfection/")

I installed it, but after that launching Xsane resulted in an error, saying that there was an I/O communication problem with the scanning device.
This is most probably because the firmware "bin" file included in the DEB package from "[arakhne.org]("http://www.arakhne.org")" is not updated.

So I downloaded the zip kindly posted by dionp2 (many many thanks for the comfortable link, I'm a lazy man! :D), even if I think I could have taken it directly from the Windows disk, and i copied the bin in the zip archive as super user, and put in the /usr/lib/epson-perfection folder.

After that, I powered off the scanner, unplugging the electrical cable (brutal, Isn't it? XD but there's no other way to turn off! :S), and Xsane launched without any problem!

Yeah! :guitar:

EDIT: the frontend is even better than in Window$!
Result (:P):
[IMG]http://www.webalice.it/famiglia.merlotti/Lady_Ermine.jpg[/IMG]

---

### Post by neithere on 2010-01-14
Downloaded the firmware file (no .deb packages, just the [http://luc.byhet.free.fr/epson2480/esfw41.bin](http://luc.byhet.free.fr/epson2480/esfw41.bin)), copied it into the suggested directory and edited one line in /etc/sane.d/snapscan.conf so that it points to the firmware -- and it works! Thanks a lot :)

UPD: Kubuntu 9.10 Karmic Koala.

---

### Post by myownserver on 2010-04-28
This still works as of Ubuntu 10.04 Lucid!

Lucid comes with Simple Scan, which doesn't work, so you can either uninstall it or just ignore it, but you need to download/install xSane.

Then download the firmware file [http://luc.byhet.free.fr/epson2480/esfw41.bin](http://luc.byhet.free.fr/epson2480/esfw41.bin) from post #9,

And follow these steps from #4:
Create the directory **/usr/lib/epson-perfection/**
Copy the **esfw41.bin** file into the **/usr/lib/epson-perfection/** 
Open the file **/etc/sane.d/snapscan.conf** with gedit, then add the following line:

```
firmware /usr/lib/epson-perfection/esfw41.bin
```

Save the file, then launch xsane and there ya go!
You may need to unplug/plug the scanner back in.

---

### Post by SlappyPappy on 2010-04-29
Thanks to this thread I got my Epson 2480 up and running in 9.10 in just a matter of a few minutes. Had to scan about a hundred documents and for whatever reason I had not installed the firmware for my scanner.

One thing I might add here is that I had to change permissions on the firmware so it would work. No big deal.

Ubuntu and its users, still the best!

Thanks again.  :guitar::guitar::guitar::guitar::guitar:

---

### Post by megahertz on 2010-10-12
&#65279;To set up the Epson 2480 or 2580 scanner to work with Xsane you need:
- Install p7zip-full (Synaptic Package Manager)
- Install Xsane (Synaptic Package Manager)
- Extract esfw41.bin from /ESCAN/ModUsd.cab from Epson scanner CD
- On terminal type sudo nautilus (to open file manager as root)
- make folder /usr/share/sane/snapscan
- move  extracted file esfw41.bin to /usr/share/sane/snapscan

- with Nautilus (as root) go to /etc/sane.d and edit /etc/sane.d/snapscan.conf so at the 4th line you should have:

firmware /usr/share/sane/snapscan/esfw41.bin


- with Nautilus (as root) go to /etc/sane.d and edit /etc/sane.d/dll.conf and put a # on the beginning off all lines EXEPT on snapscan

Be sure the Epson scanner appears with command lsusb on terminal
- Bus 001 Device 003: ID 04b8:0121 Seiko Epson Corp. Perfection 2480 Photo

Your Epson scanner should be working
Applications - Graphics - Xsane

---

