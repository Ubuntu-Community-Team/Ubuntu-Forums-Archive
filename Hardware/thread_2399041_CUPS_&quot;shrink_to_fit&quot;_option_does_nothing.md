---
title: "CUPS &quot;shrink to fit&quot; option does nothing"
date: 2018-08-21
forum: Hardware
---

### Post by willsc123 on 2018-08-21
[FONT=arial]Hi,

I've more or less configured a dye-sublimation printer (Mitsubishi CP-D80D) to print images directly from command line using lp or lpr but I'm experiencing an issue with the shrink to fit option in CUPS.[/FONT][FONT=arial][FONT=arial]
[/FONT][/FONT]
[FONT=arial][FONT=arial]The problem is that CUPS automatically scales the images to full page size no matter what option I select between 'Shrink', 'Crop' or 'Expand'. The image gets cut at the borders. I've tried printing the image from GIMP's printing dialog and it goes fine, but I need to do it automatically from command line.

I've read in other forums that the cups-filters package README says image printing defaults were changed and to get back to the old behavior I need to supply one of four options [COLOR=#24292E] "nofitplot", "filplot=Off", "nofit-to-page", or "fit-to-page=Off".[/COLOR][/FONT][/FONT]
[FONT=arial][FONT=arial]
[/FONT][/FONT]
[FONT=arial][FONT=arial]Does anyone know where do I have to put these options? I've tried passing them as options for lp or lpr but the results don't change. Is there any configuration file I need to edit or do I have to manually compile the package and set these options then?[/FONT][/FONT]
[FONT=arial][FONT=arial]
[/FONT][/FONT]
[FONT=arial][FONT=arial]I would appreciate any help on this.
[/FONT][/FONT]
[FONT=arial][FONT=arial]Thanks in advance[/FONT][/FONT]
[FONT=arial][FONT=arial]
[/FONT][/FONT]
[FONT=arial][FONT=arial]Guillermo[/FONT][/FONT]

---

### Post by wyliecoyoteuk on 2018-08-21
lpr -l specifies no filtering

lpr -o scaling=<percent> scales page

