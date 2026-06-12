---
title: "Printing to custom paper sizes with CUPS"
date: 2013-02-22
forum: Hardware
---

### Post by jbhtexas on 2013-02-22
I'm having trouble printing custom paper sizes from LibreOffice to my Xerox 6180DN.  I'm not sure where the problem lies...CUPS, driver, LibreOffice...so I guess I'll start here.  I'm using Ubunto 12.04 LTS and LibreOffice 3.5.7.2.

Here's how it works in Windows...
1) Set up the document for a custom page size
2) When printing using Postscript, select "Custom" paper size in the printer dialog box
3) Click the "Edit" button that appears in the printer dialog after "Custom" paper size is selected, and input the custom paper dimensions
4) Print

In LibreOffice, there is no "Custom" paper size available.  LibreOffice picks a paper size closest to the document page size.  If opening the Printing app and selecting Job Options, there is a "Custom" option in the "Media Size" list available, but somehow LiberOffice isn't picking up that option.  Also when printing in LibreOffice, when clicking "Properties" from the printer dialog and selecting the "Device" tab, there is no "Media Size" setting.  

My solution has been to export to PDF, and then open the PDF in Adobe Reader.  When printing in Adobe Reader, under "Printer Properties", there is a "Custom" option in the "Media size" setting, but there is no dialog box to input a custom media paper size.  So, I pick the manual paper tray (MPT) for input, check "Choose paper souce by PDF page size" and it does print. The printer prompts me to load a custom size paper in the MPT.

As the export-to-PDF method is tedious, I'm wondering if anybody has any suggestions how to do this directly from LibreOffice.  Perhaps I am missing something.  It seems there could be an issue with both LibreOffice (not presenting the custom paper size option) and the CUPS printing dialog (no way to input the custom dimensions once the custom media size option is selected).

Thanks for any tips or suggestion!

---

### Post by Robertjm on 2014-01-09
Did you ever resolve this problem? I'm having the same problem with my Canon ip1800 printer. I see Custom as an option. however, it says the paper size is 0.00" by 0.00" with no way to change it.

---

### Post by frankaen on 2014-04-06
[SIZE=3]Hi,
I am new here, and a newbie in Linux, after 25 years of working in Windows. :)
Same problem.
Xubuntu, 13.10, xfce
LibreOffice 4.1.4
We have in the company HP CP1215, few pieces, and because bugged drivers for Win8 (thank you HP) we are trying to find a solution.
We use for our clients a custom paper size, in mm: 210 x 165. Almost A5.
And everything like above: printer has the option, but when printing from LibreOffice no option for custom size.
I read this:
[http://ubuntuforums.org/showthread.php?t=1619543](http://ubuntuforums.org/showthread.php?t=1619543)
but it does not work in this case. No simplified drivers or something.

Has anyone got a clue?
Any help highly appreciated.
Peter
[/SIZE]

---

