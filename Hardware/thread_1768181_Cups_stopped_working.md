---
title: "Cups stopped working"
date: 2011-05-26
forum: Hardware
---

### Post by dargaud on 2011-05-26
Hello all,
I just noticed that the 11.04 upgrade broke my printing. I would get the message
```
stopped  "File '/System/Library/ColorSync/Profiles/sRGB Profile.icc' not found"
```
So I looked around, plenty of hits on google with those keywords, but very inconclusive. I tried: 
- blacklisting the usblp driver
- deleting/reinstalling the printer
- using the full or simplified driver (Epson R1800)
- printing from Virtualbox (this works).
- editing /etc/cups/ppd/EPSON_Stylus_Photo_R1800.ppd to remove the lines with the non-existant ...ColorSync... directory which is aparently for the Mac, but now I'm stuck with ```
stopped 
"/usr/lib/cups/filter/pdftoraster-poppler failed"
```  which also has tons of hits all over the place.

Suggestions ?!?

---

### Post by avryhof on 2011-05-27
I'm no expert, but have had some dealings with Adjusting ICC Profiles for Scribus, Gimp and Krita.

Reading through the cups mailing list, it looks like it's a bug in gutenprint that just surfaced with the newest release that changed the PDF library (looks like to poppler) which actually uses the ICC Profiles now.

looks like someone submitted a bug report... but it might be a good idea to if pointing your PPD to installed ICC Profiles works.

Check /usr/share/color/icc/ to see if you have an sRGB.icc in there and point your PPD to it. (looks like there are a few incorrect paths in some PPDs, so point them appropriately if you need to)

Not sure if this will work, but if you really need to print, it might be worth a try.

---

### Post by dargaud on 2011-05-27
Thanks for the answer.

I don't have a /usr/share/color directory. A search for icc profiles on my system finds nothing. I have a sRGB.icc leftover from an old Windows backup, are they all equivalent ?

Hopefully if this is a recognized bug, it will be corrected quickly... But unfortunately writing printing software is not a sexy activity so I'll keep my fingers crossed.

---

### Post by dargaud on 2011-05-27
Some additional info: I can print a self-test page but not a test page... From the /var/log/cups/error_log file:
```

