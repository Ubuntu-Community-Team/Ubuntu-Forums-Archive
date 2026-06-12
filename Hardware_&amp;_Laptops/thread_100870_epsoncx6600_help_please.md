---
title: "epsoncx6600 help please"
date: 2005-12-08
forum: Hardware &amp; Laptops
---

### Post by teaker1s on 2005-12-08
installing driver with alien it installs but won't work, printer shown as installed will say it's printing testpage and nothing either on Photo Image Print System or epson stylus cx6600 but works on cx4800 driver

[For CUPS ver.] Stylus CX6500/CX6600 Series Photo Image Print System for Linux Description

Copyright (C) SEIKO EPSON CORPORATION 2004.

Note:
     About the latest information, please refer to our Web page.
     [http://www.epkowa.co.jp/](http://www.epkowa.co.jp/)

Contents
1   License Agreement
2   Version Up Record
3   Products Description
4   How to Install
5   Print
    5.1  Settings
    5.2  Stylus CX6500/CX6600 Series Setting Details
    5.3  How to Set
    5.4  How to Print
6  Other Software
    6.1  ekpd
    6.2  ekpstm
7  Paper Size and Margin
8  Handling Instructions
9  Acknowledgement


-------------------------------------------------------------------------------
1  License Agreement
-------------------------------------------------------------------------------
This package contains source code covered by the GNU General Public
License and the GNU Library General Public License (see ./COPYING and
./COPYING.LIB for their terms) and object code distributed under the
terms of the EPSON KOWA Public Licence (see ./COPYING.KOWA for
details).

All object code contained in the sources are Copyright EPSON KOWA
Corporation and SEIKO EPSON Corporation.


-------------------------------------------------------------------------------
2  Version Up Record
-------------------------------------------------------------------------------
Contents moved to ./ChangeLog.


-------------------------------------------------------------------------------
3  Products Description
-------------------------------------------------------------------------------
This software is a filter program used with Common UNIX Printing System
(CUPS) from the Linux. This can supply the high quality print with
SEIKO EPSON Color Ink Jet Printers.


-------------------------------------------------------------------------------
4  How to Install
-------------------------------------------------------------------------------
*  Before installing this software, check if the following CUPS software
   has been installed. This software does not work correctly without CUPS.

   Common UNIX Printing System (CUPS) <http://www.cups.org>


(1).... Installing a rpm file
Execute the rpm command to complete the installation.

rpm -i pips-scx6500_6600s-cups-2.6.2-1.i386.rpm

Depends on the distribution, dependent errors may occur.
Execution of the rpm command shown below may help you to avoid the error.

rpm -i --nodeps pips-scx6500_6600s-cups-2.6.2-1.i386.rpm


(2).... Setting after the installation

To use Photo Image Print System, CUPS must be set.
Be sure to set it up before you print first.

[ Restart CUPS ]
To make the installed filter active, restart CUPS.

(Ex.)
kill -HUP `pidof cupsd`

[ Add a Printer ]

- Add by command
  Execute the following command:

  /usr/sbin/lpadmin -p scx6500_6600s -E -v ekplp:/var/ekpd/ekplp0 -m ekscx6500_6600s.ppd

  Option Script:         p      Specify the setting name of the printer
                         E      Make the printer active
                         v      Specify driver and the destination to connect
                         m      Specify the setting file(PPD)

  Refer to lpadmin(8) for details of lpadmin.

- Add by using browser
  CGI is available in CUPS, so that printer setting is possible by using browser.
  To add a printer, follow the steps below.

  (1) Connect to CUPS Server(Port:631) from browser
      * (EX.)
      When CUPS is on the localhost, access to "http://localhost:631/"
  (2) Choose "Manage Printers"
  (3) Choose "Add Printer"
  (4) Enter a printer setting name in "Name", and choose "Continue"
      (set other items if required)
  (5) Set "EPSON Inkjet Printer #1 (Photo Image Print System)" for "Device",
      and choose "Continue"
  (6) Set "EPSON" for "Make", and choose "Continue"
  (7) Set "EPSON Stylus CX6500/CX6600 Series, Photo Image Print System (en)" for "Model",
      and choose "Continue"

A printer is added for Photo Image Print System.


-------------------------------------------------------------------------------
5  Print
-------------------------------------------------------------------------------
5.1  Settings

Following items can be set in Photo Image Print System for CUPS.

- Ink

        Choose monochrome or color print.

- Paper Size

        Choose the paper size for your document.

- Print Quality

        Choose the media and print quality for your document.


5.2  Stylus CX6500/CX6600 Series Setting Details

Options which can be specified in Stylus CX6500/CX6600 Series are listed below.
"Setting name by the optional specification" is not case sensitive.

     * The meaning of the list items
       keyword          setting string to specify an option
       browser display  strings appear in browser window of CUPS setting
       description      description of the setting

[ Ink ]
  Setting name for optional settings : Ink
  Setting name appears on browser: Ink

  keyword  | description
  -------- + -------------
  COLOR    | Color
  MONO     | Monochrome

[Paper Size]
  Setting name for optional settings: PageSize or media
  Setting name appears on browser: MediaSize

   * When describing multiple settings in the media option,
     put Paper Size at the beginning.
     Details of the media option can be found in the user's manual of CUPS

  keyword      |   description
  ------------ + -----------------------------------
  A4_AUTO      |   A4 210 x 297 mm
  B5_AUTO      |   B5 182 x 257 mm
  A5_AUTO      |   A5 148 x 210 mm
  LT_AUTO      |   Letter 8 1/2 x 11 in
  LGL_AUTO     |   Legal 8 1/2 x 14 in
  EXE_AUTO     |   Executive 7 1/4 x 10 1/2 in
  HLT_AUTO     |   Half Letter 5 1/2 x 8 1/2 in
  A6_AUTO      |   A6 Index card 105 x 148 mm
  INDEX5_AUTO  |   Index card 5 x 8 in
  INDEX8_AUTO  |   Index card 8 x 10 in
  ENV10_AUTO   |   Envelope #10 4 1/8 x 9 1/2 in
  ENVDL_AUTO   |   Envelope DL 110 x 220 mm
  ENVC6_AUTO   |   Envelope C6 114 x 162 mm
  ENV5X8_AUTO  |   Envelope 132 x 220 mm
  PHOTO_AUTO   |   Photo Paper 4x6 in
  4X6FULL_AUTO |   Photo Paper 4x6 in No Perforations
  PP100_AUTO   |   10 x 15 cm Photo

[ Print Quality ]
  Setting name for optional settings : Quality
  Setting name appears on browser : Quality

  keyword      | description
  ------------ + -------------------------------------------
  PLAIN_Q      | Plain Paper - Quality
  PLAIN_M      | Plain Paper - Medium
  PLAIN_S      | Plain Paper - Speed
  PLAIN_BKSAVE | Plain Paper (Black Ink Save Mode)
  BWP_Q        | Bright White Paper - Quality
  BWP_M        | Bright White Paper - Medium
  BWP_S        | Bright White Paper - Speed
  PMMATT_Q     | Matte Paper Heavyweight - Quality
  PMMATT_S     | Matte Paper Heavyweight - Speed
  EPP_P_Q      | DURABrite Photo Paper - Quality
  EPP_P_S      | DURABrite Photo Paper - Speed
  GPAPER_Q     | Photo Paper - Quality
  GPAPER_S     | Photo Paper - Speed
  OHP          | Ink Jet Transparencies

  * Black Ink Save Mode
    You can use a mixture of color inks to create black for printing black and
    white documents.
    Ink from the black ink cartridge is not used.
    the following requirements are in need:
         There is more color ink than black ink.
         The black ink cartridge is not empty.
         The color ink cartridges are not low.

5.3  How to Set

There are three method of print setting.
- Setting by Command

        Use lpoptions. Refer to the manual pages for lpoptions(1) for detail.
        (Ex. : ink=COLOR, Page Size=A4_AUTO, quality=PLAIN_Q)
        lpoptions -p scx6500_6600s -o ink=COLOR -o media=A4_AUTO -o quality=PLAIN_Q

- Setting by Browser
        Choose "Configure Printer" from the printer window to view the
        setting window.

- Specifying Options when Printing.

        Set by -o option as well as lpoptions.
        Refer to the manual pages for lpr(1) and lp(1) for details.


5.4  How to Print

Same as the existing LPR, execute the lpr or lp command to print.
Formats which can be printed are listed below.
        -Postscript
        -PDF
        -Text
        -Various image files

        (Command Ex.)
        When printing by default:

        lpr -P scx6500_6600s <file>
        lp -d scx6500_6600s <file>

        (Command Ex.) ink=MONO, media=LGL_AUTO,

        lpr -P scx6500_6600s -o ink=MONO -o media=LGL_AUTO <file>
        lp -d scx6500_6600s -o ink=MONO -o media=LGL_AUTO <file>

The print method varies depending on the implementation of CUPS.
Refer to the CUPS document for more information.


-------------------------------------------------------------------------------
6  Other Software
-------------------------------------------------------------------------------
6.1  ekpd

[ Description ]
ekpd is the communication daemon for bidirectional communication with
a printer.  It is necessary to start ekpd to use printer. Usually ekpd
automatically starts when starting Linux. If it is not running,
execute the following command with the root authority.

(Ex.  Redhat system of Linux)
/etc/rc.d/init.d/ekpd start

Following optional commands are available.

    start       start ekpd
    stop        stop ekpd
    restart     restart ekpd

[ Setup ]
The ekpd setting is described in /etc/ekpdrc. Setting items are as
follows (the defaults are shown in parentheses)

PrinterName
    The printer name described in CUPS  (scx6500_6600s)

PrinterDevicePath
    Path to the target device driver of a printer (/dev/usb/lp0)

DummyDevicePath
    Path to FIFO file for inputting a print data (/var/ekpd/ekplp0)

CommandServerPort
    The port number for communication       (35586)

Interactive setting can also be used with setting script
(/usr/local/EPKowa/SCX6500_6600S/setup).


6.2  ekpstm

ekpstm is a printer status monitor. It can display the status, and can
properly remove errors occurred in the printer.

Be sure to execute ekpd to use ekpstm.


-------------------------------------------------------------------------------
7  Paper Size and Margin
-------------------------------------------------------------------------------
Seiko Epson Ink Jet Printers provide margins (edges not to be printed) by default.
An image that exceeds the margins is cut off.
Paper Sizes and respective margins are listed below.

  PaperSize                           | Paper Size(1mm) | Margin(1mm)
  Name                                | Width  Height   | Left   Top    Right   Bottom
  ----------------------------------- + --------------- + ---------------------------
  A4 210 x 297 mm                     | 210    297      | 3      3      3       13
  B5 182 x 257 mm                     | 182    257      | 3      3      3       13
  A5 148 x 210 mm                     | 148    210      | 3      3      3       13
  Letter 8 1/2 x 11 in                | 216    279      | 3      3      3       13
  Legal 8 1/2 x 14 in                 | 216    356      | 3      3      3       13
  Executive 7 1/4 x 10 1/2 in         | 184    267      | 3      3      3       13
  Half Letter 5 1/2 x 8 1/2 in        | 140    216      | 3      3      3       13
  A6 Index card 105 x 148 mm          | 105    148      | 3      3      3       13
  Index card 5 x 8 in                 | 127    203      | 3      3      3       13
  Index card 8 x 10 in                | 203    254      | 3      3      3       13
  Envelope #10 4 1/8 x 9 1/2 in       | 105    241      | 3      3      3       20
  Envelope DL 110 x 220 mm            | 110    220      | 3      3      3       20
  Envelope C6 114 x 162 mm            | 114    162      | 3      3      3       20
  Envelope 132 x 220 mm               | 132    220      | 3      3      3       20
  Photo Paper 4 x 6 in                | 114    164      | 3      3      3       3
  Photo Paper 4 x 6 in No Perforations| 102    152      | 3      3      3       13
  10x15 cm Photo                      | 100    150      | 3      3      3       13


-------------------------------------------------------------------------------
8  Handling Instructions
-------------------------------------------------------------------------------

When you print using Photo Image Print System for CUPS, you may
encounter the problems listed below.

1. PostScript cannot be output in Japanese.
2. Print result differs from the document displayed on the application
you use.
    e.g.) A line feed is inserted where it should not be. 
