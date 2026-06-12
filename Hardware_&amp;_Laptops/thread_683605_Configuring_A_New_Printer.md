---
title: "Configuring A New Printer"
date: 2008-01-31
forum: Hardware &amp; Laptops
---

### Post by markdashabout on 2008-01-31
Ive just purchased a new Photosmart HP8750 printer: This is an A3 photo printer from HP, and its connected via ethernet. Installation went well and I can use it via HPLIP, which very strangely comes under preferences in Gutsy. (So to print a file I need to go to system preferences, surely some mistake???) 

This thread is a general critique of some things that seem very strange when using HPLIP and this printer in general. Most issues I have not managed to solve, and I dont know if they are printer specific, driver specific, or OS specific.

1st problem, which I believe to be a printer hardware issue is that if I use 4x6 inch paper from the lower cartridge and add more than one sheet as you should be able to do, the printer prints the 1st sheet ok, then spits out 4 or 5 sheets of paper and then jams, every time. This does not happen with larger paper, eg A4. I am using HP Premium Photo Paper Glossy. Seems simple, send the printer back. Ive done this and the new one is identical. They are sending another.. But has anyone else had this issue on either Ubuntui or Windoze with this printer. I am reasonably sure the 3rd printer will be the same. 

2nd Problem - "Full Bleed" doesnt seem to work. I take full bleed to be synonemous with borderless. But I have not been able to achieve this. Ive created a jpeg that has corners at the edge and a box at what ought to be 5mm in. It has the correct aspect ration for the paper Im using. I am still experimenting, but I get a nasty border round it. This completely destroys my ability to print stuff acurately where I want it! I am printing by using the "fit to page" option in HPLIP. 

3rd problem - Did I really install an HP8750 printer ? No, there was only HP8700 to choose so may be that is a cause of some of these. I've tryied to edit the PPD file but have not had much success wit this. Its also not clear when the ppd file is read - at system start up, or if I reset the cupsys demon or every time I submit a print job or when its printed? 

4th problem command line support. Ive read quite a lot about command line support and the use of lpr. But what I really need here is a couple of different queues for printing images, perhaps for different paper sizes, qualities etc. I cant find anywhere how to set up more than one queue with different default options on one printer. Thats what I think I need to do. I am open to other suggestions. Perhaps I should use alias or shell scripts to supply different default parameters. 

Does anyone have any answers? Ive been quite specific here about the printer I am using, but I think these issues could help many others.

---

### Post by markdashabout on 2008-02-03
Is anybody reading this? Does anyone have any suggestions at all?

---