Job stopped due to filter errors; please consult the error_log file for details.
The following messages were recorded from 16:32:21 to 16:32:22
Adding start banner page "none".
Adding end banner page "none".
File of type application/vnd.cups-banner queued by "dargaud".
hold_until=0
Queued on "EPSON_Stylus_Photo_R1800" by "dargaud".
job-sheets=none,none
argv[0]="EPSON_Stylus_Photo_R1800"
argv[1]="123"
argv[2]="dargaud"
argv[3]="Test Page"
argv[4]="1"
argv[5]="job-uuid=urn:uuid:0b209b6b-792c-3e47-550d-d8772d53df3d job-originating-host-name=localhost time-at-creation=1306506741 time-at-processing=1306506741 AP_D_InputSlot="
argv[6]="/var/spool/cups/d00123-001"
envp[0]="CUPS_CACHEDIR=/var/cache/cups"
envp[1]="CUPS_DATADIR=/usr/share/cups"
envp[2]="CUPS_DOCROOT=/usr/share/cups/doc-root"
envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
envp[4]="CUPS_REQUESTROOT=/var/spool/cups"
envp[5]="CUPS_SERVERBIN=/usr/lib/cups"
envp[6]="CUPS_SERVERROOT=/etc/cups"
envp[7]="CUPS_STATEDIR=/var/run/cups"
envp[8]="HOME=/var/spool/cups/tmp"
envp[9]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
envp[10]="SERVER_ADMIN=root@penguin"
envp[11]="SOFTWARE=CUPS/1.4.6"
envp[12]="TMPDIR=/var/spool/cups/tmp"
envp[13]="USER=root"
envp[14]="CUPS_SERVER=/var/run/cups/cups.sock"
envp[15]="CUPS_ENCRYPTION=IfRequested"
envp[16]="IPP_PORT=631"
envp[17]="CHARSET=utf-8"
envp[18]="LANG=en_US.UTF-8"
envp[19]="PPD=/etc/cups/ppd/EPSON_Stylus_Photo_R1800.ppd"
envp[20]="RIP_MAX_CACHE=auto"
envp[21]="CONTENT_TYPE=application/vnd.cups-banner"
envp[22]="DEVICE_URI=usb://EPSON/Stylus%20Photo%20R1800?serial=RS0070507301426530"
envp[23]="PRINTER_INFO=EPSON Stylus Photo R1800"
envp[24]="PRINTER_LOCATION="
envp[25]="PRINTER=EPSON_Stylus_Photo_R1800"
envp[26]="CUPS_FILETYPE=document"
envp[27]="FINAL_CONTENT_TYPE=printer/EPSON_Stylus_Photo_R1800"
Started filter /usr/lib/cups/filter/bannertops (PID 16384)
Started filter /usr/lib/cups/filter/pstopdf (PID 16385)
Started filter /usr/lib/cups/filter/pdftopdf (PID 16386)
Started filter /usr/lib/cups/filter/pdftoraster-poppler (PID 16387)
Started filter /usr/lib/cups/filter/rastertogutenprint.5.2 (PID 16388)
Started backend /usr/lib/cups/backend/usb (PID 16389)
pstopdf 5 args: 123 dargaud Test Page 1 job-uuid=urn:uuid:0b209b6b-792c-3e47-550d-d8772d53df3d job-originating-host-name=localhost time-at-creation=1306506741 time-at-processing=1306506741 AP_D_InputSlot=
PPD: /etc/cups/ppd/EPSON_Stylus_Photo_R1800.ppd
STATE: +connecting-to-device
print_device_libusb
usb_find_busses=8
load_banner(filename="/var/spool/cups/d00123-001")
Page = 595x842; 0,0 to 595,842
PNG image: 128x128x8, color_type=6 (RGB+ALPHA)
PNG image: 192x128x8, color_type=2 (RGB)
Resolution: 361x360
Gutenprint 5.2.6 Starting
Gutenprint command line: EPSON_Stylus_Photo_R1800 '123' 'dargaud' 'Test Page' '1' <args>
Gutenprint using PPD file /etc/cups/ppd/EPSON_Stylus_Photo_R1800.ppd
Gutenprint: CUPS option count is 5 (164 bytes)
Gutenprint: CUPS option 0 AP_D_InputSlot = 
Gutenprint: CUPS option 1 job-originating-host-name = localhost
Gutenprint: CUPS option 2 job-uuid = urn:uuid:0b209b6b-792c-3e47-550d-d8772d53df3d
Gutenprint: CUPS option 3 time-at-creation = 1306506741
Gutenprint: CUPS option 4 time-at-processing = 1306506741
Gutenprint: Driver Epson Stylus Photo R1800
Gutenprint: Using fd 0
Page size: A4
Gutenprint: Set options:
[...]
Gutenprint: End options
Width: 595, height: 842, absolute margins: 0, 0, 595, 842
Relative margins: 0, 0, 0, 0
PPD options: -r360 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842
PostScript to be injected: 
Running cat | /usr/bin/gs -q -dNOPAUSE -dBATCH -sDEVICE=pdfwrite -dCompatibilityLevel=1.3 -dAutoRotatePages=/None -dAutoFilterColorImages=false -dNOPLATFONTS -dPARANOIDSAFER -sstdout=%stderr -dColorImageFilter=/FlateEncode                 -dPDFSETTINGS=/printer                 -dColorConversionStrategy=/LeaveColorUnchanged -dDoNumCopies -r360 -dDEVICEWIDTHPOINTS=595 -dDEVICEHEIGHTPOINTS=842 -sOutputFile=-  -c .setpdfwrite -f -
usb_find_devices=12
STATE: +connecting-to-device
STATE: -connecting-to-device
Gutenprint: About to start printing loop.
mediaBox = [ 0.000000 0.000000 595.000000 842.000000 ]
size = A4
Bogus memory allocation size
Gutenprint: Printed total 0 bytes
Gutenprint: Used 0.070 seconds user, 0.020 seconds system, 0.757 seconds elapsed
End of messages
printer-state=3(idle)
printer-state-message="/usr/lib/cups/filter/pdftoraster-poppler failed"
printer-state-reasons=none
Stopping unresponsive job!

```

---

### Post by avryhof on 2011-05-27
You can try your sRGB.icc profile.  The only difference if any would be different color information....unless it is one from your printer software, in which case it would probably be more accurate than the gutenprint one could be.

I wouldn't worry too much about what the actual path is, as long as your PPD points to the right place.  There are a few "right" places to put profiles, such as ~/.color or /usr/share/color (mine was probably created by Scribus or the CMYK filter for Gimp) but you're probably safe just dropping it in your home folder, and pointing to it in your PPD.  You might have a CUPS or Print group/user so you should also make sure whichever it is has permissions to access the file.

Looking at your log, it looks like poppler is what is failing, so I would bet it's the color profile.

The tell-tale lines are

[INDENT]Job stopped due to filter errors; please consult the error_log file for details.
printer-state-message="/usr/lib/cups/filter/pdftoraster-poppler failed"[/INDENT]

My guess is that CUPS is getting the job as PostScript, and trying to Rasterize (make it a bitmap) it before sending it to the printer.

As for the self test vs. test page, I would guess the self test is generated by the printer with a command, where the test page is "sent" to the printer as a job.

This is all guesswork though, but it *seems* simple enough. :) Worst case scenario, your printer still doesn't work.... otherwise, you learned something handy.

---

### Post by dargaud on 2011-05-27
Yes, this last log was generated after I changed the profiles in the /etc/cups/ppd/EPSON_Stylus_Photo_R1800.ppd file. Your observations go along with my own conclusions, but where do I go from there ? Can I switch pdftoraster-poppler with pdftoraster ?

I'm just surprised at the complexity of the printing process which, if I read the log correctly, goes from banner to ps, then ps to pdf, then pdf to pdf (!?!), then pdf to raster-poppler, and finally raster to gutenprint.5.2.

---

### Post by avryhof on 2011-05-27
Based on [https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/765514](https://bugs.launchpad.net/ubuntu/+source/poppler/+bug/765514)

making pdftoraster-poppler a symlink to pdftoraster works fine for the poster, so I'm guessing you can.

---

### Post by dargaud on 2011-05-28
Great, thanks, that worked. I should have tried without asking first...

---

