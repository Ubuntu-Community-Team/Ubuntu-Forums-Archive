---
title: "Printer Recommendations"
date: 2015-03-01
forum: Hardware
---

### Post by Keith_Beef on 2015-03-01
I'm just about as annoyed as it is possible to be with a printer&#8230;

My Epson Stylus Photo 890 has given many years of reasonably good service, but I am sick and tired of its quirks and irritations, and it is really not the printer that I need these days.

When I bought it, it was pretty much the best printer on the market for my needs, but the real big annoyance is that I can not reliably get ink levels reported from it and it is really, really slow when printing high quality black text on white paper.

Yesterday and today, helping my daughter to understand printing and bookbinding for her school project, has been an endless source of frustration for us both. I'm reduced to sending the PDF file one page at a time; I tried printing the whole PDF and the printer started printing gibberish after the first five pages. (To be fair, though, I didn't have the time to spend really troubleshooting this, so I can't be absolutely certain that it was the printer, rather than CUPS)

So, my ideal printer:
[LIST]
[*]should be an inkjet (pages of laser printed text have a shininess to the text that I don't like, and a few years after binding the pages stick together or stick to plasticated covers),
[*]should print in colour and have separate cartridges for each colour (not a single cartridge with three or more colours) and for black,
[*]should print both sides of the sheet of paper (duplex printing),
[*]should print at least ten pages per minute in very high quality black text on plain paper.
[/LIST]

Secondary considerations are:
[LIST]
[*]printing on A3 paper (roll paper would be nice, but not necessary).
[*]network printing (ethernet or WiFi, or compatibility with the printer server built into my ISP box, from Orange).
[/LIST]

The big question, though, is absolute Linux (and specifically Ubuntu compatibility).

So, any recommendations?

---

### Post by gifford on 2015-03-01
My recommendation is always a Brother printer for Linux compatibility. We currently use a MFC-495CW on the network and have never had any issues with our Ubuntu machines printing
or scanning to it. We have always had very good luck with the Multi-function printers from Brother. This model is several years old so am not sure what has replaced it. 
It does have separate ink cartridges for colors and black and the print quality is very good.

---

### Post by Mike_Walsh on 2015-03-01
Hallo, Keith.

Hm. You sound like me; an Epson man. I, too, have been using them for years.....very good printers. I admit, they're not the easiest to set up in Ubuntu; the separate installations, and set-up for, the printer section and THEN the scanner, rather threw me when I first started using Linux last year.....but having been using these things for over 35 years, it didn't take me long to suss things out.

I'm currently using a Stylus SX 218; I don't think they're on the market any more, but they were, I believe, the consumer segment fore-runner to the business-class WorkForce Series. Certainly they seem to use the same Linux software as mine, and I've helped a few people to get their WorkForce machines up & running.

I would thoroughly recommend the WorkForce printers. There is, I believe, a model with large, external ink tanks ((one for each colour, and separate black of course), which will print somewhere in the region of 3000 A4 pages or so between refills!

Of course, there ARE many different makes of printers on the market; some easier to set-up in Linux, some harder. In all honesty, once you get used to the 'quirks' of the Epson install routine, it's all pretty straight-forward. That's just my opinion, however; I happen to be rather biased!

In the long run, the decision has to be yours; no-one can make that for you...

EDIT: Am currently investigating the 'escputil' command-line utility app for Epson printers. It's taking some getting used to..!


Regards,

Mike. :)

---

### Post by Keith_Beef on 2015-05-25
> **Mike_Walsh said:**
> 
In the long run, the decision has to be yours; no-one can make that for you...

Thanks for your reply, Mike. You're right, that the decision is going to be entirely mine, and probably no two people have exactly the same requirements.

> **Mike_Walsh said:**
> EDIT: Am currently investigating the 'escputil' command-line utility app for Epson printers. It's taking some getting used to..!


I don't find the 'escputil' command particularly difficult to use, but the enormous problem I have always had with it is that when the ink in any of the cartridges in my StylusPhoto 890 gets below a certain level (I don't know what that is, though) the printer seems to stop replying to the command.

Since there is one combination cartridge for the colour inks, and one for the black ink, this means I have a 50% chance of changing the wrong cartridge whenever I run into this problem... this explains why I want a separate cartridge for each colour and something that I didn't put in a bullet point, but which can be inferred from what I have written, **accurate ink level reporting**.

One nice feature I've seen on some big colour laser printers at work is a message on the printer's display panel to order a colour toner pack, but not to install it yet. It would be great to be able to able to get CUPS to poll the printer's levels at the start and end of each print job and make those statistics available... Hmm, now there's a thought... maybe this would happen if I turned on accounting... it would make sense to record the different kinds of paper (in a printer capable of different surface finishes, weights and sizes) and the ink (assuming colour ink is still dearer than black ink) used in a print job to be able to bill users, teams, projects or departments for printer consumables.

---

