---
title: "SANE - invalid argument (Canon Lide 210)"
date: 2014-05-01
forum: Hardware
---

### Post by Jesper_Madsen on 2014-05-01
Hi.

I went ahead and advised my parents to pick up a Canon Lide 210 scanner on the basis of it being fully supported in linux, thinking I could avoid the configuration nightmare that was their Brother all-in-one printer with shoddy linux support.

We picked up a CanoScan Lide210 due to it being fully supported, as listed on this page:
[http://www.sane-project.org/sane-mfgs.html](http://www.sane-project.org/sane-mfgs.html)

Anyway, low and behold, it doesn't work - I've taken the liberty of pasing the output of running "simple-scan -d" as root - the process stops with  : 
"[+20,68s] DEBUG: scanner.vala:1209: sane_start (page=0, pass=0) -> SANE_STATUS_INVAL"

and from there, it's just slowly stopping the process.

Any and every bit of help is greatly appreciated as this is a real stumbling block and I'd rather not have to try and move my parent's machine back to Windows again, especially since this move was largely motivated by them inadvertently hosing the machine with a virus.

```

[+0,00s] DEBUG: simple-scan.vala:582: Starting Simple Scan 3.12.0, PID=9811
[+0,00s] DEBUG: Connecting to session manager
[+0,03s] DEBUG: ui.vala:1648: Loading state from /root/.cache/simple-scan/state
[+0,03s] DEBUG: ui.vala:1629: Restoring window to 600x400 pixels
[+0,03s] DEBUG: autosave-manager.vala:64: Loading autosave information
[+0,03s] DEBUG: autosave-manager.vala:258: Waiting to autosave...
[+0,03s] WARNING: autosave-manager.vala:76: Could not load autosave infomation; not restoring any autosaves
[+0,06s] DEBUG: scanner.vala:1443: sane_init () -> SANE_STATUS_GOOD
[+0,06s] DEBUG: scanner.vala:1449: SANE version 1.0.23
[+0,06s] DEBUG: scanner.vala:1510: Requesting redetection of scan devices
[+0,06s] DEBUG: scanner.vala:802: Processing request
[+0,13s] DEBUG: autosave-manager.vala:280: Autosaving book information
[+0,16s] DEBUG: ui.vala:1739: Saving state to /root/.cache/simple-scan/state
[+0,35s] DEBUG: scanner.vala:338: sane_get_devices () -> SANE_STATUS_GOOD
[+0,35s] DEBUG: scanner.vala:350: Device: name="genesys:libusb:003:014" vendor="Canon" model="LiDE 210" type="flatbed scanner"
[+18,88s] DEBUG: simple-scan.vala:310: Requesting scan at 600 dpi from device 'genesys:libusb:003:014'
[+18,88s] DEBUG: scanner.vala:1556: Scanner.scan ("genesys:libusb:003:014", dpi=600, scan_mode=ScanMode.COLOR, depth=8, type=ScanType.SINGLE, paper_width=2100, paper_height=2970, brightness=0, contrast=0)
[+18,88s] DEBUG: scanner.vala:802: Processing request
[+19,86s] DEBUG: scanner.vala:863: sane_open ("genesys:libusb:003:014") -> SANE_STATUS_GOOD
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (0)
[+19,86s] DEBUG: scanner.vala:734: Option 0: title='Number of options' type=int size=4 cap=,soft-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Read-only option that specifies how many options a specific devices supports.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (1)
[+19,86s] DEBUG: scanner.vala:734: Option 1: name='(null)' title='Scan Mode' type=group size=0
[+19,86s] DEBUG: scanner.vala:737:   Description: 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (2)
[+19,86s] DEBUG: scanner.vala:734: Option 2: name='mode' title='Scan mode' type=string size=8 values=["Color", "Gray", "Lineart"] cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Selects the scan mode (e.g., lineart, monochrome, or color).
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (3)
[+19,86s] DEBUG: scanner.vala:734: Option 3: name='source' title='Scan source' type=string size=21 values=["Flatbed", "Transparency Adapter"] cap=,soft-select,soft-detect,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: Selects the scan source (such as a document-feeder).
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (4)
[+19,86s] DEBUG: scanner.vala:734: Option 4: name='preview' title='Preview' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Request a preview-quality scan.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (5)
[+19,86s] DEBUG: scanner.vala:734: Option 5: name='depth' title='Bit depth' type=int size=4 values=[8, 16] cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Number of bits per sample, typical values are 1 for "line-art" and 8 for multibit scans.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (6)
[+19,86s] DEBUG: scanner.vala:734: Option 6: name='resolution' title='Scan resolution' type=int size=4 unit=dpi values=[4800, 2400, 1200, 600, 300, 150, 100, 75] cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Sets the resolution of the scanned image.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (7)
[+19,86s] DEBUG: scanner.vala:734: Option 7: name='(null)' title='Geometry' type=group size=0 cap=,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (8)
[+19,86s] DEBUG: scanner.vala:734: Option 8: name='tl-x' title='Top-left x' type=fixed size=4 unit=mm min=0,000000, max=216,699997, quant=0 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Top-left x position of scan area.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (9)
[+19,86s] DEBUG: scanner.vala:734: Option 9: name='tl-y' title='Top-left y' type=fixed size=4 unit=mm min=0,000000, max=300,000000, quant=0 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Top-left y position of scan area.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (10)
[+19,86s] DEBUG: scanner.vala:734: Option 10: name='br-x' title='Bottom-right x' type=fixed size=4 unit=mm min=0,000000, max=216,699997, quant=0 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Bottom-right x position of scan area.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (11)
[+19,86s] DEBUG: scanner.vala:734: Option 11: name='br-y' title='Bottom-right y' type=fixed size=4 unit=mm min=0,000000, max=300,000000, quant=0 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Bottom-right y position of scan area.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (12)
[+19,86s] DEBUG: scanner.vala:734: Option 12: name='(null)' title='Enhancement' type=group size=0 cap=,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (13)
[+19,86s] DEBUG: scanner.vala:734: Option 13: name='custom-gamma' title='Use custom gamma table' type=bool size=4 cap=,soft-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Determines whether a builtin or a custom gamma-table should be used.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (14)
[+19,86s] DEBUG: scanner.vala:734: Option 14: name='gamma-table' title='Image intensity' type=int size=1024 min=0, max=65535, quant=0 cap=,soft-select,soft-detect,inactive,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Gamma-correction table.  In color mode this option equally affects the red, green, and blue channels simultaneously (i.e., it is an intensity gamma table).
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (15)
[+19,86s] DEBUG: scanner.vala:734: Option 15: name='red-gamma-table' title='Red intensity' type=int size=1024 min=0, max=65535, quant=0 cap=,soft-select,soft-detect,inactive,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Gamma-correction table for the red band.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (16)
[+19,86s] DEBUG: scanner.vala:734: Option 16: name='green-gamma-table' title='Green intensity' type=int size=1024 min=0, max=65535, quant=0 cap=,soft-select,soft-detect,inactive,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Gamma-correction table for the green band.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (17)
[+19,86s] DEBUG: scanner.vala:734: Option 17: name='blue-gamma-table' title='Blue intensity' type=int size=1024 min=0, max=65535, quant=0 cap=,soft-select,soft-detect,inactive,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Gamma-correction table for the blue band.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (18)
[+19,86s] DEBUG: scanner.vala:734: Option 18: name='swdeskew' title='Software deskew' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Request backend to rotate skewed pages digitally
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (19)
[+19,86s] DEBUG: scanner.vala:734: Option 19: name='swcrop' title='Software crop' type=bool size=4 cap=,soft-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Request backend to remove border from pages digitally
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (20)
[+19,86s] DEBUG: scanner.vala:734: Option 20: name='swdespeck' title='Software despeck' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Request backend to remove lone dots digitally
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (21)
[+19,86s] DEBUG: scanner.vala:734: Option 21: name='despeck' title='Software despeckle diameter' type=int size=4 min=1, max=9, quant=1 cap=,soft-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Maximum diameter of lone dots to remove from scan
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (22)
[+19,86s] DEBUG: scanner.vala:734: Option 22: name='swskip' title='Software blank skip percentage' type=fixed size=4 unit=percent min=0,000000, max=100,000000, quant=65536 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Request driver to discard pages with low numbers of dark pixels
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (23)
[+19,86s] DEBUG: scanner.vala:734: Option 23: name='swderotate' title='Software derotate' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Request driver to detect and correct 90 degree image rotation
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (24)
[+19,86s] DEBUG: scanner.vala:734: Option 24: name='(null)' title='Extras' type=group size=0 cap=,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (25)
[+19,86s] DEBUG: scanner.vala:734: Option 25: name='lamp-off-time' title='Lamp off time' type=int size=4 min=0, max=60, quant=0 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: The lamp will be turned off after the given time (in minutes). A value of 0 means, that the lamp won't be turned off.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (26)
[+19,86s] DEBUG: scanner.vala:734: Option 26: name='lamp-off-scan' title='Lamp off during scan' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: The lamp will be turned off during scan. 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (27)
[+19,86s] DEBUG: scanner.vala:734: Option 27: name='threshold' title='Threshold' type=fixed size=4 unit=percent min=0,000000, max=100,000000, quant=65536 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Select minimum-brightness to get a white point
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (28)
[+19,86s] DEBUG: scanner.vala:734: Option 28: name='threshold-curve' title='Threshold curve' type=int size=4 min=0, max=127, quant=1 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Dynamic threshold curve, from light to dark, normally 50-65
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (29)
[+19,86s] DEBUG: scanner.vala:734: Option 29: name='disable-dynamic-lineart' title='Disable dynamic lineart' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Disable use of a software adaptive algorithm to generate lineart relying instead on hardware lineart.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (30)
[+19,86s] DEBUG: scanner.vala:734: Option 30: name='disable-interpolation' title='Disable interpolation' type=bool size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: When using high resolutions where the horizontal resolution is smaller than the vertical resolution this disables horizontal interpolation.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (31)
[+19,86s] DEBUG: scanner.vala:734: Option 31: name='color-filter' title='Color Filter' type=string size=6 values=["Red", "Green", "Blue", "None"] cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: When using gray or lineart this option selects the used color.
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (32)
[+19,86s] DEBUG: scanner.vala:734: Option 32: name='sensors' title='Sensors' type=group size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: Scanner sensors and buttons
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (33)
[+19,86s] DEBUG: scanner.vala:734: Option 33: name='scan' title='Scan button' type=bool size=4 cap=,hard-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Scan button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (34)
[+19,86s] DEBUG: scanner.vala:734: Option 34: name='file' title='File button' type=bool size=4 cap=,hard-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: File button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (35)
[+19,86s] DEBUG: scanner.vala:734: Option 35: name='email' title='Email button' type=bool size=4 cap=,hard-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Email button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (36)
[+19,86s] DEBUG: scanner.vala:734: Option 36: name='copy' title='Copy button' type=bool size=4 cap=,hard-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Copy button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (37)
[+19,86s] DEBUG: scanner.vala:734: Option 37: name='page-loaded' title='Page loaded' type=bool size=4 cap=,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: Page loaded
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (38)
[+19,86s] DEBUG: scanner.vala:734: Option 38: name='ocr' title='OCR button' type=bool size=4 cap=,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: OCR button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (39)
[+19,86s] DEBUG: scanner.vala:734: Option 39: name='power' title='Power button' type=bool size=4 cap=,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: Power button
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (40)
[+19,86s] DEBUG: scanner.vala:734: Option 40: name='need-calibration' title='Need calibration' type=bool size=4 cap=,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: The scanner needs calibration for the current settings
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (41)
[+19,86s] DEBUG: scanner.vala:734: Option 41: name='Buttons' title='Buttons' type=group size=4 cap=,soft-select,soft-detect
[+19,86s] DEBUG: scanner.vala:737:   Description: 
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (42)
[+19,86s] DEBUG: scanner.vala:734: Option 42: name='calibrate' title='Calibrate' type=button size=4 cap=,inactive
[+19,86s] DEBUG: scanner.vala:737:   Description: Start calibration using special sheet
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (43)
[+19,86s] DEBUG: scanner.vala:734: Option 43: name='clear-calibration' title='Clear calibration' type=button size=0 cap=,soft-select,soft-detect,advanced
[+19,86s] DEBUG: scanner.vala:737:   Description: Clear calibration cache
[+19,86s] DEBUG: scanner.vala:884: sane_get_option_descriptor (44)
[+19,86s] DEBUG: scanner.vala:895: SCAN_SOURCE not available, trying alternative "doc-source"
[+19,86s] DEBUG: scanner.vala:546: sane_control_option (2, SANE_ACTION_SET_VALUE, "Color") -> (SANE_STATUS_GOOD, "Color")
[+19,86s] DEBUG: scanner.vala:462: sane_control_option (6, SANE_ACTION_SET_VALUE, 600) -> (SANE_STATUS_GOOD, 600)
[+19,86s] DEBUG: scanner.vala:462: sane_control_option (5, SANE_ACTION_SET_VALUE, 8) -> (SANE_STATUS_GOOD, 8)
[+19,86s] DEBUG: scanner.vala:502: sane_control_option (10, SANE_ACTION_SET_VALUE, 210,000000) -> (SANE_STATUS_GOOD, 210,000000)
[+19,86s] DEBUG: scanner.vala:502: sane_control_option (11, SANE_ACTION_SET_VALUE, 297,000000) -> (SANE_STATUS_GOOD, 297,000000)
[+20,68s] DEBUG: scanner.vala:1209: sane_start (page=0, pass=0) -> SANE_STATUS_INVAL
[+20,68s] WARNING: scanner.vala:1216: Unable to start device: Invalid argument
[+21,57s] DEBUG: scanner.vala:764: sane_cancel ()
[+21,88s] DEBUG: scanner.vala:767: sane_close ()
[+21,98s] DEBUG: ui.vala:1739: Saving state to /root/.cache/simple-scan/state

```

(**updated:** changed "scanimage" to "simple-scan")

---

### Post by pqwoerituytrueiwoq on 2014-05-01
have you checked for a linux driver on the canon site?

if you want a painless printer/scanner setup use a hp unit, it does not get any easier than plugging the usb cable in while the computer is on and waiting about 10 seconds for it to auto-configure
only issue i ever had was on ubuntu server where sane-hpaio was not installed and i did not have a GUI to configure the printer and i ended up using elinks

i have setup a epson printer/scanner it was easily done manually from the add printer dialog window

---

### Post by pdc on 2014-05-02
sorry to hear you are having issues: can you tell us which version of ubuntu you are using please? 

I note you say you ran > scanimage -d         ..........I must confess that is not a common version of the command

When I issue the command > man scanimage in a terminal, it says > The  -d or --device-name options must be followed by a SANE device-name like `epson:/dev/sg0' or `hp:/dev/usbscanner0'.

........so I was curious where you got the advice to run the command:

the two one most often sees are

> sane-find-scanner

and 

> scanimage -L        (man scanimage says this latter command is the way to "To get a list of devices:"

if no joy with the above, some suggest repeating both commands with sudo in front; to see if there are permission issues to identification 

_______________

so you have xsane installed? and sane? and sane-backends ..............and you turn on xsane; and it says it can't find the device?

____________________________

and I guess another background check to run is that the user is a member of the scanner group: [https://help.ubuntu.com/community/SettingScannerPermissions](https://help.ubuntu.com/community/SettingScannerPermissions)

---

### Post by Jesper_Madsen on 2014-05-02
Hi, and thank you both for taking interest!

I'm using a new Ubuntu 14.04 install (x86_64) - not any of the derivative variants, just regular Ubuntu.

In regards to 'scan-image' -- silly me! I'm sorry, I had already terminated my session to the computer in question, I was actually running "sudo simple-scan -d".

---

### Post by Lundin on 2014-07-22
I've got the a Canon Lide 110 and I've used it without problems on my (very) old HP Pavilion TX1000. 

However on my new Samsung Ativ book9 I can only scan once. The first scan works well without any problems, when I try the same scan command again it times out and I get "scanimage: sane_start: Invalid argument" and I must ctrl-C it to end it.
Between the scans the scanner is found with scanimage -L 
If I unplug/replug the scanner I can scan once again.

It's not exactly the same scanner but I'm pretty sure that the issues are related.
I'm running Ubuntu 14.04 on both boxes.

Any suggestions on how to compare these two installations to be able to pinpoint the root cause?
Or is there a way to simulate the plug/unplugging with a command?

---

### Post by davethesteam on 2014-08-13
Hi
I have had problems with my old (aka ancient) Umax Astra 5400 to the point it's going into freecycle!!
I am now looking for a replacement scanner - all the HP's available today are NOT supported according to Sane. Nor are any of the currently (reasonable priced) available Epsons. Thus I am driven to Canon. There appears to be problems with all 3 within my budget viz Lide 110, Lide 210 and the heavyweight 9900F Mk2. despite being reported on Sane as 'Complete  Can anyone recommend a new  scanner avaiulable today that actually works as 'plug and play' in 14.04 LTS please??

---

### Post by davethesteam on 2014-08-14
Since my last post I have checked the Canon site and they specifically state that they do NOT support Linux on any of their products except the Pixma range.
I have now looked at HP site and the Scanjet 300 does show as suitable for Linux.
Sane shows the Scanjet 300 as Not Supported.
Can anyone advise which to believe and which printer to go for??
Many thanks

---

### Post by Peter_Ebert on 2014-08-24
I have had the same problem with my Canon LiDe 110 since I upgraded to (K)Ubuntu 14.04 (x86_64), it was working out of the box in 12.04. I found this bug report [https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/1247371](https://bugs.launchpad.net/ubuntu/+source/xsane/+bug/1247371) which also contains a solution/a workaround to the problem: the "Intel xHCI Mode" needs to be disabled in the BIOS/UEFI, that fixed the issue for me (Asus H97M-Plus, Kubuntu 14.04 3.13.0-34-generic with sane lib 1.0.14-9). Maybe this helps you, too.

---

