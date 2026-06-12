---
title: "Working on a project and need sample scanner data"
date: 2013-06-22
forum: Hardware
---

### Post by pqwoerituytrueiwoq on 2013-06-22
If you don't have a scanner you can't provide any help, sorry
I am working on a update to my [PHP Scanner Server]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server")
and I could use some sample scanner info, if you can post the output of this here using code tags or [http://pastebin.com/]pastebin](http://pastebin.com/]pastebin)
If you only have 1 scanner
```
scanimage -L;scanimage --help
```
If you have more than one scanner
do this, i will need the output of every command
```
chad@M4A79XTD-EVO:~$ scanimage -L;
device `**plustek:libusb:003:004**' is a UMAX 3450 flatbed scanner
device `**hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5**' is a Hewlett-Packard Deskjet_F4400_series all-in-one
chad@M4A79XTD-EVO:~$ scanimage --help -d **plustek:libusb:003:004**
[snip]
chad@M4A79XTD-EVO:~$ scanimage --help -d **hpaio:/usb/Deskjet_F4400_series?serial=CN05DC61TP05C5**
[snip]
```
edit: looks like nobody is going to reply here... am I the only one here with a scanner in there printer?
I am just placing the output [here]("https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/tree/master/inc/scanhelp") these files are used for a developer feature

---

### Post by praseodym on 2013-06-23
Why not moving/copying the posting to "Hardware" and/or "Developing&Programming"?

---

### Post by pqwoerituytrueiwoq on 2013-06-23
did not think of putting it here, hardware makes sense so if a mod/admin wants to move it there i have no problem with that

---

### Post by Cheesemill on 2013-06-25
Here you go...
```
device `hpaio:/usb/Deskjet_2510_series?serial=CN2CQ3HM1R05QX' is a Hewlett-Packard Deskjet_2510_series all-in-one
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `hpaio:/usb/Deskjet_2510_series?serial=CN2CQ3HM1R05QX':
  Scan mode:
    --mode Lineart|Gray|Color [Lineart]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 75|100|200|300|600|1200|2400dpi [75]
        Sets the resolution of the scanned image.
    --source Flatbed [Flatbed]
        Selects the scan source (such as a document-feeder).
  Advanced:
    --contrast 0..2000 [1000]
        Controls the contrast of the acquired image.
    --compression JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [inactive]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
  Geometry:
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..297.011mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [215.9]
        Width of scan-area.
    -y 0..297.011mm [297.011]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hpaio:/usb/Deskjet_2510_series?serial=CN2CQ3HM1R05QX

```

---

### Post by praseodym on 2013-06-25
Here we are:
```

device `hpaio:/usb/Officejet_J4500_series?serial=CN99FDB2XB052T' is a Hewlett-Packard Officejet_J4500_series all-in-one
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information
WARNING: gnome-keyring:: couldn't connect to: /tmp/keyring-MMpymT/pkcs11: No such file or directory

Options specific to device `hpaio:/usb/Officejet_J4500_series?serial=CN99FDB2XB052T':
  Scan mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 100|150|200|300|600dpi [100]
        Sets the resolution of the scanned image.
  Advanced:
    --contrast 0..100 [inactive]
        Controls the contrast of the acquired image.
    --compression None|JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [10]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
    --batch-scan[=(yes|no)] [no]
        Enables continuous scanning with automatic document feeder (ADF).
    --source Auto|Flatbed|ADF [Auto]
        Selects the scan source (such as a document-feeder).
  Geometry:
    --length-measurement Unknown|Approximate|Padded [Padded]
        Selects how the scanned image length is measured and reported, which
        is impossible to know in advance for scrollfed scans.
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..381mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [215.9]
        Width of scan-area.
    -y 0..381mm [381]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hpaio:/usb/Officejet_J4500_series?serial=CN99FDB2XB052T

```
Its an Officejet J4580 All-in-One printer

---

### Post by pqwoerituytrueiwoq on 2013-06-25
Thanks, now i have 11 samples :)
3 Cannon
5 HP
1 Xerox
1 Umax

---

### Post by VMC on 2013-06-25
```
$ scanimage -L;scanimage --helpdevice `plustek:libusb:002:004' is a **Canon CanoScan N1220U flatbed scanner**
Usage: scanimage [OPTION]...


Start image acquisition on a scanner device and write image data to
standard output.


Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information


