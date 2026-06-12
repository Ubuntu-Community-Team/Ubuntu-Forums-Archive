---
title: "xsane not working in fresh 16.04 install"
date: 2016-06-23
forum: Hardware
---

### Post by xin3 on 2016-06-23
did a fresh install of Ubuntu Mate 16.04 and now my Canon CanoScan LiDE 25 scanner is like a dead body.

simple scan wasn't working so i installed xsane.

xsane opens and says it recognizes my scanner.

when i push "acquire preview" or "scan", the windows gray out but the scanner doesn't do anything.
and i hear a quit, high pitched beeping but can't place it--somewhere in my laptop.

after awhile, it returns an all black image.

---

threw in a live cd (Ubuntu Studio 14.04), the scanner worked without any issues.

---

lsusb:
```
xin@office:~$ lsusb
Bus 002 Device 005: ID 045e:0728 Microsoft Corp. LifeCam VX-5000
Bus 002 Device 004: ID 04a9:2220 Canon, Inc. CanoScan LIDE 25
Bus 002 Device 003: ID 046d:c525 Logitech, Inc. MX Revolution Cordless Mouse
Bus 002 Device 002: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


```

note: it is running through a usb hub. i don't think that should matter because it worked w/ the live cd.

---

sane-find-scanner:
```
xin@office:~$ sudo sane-find-scanner

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x2220 [CanoScan], chip=LM9832/3) at libusb:002:004
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.


```

---

### Post by xin3 on 2016-06-23
update:

```
xin@office:~$ scanimage > Desktop/test.pnm
``` worked!! (re-saved as png to upload, obv.)

---

### Post by xin3 on 2016-06-23
found a [thread on Linux Questions]("http://www.linuxquestions.org/questions/slackware-14/xsane-and-scanimage-segfaulting-4175550933/") asked for the out put of [FONT=courier new]scanimage -h -d '[device]'[/FONT]

```
xin@office:23th scanns$ scanimage -h -d 'plustek:libusb:002:012'
[...]

Options specific to device `plustek:libusb:002:012':
  Scan Mode:
    --mode Lineart|Gray|Color [Color]
        Selects the scan mode (e.g., lineart, monochrome, or color).
    --depth 8|16bit [8]
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
    plustek:libusb:002:012
```

---

### Post by xin3 on 2016-07-02
got some time to put to solving this today. i think it's solved.

i started up xsane and tried it (hoping maybe some update fixed the problem). and i actually got a preview!! but the scanner bar stayed at the bottom.

so i ran scanimage a couple of times to get it back to the top. even then, xsane wasn't doing ****. simplescan pulled off one scan, but all black images after that.

i googled "xsane scanner not returning" and found this link: [URL="http://askubuntu.com/questions/599694/scanimage-works-but-xsane-or-any-other-ui-does-not"]14.04 - Scanimage works, but Xsane or any other UI does not - Ask Ubuntu
[/URL]
SOLUTION:
added:
```
 USB_BLACKLIST="04a9:2220"
```[INDENT]via "[FONT=courier new]lsusb | grep Canon[/FONT]"
[/INDENT]
 to:
```
/etc/default/tlp
```

note:
xsane needs to be closed and restarted after the system has been suspended.

---

### Post by xin3 on 2016-07-06
so... appearently my printer was experiencing a very similar problem...

FIXED::

```
xin@office:~$ lsusb | grep Samsung
Bus 002 Device 015: ID 04e8:326c Samsung Electronics Co., Ltd ML-2010P Mono Laser Printer
xin@office:~$ cd /etc/default/
xin@office:default$ sudo nano tlp
[sudo] password for xin: 


```

and added this just under the previous entry:

```
USB_BLACKLIST="04e8:326c"
```

---

### Post by xin3 on 2016-07-12
aaaaand... it's not working again. :-(

---

### Post by xin3 on 2016-07-12
[this thread]("http://ubuntuforums.org/showthread.php?t=2324912") links to a bug report... [http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795](http://news.gmane.org/gmane.comp.graphics.scanning.sane.devel/cutoff=25795)

---

### Post by Kenzo on 2016-08-19
Sorry but the link doesn't work. Did you find a fix for the problem?  If so could you post please.  Thanks

---

