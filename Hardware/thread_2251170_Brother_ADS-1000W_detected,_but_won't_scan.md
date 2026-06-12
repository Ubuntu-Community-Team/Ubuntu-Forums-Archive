---
title: "Brother ADS-1000W detected, but won't scan"
date: 2014-11-02
forum: Hardware
---

### Post by Occasionally Correct on 2014-11-02
Hey there.

I have a Brother ADS-1000W scanner which is advertised to work with Linux. I've had it for a couple months now. It worked perfectly in 14.04, but since upgrading to 14.10, it doesn't scan (I did a clean install). I went through and did all the steps listed on the [Brother Solutions Center page]("http://support.brother.com/g/s/id/linux/en/before.html?c=us&lang=en&prod=ads1000w_us&redirect=on"). I've also tried to research a lot of different possible scanner issues.

Currently, the scanner is seen by lsusb (bus 005, dev 004):
```
...
Bus 005 Device 004: ID 04f9:60a6 Brother Industries, Ltd 
...
```

Output of *sudo sane-find-scanner*:
```
$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.


  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.


could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x04f9 [Brother], product=0x60a6 [ADS-1000W]) at libusb:005:004
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
could not fetch string descriptor: Pipe error
found USB scanner (vendor=0x22b8, product=0x2e82) at libusb:005:002
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.
```

