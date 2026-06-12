---
title: "Stuck and really need some help with printer-scanner"
date: 2018-05-22
forum: Hardware
---

### Post by bobsone on 2018-05-22
Hi

 I am experimenting with a clean 18.04 Mate install on a desktop with the OS on a SSD and the Home folder on a HDD.

As the title says, I need some help with the setup of our USB Brother DCP-135c printer-scanner.  
 The good news is that I have managed to get the printer to work, but half of the top line of print is off the top of the page and, I can not get the scanner to work.
 
  I have downloaded the Scanner, LPR and CUPS Deb drivers from here:  [http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp135c_eu_as&os=128 ]("http://support.brother.com/g/b/downloadlist.aspx?c=gb&lang=en&prod=dcp135c_eu_as&os=128")
 
 I tried the pre-installation / Pre-required procedures listed on the brother web site for *“**Related distributions Ubuntu8.04 or greater”*  [http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#prereq](http://support.brother.com/g/s/id/linux/en/before.html?c=us_ot&lang=en&redirect=on#prereq) [B] 
sudo aa-complain cupsd     [/B]Unfortunately this one didn't work and     returned [I]sudo:     aa-complain: command not found
 [/I]**sudo mkdir /usr/share/cups/model **

 
As I noted the printer is now working… but the print area vs page is wrong with  half of the top print line being off the top of the page and the bottom line is moved up the page by about the same amount.
  I have checked:
 Librewriter Format>Page>Page shows the Page Format is set to A4 (210x297) with 20mm margins.
 Printer-localhost>Printer Properties>Printer Options>Media is set to A4 (I have also unsuccessfully tried A4 Borderless).
 
 Going to [http://localhost:631/printers/DCP135C](http://localhost:631/printers/DCP135C) returns the following;
**Description:**     DCP135C
 [LEFT][B]Location:         
Driver:[/B]         Brother DCP-135C CUPS v1.1 (color)
**Connection:**     usb://Brother/DCP-135C?serial=BROE8F960670
**Defaults:**         Job-sheets=none, none media=iso_a4_210x297mm                    sides=one-sided

[/LEFT]
As for the scanner, not much to report, I have the drivers, and have searched for info online but Simple-scan only ever returns “No scanners detected”.
I have seen a number of posts with the following instructions, (unfortunately I didn't have a file, 40-libsane.rules)
The following is from a helpful post by [Daniel W.]("https://askubuntu.com/users/32010/daniel-w") [https://askubuntu.com/questions/113272/how-to-configure-brother-dcp-7030-scanner](https://askubuntu.com/questions/113272/how-to-configure-brother-dcp-7030-scanner) 
  
[I]Finally type 
sudo gedit /lib/udev/rules.d/40-libsane.rules 

  and at the following text right before this line (pretty far down at the bottom)
  '# The following rule will disable USB autosuspend for the device'
  Text to add: 
# Brother scanners 
ATTRS{idVendor}=="04f9", ENV{libsane_matched}="yes" [/I]

  
Regards.

---

### Post by slickymaster on 2018-05-22
*Thread moved to **Hardware**.*

---

### Post by kenj69 on 2018-06-05
Maybe this topic can help, at least with the scanner -->

[https://ubuntuforums.org/showthread.php?t=2388273](https://ubuntuforums.org/showthread.php?t=2388273)

-=Ken=-

---

