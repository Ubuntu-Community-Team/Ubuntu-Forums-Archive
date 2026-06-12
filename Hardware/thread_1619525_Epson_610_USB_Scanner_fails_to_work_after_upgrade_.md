---
title: "Epson 610 USB Scanner fails to work after upgrade to Ubuntu 10.10"
date: 2010-11-11
forum: Hardware
---

### Post by mtinman on 2010-11-11
Hey All,

I'm having problems getting my Epson 610 USB scanner working, after an upgrade to Maverick. It has worked well in every version of Ubuntu since 8.04, and it shows up in the device list just fine.

```
lsusb
Bus 002 Device 005: ID 04b8:0103 Seiko Epson Corp. Perfection 610
Bus 002 Device 004: ID 04e8:324c Samsung Electronics Co., Ltd ML-1740 Printer
Bus 002 Device 003: ID 046d:c03f Logitech, Inc. UltraX Optical Mouse
Bus 002 Device 002: ID 047d:105e Kensington Bluetooth EDR Dongle
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 040d:6205 VIA Technologies, Inc. USB 2.0 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

The problem is, I get an invalid argument error every time I try to scan something. The device is seen by simple scan, Xsane, and gscan2pdf. I have changed the permissions on the device, installed libsane-extras, run simple scan & Xsane as root, and it still doesn't work. I also ran simple scan in debug mode, here is the output:

```
simple-scan -d
** (simple-scan:4433): DEBUG: Starting Simple Scan 2.32.0, PID=4433
** (simple-scan:4433): DEBUG: Restoring window to 600x400 pixels
** (simple-scan:4433): DEBUG: sane_init () -> SANE_STATUS_GOOD
** (simple-scan:4433): DEBUG: SANE version 1.0.21
** (simple-scan:4433): DEBUG: Requesting redetection of scan devices
** (simple-scan:4433): DEBUG: Processing request
** (simple-scan:4433): DEBUG: sane_get_devices () -> SANE_STATUS_GOOD
** (simple-scan:4433): DEBUG: Device: name="epson2:libusb:002:005" vendor="Epson" model="Perfection610" type="flatbed scanner"
** (simple-scan:4433): DEBUG: Requesting scan at 600 dpi from device 'epson2:libusb:002:005'
** (simple-scan:4433): DEBUG: scanner_scan ("epson2:libusb:002:005", 600, SCAN_SINGLE)
** (simple-scan:4433): DEBUG: Processing request
** (simple-scan:4433): DEBUG: sane_open ("epson2:libusb:002:005") -> SANE_STATUS_GOOD
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (0)
** (simple-scan:4433): DEBUG: Option 0: title='Number of options' type=int size=4 cap=soft-detect
** (simple-scan:4433): DEBUG:   Description: Read-only option that specifies how many options a specific devices supports.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (1)
** (simple-scan:4433): DEBUG: Option 1: title='Scan Mode' type=group size=4
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (2)
** (simple-scan:4433): DEBUG: Option 2: name='mode' title='Scan mode' type=string size=8 values=["Lineart", "Gray", "Color"] cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Selects the scan mode (e.g., lineart, monochrome, or color).
** (simple-scan:4433): DEBUG: sane_control_option (2, SANE_ACTION_SET_VALUE, "Color") -> (SANE_STATUS_GOOD, "Color")
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (3)
** (simple-scan:4433): DEBUG: Option 3: name='depth' title='Bit depth' type=int size=4 values=[8] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Number of bits per sample, typical values are 1 for "line-art" and 8 for multibit scans.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (4)
** (simple-scan:4433): DEBUG: Option 4: name='halftoning' title='Halftoning' type=string size=26 values=["None", "Halftone A (Hard Tone)", "Halftone B (Soft Tone)", "Halftone C (Net Screen)"] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Selects the halftone.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (5)
** (simple-scan:4433): DEBUG: Option 5: name='dropout' title='Dropout' type=string size=6 values=["None", "Red", "Green", "Blue"] cap=soft-select,soft-detect,inactive,advanced
** (simple-scan:4433): DEBUG:   Description: Selects the dropout.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (6)
** (simple-scan:4433): DEBUG: Option 6: name='brightness' title='Brightness' type=int size=4 min=0, max=0, quant=0 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Selects the brightness.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (7)
** (simple-scan:4433): DEBUG: Option 7: name='sharpness' title='Sharpness' type=int size=4 min=-2, max=2, quant=0 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (8)
** (simple-scan:4433): DEBUG: Option 8: name='gamma-correction' title='Gamma Correction' type=string size=25 values=["User defined (Gamma=1.0)", "User defined (Gamma=1.8)"] cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Selects the gamma correction value from a list of pre-defined devices or the user defined table, which can be downloaded to the scanner
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (9)
** (simple-scan:4433): DEBUG: Option 9: name='color-correction' title='Color correction' type=string size=25 values=["None", "Built in CCT profile", "User defined CCT profile"] cap=soft-select,soft-detect,inactive,advanced
** (simple-scan:4433): DEBUG:   Description: Sets the color correction table for the selected output device.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (10)
** (simple-scan:4433): DEBUG: Option 10: name='resolution' title='Scan resolution' type=int size=4 unit=dpi values=[75, 150, 300, 600] cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Sets the resolution of the scanned image.
** (simple-scan:4433): DEBUG: sane_control_option (10, SANE_ACTION_SET_VALUE, 600) -> (SANE_STATUS_GOOD, 600)
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (11)
** (simple-scan:4433): DEBUG: Option 11: name='threshold' title='Threshold' type=int size=4 min=0, max=255, quant=0 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Select minimum-brightness to get a white point
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (12)
** (simple-scan:4433): DEBUG: Option 12: title='Advanced' type=group size=4 cap=advanced
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (13)
** (simple-scan:4433): DEBUG: Option 13: name='mirror' title='Mirror image' type=bool size=4 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Mirror the image.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (14)
** (simple-scan:4433): DEBUG: Option 14: name='auto-area-segmentation' title='Auto area segmentation' type=bool size=4 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Enables different dithering modes in image and text areas
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (15)
** (simple-scan:4433): DEBUG: Option 15: name='red-gamma-table' title='Red intensity' type=int size=1024 min=0, max=255, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Gamma-correction table for the red band.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (16)
** (simple-scan:4433): DEBUG: Option 16: name='green-gamma-table' title='Green intensity' type=int size=1024 min=0, max=255, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Gamma-correction table for the green band.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (17)
** (simple-scan:4433): DEBUG: Option 17: name='blue-gamma-table' title='Blue intensity' type=int size=1024 min=0, max=255, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Gamma-correction table for the blue band.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (18)
** (simple-scan:4433): DEBUG: Option 18: name='wait-for-button' title='Wait for Button' type=bool size=4 cap=soft-select,soft-detect,advanced
** (simple-scan:4433): DEBUG:   Description: After sending the scan command, wait until the button on the scanner is pressed to actually start the scan process.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (19)
** (simple-scan:4433): DEBUG: Option 19: title='Color correction' type=group size=4 cap=advanced
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (20)
** (simple-scan:4433): DEBUG: Option 20: name='cct-type' title='CCT Profile Type' type=string size=21 values=["Automatic", "Reflective", "Colour negatives", "Monochrome negatives", "Colour positives"] cap=soft-select,soft-detect,inactive,advanced
** (simple-scan:4433): DEBUG:   Description: Color correction profile type
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (21)
** (simple-scan:4433): DEBUG: Option 21: name='cct-profile' title='CCT Profile' type=fixed size=36 min=-2.000000, max=2.000000, quant=0 cap=soft-select,soft-detect,advanced
** (simple-scan:4433): DEBUG:   Description: Color correction profile data
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (22)
** (simple-scan:4433): DEBUG: Option 22: title='Preview' type=group size=4 cap=advanced
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (23)
** (simple-scan:4433): DEBUG: Option 23: name='preview' title='Preview' type=bool size=4 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Request a preview-quality scan.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (24)
** (simple-scan:4433): DEBUG: Option 24: title='Geometry' type=group size=4 cap=advanced
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (25)
** (simple-scan:4433): DEBUG: Option 25: name='tl-x' title='Top-left x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Top-left x position of scan area.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (26)
** (simple-scan:4433): DEBUG: Option 26: name='tl-y' title='Top-left y' type=fixed size=4 unit=mm min=0.000000, max=297.857330, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Top-left y position of scan area.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (27)
** (simple-scan:4433): DEBUG: Option 27: name='br-x' title='Bottom-right x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Bottom-right x position of scan area.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (28)
** (simple-scan:4433): DEBUG: Option 28: name='br-y' title='Bottom-right y' type=fixed size=4 unit=mm min=0.000000, max=297.857330, quant=0 cap=soft-select,soft-detect
** (simple-scan:4433): DEBUG:   Description: Bottom-right y position of scan area.
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (29)
** (simple-scan:4433): DEBUG: Option 29: title='Optional equipment' type=group size=4 cap=advanced
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (30)
** (simple-scan:4433): DEBUG: Option 30: name='source' title='Scan source' type=string size=8 values=["Flatbed"] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Selects the scan source (such as a document-feeder).
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (31)
** (simple-scan:4433): DEBUG: Option 31: name='auto-eject' title='Auto eject' type=bool size=4 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Eject document after scanning
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (32)
** (simple-scan:4433): DEBUG: Option 32: name='film-type' title='Film type' type=string size=15 values=["Positive Film", "Negative Film", "Positive Slide", "Negative Slide"] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: 
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (33)
** (simple-scan:4433): DEBUG: Option 33: name='focus-position' title='Focus Position' type=string size=24 values=["Focus on glass", "Focus 2.5mm above glass"] cap=soft-select,soft-detect,inactive,advanced
** (simple-scan:4433): DEBUG:   Description: Sets the focus position to either the glass or 2.5mm above the glass
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (34)
** (simple-scan:4433): DEBUG: Option 34: name='bay' title='Bay' type=string size=2 values=["1", "2", "3", "4", "5", "6"] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Select bay to scan
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (35)
** (simple-scan:4433): DEBUG: Option 35: name='eject' title='Eject' type=button size=4 cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Eject the sheet in the ADF
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (36)
** (simple-scan:4433): DEBUG: Option 36: name='adf-mode' title='ADF Mode' type=string size=8 values=["Simplex", "Duplex"] cap=soft-select,soft-detect,inactive
** (simple-scan:4433): DEBUG:   Description: Selects the ADF mode (simplex/duplex)
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (37)
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (27)
** (simple-scan:4433): DEBUG: sane_control_option (27, SANE_ACTION_SET_VALUE, 215.899994) -> (SANE_STATUS_GOOD, 215.899994)
** (simple-scan:4433): DEBUG: sane_get_option_descriptor (28)
** (simple-scan:4433): DEBUG: sane_control_option (28, SANE_ACTION_SET_VALUE, 297.857330) -> (SANE_STATUS_GOOD, 297.857330)
** (simple-scan:4433): DEBUG: sane_start (page=0, pass=0) -> SANE_STATUS_INVAL