Options specific to device `plustek:libusb:002:004':
  Scan Mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|14bit [8]
        Number of bits per sample, typical values are 1 for "line-art" and 8
        for multibit scans.
    --source Normal|Transparency|Negative [inactive]
        Selects the scan source (such as a document-feeder).
    --resolution 50..2400dpi [50]
        Sets the resolution of the scanned image.
    --preview[=(yes|no)] [no]
        Request a preview-quality scan.
  Geometry:
    -l 0..215mm [0]
        Top-left x position of scan area.
    -t 0..297mm [0]
        Top-left y position of scan area.
    -x 0..215mm [103]
        Width of scan-area.
    -y 0..297mm [76.21]
        Height of scan-area.
  Enhancement:
    --brightness -100..100% (in steps of 1) [0]
        Controls the brightness of the acquired image.
    --contrast -100..100% (in steps of 1) [0]
        Controls the contrast of the acquired image.
    --custom-gamma[=(yes|no)] [no]
        Determines whether a builtin or a custom gamma-table should be used.
    --gamma-table 0..255,... [inactive]
        Gamma-correction table.  In color mode this option equally affects the
        red, green, and blue channels simultaneously (i.e., it is an intensity
        gamma table).
    --red-gamma-table 0..255,... [inactive]
        Gamma-correction table for the red band.
    --green-gamma-table 0..255,... [inactive]
        Gamma-correction table for the green band.
    --blue-gamma-table 0..255,... [inactive]
        Gamma-correction table for the blue band.
  Device-Settings:
    --lamp-switch[=(yes|no)] [no]
        Manually switching the lamp(s).
    --lampoff-time 0..999 (in steps of 1) [300]
        Lampoff-time in seconds.
    --lamp-off-at-exit[=(yes|no)] [yes]
        Turn off lamp when program exits
    --warmup-time -1..999 (in steps of 1) [inactive]
        Warmup-time in seconds.
    --lamp-off-during-dcal[=(yes|no)] [no]
        Always switches lamp off when doing dark calibration.
    --calibration-cache[=(yes|no)] [no]
        Enables or disables calibration data cache.
    --speedup-switch[=(yes|no)] [inactive]
        Enables or disables speeding up sensor movement.
    --calibrate [inactive]
        Performs calibration
  Analog frontend:
    --red-gain -1..63 (in steps of 1) [-1]
        Red gain value of the AFE
    --green-gain -1..63 (in steps of 1) [-1]
        Green gain value of the AFE
    --blue-gain -1..63 (in steps of 1) [-1]
        Blue gain value of the AFE
    --red-offset -1..63 (in steps of 1) [-1]
        Red offset value of the AFE
    --green-offset -1..63 (in steps of 1) [-1]
        Green offset value of the AFE
    --blue-offset -1..63 (in steps of 1) [-1]
        Blue offset value of the AFE
    --redlamp-off -1..16363 (in steps of 1) [-1]
        Defines red lamp off parameter
    --greenlamp-off -1..16363 (in steps of 1) [-1]
        Defines green lamp off parameter
    --bluelamp-off -1..16363 (in steps of 1) [-1]
        Defines blue lamp off parameter
  Buttons:


Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.


List of available devices:
    plustek:libusb:002:004



```

---

### Post by pqwoerituytrueiwoq on 2013-06-25
Thanks

---

### Post by squakie on 2013-06-26
Here's mine (though I question the need for scanimage --help from everyone):

```
dave@davezbox:~$ scanimage -L;scanimage --help
device `hpaio:/net/Photosmart_Prem_C310_series?zc=HP8D6E68' is a Hewlett-Packard Photosmart_Prem_C310_series all-in-one
Usage: scanimage [OPTION]...

Start image acquisition on a scanner device and write image data to
standard output.

Parameters are separated by a blank from single-character options (e.g.
-d epson) and by a "=" from multi-character options (e.g. --device-name=epson).
-d, --device-name=DEVICE   use a given scanner device (e.g. hp:/dev/scanner)
    --format=pnm|tiff      file format of output file
-i, --icc-profile=PROFILE  include this ICC profile into TIFF file
-L, --list-devices         show available scanner devices
-f, --formatted-device-list=FORMAT similar to -L, but the FORMAT of the output
                           can be specified: %d (device name), %v (vendor),
                           %m (model), %t (type), %i (index number), and
                           %n (newline)
