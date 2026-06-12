---
title: "Printer Model Suggestions"
date: 2015-01-06
forum: Hardware
---

### Post by SpikeLS6 on 2015-01-06
I made a mistake buying a new Canon MFP; not even the after market driver Mfg's make anything to run it.

I now know there are places to look to find Linux supported Printers and Multi-function machines. Unfortunately, the new models that are being sold do not appear on any of the lists I have searched. I know now that HP has the best Linux support, or at least works with the Linux developers.

Can anyone recommend an HP Mono color (B&W) Laser Multi-function machine that also has wireless capability? I am using Ubuntu 14.10.

Thank you.

Spike

---

### Post by weatherman2 on 2015-01-06
I assume you've already posted a thread about your Canon trying to make it work?  Looked for a driver on Canon's Europe or Asia websites?  My Canon printers have worked pretty well in Ubuntu.

---

### Post by SpikeLS6 on 2015-01-06
All of the above. It is a Canon ImageClass D530, one of the few that does not use CUPS. I have already downloaded and installed up to Ver. 2.9 of the Canon drivers, but it will not even print a test page.  I have even gone to other countries Canon web sites for drivers, but none of them worked either. Not even TurboPrint is supporting it I learned from my last email query to them. WIN 7 works as advertised in all respects, so I know the printer/scanner/copier works.

Hence my reason for looking for an HP machine. I am having difficulty finding which of the currently available models work.

---

### Post by weatherman2 on 2015-01-06
So you're not looking for another Canon because one particular model didn't have good Linux support?  Might there be a few HP models that also aren't well supported in Linux?

I have two Canon Pixmas that have always worked Linux - the Pixma MX340 and the MX420 (both probably no longer made).  Canon had official drivers for the printer and scanner functions on their European and Asian websites.  It seems they don't support Linux (or not well) in the US for some reason.  I think if you can find Linux drivers on their European site for a model you are considering (or a very similar model) you will probably be good.

A quick search shows that no obvious European driver from Canon is available on their support site.  Maybe that's because they don't market that line of printers outside of the US.   Mine were apparently.

I personally won't buy an HP product again for reasons having nothing to do with Linux support. I've had too many issues (sometimes design issues, sometimes support issues) with various HP products through the years. I know Canon isn't perfect either but my two Canon printers have worked beautifully for me over the last few years, and I'm glad I can use them in Linux.

---

### Post by Mike_Walsh on 2015-01-06
Hi, Spike.

How about considering an Epson?

They may not appear, on the face of it, to have much in the way of Linux support from the manufacturer. However, there are a few places where you will have plenty of luck with obtaining drivers. One such site is openprinting.org. This is where I have obtained many of my drivers in recent years.

Also, with regard to the scanner component of Epson all-in-ones; Epsons need to have printer and scanner/data packages installed separately in Linux (for all I know, this may well be the case with other manufacturers, too). However, although there are quite a few different printer 'filters' (they're not really 'drivers' in Linux; strictly speaking, they're 'filters' that allow your machine to interface with the CUPS system), when it comes to the scanner/data packages, there seem to be only a couple of them, to cover nearly everything that Epson have produced over at least the last decade.

Food for thought?


Regards,

Mike.

---

### Post by pdc on 2015-01-07
Hi Spike: sorry to hear of the issues you are having; 

You have installed the UFR driver that Canon supply: is your system 64bit ubuntu?  I ask because it needs some extra files installed for the UFR driver to work;

so can we have a go at getting the D530 to work?

