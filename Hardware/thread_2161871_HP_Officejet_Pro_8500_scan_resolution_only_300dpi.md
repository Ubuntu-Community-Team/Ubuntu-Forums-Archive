---
title: "HP Officejet Pro 8500 scan resolution only 300dpi"
date: 2013-07-12
forum: Hardware
---

### Post by Turkulainen on 2013-07-12
HP OfficejetPro 8500 (a909a) stopped to scan greater resolution than 300dpi. HP support page says that printer should be fully supported by sane project. For some reason using xsane 0.998 the best resolution that can be selected is only 300 dpi. I have also installed latest hplib 3.13.6.

Scanner used to work fine with previous versions of ubuntu. This may be related to upgrading ubuntu 12.04 or maybe not. I tried to find solution from this and other forums with no luck. Can anyone help me to get my device work properly again? Thanks!

---

### Post by Turkulainen on 2013-07-16
Here's some more information:
as [suggested]("http://hplipopensource.com/node/333"), I run ```
hp-check
```[INDENT]"No errors or warnings."
[/INDENT]
 and 
```
scanimage -L
```[INDENT]device `hpaio:/usb/Officejet_Pro_8500_A909a?serial=MY922220FX' is a Hewlett-Packard Officejet_Pro_8500_A909a all-in-one[/INDENT]
and

 ```
xsane -v
```[INDENT]xsane-0.998 (c) 1998-2010 Oliver Rauch
  E-mail: [EMAIL="Oliver.Rauch@xsane.org"]Oliver.Rauch@xsane.org[/EMAIL]
  package xsane-0.996
  compiled with GTK-2.24.10
  with color management function
  with GIMP support, compiled with GIMP-2.6.12
  XSane output formats: jpeg, pdf(compr.), png, pnm, ps(compr.), tiff, txt
[/INDENT]

In [Xsane docs]("http://www.xsane.org/doc/sane-xsane-scan-options-doc.html") it's said that:
> Select resolution that is used for scanning. If the backends makes available a range of resolutions (e.g. 100-600 dpi) XSane can display a slider or a list of resolutions. You select this via *Preferences/Show resolution list*. 
The backend can define a list of resolutions insted of a range, in this case it is not possible to enable the slider.
 
This "slider" was available before but not anymore! 


If I have understood correctly, I have external backend "hpaio" which comes with HPLIP. [Support status]("http://www.sane-project.org/lists/sane-backends-external.html") for "HP Officejet Pro 8500 All-in-one Printer - a909a" should be "good" and according to [this]("http://hplipopensource.com/hplip-web/models/officejet/officejet_pro_8500_a909a.html") scanning should be "supported".

I do not know why I can't scan better that 300ppi. Scanner should be able to scan [4800 x 4800 ppi]("http://h10025.www1.hp.com/ewfrf/wc/document?cc=us&lc=en&dlc=en&tmp_geoLoc=true&docname=c01657988").

---

### Post by Turkulainen on 2013-08-18
Anyone?

---