Output of *scanimage -L*:
```
$ scanimage -L
device `brother4:bus2;dev3' is a Brother ADS-1000W USB scanner
```

Additionally, Simple Scan sees the scanner in the preferences dialog, but when I try to scan anything it returns errors via --debug and states "Unable to start scan" (included all the output but bolded the bits that point to an error):
```
[+80.21s] DEBUG: simple-scan.vala:310: Requesting scan at 300 dpi from device 'brother4:bus2;dev3'
[+80.21s]** DEBUG: scanner.vala:1559: Scanner.scan ("brother4:bus2;dev3", dpi=300, scan_mode=ScanMode.GRAY, depth=2, type=ScanType.SINGLE, paper_width=2159, paper_height=2794, brightness=0, contrast=0)**
[+80.21s] DEBUG: scanner.vala:802: Processing request
[+80.34s] DEBUG: ui.vala:1969: Saving state to /home/sam/.cache/simple-scan/state
[+81.26s] DEBUG: scanner.vala:863: sane_open ("brother4:bus2;dev3") -> SANE_STATUS_GOOD
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (0)
[+81.26s] DEBUG: scanner.vala:734: Option 0: name='(null)' title='Number of options' type=bool size=4 cap=,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Read-only option that specifies how many options a specific devices supports.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (1)
[+81.26s] DEBUG: scanner.vala:734: Option 1: name='(null)' title='Mode' type=group size=4 cap=,advanced
[+81.26s] DEBUG: scanner.vala:737:   Description: 
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (2)
[+81.26s] DEBUG: scanner.vala:734: Option 2: name='mode' title='Scan mode' type=string size=30 values=["Black & White", "Gray[Error Diffusion]", "True Gray", "24bit Color[Fast]"] cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Select the scan mode
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (3)
[+81.26s] DEBUG: scanner.vala:734: Option 3: name='resolution' title='Scan resolution' type=int size=4 unit=dpi values=[100, 150, 200, 300, 400, 600, 1200, 2400, 4800, 9600] cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Sets the resolution of the scanned image.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (4)
[+81.26s] DEBUG: scanner.vala:734: Option 4: name='source' title='Scan source' type=string size=64 values=["Automatic Document Feeder(left aligned)", "Automatic Document Feeder(left aligned,Duplex)", "Automatic Document Feeder(centrally aligned)", "Automatic Document Feeder(centrally aligned,Duplex)"] cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Selects the scan source (such as a document-feeder).
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (5)
[+81.26s] DEBUG: scanner.vala:734: Option 5: name='brightness' title='Brightness' type=fixed size=4 unit=percent min=-50.000000, max=50.000000, quant=65536 cap=,soft-select,soft-detect,inactive
[+81.26s] DEBUG: scanner.vala:737:   Description: Controls the brightness of the acquired image.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (6)
[+81.26s] DEBUG: scanner.vala:734: Option 6: name='contrast' title='Contrast' type=fixed size=4 unit=percent min=-50.000000, max=50.000000, quant=65536 cap=,soft-select,soft-detect,inactive
[+81.26s] DEBUG: scanner.vala:737:   Description: Controls the contrast of the acquired image.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (7)
[+81.26s] DEBUG: scanner.vala:734: Option 7: name='(null)' title='Geometry' type=group size=4 cap=,advanced
[+81.26s] DEBUG: scanner.vala:737:   Description: 
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (8)
[+81.26s] DEBUG: scanner.vala:734: Option 8: name='tl-x' title='Top-left x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=6553 cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Top-left x position of scan area.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (9)
[+81.26s] DEBUG: scanner.vala:734: Option 9: name='tl-y' title='Top-left y' type=fixed size=4 unit=mm min=0.000000, max=355.599991, quant=6553 cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Top-left y position of scan area.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (10)
[+81.26s] DEBUG: scanner.vala:734: Option 10: name='br-x' title='Bottom-right x' type=fixed size=4 unit=mm min=0.000000, max=215.899994, quant=6553 cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Bottom-right x position of scan area.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (11)
[+81.26s] DEBUG: scanner.vala:734: Option 11: name='br-y' title='Bottom-right y' type=fixed size=4 unit=mm min=0.000000, max=355.599991, quant=6553 cap=,soft-select,soft-detect
[+81.26s] DEBUG: scanner.vala:737:   Description: Bottom-right y position of scan area.
[+81.26s] DEBUG: scanner.vala:884: sane_get_option_descriptor (12)
**[+81.26s] WARNING: scanner.vala:949: Unable to set single page source, please file a bug**
[+81.26s] DEBUG: scanner.vala:546: sane_control_option (2, SANE_ACTION_SET_VALUE, "True Gray") -> (SANE_STATUS_GOOD, "True Gray")
[+81.26s] DEBUG: scanner.vala:462: sane_control_option (3, SANE_ACTION_SET_VALUE, 300) -> (SANE_STATUS_GOOD, 300)
[+81.26s] DEBUG: scanner.vala:502: sane_control_option (10, SANE_ACTION_SET_VALUE, 215.900000) -> (SANE_STATUS_GOOD, 215.880234)
[+81.26s] DEBUG: scanner.vala:502: sane_control_option (11, SANE_ACTION_SET_VALUE, 279.400000) -> (SANE_STATUS_GOOD, 279.374420)
**[+87.31s] DEBUG: scanner.vala:1212: sane_start (page=0, pass=0) -> SANE_STATUS_INVAL**
**[+87.31s] WARNING: scanner.vala:1219: Unable to start device: Invalid argument**
[+87.31s] DEBUG: scanner.vala:764: sane_cancel ()
[+87.31s] DEBUG: scanner.vala:767: sane_close ()
```

xsane also states that it can't start the device because of an invalid argument.

I have tried solutions like chmodding /dev/bus/usb/*, scanning as sudo, etc. Same result. Notice how most of the output says "brother4:bus2;dev3" (scanimage, simple-scan --debug) but lsusb and sane-find-scanner list it as bus005, dev004. Is it for some reason looking in the wrong place for the scanner?

The other interesting bit is that the VueScan software both sees the scanner *and* performs a scan without any trouble. However, it also adds watermarks all over the scanned document so it isn't a viable solution for me (I'm an office manager for a small business, so watermarked documents don't fly). If it comes down to it, I guess I could just purchase VueScan, but I really love Simple Scan and would prefer to fix the issue so I can keep using that instead. :)

Any suggestions?

---

### Post by Occasionally Correct on 2014-11-03
Update on the situation: I've tried a few more things listed on another site and the xsane GUI can successfully scan images (when I open it, it fails the first scan with the "invalid argument" message, but subsequent scans works). The scanner still isn't working in Simple Scan, though, and I'm finding xsane really cumbersome for scanning in a lot of multi-page documents. Does *anyone* know what could be going on? :?

---