-b, --batch[=FORMAT]       working in batch mode, FORMAT is `out%d.pnm' or
                           `out%d.tif' by default depending on --format
    --batch-start=#        page number to start naming files with
    --batch-count=#        how many pages to scan in batch mode
    --batch-increment=#    increase page number in filename by #
    --batch-double         increment page number by two, same as
                           --batch-increment=2
    --batch-prompt         ask for pressing a key before scanning a page
    --accept-md5-only      only accept authorization requests using md5
-p, --progress             print progress messages
-n, --dont-scan            only set options, don't actually scan
-T, --test                 test backend thoroughly
-A, --all-options          list all available backend options
-h, --help                 display this help message and exit
-v, --verbose              give even more status messages
-B, --buffer-size=#        change input buffer size (in kB, default 32)
-V, --version              print version information

Options specific to device `hpaio:/net/Photosmart_Prem_C310_series?zc=HP8D6E68':
  Scan mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --resolution 75|100|150|200|300|600|1200dpi [75]
        Sets the resolution of the scanned image.
  Advanced:
    --contrast -127..127 [0]
        Controls the contrast of the acquired image.
    --compression None|JPEG [JPEG]
        Selects the scanner compression method for faster scans, possibly at
        the expense of image quality.
    --jpeg-quality 0..100 [10]
        Sets the scanner JPEG compression factor. Larger numbers mean better
        compression, and smaller numbers mean better image quality.
    --batch-scan[=(yes|no)] [no]
        Enables continuous scanning with automatic document feeder (ADF).
    --source Flatbed [Flatbed]
        Selects the scan source (such as a document-feeder).
    --duplex[=(yes|no)] [inactive]
        Enables scanning on both sides of the page.
  Geometry:
    --length-measurement Unknown|Approximate|Padded [Padded]
        Selects how the scanned image length is measured and reported, which
        is impossible to know in advance for scrollfed scans.
    -l 0..215.9mm [0]
        Top-left x position of scan area.
    -t 0..296.926mm [0]
        Top-left y position of scan area.
    -x 0..215.9mm [215.9]
        Width of scan-area.
    -y 0..296.926mm [296.926]
        Height of scan-area.

Type ``scanimage --help -d DEVICE'' to get list of all options for DEVICE.

List of available devices:
    hpaio:/net/Photosmart_Prem_C310_series?zc=HP8D6E68
dave@davezbox:~$ 

```

---

### Post by VMC on 2013-06-26
I thought so too, so maybe the --help on the device is what's needed.  "[COLOR=#000000][FONT=Ubuntu Mono]scanimage --help -d DEVICE"[/FONT][/COLOR]

---

### Post by squakie on 2013-06-26
> **VMC said:**
> I thought so too, so maybe the --help on the device is what's needed.  "[COLOR=#000000][FONT=Ubuntu Mono]scanimage --help -d DEVICE"[/FONT][/COLOR]

Now THAT would make a lot more sense!  ;)

---

### Post by pqwoerituytrueiwoq on 2013-06-26
> **VMC said:**
> I thought so too, so maybe the --help on the device is what's needed.  "[COLOR=#000000][FONT=Ubuntu Mono]scanimage --help -d DEVICE"[/FONT][/COLOR]
[QUOTE=squakie;12706869]Now THAT would make a lot more sense!  ;)[/QUOTE]

How did this conversation get started?
in my exp -d is only needed if you have more than one scanner, you can also get different results if you add --source
[help without --source](https://github.com/GM-Script-Writer-62850/PHP-Scanner-Server/blob/master/inc/scanhelp/UMAX%203450%20flatbed%20scanner)
UMAX 3450 flatbed scanner

[LIST]
[*]plustek:libusb:003:003 
[*]The 'Normal' source supports
[LIST]
[*]A bay width of 8.46" 
[*]A bay height of 11.69" 
[*]A scanner resolution of 50 DPI to 1,200 DPI 
[*]No duplex (double sided) scanning 
[*]3 color modes 
[/LIST]
  
[*]The 'Transparency' source supports
[LIST]
[*]A bay width of 4.1" 
[*]A bay height of 4.82" 
[*]A scanner resolution of 150 DPI to 1,200 DPI 
[*]No duplex (double sided) scanning 
[*]1 color mode 
[/LIST]
  
[*]The 'Negative' source supports
[LIST]
[*]A bay width of 4.17" 
[*]A bay height of 5.17" 
[*]A scanner resolution of 150 DPI to 1,200 DPI 
[*]No duplex (double sided) scanning 
[*]1 color mode 
[/LIST]
  
[/LIST]

---

