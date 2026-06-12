---
title: "Hewlett-Packard Officejet 7612, problems with different paper sizes"
date: 2015-10-04
forum: Hardware
---

### Post by Keith_Beef on 2015-10-04
Following on from [another thread]("http://ubuntuforums.org/showthread.php?t=2267393"), where I asked for advice on choosing a new printer and then started to describe my experiences with this printer, I'm starting a new thread to explore problems printing to paper sizes other than A4.

I wanted to print some labels on Avery 05453 stock. These are sheets 4"  × 6", each sheet has two 3" × 4" labels.

I designed my labels in gLabels, and found that the printer complained that the detected size of the labels loaded in the feeder did no match the defined page size: the message "paper detected does not match paper size selected" appears on the printer's touchscreen.

[This thread]("http://h30434.www3.hp.com/t5/Other-Printing-Questions/HP-1515-Printer-doesn-t-print-A5-paper/td-p/4955567") on an HP support forum reveals that some HP printers that are supposed to be able to print on A5 paper will not do so when you use the printer driver intended for that model of printer. The advice given is "try a different driver"&#8230; :rolleyes: In the case described on that other forum, the advice was to use the HP Deskjet 5550 or the HP Deskjet 6940 driver for an HP 1515 printer.

Has anybody else run into problems of paper sizes with this printer, and found a solution?

---

### Post by tgalati4 on 2015-10-04
I've printed labels with 7110, 7210 and 7310 printers without issue.

Couple of things to try:

1.  Create a custom paper size that is slightly different from A5, but close enough to print your labels correctly.  Use the single-sheet feeder and pull down the back panel so the sheet comes out the back--sometimes the paper-detection needs that back door open.

2.  Add several different printers in CUPS.  Use different drivers with each and see what works.  Even try older Officejet drivers.  All you need is one driver to work. 

3.  Find some A4 sheets of Labels and modify your glabels template to get the end result.  Sometimes you need to pick a working solution than fight something that is supposed to work but doesn't.

4.  Tape 4 of the 4"x 6" sheets together to make a 8" x 12" sheet of labels.  Modify your glabels template to print this.  Create a custom paper size for the 8" x 12".  You will need to adjust borders and margins.  Once you have used up these 4x6 label sheets, find new Avery sheets that are A4.

5.  Take a single 4" x 6" label sheet and tape it to a single sheet of A4 paper.  Modify your glabels template to work with this A4 sheet, but only print one corner.  The paper acts as a carrier for the label paper, using a full-size sheet.  It wastes paper, but at least you work around paper detection issue.

The only issue I have had with 4x6 are photos with bleed edges.  Sometimes the paper feed is off or the margins are off, but then the Officejet is not really a photoprinter.

---

### Post by Keith_Beef on 2015-10-05
> **tgalati4 said:**
> I've printed labels with 7110, 7210 and 7310 printers without issue.

Thanks for replying… that you've managed to print labels is encouraging news, but what sheet size were your labels, A4, A5, 3"×5", 4"×6", something else?

> **tgalati4 said:**
> Couple of things to try:

1.  Create a custom paper size that is slightly different from A5, but close enough to print your labels correctly.  Use the single-sheet feeder and pull down the back panel so the sheet comes out the back--sometimes the paper-detection needs that back door open.

The single-sheet feeder and back door trick is a good idea, and not one that I had thought of.

> **tgalati4 said:**
> 2.  Add several different printers in CUPS.  Use different drivers with each and see what works.  Even try older Officejet drivers.  All you need is one driver to work. 

Yes, that is essentially the advice in the HP forum. I was hoping that somebody here might have run into exactly my combination of printer and paper-size problem and might have found which driver already works.

I'm lazy and an ecologist: if somebody else has already found the solution to my problem, I would rather not spend fifteen hours and not waste thirty sheets of paper rediscovering the solution.

Rule N° 4: don't reinvent the wheel.

> **tgalati4 said:**
> 3.  Find some A4 sheets of Labels and modify your glabels template to get the end result.  Sometimes you need to pick a working solution than fight something that is supposed to work but doesn't.

Again, good advice, but see my response to your point 2 above.

> **tgalati4 said:**
> 4.  Tape 4 of the 4"x 6" sheets together to make a 8" x 12" sheet of labels.  Modify your glabels template to print this.  Create a custom paper size for the 8" x 12".  You will need to adjust borders and margins.  Once you have used up these 4x6 label sheets, find new Avery sheets that are A4.

NO NO NO! That just sounds like a recipe for paper jams and bits of sticky tape getting dragged into the feeder mechanism.

> **tgalati4 said:**
> 5.  Take a single 4" x 6" label sheet and tape it to a single sheet of A4 paper.  Modify your glabels template to work with this A4 sheet, but only print one corner.  The paper acts as a carrier for the label paper, using a full-size sheet.  It wastes paper, but at least you work around paper detection issue.

Same as above: I don't trust the tape to stay in place.

> **tgalati4 said:**
> The only issue I have had with 4x6 are photos with bleed edges.  Sometimes the paper feed is off or the margins are off, but then the Officejet is not really a photoprinter.

True, it's not really a photo printer, and that's not what I bought it for, really. 

I'm going to play around with some other sizes of paper; I don't have any A5, but I should have some 3"×5" and 4"×6" card stock, as well as some other square (maybe 6"×6") stock around.

---

