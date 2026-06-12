---
title: "Scanning using the Automatic document Feeder, Brother MFC-9330CDW"
date: 2016-12-21
forum: Hardware
---

### Post by coverup1128 on 2016-12-21
I am using Ubuntu 14.04, kernel 4.4. My multifunction printer/scanner is Brother MFC-9330CDW, it is on the home LAN connected over WiFi. I installed the proprietary driver brscan4-0.4.4-1.amd64.deb from Brother. 

I have a problem with a scanner. Scanning using flatbed works, but when I attempt using the Document Feeder, simple scan produces an error "Error communicating with Scanner, Change Scanner". I can hear the scanner trying to feed pages, but nothing happens an the error pops up. Obviously, the scanner is connected, since there are no issues with scanning from flatbed. Running simple-scan from the command line with the debug option produces bunch of lines, and a few of them indicate an error (highlighted in bold), however I cannot make sense out of it:

```
 $ simple-scan -d
[+0.00s] DEBUG: simple-scan.vala:596: Starting Simple Scan 3.12.3, PID=7358
[+0.00s] DEBUG: Connecting to session manager
[+0.06s] DEBUG: ui.vala:1647: Loading state from /home/XXXXXX/.cache/simple-scan/state
[+0.06s] DEBUG: ui.vala:1628: Restoring window to 600x400 pixels
[+0.06s] DEBUG: autosave-manager.vala:64: Loading autosave information
[+0.06s] DEBUG: autosave-manager.vala:258: Waiting to autosave...
[+0.06s] WARNING: autosave-manager.vala:76: Could not load autosave infomation; not restoring any autosaves
[+0.09s] DEBUG: scanner.vala:1446: sane_init () -> SANE_STATUS_GOOD
[+0.09s] DEBUG: scanner.vala:1452: SANE version 1.0.23
[+0.09s] DEBUG: scanner.vala:1513: Requesting redetection of scan devices
[+0.09s] DEBUG: scanner.vala:802: Processing request
[+0.16s] DEBUG: autosave-manager.vala:280: Autosaving book information
[+0.19s] DEBUG: ui.vala:1738: Saving state to /home/XXXXXX/.cache/simple-scan/state
[+3.51s] DEBUG: simple-scan.vala:310: Requesting scan at 150 dpi from device '(null)'
[+3.51s] DEBUG: scanner.vala:1559: Scanner.scan ("(null)", dpi=150, scan_mode=ScanMode.GRAY, depth=2, type=ScanType.SINGLE, paper_width=2100, paper_height=2970, brightness=0, contrast=0)
[+5.42s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+5.42s] DEBUG: scanner.vala:350: Device: name="brother4:net1;dev0" vendor="Brother" model="MFC-9330CDW" type="MFC-9330CDW"
[+5.42s] DEBUG: scanner.vala:802: Processing request
[+9.76s] DEBUG: scanner.vala:863: sane_open ("brother4:net1;dev0") -> SANE_STATUS_GOOD
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (0)
[+9.76s] DEBUG: scanner.vala:734: Option 0: name='(null)' title='Number of options' type=bool size=4 cap=,soft-detect
[+9.76s] DEBUG: scanner.vala:737:   Description: Read-only option that specifies how many options a specific devices supports.
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (1)
[+9.76s] DEBUG: scanner.vala:734: Option 1: name='(null)' title='Mode' type=group size=4 cap=,advanced
[+9.76s] DEBUG: scanner.vala:737:   Description: 
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (2)
[+9.76s] DEBUG: scanner.vala:734: Option 2: name='mode' title='Scan mode' type=string size=30 values=["Black & White", "Gray[Error Diffusion]", "True Gray", "24bit Color", "24bit Color[Fast]"] cap=,soft-select,soft-detect
[+9.76s] DEBUG: scanner.vala:737:   Description: Select the scan mode
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (3)
[+9.76s] DEBUG: scanner.vala:734: Option 3: name='resolution' title='Scan resolution' type=int size=4 unit=dpi values=[100, 150, 200, 300, 400, 600, 1200, 2400, 4800, 9600] cap=,soft-select,soft-detect
[+9.76s] DEBUG: scanner.vala:737:   Description: Sets the resolution of the scanned image.
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (4)
[+9.76s] DEBUG: scanner.vala:734: Option 4: name='source' title='Scan source' type=string size=64 values=["FlatBed", "Automatic Document Feeder(left aligned)", "Automatic Document Feeder(centrally aligned)"] cap=,soft-select,soft-detect
[+9.76s] DEBUG: scanner.vala:737:   Description: Selects the scan source (such as a document-feeder).
[+9.76s] DEBUG: scanner.vala:884: sane_get_option_descriptor (5)
[+9.77s] DEBUG: scanner.vala:734: Option 5: name='brightness' title='Brightness' type=fixed size=4 unit=percent min=-50.000000, max=50.000000, quant=65536 cap=,soft-select,soft-detect,inactive
[+9.77s] DEBUG: scanner.vala:737:   Description: Controls the brightness of the acquired image.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (6)
[+9.77s] DEBUG: scanner.vala:734: Option 6: name='contrast' title='Contrast' type=fixed size=4 unit=percent min=-50.000000, max=50.000000, quant=65536 cap=,soft-select,soft-detect,inactive
[+9.77s] DEBUG: scanner.vala:737:   Description: Controls the contrast of the acquired image.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (7)
[+9.77s] DEBUG: scanner.vala:734: Option 7: name='(null)' title='Geometry' type=group size=4 cap=,advanced
[+9.77s] DEBUG: scanner.vala:737:   Description: 
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (8)
[+9.77s] DEBUG: scanner.vala:734: Option 8: name='tl-x' title='Top-left x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=6553 cap=,soft-select,soft-detect
[+9.77s] DEBUG: scanner.vala:737:   Description: Top-left x position of scan area.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (9)
[+9.77s] DEBUG: scanner.vala:734: Option 9: name='tl-y' title='Top-left y' type=fixed size=4 unit=mm min=0.000000, max=355.599991, quant=6553 cap=,soft-select,soft-detect
[+9.77s] DEBUG: scanner.vala:737:   Description: Top-left y position of scan area.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (10)
[+9.77s] DEBUG: scanner.vala:734: Option 10: name='br-x' title='Bottom-right x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=6553 cap=,soft-select,soft-detect
[+9.77s] DEBUG: scanner.vala:737:   Description: Bottom-right x position of scan area.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (11)
[+9.77s] DEBUG: scanner.vala:734: Option 11: name='br-y' title='Bottom-right y' type=fixed size=4 unit=mm min=0.000000, max=355.599991, quant=6553 cap=,soft-select,soft-detect
[+9.77s] DEBUG: scanner.vala:737:   Description: Bottom-right y position of scan area.
[+9.77s] DEBUG: scanner.vala:884: sane_get_option_descriptor (12)
[+9.77s] DEBUG: scanner.vala:546: sane_control_option (4, SANE_ACTION_SET_VALUE, "FlatBed") -> (SANE_STATUS_GOOD, "FlatBed")
[+9.77s] DEBUG: scanner.vala:546: sane_control_option (2, SANE_ACTION_SET_VALUE, "True Gray") -> (SANE_STATUS_GOOD, "True Gray")
[+9.77s] DEBUG: scanner.vala:462: sane_control_option (3, SANE_ACTION_SET_VALUE, 150) -> (SANE_STATUS_GOOD, 150)
[+9.77s] DEBUG: scanner.vala:502: sane_control_option (10, SANE_ACTION_SET_VALUE, 210.000000) -> (SANE_STATUS_GOOD, 209.980774)
[+9.77s] DEBUG: scanner.vala:502: sane_control_option (11, SANE_ACTION_SET_VALUE, 297.000000) -> (SANE_STATUS_GOOD, 296.972809)
[+17.92s] DEBUG: scanner.vala:1212: sane_start (page=0, pass=0) -> SANE_STATUS_GOOD
[+17.93s] DEBUG: scanner.vala:1229: sane_get_parameters () -> SANE_STATUS_GOOD
[+17.93s] DEBUG: scanner.vala:1241: Parameters: format=SANE_FRAME_GRAY last_frame=SANE_TRUE bytes_per_line=1232 pixels_per_line=1232 lines=1753 depth=8
[+17.93s] DEBUG: simple-scan.vala:254: Page is 1232 pixels wide, 1753 pixels high, 2 bits per pixel
[B][+17.93s] DEBUG: scanner.vala:1313: sane_read (1233) -> (SANE_STATUS_IO_ERROR, 0)
[+17.93s] WARNING: scanner.vala:1329: Unable to read frame from device: Error during device I/O
[+17.93s] DEBUG: simple-scan.vala:188: Getting color profile for device brother4:net1;dev0
[+17.94s] DEBUG: simple-scan.vala:208: Unable to find colord device brother4:net1;dev0: property match 'Serial'='sane:brother4:net1;dev0' does not exist
[/B][+18.03s] DEBUG: ui.vala:1738: Saving state to /home/XXXXXX/.cache/simple-scan/state
[+21.06s] DEBUG: scanner.vala:764: sane_cancel ()
[+21.06s] DEBUG: scanner.vala:767: sane_close ()
[+21.16s] DEBUG: ui.vala:1738: Saving state to /home/XXXXXX/.cache/simple-scan/state

```


