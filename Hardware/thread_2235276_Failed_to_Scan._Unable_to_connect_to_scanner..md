---
title: "Failed to Scan. Unable to connect to scanner."
date: 2014-07-20
forum: Hardware
---

### Post by webmanoffesto on 2014-07-20
I have a new Ubuntu 14 installation. I followed the instructions on the Brother website and driver installation went smoothly. But I can't get the scanner working. I'm on an Asus K55a laptop. It's a Brother MFC-7460dn multi-function printer.
I get a "Failed to Scan. Unable to connect to scanner." Error
[http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006893_000&flang=4&type3=625)


The printer works because I already used
Driver Install Tool - The tool will install LPR, CUPSwrapper driver and scanner driver (for scanner models).
[http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128)

[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/BrotherScannerProblemn01v01.png[/IMG]

XSane also gives me an error
"Failed to open device 'brother4:bus2;dev3: invalid argument"

[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/ScannerXSaneErrorn01v01.png[/IMG]

---

### Post by ajgreeny on 2014-07-20
I'm not sure if this is still current, but in the past when I needed to install another multifunction brother printer/scanner I had to do the following:-

Install libsane-extras, then
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    The lines to be added:-

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

    3. Restart the OS.

---

### Post by webmanoffesto on 2014-07-21
I tried to modify "/lib/udev/rules.d/40-libsane.rules" but I don't have permissions. How do I give myself permission.
But, I think I'm making progress anyway. 

At first Ubuntu didn't "see" the scanner at all. I followed the instructions here [http://ubuntuforums.org/showthread.php?t=783599](http://ubuntuforums.org/showthread.php?t=783599). 
**[FONT=courier new]sudo chmod a+w /dev/bus/usb/003/013 [/FONT]**[FONT=courier new]
[FONT=arial]thought I was making progress because Ubuntu did "see" the printer/scanner. [/FONT][/FONT]

But then I go the error message
[FONT=courier new]Failed to start scanner: Invalid argument[/FONT]

**Output from the "lsub" command**[INDENT][FONT=courier new]tom@Toms-Laptop-K55A:~$ lsusb
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 058f:a014 Alcor Micro Corp. Asus Integrated Webcam
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 0bc2:a013 Seagate RSS LLC 
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 015: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 003 Device 014: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 003 Device 013: ID 04f9:024e Brother Industries, Ltd 
Bus 003 Device 012: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 011: ID 1a40:0101 Terminus Technology Inc. 4-Port HUB
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
tom@Toms-Laptop-K55A:~$ sudo chmod a+w /dev/bus/usb/003/013 
[sudo] password for tom: [/FONT]
[/INDENT]

I'm on Ubuntu 14
Printer is Brother MFC-7460dn

[IMG]http://i1232.photobucket.com/albums/ff365/webmanoffesto/XSaneScannerAlmostWorkedv01.png[/IMG]

What do you recommend?

---
Following directions [here]("http://forums.fedoraforum.org/showthread.php?t=247308&highlight=Failed+to+start+scanner%3A+Invalid+argument+HPc6380").
tom@Toms-Laptop-K55A:~$ scanimage -L
device `brother4:bus2;dev3' is a Brother MFC-7460DN USB scanner

---

### Post by pdc on 2014-07-21
so ajgreeny was suggesting you edit the file [COLOR="#EE82EE"]40-libsane.rules[/COLOR] and the command to do that would be:

> [COLOR="#FF0000"]gksudo gedit /lib/udev/rules.d/40-libsane.rules[/COLOR]        .............and that opens the file that is called [COLOR="#EE82EE"]40-libsane.rules[/COLOR] using the text editor called [COLOR="#0000FF"]gedit[/COLOR]

and then paste in what he suggested; which is also here [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04)

---

### Post by webmanoffesto on 2014-07-22
Problem solved. Information which helped me. The above responses and:
- [http://ubuntuforums.org/showthread.php?t=1601221&page=2](http://ubuntuforums.org/showthread.php?t=1601221&page=2)
- [http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006645_000&flang=4&type3=566](http://support.brother.com/g/b/downloadend.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006645_000&flang=4&type3=566)
- [http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006645_000&flang=4&type3=566](http://support.brother.com/g/b/downloadhowto.aspx?c=us&lang=en&prod=mfc7460dn_all&os=128&dlid=dlf006645_000&flang=4&type3=566)

"1. For the Scanner
2. Download the 64-bit brscan3 drivers ([http://welcome.solutions.brother.com...nload_scn.html]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_scn.html"))
3. Install them (we don't need to force this time!) (dpkg -i [driver])
4. Check to make sure it worked [dpkg -l | grep Brother]
5. Use the brother tool for adding a new scanner (brsaneconfig3 -a  name=SomeName model=MFC-NOLOWERCASELETTERSALLOWEDHERE  ip=xxx.xxx.xxx.xxx)
6. Open your favorite scanning program and try it out!" 
([http://ubuntuforums.org/showthread.php?t=1601221&page=2](http://ubuntuforums.org/showthread.php?t=1601221&page=2))





Okay, I know this is getting picky. One small problem. When I scan using the "auto-document feeder" for a multi-page scan it feeds the pages through, but then I only find one file (one page, the first page) saved to my HD. I tried this in a few different formats .jpg, .png, .pdf and the same happens with all of them.
Can you recommend a solution.

I'm viewing the scanned images with Image Viewer 3.

Other than that small problem, Ubuntu is working Great! (and this "problem" may not be "Ubuntu's fault".

---

### Post by plucky on 2014-07-23
> Okay, I know this is getting picky. One small problem. When I scan using the "auto-document feeder" for a multi-page scan it feeds the pages through, but then I only find one file (one page, the first page) saved to my HD. I tried this in a few different formats .jpg, .png, .pdf and the same happens with all of them.
Can you recommend a solution.


Simple scan requires me to Select **Document > Scan > Allpages from Feeder** or press CTRL + F to scan all pages from feeder, otherwise it scans only one page at a time from the feeder on Brother DCP-120C.

Good Luck

---

### Post by webmanoffesto on 2014-07-23
> **plucky said:**
> Simple scan requires me to Select **Document > Scan > Allpages from Feeder** or press CTRL + F to scan all pages from feeder, otherwise it scans only one page at a time from the feeder on Brother DCP-120C. Good Luck

Yes, I see that in Simple Scan. I see 1. "Scan / Single Page" or 2. "Scan / All Pages from Feeder". So, I would say 2 is the same as XSane 1. "Flatbed" or 2. "Auto Document Feeder"

Also, Simple Scan couldn't find my scanner. I'm tired of that problem. I got XSane and Gimp scanning, that's enough.

---

### Post by M_Hao on 2015-01-24
> **ajgreeny said:**
> I'm not sure if this is still current, but in the past when I needed to install another multifunction brother printer/scanner I had to do the following:-

Install libsane-extras, then
    1. Open "/lib/udev/rules.d/40-libsane.rules" file.
    2.Add the following two lines to the end of the device list. (Before the line "# The following rule will disable ..."):
    The lines to be added:-

# Brother scanners
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes"

    3. Restart the OS.

This one works great. I want to verify it so that you do not need to spend time on other methods. after install brother's driver. my printer work but unable to connect to scanner. This one solve the problem. :lolflag:

---

