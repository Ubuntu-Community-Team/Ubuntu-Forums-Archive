---
title: "Can Canon CanoScan 9000F Mark II scanner work on Ubuntu"
date: 2019-03-04
forum: Hardware
---

### Post by satimis on 2019-03-04
Hi all,

I'm prepared to purchase Canon CanoScan 9000F Mark II scanner to scan my old stock of film negatives.  The scanner is not expensive.

It was recommended on;
Best Film Scanners for Photographers
[https://www.adorama.com/alc/best-film-scanners-for-photographers](https://www.adorama.com/alc/best-film-scanners-for-photographers)
```
Key Features:
    Optical Resolution: 9600dpi (Film) / 4800dpi (Documents)
    Max Resolution: 12800dpi x 12800dpi (Interpolated)
    Scan Formats (Film): 35mm Film, 35mm Mounted Slides, Medium Format Film
    Scan Area: 8.5in x 11.7in
    Color Depth: 48-Bit
    Scan Speeds: 18 secs. (35mm film/1200dpi), 7 seconds (A4 color document/300dpi)
    FARE (Film Automatic Retouching and Enhancement) Technology
    Compatible with Windows and Mac

```
I hesitate whether this Cannon scanner can work on Ubuntu 16.04 or Ubuntu 18.04.  I have been searching on Internet a while and found following link;

Canon CanoScan 9000F Mark II
[https://ubuntuforums.org/showthread.php?t=2403378](https://ubuntuforums.org/showthread.php?t=2403378)

Could you please give me some advice before I purchase this scanner.

Thanks in advance.

Regards
satimis

---

### Post by torkel-c on 2019-03-09
Works fine, at least for Ubuntu 18.04.2 LTS. I had some problems with XSane when scanning the four slides; troubles occurred when using higher resolutions (> 1200 p/i). When I ran scanimage from prompt, it worked OK - I could also delimit the scanning areas:
scanimage --source 'Transparency Unit' --resolution 4800 -l 91 -t 206 -x 35 -y 24 > p484.png
scanimage --source 'Transparency Unit' --resolution 4800 -l 91 -t 150 -x 35 -y 24 > p483.png
scanimage --source 'Transparency Unit' --resolution 4800 -l 91 -t 94 -x 35 -y 24 > p482.png
scanimage --source 'Transparency Unit' --resolution 4800 -l 91 -t 38 -x 35 -y 24 > p481.png

---