### Post by SeijiSensei on 2015-05-25
Since I don't share your aesthetic objections to laser or laser-like printers, I'm using a Brother HL-3170CDW.  It has all the other features you're looking for.

---

### Post by finnbuntu on 2015-05-26
Hello,

I am currently using a HP Officejet Pro 8600 printer and would wholeheartedly recommend it. I purchased it new in July 2013, and it has been working flawlessly since then under all 3 platforms I have used it on (Linux, Chrome OS and Windows 7/8). 

The HPLIP Linux driver is very good and wireless printing works extremely well, but I have not yet tested Ethernet. It has four seperate ink tanks (cyan, magenta, yellow and black), and the black XL cartridge is rated for 2100 pages, which is realistic in my experience. It has a duplexer built in, and print speeds are very fast. The only negatives are that blacks come out as extremely dark gray, and it does not support A3, but it has everything else you are looking for.

I believe that the 8600 has been replaced with the Pro 8620, if you need the all-in-one functionality, but if you need just a printer, the Pro 8100 is the same printer, but without the scanner or fax modem. The 8100 is also half the price of the 8620 (€185 vs €90 on Amazon France), and a full set of high-capacity compatible cartridges seems to be €30, and a genuine set €85.

I hope this helps,
Finn

---

### Post by SeijiSensei on 2015-05-26
I dumped my HP inkjet (Photosmart 8250) after it kept complaining about "expired" ink cartridges.  Perhaps that's not an issue in a high-volume printing environment like an office, but for a home user like me who only prints a few pages now and then it became extremely annoying and expensive.  There are tricks you can try to get it to use an "expired" cartridge, and the results showed that there was nothing wrong with the cartridges.  It seemed largely designed so that HP can sell more cartridges, and I'm not going to play their game.

If they offered an override option in the menus, I might have been less unhappy, but of course that would spoil their little scam.

---

### Post by mattharris4 on 2015-05-26
I haven't had any trouble with the MG series from Canon, I have both an MG2120 and an MG3520 and both were easy to set-up in Canonical OSes.  They have a copier, scanner and printer on them.  If you need a fax this series does not come with one, though.

---

### Post by Keith_Beef on 2015-09-19
Thanks for all the advice.

After a lot of research and hesitation, I bought a HP OfficeJet Pro 7612  for a bit less than &#8364;200 and a set of cartridges for &#8364;60. It works fine, wirelessly, for printing and also for scanning.

I was surprised by that: I started Simple Scan and the scanner was detected automatically as an "HP Officejet_7610_series". The scanning mechanism is a bit noisy at times and a full-colour A3 scan at 600dpi takes 2 minutes 17 seconds and gave me a 3.9MB file. This was two of the standard Ubuntu test pages on A4 paper, put side by side, so there is lots of white space that compresses well as a JPeg.

One annoyance, is that I can't read the ink levels remotely&#8230; I have to press the touchscreen on the printer. This is annoying for my wife and kids, who will want to print from other rooms in the house than the attic office / spare bedroom where the printer is kept; it means a trip upstairs to check the ink levels, back down to wherever the computer is, then back up to collect the printed pages.

A second annoyance is that the printer doesn't get its time and date from an NTP server, I have to enter these from the touchpanel.

But on the whole, I've been very pleased with the printer so far. 

Well, I'm a little bit less happy now&#8230; I tried printing some self-adhesive labels, as a test. I took some [Avery 05453 labels]("http://www.avery.com/avery/en_us/Products/Labels/Identification-Labels/Print-or-Write-Multi_Use-Labels_05453.htm"), these are 4" wide by 3" high, two labels to a sheet.

In "Printer Properties - Printer Options", I set the media size to Photo 4x6in, Type to Plain Paper, Double-sided printing Off.

I loaded the labels in the tray, set the guides so the edges of the stack of labels and push it all the way in.

In gLabels, I started a new label, using the Avery 0543 template, normal orientation.

I set  gLabels to print 1 sheet of two labels, and they were printed on the backing-paper side! I had loaded the labels label-side up, so it is clear I have to load them backing-paper side up.

Also, very curiously, although my text was laid out to be in the top right-hand corner of the label, it was printed in the top left-hand corner.

I altered the label a bit, putting a QR code of the address in the top left-hand corner with the textual address immediately to the right. The first label came out blank. I tried again, still blank, but the printer panel said that the media size was wrong, and didn't match the detected size.

I went to "Printer Properties - Printer Options", set the media size to Custom. Another blank page, and the printer panel again said that the media size was wrong.

I went to "Printer Properties - Printer Options", set the media size to Index Card 4x6in. Another blank page, and the printer panel again said that the media size was wrong.

Finally, loaded A4 paper, and asked gLabels to print me a sheet with outlines and crop marks&#8230; and this time the labels were printed, with a line where the separation between two labels would have been.

So there seems to be some problem in the way that the printer detects the size of loaded paper.

---

