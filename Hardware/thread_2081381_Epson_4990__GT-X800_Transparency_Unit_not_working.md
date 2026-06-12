---
title: "Epson 4990 / GT-X800 Transparency Unit not working"
date: 2012-11-06
forum: Hardware
---

### Post by TreibAir on 2012-11-06
I have an Epson Perfection 4990 Photo (GT-X800 in the US) Scanner which used to work properly under Ubuntu 12.04 and 10.04 both with the flatbed and the transparency unit as source. 

While the flatbed still works like a charm, the transparency unit troubles me for days now. 

[LIST]
[*]Even preview scans (in xsane) or low-resolution scans (xsane or scanimage) are really slow - way over one minute.
[*]The scanned image is (almost) completely white. While the scanning process is not completed yet, a very faint "shadow" of my slides can sometimes be seen in the preview window in xsane, but after the preview is completed and the automatic corrections start working, the image is gone. Using scanimage I only get a file full of white pixels.
[/LIST]
I used to start scanning with something like this:
```
scanimage --resolution 100 --mode Color --source 'Transparency Unit' --format=png -t 2 -y 207 -l 12 -x 215 > 66_1.png
```On one of the last days when the scanner was still working properly I experimented with custom gamma tables:
```
scanimage --gamma-correction="User defined" --resolution 600 --focus-position="Focus 2.5mm" --mode Color --source 'Transparency Unit' --depth=8 --format=png -t 50.5 -y 55.5 -l 69 -x 55.5 --gamma-table 'gamma4scanimage 1.6 0 11500 16383 255' > 66_1_gamma.png
```but with no effect. Is it possible that I have permanently messed up some internal settings of the scanner?


The scanner shows the same behaviour on a Windows 7 system and even on a fresh Ubuntu installation. I am out of ideas and really would appreciate some help.

---

### Post by TreibAir on 2012-11-08
Solved it...what has changed is that I cut myself a slide holder that covered up the calibration gap of my scanner. I did not know its function.

---