Anyone has the same problem or knows a solution?

---

### Post by TheFu on 2016-12-22
My Brother all-in-one scanner stopped working after 10.04 (I think).  It is a $50 thing and hasn't been used for printing since the included ink ran out. Just wanted it for the sheet feed scanner and fax. ;)

Haven't looked at this in a few years. The 5 times a year scanning is needed, it gets connected to a Win7 laptop. Not ideal, but ... No printer drivers for Vista or later exist for it.

I really need to setup a 10.04 minimal VM with USB passthru just for scanning. Should be able to get that working in under 1GB of space. The good thing is no X/Server is needed, just the X/Client stuff for xscan2pdf (which includes all the ghostscript and OCR stuff). I know xscan2pdf works over remote X, at least the 10.04 version did. That was how I used it previously. Need to add that to my ToDo list for next year.  Might try a 10.04 "container" first, but doubt that will work.  When I do it, the firewall will be highly, highly, highly restricted, in AND out, even for the local LAN. An unpatched system is bad news.  Will probably create a spin-up and spin-down VM controller script too.

Sorry, don't have a better option or any newer data.   Does the SANE-scanner site have any specific instructions for this driver on the release you plan to run?

---

### Post by coverup1128 on 2016-12-23
Thank you for sharing your experience. Unfortunately I need to use scanner more often than 5 times a year. Installing VM just for that purpose is rather combersome. The list of supported Brother devices on the SANE website seems to be quite outdated, and the site was not updated for a year (last updated in October 2015). There must be an explanation why flatbed works and feeder does not, and possibly a fix.

---

### Post by coverup1128 on 2016-12-27
For the benefit of others, the Brother Technical Support suggested to reinstall the drivers using their driver install tool: 

   [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625]("http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfc9330cdw_us_eu_as&os=128&dlid=dlf006893_000&flang=4&type3=625")

This has solved the issue for me.

---