### Post by tgalati4 on 2015-10-05
I always get 8.5" by 11" Avery labels (US Letter size).  I have not printed smaller sizes.  If your printer can print A5 card stock or even plain paper cut down to A5, then it should be able to handle labels.  Because of the paper path, sometimes the labels will peel off.  That is why you need to use the back door, if your printer has one.  That allows a straighter paper path so the labels won't peel off on the rollers.  Using cellophane tape has worked on my 7310 printer to print 3x5 index cards stuck to Letter plain paper to print full-bleed 3x5 since the paper handler has trouble with full bleed in 3x5.

---

### Post by Keith_Beef on 2015-11-28
Right, I think I've found out why gLabels would not print correctly. At least, I have found out how to make it work.

First of all, I made sure I knew how the paper should be loaded: the labels need to be face down in portrait orientation inthe loader.

When I tried printing the labels directly to the printer, I saw the paper size as defined by the template I have made:  152.4mm high by 101.6mm wide, but the options for Paper size (set to Other) and Orientation (set to Portrait) are both ghosted out, so I can't change them.

I think that this is where the problem lies. I had set the default paper size for the printer to A4. I *think* that this means that gLabels sends something (a PDF, maybe?) to the CUPS which expects to use the default paper size of A4. The printer receives conflicting paper sizes, and complains.

To get around this, I generated from gLabels a PDF of a full page of two labels. Then I opened this PDF in Evince (the default PDF viewer). Here, when I choose Print, I get more or less the same dialog as in gLabels, but Paper size and Orientation are both active. I left Orientation as Portrait, and noticed that the paper size had been set automatically to Index Card 4×6in, which corresponds to 101.6×152.4mm.

Now I was able to print the PDF file of the label sheet.

Now for something very curious… In Paper Size I saw (among the list of dozens of predefined sizes) an option to Manage Custom Sizes…. Here, I was able to create a custom size that I named Avery 05453 which I set up as being 152.4mm high by 101.6mm wide. If I print to that paper size, I get no error messages (neither on the computer nor on the printer's own display panel), but the printer spits out a blank sheet.

---

### Post by tgalati4 on 2015-11-28
Well in Windows, if you install the Avery software, several Avery label templates get installed and they show up as page size selections in the printer dialogs and they work and print as you expect.  With no Avery software for Linux (that I know of), you have to create these templates yourself.  If you get the size or orientation off, then the printer will get confused.  It's a lot of experimentation just to get a label.    

I've had the best luck with full page size labels (letter or A4) with *glabel* templates that are also full size.  This is fine if you want to print several labels at once.  If you want one-at-time, custom address labels, then this won't work very well.  For that, I have used the cellophane tape method--taping a single address label (3"x5") to a Letter size manilla folder stock as a carrier.  This works fine if you only have a few labels.  This would not work for production use.  

Label printers:  [http://calltheninja.com/blog/ubuntulinux-compatible-label-printers/](http://calltheninja.com/blog/ubuntulinux-compatible-label-printers/)

[http://ask.slashdot.org/story/09/07/30/2317215/linux-friendly-label-printer-recomendations](http://ask.slashdot.org/story/09/07/30/2317215/linux-friendly-label-printer-recomendations)

---

### Post by Keith_Beef on 2015-11-30
> **tgalati4 said:**
> Well in Windows, if you install the Avery software, several Avery label templates get installed and they show up as page size selections in the printer dialogs and they work and print as you expect.  With no Avery software for Linux (that I know of), you have to create these templates yourself.  If you get the size or orientation off, then the printer will get confused.  It's a lot of experimentation just to get a label.    

I've had the best luck with full page size labels (letter or A4) with *glabel* templates that are also full size.  This is fine if you want to print several labels at once.  If you want one-at-time, custom address labels, then this won't work very well.  For that, I have used the cellophane tape method--taping a single address label (3"x5") to a Letter size manilla folder stock as a carrier.  This works fine if you only have a few labels.  This would not work for production use.  

Label printers:  [http://calltheninja.com/blog/ubuntulinux-compatible-label-printers/](http://calltheninja.com/blog/ubuntulinux-compatible-label-printers/)

[http://ask.slashdot.org/story/09/07/30/2317215/linux-friendly-label-printer-recomendations](http://ask.slashdot.org/story/09/07/30/2317215/linux-friendly-label-printer-recomendations)

Those links are useful, thanks. I've used Zebra label printers at work a few times, and was impressed by them, but for my needs they are too expensive.

I also have a Dymo Duo label and tape printer that I have struggled with… It was quite a long time ago… I just looked for [the thread]("http://ubuntuforums.org/showthread.php?t=861781"): 2008! I had completely given up on it, and only used it with the Windows computer that my employer forced me to use… now I no longer work there, I'm tempted to dig out that Dymo label printer to give it another try.

---

### Post by Keith_Beef on 2015-12-06
So I connected that old Dymo printer to my computer; CUPS saw two printers, and assigned them the URIs "usb://DYMO/LabelWriter%20DUO%20Label?serial=06102216133691" and  "usb://DYMO/LabelWriter%20DUO%20Tape%20128?serial=06102216133691&interface=1".

I sent a test page to the first of those, and out came a label, but it was printed too small…

I set the page size to Shipping Address, and the test page was a tad too big, the right hand border was not printed; so I tried again but with the option "Scale to fit" checked, and it printed just fine.

I've not managed to get anything from the other URI, which looks like it should be the tape printer.

---