3. Vertical lines are printed on the left side of printouts. 

This occurs when the rendering program of CUPS (which converts printing
documents into image data that Photo Image Print System can use)
converts PostScript files into image data, and it cannot be avoided with
this product. 

We appreciate your understanding. 
For your information, aforementioned problems have been found in CUPS
version 1.1.14.


-------------------------------------------------------------------------------
9  Acknowledgement 
-------------------------------------------------------------------------------
    We express our appreciation to the following people for cooperating 
    with us in developing this product.

    Nobby N Hirano <nobby@nmail.hiug.ne.jp>
    Toshihiro Yamagishi <toshihiro@turbolinux.co.jp>
    Nozomi Satou <nozomi@esd.spr.epson.co.jp>

***End of file

---

### Post by Haegin on 2005-12-13
WOW! lots of information - i must admit I didn't read it all and apologies if you have already seen this but this is how I got mine working: [http://www.ubuntuforums.org/showthread.php?t=38445](http://www.ubuntuforums.org/showthread.php?t=38445).

If you hadn't even searched for other posts - try it next time as somebody is almost always having a similar problem. Again, apologies if you did search...

---

### Post by teaker1s on 2005-12-13
thanks I did this as I still can't get the cx6600 printer driver to work

running epson iscan program and I've altered sane so now I can Scan with
iscan
sane 
sane through gimp

with sane I removed sane extra libs -if you don't you will have a terrible time with alien
sudo alien -di- iscan-1.18.0-1.c2.i386.rpm

to run iscan 'iscan'
edit the epkowa.conf in sane so it has this line
usb  0x04b8 0x0813
I've yet to get the cx6600 driver to work but cx 8300 works as well as cx6400

---

