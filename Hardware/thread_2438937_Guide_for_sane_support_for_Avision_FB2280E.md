---
title: "Guide for sane support for Avision FB2280E"
date: 2020-03-20
forum: Hardware
---

### Post by lt_gustavsen on 2020-03-20
Hello
**Update 21/3 2019. **[COLOR="#FF0000"]Only color mode are supported.[/COLOR]** Not gray or lineart. scanimage gives sane_start: Error during device I/O mode. And I have to unplug power on scanner.**

I picked up my new Avision FB2280E yesterday. I had googled a lot before and had  hope it should be usable under linux. It can use the same driver as FB2080E but for some unknown reason it's not enabled in sane.

So this is a note to self, that maybe others find usefull.

It's based on this pages.

[https://forum.ubuntuusers.de/topic/usb-scanner-wird-von-xsane-nicht-erkannt/](https://forum.ubuntuusers.de/topic/usb-scanner-wird-von-xsane-nicht-erkannt/)
[https://tovotu.de/blog/546-BuchkantenScanner-fr-die-private-Buchdigitalisierung/](https://tovotu.de/blog/546-BuchkantenScanner-fr-die-private-Buchdigitalisierung/)


First we install some tools and download sane-backends



```
mkdir ~/sane
cd ~/sane
sudo apt-get install autopoint autogen libtool shtool autoconf-archive
sudo apt-get install libusb-dev
sudo apt install git

git clone https://gitlab.com/sane-project/backends.git

cd backends
```

Then I create a patch for avision.c

```
echo "    " |tee   avision-patch
echo "    { NULL, NULL," |tee -a  avision-patch
echo "      0x0638, 0x2a1f," | tee -a  avision-patch
echo "      \"Avision\", \"FB2280E\"," | tee -a  avision-patch
echo "      0}," | tee -a  avision-patch
echo "    /* comment=\"1 pass, 600 dpi, zero-edge\" ASIC 7 */" | tee -a  avision-patch
echo "    " |tee  -a avision-patch
```

Next step are a little hack. I find  a linenumber just above the FB2080E
and insert the patch there.

```
line=`cat -n backend/avision.c| grep -B 3 FB2080 |head -n1|tr -d ' '`
insert above patch at linenumber(be carefull here)
printf "%s\n" "${line}r avision-patch" w |ed -s  backend/avision.c
```

Time to built. Look out for error on missing dependencies.
```
./autogen.sh
./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo make install
```

The libearies libsane-avi* needs to be accessible by sane. I just copy all of them.
```
sudo cp -v -a /usr/lib/sane/* /usr/lib/x86_64-linux-gnu/sane/
```
Check that they are linking correct. The should now link like this (there are a few more files here)
```
ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-avi* 
/usr/lib/x86_64-linux-gnu/sane/libsane-avision.so.1 -> libsane-avision.so.1.0.29
#check also libsane-dll*
ls -l /usr/lib/x86_64-linux-gnu/sane/libsane-dll*
/usr/lib/x86_64-linux-gnu/sane/libsane-dll.so -> libsane-dll.so.1.0.29

```

Test scanimage -V
```
scanimage -V
scanimage (sane-backends) 1.0.29-293-g1ed4c7d8-dirty; backend version 1.0.29
```


Now I was able to scan as sudo user!
```
sudo scanimage -d 'avision' --format pnm > out.pnm
```

But, not as normal user. I add a few more steps.

Making a new patch. I'm still in the same folder.

```
echo '' |  tee  patch.txt
echo ':model "FB2280E"' |  tee -a patch.txt
echo ':interface "USB"' |  tee -a patch.txt
echo ':usbid "0x0638" "0x2a1f"' |  tee -a patch.txt
echo ':comment "1 pass, 600 dpi, zero-edge" ASIC 7' |  tee -a patch.txt
echo ':status :basic' |  tee -a patch.txt
```


Patching
```
sed -i '/:mfg "Avision"/ r patch.txt'  doc/descriptions/avision.desc
```

Generating hwdb file
```
tools/sane-desc -s doc/descriptions -m hwdb |sudo tee /lib/udev/hwdb.d/20-sane.hwdb
```


Creating udev-rules
```
echo 'ATTRS{manufacturer}=="AVISION", DRIVERS=="usb", SUBSYSTEM=="usb", ATTRS{idVendor}=="0638", ATTRS{idProduct}=="2a1f", ENV{libsane_matched}="yes", MODE="0777"' | sudo tee -a /etc/udev/rules.d/55-udev-avision.rules
```


Some add  the device to /etc/sane.d/avision.conf
#usb 0x0638 0x2a1f
**Don&#8217;t** do that. it will give a warning like this when running scanimage
[avision] attach: "AVISION" - "FB2280E" not yet in whitelist!&#8221;

#reboot or
```
sudo udevadm control --reload-rules 
sudo udevadm trigger
```

And we can now scan :-)
```
scanimage -d 'avision' --format pnm > out.pnm
```

At least until next update.
I had some problems when I tried to figure out this. I set this debug variable, and it was great help.
```
export SANE_DEBUG_DLL=255
```

I have not tested the scanner much yet. I just had to document everything when it was fresh in mind. Hope someone find this usefull.

---

### Post by lt_gustavsen on 2020-03-21
I primarily bought this scanner for book scanning. But I had to test the photo capabilities.Straight out of the scanner the photos are washed out. Fortunately have I a scan target and a spectrometer somewhere....
Output from command```
scanimage -d 'avision'  --resolution 600 --format tiff    --mode "16bit Color"    | convert -   -rotate 90 albumsheet.jpg

```
[IMG]https://drive.google.com/thumbnail?authuser=0&sz=w320&id=1U7Z06fLtexeC4-HL0s4oshL1Hfp3p_fN[/IMG]
[Full size]("https://drive.google.com/thumbnail?authuser=0&sz=w320&id=1U7Z06fLtexeC4-HL0s4oshL1Hfp3p_fN")

After scanning the target and creating a profile with argyllcms, I got this output. No other processing applied.
```
scanimage -d 'avision'  --resolution 600 --format tiff    --mode "16bit Color"  -i Avision_FB2280E.icc   | convert - -intent Relative -black-point-compensation -profile  /usr/share/color/icc/colord/sRGB.icc  -rotate 90 albumsheet-color-corrected.jpg
```

[IMG]https://drive.google.com/thumbnail?authuser=0&sz=w320&id=1Xu-BobQ9J2vUY6T40XtVtqrgTapp0I9M[/IMG]
[Full size]("https://drive.google.com/open?id=1Xu-BobQ9J2vUY6T40XtVtqrgTapp0I9M")

This color profile may work with FB2080E also.
You can [find it here.]("https://drive.google.com/open?id=120N5qA9hDNaqU_nDFGU8yXUje1Ia227D")

---

### Post by lt_gustavsen on 2020-03-31
**Scanning time**
Just some more info:
Scanning  time in seconds for color scan:
```

Resolution   Full page   Novel page
100          3.42        3.12
200          3.44        3.12
300          3.46        3.11
301          9.78        7.77
350          9.79        7.78
400          9.82        7.78
500          9.85        7.78
600          9.87        7.78


```


**Scanned quality**
I scanned 11 page from a novel where I found a sample chapter at the publisher. Then I was able to compare the quality. For the quality control I used ocrevalutf8 from [https://github.com/ryanfb/ancientgreekocr-ocr-evaluation-tools](https://github.com/ryanfb/ancientgreekocr-ocr-evaluation-tools) I created my groundtruth file like this: It was a two colum paged file.
```
k2pdfopt -mode 2col sample_chapter.pdf
~/Downloads/xpdf-tools-linux-4.02/bin64/pdftotext   -layout  -enc UTF-8 sample_chapter_k2opt.pdf - > groundtruth.txt
```

Accuracy check was done like this:
```
ocrevalutf8 accuracy  groundtruth.txt 100pbm.txt |head -n 5
ocrevalutf8 wordacc groundtruth.txt 100pbm.txt |head -n 5
```



```

Reolution UT*    TT*              pbm            pgm            ppm
                                   Accuracy/
                                                  A/W            A/W
                                   Wordaccuracy
100       3.2    6/5.5/6.3        98.44/ 94.44   99.35/ 98.52   99.29/ 98.23
200       11.2   9.6/10/13.2      99.48/ 99.06   99.49/ 99.09   99.47/ 99.06
300       23.2   10.7/13.1/18.6   99.47/ 99.02   99.49/ 99.14   99.49/ 99.14
400       38.7   12.5/16.4/27.9   99.48/ 99.11   99.50/ 99.16   99.58/ 99.16
500       58     14.8/21.5/35.6   99.48/ 99.14   99.49/ 99.11   99.48/ 99.14
600       87.7   18/26.2/44       99.48/ 99.16   99.48/ 99.16   99.48 / 99.11



```

UT. Average unpaper processing time all 11 sheets from a novel. Ppm time was the fastest, but newer more than 1sec faster.
TT. Average tesseract processing time

I'm very impressed by the quality of tesseract.

My full processing workflow was like this:

#unpaper step
```
$ls -d */
$100/  200/  300/  400/  500/  600/
$ls 100/
page006.tif  page008.tif  page010.tif  page012.tif  page014.tif  page016.tif
page007.tif  page009.tif  page011.tif  page013.tif  page015.tif  page017.tif

mkdir 100/pbm 100/pgm 100/ppm
#Next line 3 times for every resolution, pbm,pgm and ppm
alias unptime="unpaper -t pgm  -start 6 100/page%03d.tif 100/pgm/unpaper%03d.pgm"
time unptime
```

Ocr was done like this:
```
ls 100/pbm/un* > files
alias tesstt="tseseract -l nor --dpi 100 files 100pbm txt"
time tesstt
```


Just a little update.  Quite exited with the results from tseseract I had to test it against a couple of competitors. I have access to Adobe Acrobat DC (not pro) at work. I only testedt the 300 dpi pgm source.
The results where 
accuracy 98.05%
wordacc 95.18%

I also found out there was somthing called  Azure Cognitive Services from microsoft with [Computer Vision API]("https://westus.dev.cognitive.microsoft.com/docs/services/5adf991815e1060e6355ad44/operations/56f91f2e778daf14a499e1fa") , it was free for one year. The problem was it outputed json file, and not one of the [knowen ocr formats]("https://github.com/UB-Mannheim/ocr-fileformat/issues/58"). So I hacked together something. It's very basic and only ment for my whises to convert scanned novel pages. The script extract all the json lines boundingBoxes and creates a fig file (xfig package). This file are converted to pdf and text are extracted. Very basic, and use with care.
Scrip as [txt]("https://drive.google.com/uc?export=download&id=1fmtyFdLX7pI72E65rzCXk2bdgmG93-Rq") or [zip]("https://drive.google.com/open?id=1EFa2uCLZZ2hFn3x7sFOLFT-TcVnPORR-").

Anyway results are:
accuracy  99.10%  Accuracy
wordacc   99.10%  Accuracy

---

### Post by lt_gustavsen on 2020-05-05
Just a simple video describing the scanning process. Sorry for missing English.
[https://www.youtube.com/watch?v=15qR8KUzVa4&](https://www.youtube.com/watch?v=15qR8KUzVa4&)

---