** (simple-scan:4433): WARNING **: Unable to start device: Invalid argument
** (simple-scan:4433): DEBUG: sane_cancel ()
** (simple-scan:4433): DEBUG: sane_close ()
** (simple-scan:4433): DEBUG: Stopping scan thread
** (simple-scan:4433): DEBUG: Processing request
** (simple-scan:4433): DEBUG: sane_exit ()
```

Any help would be greatly appreciated, Thanks in advance.

---

### Post by inuk2600 on 2010-11-15
There's something wrong with the current Perfection 610 driver in the sane-epson2 library. Use sane-epson lib instead.
Do this by editing /etc/sane.d/dll.conf

$ sudo gedit /etc/sane.d/dll.conf

if the following two lines look like:

#epson
epson2

change them to:

epson
#epson2

Save, and re-open xsane.

---

### Post by mtinman on 2010-11-17
inuk2600:

Thank you very much, that worked perfectly.

---

### Post by mnoyes on 2010-11-26
GREAT! Thanks very much -- worked on an Epson cc-600px too.:D

---

### Post by Bryan55 on 2011-01-23
Worked on my Epson Perfection 1650

Thanks

Bryan.

---

### Post by northrnlt on 2011-04-04
Great. Worked for me also with an Epson Perfection 1650.

:P

---

### Post by SRQBri on 2012-08-05
Helpful,but did not solve issue in Epson Workforce 630. Flatbed scanner works ok using simple scan,automatic document feeder (ADF) starts,but has communication error after process starts. I/O error message (among others depending on scan software tried). I'm using Zorin  OS  (Ubuntu 12.04 build out)

---

