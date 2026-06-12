---
title: "Brother MFC-J450DW says it's connected, but wont print Ubuntu 20.04"
date: 2022-04-30
forum: Hardware
---

### Post by xl11a on 2022-04-30
I know that this is a common question ,but I haven't been able to find a solution yet.
Did a clean install of 20.04 on SSD. I am trying to get a Brother MFC-J450DW printer to work, but am having no luck with this install. I haven't had any issues doing this install on other older versions of Ubuntu, but doesn't seem to want to work here.
 Have gone to the Brother support page and downloaded and run their installer. Also tried downloading and installing deb files for the cupswrapper, lpr driver. scanner. Nothing seems to work. When I try to print, the printer says it is receiving data, but does not print. 
If I go to settings/ printers, two printers show up. One says " Cups"  (local host) The other doesn't and is "null" 
If I go into additional setting of the printer /printer properties the "uri:" says usb:/dev/usb/lp0  not sure if this is what it is supposed to be?

BTW this is just a simple USB plug in.

Any help will be greatly appreciated.

---

### Post by xl11a on 2022-05-01
FWIW
The printer will print when I manually ask it to clean print heads and do a test page, so it is working.

---

### Post by ActionParsnip on 2022-05-01
If you run an application like gedit as root then print from that, is it OK? This will show its a permissions issue

---

### Post by xl11a on 2022-05-01
Thanks.
Ran gedit as root, and tried to open a simple test file, but got...
"(gedit:94484): Tepl-WARNING **: 23:41:48.481: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata." ?
Tried to create a file while in gedit to print, same result. Tried to print them but no response from printer.

---

### Post by mIk3_08 on 2022-05-02
> **xl11a said:**
> I know that this is a common question ,but I haven't been able to find a solution yet.
Did a clean install of 20.04 on SSD. I am trying to get a Brother MFC-J450DW printer to work, but am having no luck with this install. I haven't had any issues doing this install on other older versions of Ubuntu, but doesn't seem to want to work here.
 Have gone to the Brother support page and downloaded and run their installer. Also tried downloading and installing deb files for the cupswrapper, lpr driver. scanner. Nothing seems to work. When I try to print, the printer says it is receiving data, but does not print. 
If I go to settings/ printers, two printers show up. One says " Cups"  (local host) The other doesn't and is "null" 
If I go into additional setting of the printer /printer properties the "uri:" says usb:/dev/usb/lp0  not sure if this is what it is supposed to be?

BTW this is just a simple USB plug in.

Any help will be greatly appreciated.
Do your Brother MFC-J450DW printer/scanner can be connected wirelessly directly to your router? I bet your printer is capable and can be connected thru wireless. If so, try to connect it into your router wirelessly then try to add it to your Linux Ubuntu Operating System machine wirelessly because my brother printer/scanner works smoothly with my Linux Ubuntu Operating System laptop connected vai wireless connection. My brother scanner works smoothly with Linux Ubuntu simple scan application and Xsane Image scanning application software. This setting works from over 7 years now without no hassle so far. Regards and cheers.

---

### Post by slickymaster on 2022-05-02
*Thread moved to **Hardware**.*

---

### Post by brian_p on 2022-05-02
Please give ```
dpkg -l ippusbxd
```

---

### Post by xl11a on 2022-05-02
> **mIk3_08 said:**
> Do your Brother MFC-J450DW printer/scanner can be connected wirelessly directly to your router? I bet your printer is capable and can be connected thru wireless. If so, try to connect it into your router wirelessly then try to add it to your Linux Ubuntu Operating System machine wirelessly because my brother printer/scanner works smoothly with my Linux Ubuntu Operating System laptop connected vai wireless connection. My brother scanner works smoothly with Linux Ubuntu simple scan application and Xsane Image scanning application software. This setting works from over 7 years now without no hassle so far. Regards and cheers.

