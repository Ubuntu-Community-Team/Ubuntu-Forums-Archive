---
title: "CanoSCAN LiDe 100 gets stuck using Simple Scan"
date: 2018-03-02
forum: Hardware
---

### Post by jan4 on 2018-03-02
Hi All,

Acquired myself a CanoSCAN LiDe 100 to use under Ubuntu 16.04. Sane Project states that the scanner is fully supported ([http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON)). The scanner is detected by Simple Scan and by Xsane. So far so good. And then the trouble starts :(

If I try to make a scan using Simple Scan the first scan works. Then the scan head is at the end of its travel and just stays there. It won't return to the "home position". As a result subsequent scan fail and Simple Scan indicates that no scanner is connected. Funny thing is that if I connect the scanner to a Windows computer, the first thing it does is return to the home position.

I tried Xsane and it does try to scan the document/photo but only results in a blank file. The good news is that the scan head returns to its "home position".

So I am rather confused and need some help. How do I get either Simple Scan or Xsane to produce results?

For what it's worth... 
scanimage -L results in this:
```
device `genesys:libusb:006:003' is a Canon LiDE 100 flatbed scanner
```

scanimage -A -d 'genesys:libusb:006:003' gives me:
```
All options specific to device `genesys:libusb:006:003':
  Scan Mode:
    --mode Color|Gray|Lineart [Gray]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --source Flatbed|Transparency Adapter [inactive]
        Selects the scan source (such as a document-feeder).
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
    --depth 8|16 [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --resolution 4800|2400|1200|600|300|200|150|100|75dpi [75]
        Sets the resolution of the scanned image.
  Geometry:
    -l 0..216.07mm [0]
        Top-left x position of scan area.
    -t 0..299mm [0]
        Top-left y position of scan area.
    -x 0..216.07mm [216.07]
        Width of scan-area.
    -y 0..299mm [299]
        Height of scan-area.
  Enhancement:
    --custom-gamma[=(yes|no)] [no]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table 0..65535,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..65535,... [inactive]
        Gamma-correction table for the blue band.
    --swdeskew[=(yes|no)] [no]
        Request backend to rotate skewed pages digitally
    --swcrop[=(yes|no)] [no]
        Request backend to remove border from pages digitally
    --swdespeck[=(yes|no)] [no]
        Request backend to remove lone dots digitally
    --despeck 1..9 (in steps of 1) [1]
        Maximum diameter of lone dots to remove from scan
    --swskip 0..100% (in steps of 1) [0]
        Request driver to discard pages with low numbers of dark pixels
    --swderotate[=(yes|no)] [no]
        Request driver to detect and correct 90 degree image rotation
    --brightness -100..100 (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100 (in steps of 1) [0]
        Controls the contrast of the acquired image.
  Extras:
    --lamp-off-time 0..60 [15]
        The lamp will be turned off after the given time (in minutes). A value
        of 0 means, that the lamp won't be turned off.
    --lamp-off-scan[=(yes|no)] [no]
        The lamp will be turned off during scan. 
    --threshold 0..100% (in steps of 1) [50]
        Select minimum-brightness to get a white point
    --threshold-curve 0..127 (in steps of 1) [50]
        Dynamic threshold curve, from light to dark, normally 50-65
    --disable-dynamic-lineart[=(yes|no)] [no]
        Disable use of a software adaptive algorithm to generate lineart
        relying instead on hardware lineart.
    --disable-interpolation[=(yes|no)] [no]
        When using high resolutions where the horizontal resolution is smaller
        than the vertical resolution this disables horizontal interpolation.
    --color-filter Red|Green|Blue [Green]
        When using gray or lineart this option selects the used color.
    --calibration-file <string> [/home/jan/.sane/canon-lide-100.cal]
        Specify the calibration file to use
    --expiration-time -1..30000 (in steps of 1) [245358736]
        Time (in minutes) before a cached calibration expires.A value of 0
        means cache is not used used. A negative value means cache never
        expires.
  Sensors:
    --scan[=(yes|no)] [no] [hardware]
        Scan button
    --file[=(yes|no)] [no] [hardware]
        File button
    --email[=(yes|no)] [no] [hardware]
        Email button
    --copy[=(yes|no)] [no] [hardware]
        Copy button
  Buttons:
    --clear-calibration
        Clear calibration cache
```

I have installed sane, sane-dbg and sane-utils as well as xsane but I can't get the scanner to work.

Any help greatly appreciated!

Greetz,

J@n

---

