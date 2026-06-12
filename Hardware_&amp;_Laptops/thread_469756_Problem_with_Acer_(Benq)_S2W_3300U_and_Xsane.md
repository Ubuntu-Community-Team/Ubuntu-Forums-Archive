---
title: "Problem with Acer (Benq) S2W 3300U and Xsane"
date: 2007-06-10
forum: Hardware &amp; Laptops
---

### Post by wacki on 2007-06-10
Hello,
starting xsane I get the error message

open of device snapscan:libusb:001:006 failed: wrong argument (translated from German)

in the terminal comes
> [snapscan] Cannot open firmware file /usr/share/sane/snapscan/your-firmwarefile.bin.
[snapscan] Edit the firmware file entry in snapscan.conf.

In the snapscan.conf the scanner is listed and sane-find-scanner gives
> found USB scanner (vendor=0x04a5 [Color], product=0x20b0 [ FlatbedScanner 22]) at libusb:001:006

I installed libsane-extras.

Can you please help me?

Thank you very much.

---

### Post by GoldNugget on 2007-07-11
My Acer usb scanner has been broken since a kernel upgrade several months ago. I have tried many different suggestions found on these forums. However this thread finally fixed the problem.
 
Determine which driver is correct for your scanner first, and modify these steps as needed. 
This worked for my Acer 640U:

"...download the windows driver zip file mirascanv403u10_bqa.zip

and in a terminal

expand the zip file
"unzip mirascanv403u10_bqa.zip"

change directory to the firmware directory
"cd MiraScan\ v4.03u10_BQA/BIN/"

as root user (sudo) make directory to put firmware in
"sudo mkdir /usr/share/sane/snapscan"

as root user (sudo) copy firmware file to that directory
"sudo cp u96v121.bin /usr/share/sane/snapscan/"

as root user (sudo) use gedit program to edit snapscan.conf file
"sudo gedit /etc/sane.d/snapscan.conf"
and change firmware line to location of file
firmware /usr/share/sane/snapscan/u96v121.bin


BenQ link for Acer 620U driver download
[http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D](http://www.benq.co.uk/support/downloads/downloads.cfm?product=160&page=downloads&dtype=D)  

A big thank you to dmbk for these instructions. The full thread is here:
[http://ubuntuforums.org/archive/index.php/t-317685.html](http://ubuntuforums.org/archive/index.php/t-317685.html)

---

### Post by PILGU on 2007-09-02
GOLDNUGGET, I would like to thank you very very much.I have a Benq 5000u usb scanner and following your instructions (my bin file is "u252v072.bin") I can finally scan with my scanner.
Again I feel in dept with you. thanks Pal

---

### Post by FreewheelinFrank on 2007-10-27
Is this info still relevant to an Acer S2W 3300U in Ubuntu 7.10?

I have the zip folder from Acer but there are several .bin files. Which one do I use?

There is u96v121.bin: is that the firmware for the 3300U too?

Any help much appreciated. Thanks.

---

### Post by Azunatsu on 2007-11-10
I also got this kind of situation! I use Benq 3300u scanner which really works well on xp but not in vista and planning to use on my Ubuntu Gutsy. I already installed SANE but when i switched to Kooka it said "your system doesnt provide SANE". FYI i also installed KDE desktop on my pc.I also download all the drivers needed but mostly for windows.I try to use WINE by just installing Mirascan directly on my system but still fails! Somebody can help me? I already followed the above steps but still can't!

---

### Post by FreewheelinFrank on 2007-11-16
OK, I solved this one myself, with a tip of the hat to Michael Conry:

[http://www.acronymchile.com/scanner.html](http://www.acronymchile.com/scanner.html)

Here's what I did:

Visit this page, check for model and firmware file:

[http://snapscan.sourceforge.net/](http://snapscan.sourceforge.net/)

There were two listed for S2W 3300U, but the first one seems to be working OK.

Proceed as per GoldNugget's advice, but with the appropriate .bin file.

Scanner now work via Open Office>Insert>Picture>Scan (wait a while- it appears to lock up but then noises emerge from the scanner and it's recognised) or typing 'xsane' in a terminal.

Azunatsu:

Have you tried the advice using the correct .bin file?

> Acer / Benq
3300 / 4300
USB
0x04a5, 0x20b0
"FlatbedScanner23"
u176v046.bin
	
Acer / Benq 	
3300 / 4300 	
USB 	
0x04a5, 0x20de
"FlatbedScanner21"
"FlatbedScanner22"
u222v067.bin

Good luck! Hope you get your scanner working too!

---