Thanks, but my desktop setup is wireless :-(

---

### Post by xl11a on 2022-05-02
> **brian_p said:**
> Please give ```
dpkg -l ippusbxd
```


$ dpkg -l ippusbxd
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
un  ippusbxd       <none>       <none>       (no description available)

---

### Post by brian_p on 2022-05-02
> **xl11a said:**
> Thanks, but my desktop setup is wireless :-(

Earlier in this thread you said > BTW this is just a simple USB plug in

What did you mean by that? It seems to contradict what you say above.

---

### Post by brian_p on 2022-05-02
> **xl11a said:**
> Thanks, but my desktop setup is wireless :-(

That makes it easier to get you on the right path to printing. Give

```
avahi-browse -rt _ipp._tcp
```
```
avahi-browse -rt _uscan._tcp
```
```
driverless
```

---

### Post by xl11a on 2022-05-03
> **brian_p said:**
> Earlier in this thread you said 

What did you mean by that? It seems to contradict what you say above.


Apologies Sorry for the confusion Brian.
To clarify...My printer plugs directly into my computer via USB. I meant to say that My motherboard has no wifi capabilities unless I add a card, instead of wireless. So the solution about using my router wouldn't work.

---

### Post by mIk3_08 on 2022-05-03
> **xl11a said:**
> Thanks, but my desktop setup is wireless :-( 
That's okay. It won't affect if your desktop set up via wireless and also your brother printer because my system setting has also the same set up with that. My Linux Ubuntu laptop and brother printer/scanner is connected to one router wirelessly and it works smoothly. Regards and cheers.

---

### Post by brian_p on 2022-05-03
> **xl11a said:**
> Apologies Sorry for the confusion Brian.
To clarify...My printer plugs directly into my computer via USB. I meant to say that My motherboard has no wifi capabilities unless I add a card, instead of wireless. So the solution about using my router wouldn't work.

OK, you have a USB connection to the computer you want to print from.

The Brother MFC-J450DW is too old to offer driverless printing on USB. It should be capable of driverless printing  with a wireless but such a connection is not your preferred option. So, for USB, we would need to know

```
lpinfo -v
``` ```
lpinfo -m | grep -i J450
```

---

### Post by xl11a on 2022-05-03
> **brian_p said:**
> OK, you have a USB connection to the computer you want to print from.

The Brother MFC-J450DW is too old to offer driverless printing on USB. It should be capable of driverless printing  with a wireless but such a connection is not your preferred option. So, for USB, we would need to know

```
lpinfo -v
``` ```
lpinfo -m | grep -i J450
```

```
$ lpinfo -v
network lpd
file cups-brf:/
direct hp
network https
serial serial:/dev/ttyS0?baud=115200
network beh
network ipp
network ipps
network socket
network http
direct usb://Brother/MFC-J480DW?serial=U64037C8H308289
direct hpfax
```
```
$ lpinfo -m | grep -i J450
Brother/brother_mfcj450dw_printer_en.ppd Brother MFC-J450DW CUPS
lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd Brother MFC-J450DW CUPS
hplip:0/ppd/hplip/HP/hp-dj450.ppd HP dj450, hpcups 3.19.8
hplip:1/ppd/hplip/HP/hp-dj450.ppd HP dj450, hpcups 3.19.8
hplip:2/ppd/hplip/HP/hp-dj450.ppd HP dj450, hpcups 3.19.8
hplip:3/ppd/hplip/HP/hp-dj450.ppd HP dj450, hpcups 3.19.8
drv:///hpijs.drv/hp-officejet_j4500_series-hpijs.ppd HP Officejet j4500 Series hpijs, 3.20.3
hplip:0/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:1/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:2/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:3/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:4/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:5/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:6/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:7/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:8/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
hplip:9/ppd/hplip/HP/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
drv:///hpcups.drv/hp-officejet_j4500_series.ppd HP Officejet j4500 Series, hpcups 3.20.3
```

---

### Post by xl11a on 2022-05-03
> **mIk3_08 said:**
> That's okay. It won't affect if your desktop set up via wireless and also your brother printer because my system setting has also the same set up with that. My Linux Ubuntu laptop and brother printer/scanner is connected to one router wirelessly and it works smoothly. Regards and cheers.

[COLOR=#000000]Apologies Sorry for the confusion [/COLOR]
[COLOR=#000000]To clarify...My printer plugs directly into my computer via USB. I meant to say that My motherboard has no wifi capabilities unless I add a card, instead of wireless.[/COLOR]

---

### Post by brian_p on 2022-05-03
From your info we have

```
usb://Brother/MFC-J480DW?serial=U64037C8H308289
``` and ```
lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd
```

The first is a **URI**. The second is a **PPD**.

**Substitute** for URI and PPD in this command:

Execute ```
lpadmin -p J480 -v "URI" -E -m "PPD"
```

Test printing with ```
lp -d J480 /etc/nsswitch.conf
```

---

### Post by xl11a on 2022-05-03
> **brian_p said:**
> From your info we have

```
usb://Brother/MFC-J480DW?serial=U64037C8H308289
``` and ```
lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd
```

The first is a **URI**. The second is a **PPD**.

**Substitute** for URI and PPD in this command:

Execute ```
lpadmin -p J480 -v "URI" -E -m "PPD"
```

Test printing with ```
lp -d J480 /etc/nsswitch.conf
```

Thank you, but you have kinda jumped a bit past me here.
What do I substitute ? Just the model numbers, or those complete lines?

---

### Post by brian_p on 2022-05-03
Here is the complete command:

```
lpadmin -p J480 -v "usb://Brother/MFC-J480DW?serial=U64037C8H308289" -E -m "lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd"
```

---

### Post by xl11a on 2022-05-03
> **brian_p said:**
> Here is the complete command:

```
lpadmin -p J480 -v "usb://Brother/MFC-J480DW?serial=U64037C8H308289" -E -m "lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd"
```


Thanks you!

This is the output
lpadmin: Printer drivers are deprecated and will stop working in a future version of CUPS.


lp -d J480 /etc/nsswitch.conf
request id is J480-66 (1 file(s))

Printer lights came on, but nothing printed.

---

### Post by brian_p on 2022-05-04
> **xl11a said:**
> Thanks you!

This is the output
lpadmin: Printer drivers are deprecated and will stop working in a future version of CUPS.

Nothing to worry about
> 
lp -d J480 /etc/nsswitch.conf
request id is J480-66 (1 file(s))

Printer lights came on, but nothing printed.

The lpadmin command is as fundamental as it gets. If URI and PPD are correct, it sets up what should be a working print queue. Let's check filtering:

```
sudo cupsfilter -p /etc/cups/ppd/J480.ppd -m printer/foo -e /etc/nsswitch.conf > out.dat 2> log.txt
```

Attach the file **log.txt** to your next post here. You may view it with ```
less log.txt
```

---

### Post by mIk3_08 on 2022-05-04
> **xl11a said:**
> [COLOR=#000000]Apologies Sorry for the confusion [/COLOR]
[COLOR=#000000]To clarify...My printer plugs directly into my computer via USB. I meant to say that My motherboard has no wifi capabilities unless I add a card, instead of wireless.[/COLOR]
My bad too. Sorry. What i meant is your bother printer/scanner can be connected directly to your wireless router or via wifi. There is no need to attached your brother printer/scanner to your desktop via usb. Just connect it directly to your router via wifi. Have you tried it? Regards and Cheers.

---

### Post by xl11a on 2022-05-04
> **brian_p said:**
> Nothing to worry about


The lpadmin command is as fundamental as it gets. If URI and PPD are correct, it sets up what should be a working print queue. Let's check filtering:

```
sudo cupsfilter -p /etc/cups/ppd/J480.ppd -m printer/foo -e /etc/nsswitch.conf > out.dat 2> log.txt
```

Attach the file **log.txt** to your next post here. You may view it with ```
less log.txt
```

```
cupsfilter: File "/usr/lib/cups/filter/brother_lpdwrapper_mfcj450dw" permissions OK (040755/uid=0/gid=0).
cupsfilter: File "/usr/lib/cups/filter/commandtops" permissions OK (040755/uid=0/gid=0).
DEBUG: argv[0]="cupsfilter"
DEBUG: argv[1]="1"
DEBUG: argv[2]="root"
DEBUG: argv[3]="nsswitch.conf"
DEBUG: argv[4]="1"
DEBUG: argv[5]=""
DEBUG: argv[6]="/etc/nsswitch.conf"
DEBUG: envp[0]="<CFProcessPath>"
DEBUG: envp[1]="CONTENT_TYPE=text/plain"
DEBUG: envp[2]="CUPS_DATADIR=/usr/share/cups"
DEBUG: envp[3]="CUPS_FONTPATH=/usr/share/cups/fonts"
DEBUG: envp[4]="CUPS_SERVERBIN=/usr/lib/cups"
DEBUG: envp[5]="CUPS_SERVERROOT=/etc/cups"
DEBUG: envp[6]="LANG=en_CA.UTF8"
DEBUG: envp[7]="PATH=/usr/lib/cups/filter:/usr/bin:/usr/sbin:/bin:/usr/bin"
DEBUG: envp[8]="PPD=/etc/cups/ppd/J480.ppd"
DEBUG: envp[9]="PRINTER_INFO=cupsfilter"
DEBUG: envp[10]="PRINTER_LOCATION=Unknown"
DEBUG: envp[11]="PRINTER=cupsfilter"
DEBUG: envp[12]="RIP_MAX_CACHE=128m"
DEBUG: envp[13]="USER=root"
DEBUG: envp[14]="CHARSET=utf-8"
DEBUG: envp[15]="FINAL_CONTENT_TYPE=application/vnd.cups-postscript"
INFO: texttopdf (PID 97246) started.
INFO: pdftopdf (PID 97247) started.
INFO: pdftops (PID 97248) started.
INFO: brother_lpdwrapper_mfcj450dw (PID 97249) started.
DEBUG: Page = 612x792; 9,9 to 603,783
DEBUG: pdftops - copying to temp print file "/tmp/17be0627911f4"
DEBUG: pdftopdf: Last filter determined by the PPD: brother_lpdwrapper_mfcj450dw; FINAL_CONTENT_TYPE: application/vnd.cups-postscript => pdftopdf will not log pages in page_log.
INFO: texttopdf (PID 97246) exited with no errors.
DEBUG: PDF interactive form and annotation flattening done via QPDF
INFO: pdftopdf (PID 97247) exited with no errors.
DEBUG: Printer make and model: Brother MFC-J450DW
DEBUG: Switching to Poppler's pdftops instead of Ghostscript for Brother, Minolta, Konica Minolta, Dell, and Apple LaserWriter 16/600, 4/600, 12/640, 12/600, 12/660 to work around bugs in the printer's PS interpreters
DEBUG: Running command line for pstops: pstops 1 root nsswitch.conf 1 
DEBUG: No resolution information found in the PPD file.
DEBUG: Using image rendering resolution 300 dpi
DEBUG: Running command line for pdftops: pdftops -level2 -origpagesizes -nocenter -r 300 /tmp/17be0627911f4 -
DEBUG: Started filter pdftops (PID 97265)
DEBUG: Started filter pstops (PID 97266)
DEBUG: Page = 612x792; 9,9 to 603,783
DEBUG: slow_collate=0, slow_duplex=0, slow_order=0
DEBUG: Before copy_comments - %!PS-Adobe-3.0
DEBUG: %!PS-Adobe-3.0
DEBUG: %Produced by poppler pdftops version: 0.86.1 ([http://poppler.freedesktop.org](http://poppler.freedesktop.org))
DEBUG: %%Creator: texttopdf/1.27.4
DEBUG: %%LanguageLevel: 2
DEBUG: %%DocumentSuppliedResources: (atend)
DEBUG: %%DocumentMedia: Letter 612 792 0 () ()
DEBUG: %%BoundingBox: 0 0 612 792
DEBUG: %%Pages: 1
DEBUG: %%EndComments
DEBUG: Before copy_prolog - %%BeginProlog
DEBUG: Before copy_setup - %%BeginSetup
DEBUG: Before page loop - %%Page: 1 1
DEBUG: Copying page 1...
DEBUG: pagew = 594.0, pagel = 774.0
DEBUG: bboxx = 0, bboxy = 0, bboxw = 612, bboxl = 792
DEBUG: PageLeft = 9.0, PageRight = 603.0
DEBUG: PageTop = 783.0, PageBottom = 9.0
DEBUG: PageWidth = 612.0, PageLength = 792.0
DEBUG: Wrote 1 pages...
DEBUG: PID 97265 (pdftops) exited with no errors.
DEBUG: PID 97266 (pstops) exited with no errors.
INFO: pdftops (PID 97248) exited with no errors.
DATA======*DefaultPageSize: Letter
search_data======DefaultPageSize
DATA======: Letter
search_data======Letter
DATA======*DefaultBRDuplex: None
search_data======DefaultBRDuplex
DATA======: None
search_data======None
DATA======*DefaultBRMediaType: Plain
search_data======DefaultBRMediaType
DATA======: Plain
search_data======Plain
DATA======*DefaultBRSlowDrying: OFF
search_data======DefaultBRSlowDrying
DATA======: OFF
search_data======OFF
DATA======*DefaultBRResolution: PlainNormal
search_data======DefaultBRResolution
DATA======: PlainNormal
search_data======PlainNormal
DATA======*DefaultBRMonoColor: Color
search_data======DefaultBRMonoColor
DATA======: Color
search_data======Color
DATA======*DefaultBRColorPaperThick: Regular
search_data======DefaultBRColorPaperThick
DATA======: Regular
search_data======Regular
DATA======*DefaultBRBiDir: ON
search_data======DefaultBRBiDir
DATA======: ON
search_data======ON
DATA======*DefaultBRDuplexMode: Normal
search_data======DefaultBRDuplexMode
DATA======: Normal
search_data======Normal
DATA======*DefaultBRJpeg: Recommended
search_data======DefaultBRJpeg
DATA======: Recommended
search_data======Recommended
DATA======*DefaultBRColorMatching: Vivid
search_data======DefaultBRColorMatching
DATA======: Vivid
search_data======Vivid
DATA======*DefaultBRHalfTonePattern: Diffusion
search_data======DefaultBRHalfTonePattern
DATA======: Diffusion
search_data======Diffusion
DATA======*DefaultBRColorEnhancement: OFF
search_data======DefaultBRColorEnhancement
DATA======: OFF
search_data======OFF
DATA======*DefaultBRBrightness: 0
search_data======DefaultBRBrightness
DATA======*DefaultBRContrast: 0
search_data======DefaultBRContrast
DATA======*DefaultBRRed: 0
search_data======DefaultBRRed
DATA======*DefaultBRGreen: 0
search_data======DefaultBRGreen
DATA======*DefaultBRBlue: 0
search_data======DefaultBRBlue
/usr/lib/cups/filter/brother_lpdwrapper_mfcj450dw: 137: cannot create /tmp/mfcj450dw_latest_print_info: Permission denied
/usr/lib/cups/filter/brother_lpdwrapper_mfcj450dw: 138: cannot create /tmp/mfcj450dw_latest_print_info: Permission denied
INFO: brother_lpdwrapper_mfcj450dw (PID 97249) exited with no errors.
```

---

### Post by slickymaster on 2022-05-04
@xl11a

Please [use [CODE] tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in your posts when pasting terminal output.

Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

---

### Post by xl11a on 2022-05-04
> **mIk3_08 said:**
> My bad too. Sorry. What i meant is your bother printer/scanner can be connected directly to your wireless router or via wifi. There is no need to attached your brother printer/scanner to your desktop via usb. Just connect it directly to your router via wifi. Have you tried it? Regards and Cheers.

No worries. Yes, can connect to router via wifi, but desktop has no way of communicating with it that I know of. Unless I am missing something obvious right under my nose. and that wouldn't be unusual lol.

---

### Post by brian_p on 2022-05-04
Three filters are started:

> INFO: pdftopdf (PID 97247) started.
INFO: pdftops (PID 97248) started.
INFO: brother_lpdwrapper_mfcj450dw (PID 97249) started.

All three are reported as exiting successfully, but for brother_lpdwrapper_mfcj450dw we see

> /usr/lib/cups/filter/brother_lpdwrapper_mfcj450dw: 137: cannot create /tmp/mfcj450dw_latest_print_info: Permission denied
/usr/lib/cups/filter/brother_lpdwrapper_mfcj450dw: 138: cannot create /tmp/mfcj450dw_latest_print_info: Permission denied

This is a non-free filter that I know nothing about. I assume the message indicates  the reason for non-printing.I cannot help any further. Maybe delete the Brother drivers and reinstall them? Contact Brother?

---

### Post by brian_p on 2022-05-04
You could always use a wireless connection, of course, if you did, we would want

```
avahi-browse -rt _ipp._tcp
```
```
avahi-browse -rt _uscan._tcp
```

```
driverless
```

---

### Post by xl11a on 2022-05-04
> **slickymaster said:**
> @xl11a

Please [use [CODE] tags]("https://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") in your posts when pasting terminal output.

Output posted as plain text loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand.

Thanks you. 
New to this and wasn't sure how to do that. Learning.

---

### Post by xl11a on 2022-05-04
> **brian_p said:**
> Three filters are started:



All three are reported as exiting successfully, but for brother_lpdwrapper_mfcj450dw we see



This is a non-free filter that I know nothing about. I assume the message indicates  the reason for non-printing.I cannot help any further. Maybe delete the Brother drivers and reinstall them? Contact Brother?


Thanks you .

I'm throwing this out there as a long shot, but... My OS is now 64 bit. The drivers seem to still be 32 bit. Would that make any difference?

---

### Post by mIk3_08 on 2022-05-05
> **xl11a said:**
> but desktop has no way of communicating with it  that I know of.  Does your Desktop don't have any LAN ports?  lol. So how do you connect your Linux Ubuntu Desktop to the Internet?  Are you also using a USB Ethernet for you LAN card? If so, That will not  be a problem anyway as long as your Linux Ubuntu Desktop is connected  to same router as your Brother printer/scanner is connected with.  Regards and Cheers.

---

### Post by brian_p on 2022-05-05
Please give ```
ls -l out.dat
``` ```
file out.dat
```

---

### Post by xl11a on 2022-05-21
> **brian_p said:**
> Please give ```
ls -l out.dat
``` ```
file out.dat
```

So sorry, Had to let this drop to deal with some life stuff. Now back

ls -l out.dat
-rw-rw-r-- 1 speedy speedy 542 May  4 12:02 out.dat

file out.dat
out.dat: ASCII text

---

### Post by xl11a on 2022-05-21
> **mIk3_08 said:**
> Does your Desktop don't have any LAN ports?  lol. So how do you connect your Linux Ubuntu Desktop to the Internet?  Are you also using a USB Ethernet for you LAN card? If so, That will not  be a problem anyway as long as your Linux Ubuntu Desktop is connected  to same router as your Brother printer/scanner is connected with.  Regards and Cheers.


Apologies for the delay in reply.
Forgive me here since I'm getting help at this from two completely different directions, so brain is having to shift and is a bit slow. LOL

Yes, desktop has Lan port . (Motherboard is MSI B550 Tomahawk)
Internet is connected to modem, and modem directly to computer. Also, from Modem line runs to Router for wifi HTH
Thanks!

---

### Post by xl11a on 2022-05-24
Apologies had to drop this for a bit, due to some health issues, but am now back, and would like to go back to getting this resolved.
So bringing it back up to the top.
Thanks.

---

### Post by mIk3_08 on 2022-05-25
Which do you prefer to connect your printer/scanner? via 
1. USB directly connected to your Desktop Computer System? 
 or
2. wireless directly connected to your wireless router?

If you choose to connect your printer/scanner via USB directly connected to your Desktop
You do not need to connect your printer/scanner wireless directly to your wireless router.

And if you choose to connect your printer/scanner via wireless directly to your wireless router
You do not need to connect your printer/scanner vai USB directly connected to your Desktop 

So what option do you choose? Regards and Cheers.

---

### Post by xl11a on 2022-05-25
> **mIk3_08 said:**
> Which do you prefer to connect your printer/scanner? via 
1. USB directly connected to your Desktop Computer System? 
 or
2. wireless directly connected to your wireless router?

If you choose to connect your printer/scanner via USB directly connected to your Desktop
You do not need to connect your printer/scanner wireless directly to your wireless router.

And if you choose to connect your printer/scanner via wireless directly to your wireless router
You do not need to connect your printer/scanner vai USB directly connected to your Desktop 

So what option do you choose? Regards and Cheers.


Would prefer, and have always used direct connection via USB to desktop. 
Normally this has always been an easy setup. Download and printer drivers from Brother page, and printer works.

---

### Post by mIk3_08 on 2022-05-27
> **xl11a said:**
> Would prefer, and have always used direct connection via USB to desktop. 
Normally this has always been an easy setup. Download and printer drivers from Brother page, and printer works.
I haven't tried using my printer/scanner connected directly to my Linux Ubuntu machine via USB. I only use wifi sharing connection method of my printer/scanner. We just have to wait to others in this community who has any experience on this kind of printer/scanner setup. Regards and Cheers.

---

### Post by xl11a on 2022-05-27
> **mIk3_08 said:**
> I haven't tried using my printer/scanner connected directly to my Linux Ubuntu machine via USB. I only use wifi sharing connection method of my printer/scanner. We just have to wait to others in this community who has any experience on this kind of printer/scanner setup. Regards and Cheers.


Understand. Thanks for trying.  Cheers.

---

### Post by iamjiwjr on 2022-05-27
Ubuntu was not able to handle Brother printing and scanning adequately until 20.10, when the package sane-airscan was added. My Brother HL-L2390DW printer-scanner was useless on Ubuntu until 20.10.

I suggest doing a fresh 22.04 install. I bet it'll work fine then.

---

### Post by him610 on 2022-05-27
> Ubuntu was not able to handle Brother printing and scanning adequately until 20.10
That statement is absolutely UNTRUE! I have owned a Brother MFC-7360N for several years now, and have never experienced any issues with setup or operation of any of the multi-function capabilities.

---

### Post by mIk3_08 on 2022-05-28
> **iamjiwjr said:**
> Ubuntu was not able to handle Brother printing and scanning adequately until 20.10, when the package sane-airscan was added. My Brother HL-L2390DW printer-scanner was useless on Ubuntu until 20.10.
I suggest doing a fresh 22.04 install. I bet it'll work fine then.
I have my Brother DCP printer/scanner working smoothly with my two Linux Ubuntu system for a quite a while now. I successfully connected my Brother DCP printer/scanner to my local router via wifi. printer is working smoothly with my two Linux Ubuntu system and also the scanner works great with simple scan an Ubuntu image scanning program and Xsane  application an image scanning application for Linux. so far I haven't experience any error using it for many years now. Regards and cheers.

---

### Post by xl11a on 2022-05-28
> **iamjiwjr said:**
> Ubuntu was not able to handle Brother printing and scanning adequately until 20.10, when the package sane-airscan was added. My Brother HL-L2390DW printer-scanner was useless on Ubuntu until 20.10.

I suggest doing a fresh 22.04 install. I bet it'll work fine then.

Noted.

---

### Post by xl11a on 2022-05-28
> **him610 said:**
> That statement is absolutely UNTRUE! I have owned a Brother MFC-7360N for several years now, and have never experienced any issues with setup or operation of any of the multi-function capabilities.

Also noted. Thanks

---

### Post by iamjiwjr on 2022-05-28
Sorry. My statement was inappropriately broad. Apologies.

---

### Post by mIk3_08 on 2022-05-29
Almost all devices can work on Linux Ubuntu machine its just that some new users don't have the patience to configure it. And they actually demanded too much. As they doesn't know that almost everyone here in this community are voluntarily contributors. The key here is to be more friendly so you can get what you need as the community are willing to help you. Regards and cheers.

---

### Post by xl11a on 2022-05-29
> **mIk3_08 said:**
> Almost all devices can work on Linux Ubuntu machine its just that some new users don't have the patience to configure it. And they actually demanded too much. As they doesn't know that almost everyone here in this community are voluntarily contributors. The key here is to be more friendly so you can get what you need as the community are willing to help you. Regards and cheers.

I appreciate you taking the time to respond and help, as well as guide me towards a better direction in seeking help.
 
I understand and appreciate the time and patience of all the volunteers that are willing to provide their time and help here. Apologies if I have in any way come off as being unfriendly or demanding. 
I am new to this forum, but not new to computers or Ubuntu. That being said... I am in no way remotely as knowledgeable as some of the folks on this forum, or claim to be. :-) I have to admit that some of the help I have received, has completely overwhelmed me, and is far beyond my comprehension, capabilities, and limited skill set. This might be the area that mistakenly comes off as me not having the patience to configure things... Simple answer...I want to try, but I just don't know how to, the knowledge base required is beyond me. No doubt many here have technical educations and backgrounds, and what to them is simple 101 basic logic, is light years beyond my grasp.
 
I posted here out of frustration, after exhausting all the regular methods of what should have been a simple Motherboard/CPU/OS upgrade, and subsequent installation of my working printer. 
I tried installing the normal drivers using the Brother driver installer tool, but no luck, I un-installed all the drivers and installed the Brother drivers individually, still no luck. I swapped out USB cables and tried all the different USB ports on the machine. I pulled up the "printer" in my settings page and tried to reconfigure it. I did numerous reboots of the system to make sure it wasn't something hanging up. I redid a clean install of the OS as well.
 I checked and made sure all my software was updated and current. I spent hours online searching forums for people that had had similar issues, seeking a solution.  I did find some posts where others were having similar issues with the 20.04 ver, but no solutions that applied to me. (I also searched forums that were using the motherboard that I had upgraded to, just to make sure.) 
What made me think that this was something beyond my abilities, was that my printer would respond to it having a "job" sent to it, as in, it would light up, and my machine would say "job has printed," but nothing was printed.
I tested the printer to do a head cleaning and print a test page via direct command input to the printer keypad, and it would complete the request. 

So I felt it was time to ask some experts and signed onto this forum. Being a "newb" here, I was trying to learn as I observed, but as everyone knows, every forum has it own set of rules and protocols, and some forums are purely technically driven, and ask you not to chat, or post any kind of smiley face content, and just post the technical details. Others are very social, and require a decent post count before members will "recognise" you. I'm just trying to find my footings here. So again apologies to this community if I have come across as seeming ungrateful, or unwilling to put the time and effort in to help myself.

Thank you.
Cheers

---

### Post by mIk3_08 on 2022-05-30
> **xl11a said:**
> I appreciate you taking the time to respond and help, as well as guide me towards a better direction in seeking help.
I understand and appreciate the time and patience of all the volunteers that are willing to provide their time and help here. Apologies if I have in any way come off as being unfriendly or demanding. 
I am new to this forum, but not new to computers or Ubuntu. That being said... I am in no way remotely as knowledgeable as some of the folks on this forum, or claim to be. :-) 
Again, as what I have said that some of us here are volunteers and also I accept that I am not knowledgeable/experts or pretend to be an experts here. I only share what I've experience about the use of Linux Ubuntu Operating System which in fact I have used this Linux Ubuntu Operating System for a quite a while now and I admit that I also encounter many problem using this Linux Ubuntu Operating System But I found a solution to solve my issue. I just kept read some thread post here on web and etc also in IRC. 

> **xl11a said:**
> 
I have to admit that some of the help I have received, has completely overwhelmed me, and is far beyond my comprehension, capabilities, and limited skill set. This might be the area that mistakenly comes off as me not having the patience to configure things... Simple answer...I want to try, but I just don't know how to, the knowledge base required is beyond me. No doubt many here have technical educations and backgrounds, and what to them is simple 101 basic logic, is light years beyond my grasp.
I posted here out of frustration, after exhausting all the regular methods of what should have been a simple Motherboard/CPU/OS upgrade, and subsequent installation of my working printer.

Don't get frustrated as the community can always find a solution to your problem. I mean it, when my first start of using this Linux Ubuntu Operating System I encountered a lot of issues, bugs and etc. That is no jokes. Its true but I don't lose any hope. For me, it is just a machine compared to human, machine is nothing compared to us humans. We human are the one who made the machine so why worry? Everything has a solution in terms on this area hardware computing and Linux Ubuntu Operating System. My advice to you is just wait, maybe the right expert for your issue was not online yet. :-)
 
> **xl11a said:**
> 
So I felt it was time to ask some experts and signed onto this forum. Being a "newb" here, I was trying to learn as I observed, but as everyone knows, every forum has it own set of rules and protocols, and some forums are purely technically driven, and ask you not to chat, or post any kind of smiley face content, and just post the technical details. Others are very social, and require a decent post count before members will "recognise" you. I'm just trying to find my footings here. So again apologies to this community if I have come across as seeming ungrateful, or unwilling to put the time and effort in to help myself.
Thank you.
Cheers
I get your point. Don't worry about that we all made a mistakes its just that we just don't have to repeat it again and again and being impatient is not a solution. We are all humans here we have just to understand each other. Peace, Regards and Cheers.

---

### Post by brian_p on 2022-05-30
Your earlier **lpimfo -v** has queried the printer and it responds with

> usb://Brother/MFC-J480DW?serial=U64037C8H308289

You may check this again.

Now look at the thread title and the PPD chosen to use in **lpadmin**. Comments?

Also give ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

---

### Post by xl11a on 2022-05-30
> **brian_p said:**
> Your earlier **lpimfo -v** has queried the printer and it responds with



You may check this again.

Now look at the thread title and the PPD chosen to use in **lpadmin**. Comments?

Also give ```
lsusb -v | grep -A 3 bInterfaceClass.*7
```

Okay update... Decided to try a clean install of the CUPS and drivers so did: 
[COLOR=#0000cd]apt-get purge cups [FONT=&amp] 
[/FONT]dpkg -l | grep Brother[/COLOR][COLOR=#0000ff][FONT=&amp][COLOR=#0000ff][FONT=var ff-mono]
[/FONT][/COLOR][/FONT][/COLOR][FONT=&amp][FONT=var ff-mono]
[/FONT][/FONT][FONT=&amp]Then 
[/FONT][COLOR=#0000cd]sudo apt-get install cups
sudo bash linux-brprinter-installer-2.2.3-1 MFC-J450DW [/COLOR]
[FONT=&amp]Still did not work.

[B]Revisited
 [COLOR=#0000cd]lpimfo -v   (Output was slightly different from previous file)[/COLOR][/B]
[/FONT]```
file cups-brf:/
network beh
network lpd
network https
serial serial:/dev/ttyS0?baud=115200
network ipp
network ipps
network socket
network http
direct usb://Brother/MFC-J480DW?serial=U64037C8H308289

[B][COLOR=#0000cd]
[/COLOR][/B]

```**[COLOR=#0000cd]lpinfo -m | grep -i J450  (output very different from older file) [/COLOR]**
```
Brother/brother_mfcj450dw_printer_en.ppd Brother MFC-J450DW CUPS
lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd Brother MFC-J450DW CUPS
drv:///hpijs.drv/hp-officejet_j4500_series-hpijs.ppd HP Officejet j4500 Series hpijs, 3.20.3

```

I'm a bit slow to catch on but now see the difference between the URI and PPD  (**J480 and J450 ) **Thanks for your patience```
lpadmin -p J480 -v "usb://Brother/MFC-J480DW?serial=U64037C8H308289" -E -m "lsb/usr/Brother/brother_mfcj450dw_printer_en.ppd"
```

Have to ask...Why is the MFC-J480DW there? I'm assuming the Brother drivers were for the MFC-J450DW. Also since I'm not wanting network hookup, doesn't that make the J480 URI redundant? 

[B]As well as
[/B]```
lp -d J480 /etc/nsswitch.confrequest id is J480-80 (1 file(s))
```
Same result. Printer lights up but nothing prints
[B]
And[/B]
```
lsusb -v | grep -A 3 bInterfaceClass.*7
Couldn't open device, some information will be missing
      bInterfaceClass         7 Printer
      bInterfaceSubClass      1 Printer
      bInterfaceProtocol      2 Bidirectional
      iInterface              0 
can't get debug descriptor: Resource temporarily unavailable
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing
Couldn't open device, some information will be missing

```


**Also**
```
ls /etc/cups/ppd/*.ppd
/etc/cups/ppd/J480.ppd  /etc/cups/ppd/MFCJ450DW.ppd

```


Thanks again for you patience and help.
Cheers


[COLOR=#000000][B][COLOR=#0000ff]
[/COLOR][/B][/COLOR]
[B][COLOR=#0000ff]
[/COLOR][/B]

---

### Post by brian_p on 2022-05-30
> **xl11a said:**
> 

Have to ask...Why is the MFC-J480DW there? I'm assuming the Brother drivers were for the MFC-J450DW. Also since I'm not wanting network hookup, doesn't that make the J480 URI redundant?

The URI is correct. It is for a J450DW. Why do you think the printer is a J450DW?

The correct PPD needs the result of ```
lpinfo -m | grep -i J480
``` to substitute in lpadmin.

---

### Post by xl11a on 2022-05-30
> **brian_p said:**
> The URI is correct. It is for a J450DW. Why do you think the printer is a J450DW?

The correct PPD needs the result of ```
lpinfo -m | grep -i J480
``` to substitute in lpadmin.

Well I feel really stupid now.  ](*,)For some reason I misread the number and thought it was a J450DW, and downloaded the drivers for that model.
 All along I was thinking that it was something different. 
I'll uninstall those drivers and reinstall the proper drivers. I hope that is all that was wrong. Sigh!

Thanks you!

---

### Post by xl11a on 2022-05-30
I can't begin to express how embarrassed and foolish I am feeling right now! 
Time for me to invest in some glasses. 
Thanks so much for all your help and patience brian_p I learned a lot. Thanks mIk3_08 

Problem solved! You can close this post!

---

