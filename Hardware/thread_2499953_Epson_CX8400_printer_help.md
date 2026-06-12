---
title: "Epson CX8400 printer help"
date: 2024-08-16
forum: Hardware
---

### Post by Autodave on 2024-08-16
Trying to get this printer to work.  I d-led the newest driver from Epson's site and installed it, but nothing will print.  There doesn't even have anything in the queue.

Surely someone here has gotten this printer to work?

---

### Post by Autodave on 2024-08-18
bump

---

### Post by Autodave on 2024-08-23
bump

---

### Post by him610 on 2024-08-23
@autodave,
I don't use Epson printers and I probably can't help you, but I thought I might try. I mean, after all, who gets a printer and doesn't want it to print. The last time I used an Epson printer, it was a nine pin dot matrix about twenty years ago.

Just from looking around the Epson webpage, you could probably print from your smart phone.

Where did you get the CX8400 Linux drivers from? From what I saw on the CX8400 webpage, it is only supported by MacOS and Windows OS.

Sometimes a printer can be configured using generic drivers. I have a Dell 1700n that I have had for around fifteen years that uses generic drivers - it works good.

---

### Post by Autodave on 2024-08-23
It isn't mine.....I fixed a computer for this older woman.  It only had Win7 on it and the drive failed.  I put an SSD in it and Xubuntu.  She has this printer, but very little money to replace it and she has stage 4 cancer.  I am just trying to help her out and get it working for her.  She also has an Epson flatbed scanner and I already told her that there was very little hope of getting that to work.  I did find Linux drivers on Epson's website, but tried the newest 2 of them and got nothing at all.

---

### Post by him610 on 2024-08-24
> She also has an Epson flatbed scanner 
That I may be able to help you with. I have an Epson 1640 Perfection flatbed downstairs that I used until I got a Brother MFC 7360N about eight or nine years ago.

I have seen *TheFu* say many times that Epson does not play very well with Linux.  

Have you seen this webpage, [https://www.openprinting.org/printer/Epson/Epson-Stylus_CX8400]("https://www.openprinting.org/printer/Epson/Epson-Stylus_CX8400")

They list three different, current drivers. Maybe you have tried a couple of them. 
Is the CX8400 connected to the computer with a USB cable?

---

### Post by Autodave on 2024-08-24
I will have to try that one and see what happens.  The printer is connected via a USB cable.

---

### Post by snowcrash1 on 2024-08-25
I've been finding that with my flatbed scanner from epson, having the drivers isn't enough.  I'm trying to track down a permissions and see root can detect my scanner with the command sane-find-scanner, but my user account doesn't have permission.  And I don't know how to do that on Ubuntu 24.04 since there's hadly any kind of frontend for stuff like that.  So I've been playing with UDEV unable to figure out how to restart it, and having to reboot just in case.  And making rules doesn't seem to help.  Root can see it, I can't... so neither can Scanning Made Easy- SANE libsane libusb 

I even added a entry into proc /etc/fstab calling for usbfs using #usbsfs /proc/bus/usb none usbfs defaults 0  0 I didn't much alter the permissions on that one, but that's where I'm starting from.  With that one line.  It tis said in olden days before UDEV... fstab could set permissions to all who could read or write.  Now I don't know if that's true or not, but ya can take it with a grain of salt, I'd say. I'm told the permissions need to be mode="0664" or "0660"  Because chown will merely revert, sadly, when your computer is rebooted.

Wish you luck cx8400 woo woo, nice printer

---

### Post by snowcrash1 on 2024-08-25
so it might? have been permissions? too... but what happened with the scanner was it was misconfigured.  Somehow epson2 driver is not equal to epson, therefore "we're going to ignore your scanner" >> on the driver side.  I didn't need new drivers, my configuration my dll.conf files needed edited and if you just give me a sec.... they're in the /etc/<folder file> location  As It Happened, some of my drivers are incompatible and as a result is you or me, well.... that's okay, but a poorly configured configu.. el. sick.  is going to produce poor results.  At this point i think groupid might matter, you have to join the printer group.. whatever that's called using sudo adduser <name> group.  but if it's not that I would seriously start looking at configurations file in /etc/

no i haven't fixed my problem with my scanner, but I hope you get this.  I had to edit a dll.conf file because the driver installed was commented out.

Hope it helps!  Come back when you figure it out!

---

### Post by him610 on 2024-08-26
@AutoDave

Well, I got the driver installed for the scanner (Epson 1640SU) [https://imgur.com/JyVPBnl.png]("https://imgur.com/JyVPBnl.png")
Installation was fairly straight forward - just follow the instructions. Start it from terminal with, *iscan*. I am running it on Xubuntu 22.04.4.  

There was a line that said it was applicable for Stylus CX8400 also. Is that your printer model? Can't believe Epson would have same model designation for two different pieces of equipment. It could be a universal installation package, maybe.

Anyway, here is where I downloaded the scanner driver software and manuals from - [https://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=144749&DSCCHK=82c81a0e2debb2f8f4d8f85391bed992ed8c7514]("https://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=144749&DSCCHK=82c81a0e2debb2f8f4d8f85391bed992ed8c7514")

Here is where I found you can download the CX8400 printer Software and manuals - [https://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=160679&DSCCHK=02492a93712677985b3f8811ab2a674426e24ad7]("https://download.ebz.epson.net/dsc/du/02/DriverDownloadInfo.do?LG2=EN&CN2=&DSCMI=160679&DSCCHK=02492a93712677985b3f8811ab2a674426e24ad7")

If you need any more help, just post it in this thread; I usually check it daily, or more.

---

### Post by Autodave on 2024-08-27
I will definitely give that a try!  Gonna call her later and see if she is feeling good enough for me to go over and try it.

Thank you!  Will let you know when I try it!

I didn't tell you this before.....she is an older woman fighting Stage 4 cancer.  So, I have to check with her to see when she is feeling well enough for me to drive to her place and work on the computer.

---