this link [http://jonathan.bergknoff.com/journal/printing-ubuntu-canon-mf3010](http://jonathan.bergknoff.com/journal/printing-ubuntu-canon-mf3010) 

says you need 

```
sudo apt-get install libxml2:i386
```

```
sudo apt-get install libjpeg62:i386
```

```
sudo apt-get install lib32z1
```

```
sudo apt-get install libstdc++5:i386 libstdc++6:i386
```

then 

```
sudo restart cups
```

____________________________________

you are nearly there with the UFR driver installed; the final step is registering the printer: one can use the GUI (administration-printers) to do that; or a terminal; 

how did you register the printer on your system?

---

### Post by SpikeLS6 on 2015-01-07
PDC:
     The files to install you recommended worked great! I am not sure what you meant by registering the printer on my system,  but I went to Printers - Localhost, deleted the D530, then Added it to  the Printers all over again after I installed all the new files and restarted CUPS. The new screens were definately different  from those seen previously.Re: the Jonathan link you suggested, I am using the most current UFR file version 2.9. It printed a test page, then numerous things from the Internet, and some documents from Open Office Writer. I believe the printing woes are cured. 

     I will next work on Xsane to see if scanning with Ubuntu 14.10 is possible, but this thread is SOLVED and I will mark it so.

     Everyone else, thank you for the suggestions of things to try and things to consider. Now that the Canon D530 prints with Linux, that saves enornous amounts of time going back and forth between WIN 7 on one HD and Ubuntu on the other.

     Thank you very much!

---

### Post by pdc on 2015-01-08
delighted it works for you

> I am not sure what you meant by registering the printer on my system

> but I went to Printers - Localhost, deleted the D530, then Added it to the Printers all over again

.............well done...........you exactly registered the printer ................great

__________________________________-

from here [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) the D420 and the D480 are supported; 

sane-pixma is the backend that supports this class of scanner [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

much of linux is volunteers; at this end of the above link are the authors who look after the sane-pixma project; you can contact them and they can help you get the scanner going; keep in touch and let us know how it goes;

you could greatly help them, as they do not own a D530 and you can send them useful data

---

### Post by SpikeLS6 on 2015-01-08
Again thank you for the help. Unfortunately the next morning I tried to print something and found that my PRINTERS-Localhost was completely empty! I finally did locate the HP2550l file, and magically the Canon D530 also showed up. Strange.

I will take your suggestion and contact the Xsane authors and see if they might be willing to help with this Canon D530. It is still out there available as Brand New, so perhaps there might be enough of them to develop workable drivers.

---

### Post by kurt18947 on 2015-01-08
If you're unsuccessful with Sane/Xsane, you might check VueScan.  It works very much like a DOS program in linux; download the program, unpack it, click on the executable and it should open.  If it recognizes your scanner, it will scan but the image will be watermarked.  If it works you can purchase a key to remove the watermark. We purchased a copy for a Canon scanner that worked with Sane but not all features were supported in Sane.

[http://www.hamrick.com/download.html](http://www.hamrick.com/download.html)

---

### Post by SpikeLS6 on 2015-01-08
Thank you Kurt. I will try that link. I have already corresponded with TurboPrint and learned that they do not have a driver for the D530/D560 ImageClass MFP's and have no plans to develop one, so I will try the Harrick link.

---

### Post by pdc on 2015-01-08
Spike: 

what is ID of your D530 when you type ```
lsusb
``` in a terminal.................the command is asking the system to LIST the usb connections..............eg the D420 is > 04a9:26ef and the D480 is > 04a9:26ed so yours is likely to be 04a9:26something

there is a file /etc/sane.d/pixma.conf that is usually they say only for network printers; but if we got you to enter the ID of your device there; ...and one can but see if it helps .....................

---

### Post by SpikeLS6 on 2015-01-08
I ran a "sudo lsusb" command in Terminal and received this:
mckenzie@mckenzie-desktop:~$ sudo lsusb
[sudo] password for mckenzie: 
Bus 003 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mckenzie@mckenzie-desktop:~$ 
 
Ubuntu does not even see it. Both Simple Scan and XSane never brought up their first screen to try Preferences, Options, or other settings to try to find the scanner; an "error code 98" could not be found came up with both.

Anything else I can try?

---

### Post by SpikeLS6 on 2015-01-08
Oops, I did not have it turned on. Here's the new response:

mckenzie@mckenzie-desktop:~$ sudo lsusb
[sudo] password for mckenzie: 
Bus 003 Device 003: ID 04a9:2775 Canon, Inc. 
Bus 003 Device 002: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c05a Logitech, Inc. M90/M100 Optical Mouse
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 009 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 008 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
mckenzie@mckenzie-desktop:~$ 

What is the next step now that Linux see it?

---

### Post by pdc on 2015-01-08
If you first have a read of the file that we are going to edit; and if you open it with read-only powers ...........just so you can get a look at it .............. it says network but it is the place to put an entry for a new device

the command to do that is ```
gedit /etc/sane.d/pixma.conf
``` so that tells the text editor [COLOR="#0000FF"]gedit[/COLOR] to open the file called [COLOR="#008000"]/etc/sane.d/pixma.conf[/COLOR]               ..................even if you make changes now, they won't be saved

___________

once you have had a look at the file, if you close the text editor gedit

now the command to make changes that are saved is ```
gksudo gedit /etc/sane.d/pixma.conf
``` and the system should ask you for your sudo password

If you now paste this

```
#Canon D530
usb 0x04a9 0x2775
```

(so that is two separate lines................)

in a new line below the existing entries; SAVE: CLOSE; reboot

.............. any joy?

---

### Post by SpikeLS6 on 2015-01-08
My edit file looks like this:

# pixma.conf configuration for the sane pixma backend
#
# define URI's of scanners (one per line)
# This is only used for network scanners.
# normally scanners will be detected by sending a broadcast
# if this does not work under your OS, or if the scanners
# are on a different subnet, configure your scanners URI here
#
# method must be bjnp
# port number can normally be left out, port 8612 is used as default
# Example:
# bjnp://myscanner.my.domain:8612
# bjnp://printer-1.pheasant.org
# Canon D530
usb 0x04a9 0x2775

Neither XSane nor Simple Scanner could find or identify the scanner. Should there be a "#" in front of the"usb 0x04a9 0x2775, or might there be another typing error in it? The scanner was turned on when I brought both programs up.

---

### Post by pdc on 2015-01-08
what you have done looks absolutely fine: the # symbol tells the computer to leave that line alone; so the # Canon D530 is just for you and the next line; without the #; is a "take action" line

obviously that isn't enough

can you though try these commands .......

```
sane-find-scanner
```

```
scanimage -L
```

and then repeat them with sudo in front of each of the commands please ................

________________

I would recommend you join this page [http://lists.alioth.debian.org/mailman/listinfo/sane-devel](http://lists.alioth.debian.org/mailman/listinfo/sane-devel) and they would be pleased to hear from you

if you enter this command in your terminal; ```
lsusb -v -d 04a9:2775
``` ........with the D530 turned on! ........and paste the result into your entry post; it will help them get off to a good start to help you; they are a great team

---

### Post by SpikeLS6 on 2015-01-08
Here are the results of your suggestion:

mckenzie@mckenzie-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x04a9/0x2775 at 003:004: Access denied (insufficient permissions)
could not open USB device 0x1a40/0x0101 at 003:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc05a at 004:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 009:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 008:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
mckenzie@mckenzie-desktop:~$ sudo sane-find-scanner
[sudo] password for mckenzie: 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon Inc], product=0x2775 [D530/D560]) at libusb:003:004
could not fetch string descriptor: Pipe error
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
mckenzie@mckenzie-desktop:~$ 

mckenzie@mckenzie-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
mckenzie@mckenzie-desktop:~$ sudo scanimage -L
    
No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
mckenzie@mckenzie-desktop:~$ 

I have also subscribed to the SANE site and ran the script you suggested and saved it for the first post. I already sent them an email to see if they would help and I could test whatever scripts they came up with. I'll keep going.

Thank you for your help.

---

### Post by pdc on 2015-01-08
well done; all very organised of you

I see permissions issues mentioned;

I wonder what ```
sudo xsane
``` says .............. that runs xsane as root and from the terminal, it may give you error messages that may help

Xsane is the front-end GUI that uses the sane project to drive a scanner; but you can load it from the terminal; 

as here [http://askubuntu.com/questions/211447/12-04-scanner-works-fine-as-super-user-but-is-not-recognised-as-a-normal-user](http://askubuntu.com/questions/211447/12-04-scanner-works-fine-as-super-user-but-is-not-recognised-as-a-normal-user)

If the scanner group applies to a multi-function device, if you add your username 

> sudo adduser <yourusernamehere> scanner so if your username is SpikeLS6, the command is > sudo adduser SpikeLS6 scanner

............ you can try the commands again after that .....................

---

### Post by SpikeLS6 on 2015-01-08
The "sudo xsane" command brought up a big warning that once I ran it I was on my own; no help for bugs from SANE.

So, I tried the add username and it was accepted, then ran the "sudo" commands to see if Linux would find the scanner. It responded:

mckenzie@mckenzie-desktop:~$ sudo adduser mckenzie scanner
[sudo] password for mckenzie: 
Adding user `mckenzie' to group `scanner' ...
Adding user mckenzie to group scanner
Done.
mckenzie@mckenzie-desktop:~$ sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not open USB device 0x1a40/0x0101 at 003:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 003:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 007:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 006:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 002:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 005:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 001:001: Access denied (insufficient permissions)
could not open USB device 0x046d/0xc05a at 004:002: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0001 at 004:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0003 at 009:001: Access denied (insufficient permissions)
could not open USB device 0x1d6b/0x0002 at 008:001: Access denied (insufficient permissions)
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.

  # You may want to run this program as root to find all devices. Once you
  # found the scanner devices, be sure to adjust access permissions as
  # necessary.
mckenzie@mckenzie-desktop:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

could not fetch string descriptor: Pipe error
  # No USB scanners found. If you expected something different, make sure that
  # you have loaded a kernel driver for your USB host controller and have setup
  # the USB system correctly. See man sane-usb for details.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
mckenzie@mckenzie-desktop:~$ scanimage -L

No scanners were identified. If you were expecting something different,
check that the scanner is plugged in, turned on and detected by the
sane-find-scanner tool (if appropriate). Please read the documentation
which came with this software (README, FAQ, manpages).
mckenzie@mckenzie-desktop:~$ 

By the way, the scanner is connected to the PC via USB. I do not know what the Pipe error is about.

---

