---
title: "Scanning multiple pages with Xsane"
date: 2008-11-28
forum: General Help
---

### Post by hardyfan on 2008-11-28
Scanning multiple pages using Xsane.  How can I get it to wait while I change the document ?  Epson CX3700.

Thanks to all who helped, I can now do what I wanted.  A little embarrassed that such a simple solution was overlooked by me.

---

### Post by ricardisimo on 2008-11-28
HP Officejet 5610 All-in-One in my case.

I'd like to be able to stack all 50-60 pages in the top feeder tray, come back an hour later and have every one scanned to a subfolder of "Documents". Is this even within the realm of possibility? Or am I just going to have to stand there to swap each and every page? Thanks in advance.

---

### Post by 73ckn797 on 2008-11-28
> **ricardisimo said:**
> HP Officejet 5610 All-in-One in my case.

I'd like to be able to stack all 50-60 pages in the top feeder tray, come back an hour later and have every one scanned to a subfolder of "Documents". Is this even within the realm of possibility? Or am I just going to have to stand there to swap each and every page? Thanks in advance.

I have the same HP printer and I designate how many pages are to be scanned and let it work. I do assign them to be saved to a specific directory/folder, file format and how each one is named; typically "scan001" or whatever ".tif". If you designate 60 pages and only load 50, there will be 10 blank scans produced. I typically do not scan more than 8 at a time but have scanned 15-20 at on time.

I will leave it to you to look through the set-up of Xsane and figure out how to do it.

---

### Post by 73ckn797 on 2008-11-28
> **hardyfan said:**
> Scanning multiple pages using Xsane.  How can I get it to wait while I change the document ?  Epson CX3700.


If it is a flatbed scanner and does not have document feeder, you only need to tell it to scan one page. You will then have to insert next page and click scan again. I have a document feeder so I tell it to scan however many pages I have and let it work.

---

### Post by ricardisimo on 2008-11-28
I imagine I select "Save" instead of viewer, and "ADF" instead of "Auto". Sound about right?

---

### Post by Jose Catre-Vandis on 2008-11-28
> **hardyfan said:**
> Scanning multiple pages using Xsane.  How can I get it to wait while I change the document ?  Epson CX3700.

In the main xsane window on the right near the top, there is a dialog (next to a target symbol) with "Viewer" selected. Using the drop down arrow select "Multipage". A dialog will open and you should click on the "Create Project" button. This will hold all the individual files in your project. Now you can scan one page at a time at your own pace, and they will all be stored in the one project. When you are done, click on the "Save Multipage File" button, having chosen your preferred output format. if you are happy with your resultant file you can delete the project to prevent accumulation of duplicate files on your PC.

Remember to change back from Multipage to Viewer in the main xsane dialog in order to get rid of the Multipage dialog.

---

### Post by hardyfan on 2008-11-29
Solved problem by downloading gscan2pdf simple interface to allow scanning of multiple pages.  Easy to use does everything required.

---

### Post by MountainX on 2009-01-16
I got xsane working. Just set source to ADF. Set number of pages to something large (I used 99).

You can scan a bunch of pages to the viewer and then save individually. Or you can change the selection to multipage and it will make one PDF from all pages.

xsane actually works reallly well -- much better than the Windows software that came with my HP L7680. I'm super pleased with xsane.

---

### Post by bturig on 2009-03-21
> **hardyfan said:**
> Solved problem by downloading gscan2pdf simple interface to allow scanning of multiple pages.  Easy to use does everything required.

Took your advice "hardyfan". gscanpdf worked very nicely. Thanks.

---

### Post by shahin on 2010-03-04
> **Jose Catre-Vandis said:**
> In the main xsane window on the right near the top, there is a dialog (next to a target symbol) with "Viewer" selected. Using the drop down arrow select "Multipage". A dialog will open and you should click on the "Create Project" button. This will hold all the individual files in your project. Now you can scan one page at a time at your own pace, and they will all be stored in the one project. When you are done, click on the "Save Multipage File" button, having chosen your preferred output format. if you are happy with your resultant file you can delete the project to prevent accumulation of duplicate files on your PC.

Remember to change back from Multipage to Viewer in the main xsane dialog in order to get rid of the Multipage dialog.

This worked like a charm. 
Thanks

---

### Post by gpelese on 2010-10-26
Hello,

Simple Scan is for you, very simple and efficient.

Cheers

---

### Post by MrSnowmiss on 2012-02-03
> **shahin said:**
> This worked like a charm. 
Thanks

Thank you from me too!

I raised the numbers of scans to be done (left to the Target icon) and then after 1 scan my scanner wasn't reachable anymore.

But this is the solution to make a multiple page .pdf :D

---