lpoptions command might be what you need.
[https://www.cups.org/doc/man-lpoptions.html?TOPIC=Man+Pages](https://www.cups.org/doc/man-lpoptions.html?TOPIC=Man+Pages)

Setting the Page Margins

Normally the page margins are set to the hard limits of the printer. Use the -o page-left=value, -o page-right=value, -o page-top=value, and -o page-bottom=value options to adjust the page margins:

lpr -o page-left=value filename

lpr -o page-right=value filename

lpr -o page-top=value filename

lpr -o page-bottom=value filename

lpr -o page-left=value -o page-right=value -o page-top=value -o page-bottom=value filename

The value argument is the margin in points; each point is 1/72 inch or 0.35mm.

---

### Post by willsc123 on 2018-08-22
Hi, thanks for the reply

I've tried using *lpoptions* but it outputs the same settings that are available at the CUPS GUI in the browser, which are ok except for the scale to fit one.

*lpr -l* sends the file without format and the printer is not able to interpret it and print it.

I did try* lpr - o scaling* but what I got was a lower resolution image printed full page, scaled down at the percent and then, who knows why, scaled back up to fit the page.

Found this command
[https://www.cups.org/doc/man-cupsfilter.html?TOPIC=Man+Pages](https://www.cups.org/doc/man-cupsfilter.html?TOPIC=Man+Pages)

I've been messing around with it but don't know how it works. You input the file with some options (which I don't know what they are. I've tried those "nofitplot", "fit-to-page=Off" but no luck) and it converts it to the stdout and then pipe it to *lpr*. The output of the print is even worse, just one corner printed and in like a halftone black and white.

---

### Post by wyliecoyoteuk on 2018-08-22
I think that we need some more information.
How large is the image, and what type?
If it is a raw. TIFF or jpg file for example, there will be no page size info.
If there is no size information in the file, these commands will fail.
GIMP output will supply that page size.
Unless there is page size information in the file, size is based on number of pixels i.e. @400 dpi, an a4 image is 3308 pixels wide, @1600 dpi, it is 13232 pixels wide, and so on.
So lacking page size information, an A4 sized 1600 dpi image printed @400 dpi would need to be scaled to 25% to fit on an A4 page.
The problem is raster image processing (RIP)
It might be worth looking at image magick.
[https://www.imagemagick.org/script/index.php](https://www.imagemagick.org/script/index.php)

---

### Post by willsc123 on 2018-08-23
The image is the output of a combination of 4 photos for a photobooth. I already use imagemagick for the montage.
Here's the output of Imagemagick identify:

```

Image: out.jpg  Format: JPEG (Joint Photographic Experts Group JFIF format)
  Mime type: image/jpeg
  Class: DirectClass
  Geometry: 1182x1795+0+0
  Resolution: 300x300
  Print size: 3.94x5.98333
  Units: PixelsPerInch
  Type: TrueColor
  Endianess: Undefined
  Colorspace: sRGB
  Depth: 8-bit
  Channel depth:
    red: 8-bit
    green: 8-bit
    blue: 8-bit
  Channel statistics:
    Pixels: 2121690
    Red:
      min: 0 (0)
      max: 255 (1)
      mean: 161.962 (0.635143)
      standard deviation: 52.1154 (0.204374)
      kurtosis: -0.0896188
      skewness: 0.621475
      entropy: 0.756255
    Green:
      min: 0 (0)
      max: 255 (1)
      mean: 161.577 (0.633635)
      standard deviation: 51.8019 (0.203145)
      kurtosis: -0.0382022
      skewness: 0.678239
      entropy: 0.748103
    Blue:
      min: 0 (0)
      max: 255 (1)
      mean: 161.443 (0.633111)
      standard deviation: 51.7317 (0.202869)
      kurtosis: -0.0283687
      skewness: 0.695284
      entropy: 0.744743
  Image statistics:
    Overall:
      min: 0 (0)
      max: 255 (1)
      mean: 161.661 (0.633963)
      standard deviation: 51.8833 (0.203464)
      kurtosis: -0.0526082
      skewness: 0.664787
      entropy: 0.7497
  Rendering intent: Perceptual
  Gamma: 0.454545
  Chromaticity:
    red primary: (0.64,0.33)
    green primary: (0.3,0.6)
    blue primary: (0.15,0.06)
    white point: (0.3127,0.329)
  Background color: white
  Border color: srgb(223,223,223)
  Matte color: grey74
  Transparent color: black
  Interlace: None
  Intensity: Undefined
  Compose: Over
  Page geometry: 1182x1795+0+0
  Dispose: Undefined
  Iterations: 0
  Compression: JPEG
  Quality: 92
  Orientation: Undefined
  Properties:
    date:create: 2018-08-22T18:28:55+02:00
    date:modify: 2018-08-22T16:43:58+02:00
    jpeg:colorspace: 2
    jpeg:sampling-factor: 1x1,1x1,1x1
    signature: 667857b39ffc1621e30c2ea713d93410946f7fccaebd52e66caac96c5223afc2
  Artifacts:
    filename: out.jpg
    verbose: true
  Tainted: False
  Filesize: 178KB
  Number pixels: 2.122M
  Pixels per second: 106.1MB
  User time: 0.010u
  Elapsed time: 0:01.019
  Version: ImageMagick 6.9.7-4 Q16 x86_64 20170114 http://www.imagemagick.org

```

The image is 1182x1795 pixels in size, 300dpi. This should be correct for the 4x6 inch paper size option of the printer.

As you said GIMP, does something with the image that translates correctly for the printer, as the print just as it should be. Don't know what is the difference between GIMP and command line. Maybe is the page size info missing on the jpeg, as you said.

Hope you can help me with it. If you need some more details, please let me know.

Thanks in advance

---

### Post by wyliecoyoteuk on 2018-08-26
Not sure that I can help, but this may:

Scaling Images

The -o scaling=percent, -o ppi=value, and -o natural-scaling=percent options change the size of a printed image:

lp -o scaling=percent filename 
lp -o ppi=value filename
lpr -o natural-scaling=percent filename

The scaling=percent value is a number from 1 to 800 specifying the size in relation to the page (not the image.) A scaling of 100 percent will fill the page as completely as the image aspect ratio allows. A scaling of 200 percent will print on up to 4 pages.

The ppi=value value is a number from 1 to 1200 specifying the resolution of the image in pixels per inch. An image that is 3000x2400 pixels will print 10x8 inches at 300 pixels per inch, for example. If the specified resolution makes the image larger than the page, multiple pages will be printed to satisfy the request.

The natural-scaling=percent value is a number from 1 to 800 specifying the size in relation to the natural image size. A scaling of 100 percent will print the image at its natural size, while a scaling of 50 percent will print the image at half its natural size. If the specified scaling makes the image larger than the page, multiple pages will be printed to satisfy the request.

---

