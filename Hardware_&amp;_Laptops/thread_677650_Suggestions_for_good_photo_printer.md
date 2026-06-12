---
title: "Suggestions for good photo printer?"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by bsmith1051 on 2008-01-25
I have an 'old' HP Deskjet 5150 and I think it's time to retire it.  It still prints beautifully and it's nicely supported under Linux, but it frequently locks-up or refuses to print and there's no way to tell what's wrong.  Even hard-cycling the power doesn't always work.  So here are the PROS and CONS of this printer, and hopefully someone can steer me to a good replacement:

**PROS**
- works under Linux!
- supports 'photo' print mode, i.e., >3 colors
  (it holds two cartridges, a basic 3-color plus a swappable black or photo)
- has front-load/bottom paper-tray, so it fits on a shelf (nothing sticks out the back)
- wasn't too expensive ($200?)

**CONS**
- locks-up frequently!
- only has a couple 'idiot' lights for indicators, rather than a full LCD display
- no longer for-sale, i.e., I can't simply buy a replacement

FYI - I checked the OpenPrinting web-site for suggestions but everything they discuss is no longer for-sale.   
[http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters](http://www.linux-foundation.org/en/OpenPrinting/Database/SuggestedPrinters)

Put another way, I'm looking for a printer that:

**DESIRED FEATURES**
- is a current model
- works well under Linux (HP or Epson)
- can be shared on my home LAN with Windows machines
- includes basic print-driver for Windows
- supports 4- or 6-color photo mode
- LCD status display
- front loading and front outputting
- not too expensive (<$250)

---

### Post by disturbed1 on 2008-01-25
** - front loading and front outputting**

As far as I know, this will limit you to HP printers.

BTW, my top loading printers (Epson) don't have anything sticking out the back. If top feed, bottom output is ok, look for the Epson R380

---

### Post by bsmith1051 on 2008-01-25
Thanks for the quick reply!  I think you're right about the front-load aspect being limited to HP printers.  On your suggested Epson, how much vertical clearance do you need if you've got letter-size paper loaded?  Also, does the control panel give you good feedback info, e.g., paper-jam, ink low, etc?

I've been searching the current line of HP Deskjets and the current 5xxx models still use the same cartridges as mine (which would save me exactly _one_ round of cartridges...) while the 6xxx models are made with metal cases (as if meant to be more reliable?) and include built-in networking.  But I didn't see any with a proper LCD control panel.

Any idea if the 6xxx's built-in networking is supported by Linux?  I assume it shows-up as a 'Windows' print-share but does HPLIP (or whatever) support that?  I also read one review that the printer (one of the particular 6xxx models) didn't support a base-print driver, i.e., you had to install their complete hairball application suite.

---

### Post by jeffus_il on 2008-01-25
First of all I must apologise for this response.

The best photo printer is no photo printer.

I select my best digital photos, burn them to a cd, take them to a photo shop and have them printed on photographic paper. It turns out much better quality, and much cheaper.

---

### Post by disturbed1 on 2008-01-25
I don't have that model :( I have the one without LCD. But they are close. The clearance is the roughly 4-5" less than a sheet of paper with about 5 degrre slope back. The LCD does display some info, as well as flashing lights for low ink, paper jam and so on.

If you're in a tight space, I'll tell you upfront, that printer is too big.

The only HP models I've seen with LCDs were the photosmart series from a couple of years ago, and they were really only for memory card info. I haven't kept up with HP printers since I quit selling them at that time.

I'd head out to your local Office Depot/Office Max/Staples/Best Buy/What Ever Store, bring a tape measure and push some buttons :D

---

### Post by bsmith1051 on 2008-01-25
> **jeffus_il said:**
> The best photo printer is no photo printer
ha!  good one.  Granted that is the 'best' print option but I'm just looking for a 'good' print option; I still print mostly documents rather than photos.

---

### Post by eredhuin on 2008-01-25
Maybe you should consider keeping your photo printer and buying an inexpensive laser printer. These frequently have PCL6 or Post Script 3 support. And the all-in per-page cost is usually say 5 cents versus say 25 cents for a color page. 

I have a Lexmark E322n (no longer available, but it has successors) which works beautifully with Linux. 

I also have a reasonable and inexpensive photo printer, Canon MP510. I use it connected to my mac. I assumed going in that multifunction printers are basically unsupported by Linux. I see now that Canon has a linux driver for both the scanner and the printer parts. I have NOT tested it with Linux.

[http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900](http://alpha02.c-wss.com/inc/ApplServlet?SV=WWUCA900)

---

### Post by bsmith1051 on 2008-02-07
FYI
I ended-up buying an HP PhotoSmart D7160 and it works great.  It's got an LCD status screen, low profile, and both input/output trays face forward.  And, of course, it's recognized immediately by the HPLIP driver.

The only problem I've had is that the automatic photo-print detection doesn't work, i.e., the HPLIP driver is doing something to confuse or override the printer.  So I have to manually set the paper tray to 'Photo paper' rather than letting the printer figure it out on it's own.

---

### Post by bsmith1051 on 2008-03-05
BAH, things continue to go wrong.  First, the HPLIP driver does not correctly detect the ink levels.  Fortunately, this printer has the LCD display so you can check the actual levels.

Second, we printed a page on thick/stock paper and then had terrible grinding noises (and no successful printouts) for about an hour of trying.  Finally, it started working again ... no idea how or why.  There couldn't have been any paper jams since the paper never got torn?

---

### Post by oldsoundguy on 2008-03-05
> **jeffus_il said:**
> First of all I must apologise for this response.

The best photo printer is no photo printer.

I select my best digital photos, burn them to a cd, take them to a photo shop and have them printed on photographic paper. It turns out much better quality, and much cheaper.
 
Beg to differ .. (An old ALPS dye sublimation printer (8 color)) (if one can be found!)
 or a new Epson R series (I have an 1800) (also 8 color .. but pigment ink and will print up to 18" x 45" prints and will print on canvas) It  is a great printer.  Using quality paper you can get archival quality prints that will last 200 years (according to the manufacturer) .. I have seen a print rolled up and stuffed into a tall glass of water .. resided there for 2 days during a Nikon school.  Print came out of the water in perfect condition.

But you won't get the printer for 55 bucks at Rite Aid.

bsmith, sorry you are having problems, but I have problems with heavy stock on all of my HP printers .. that is why I went with the Epson .. you can run a CD/DVD through it and print on IT! (if it is printable)

---

### Post by pellgarlic on 2008-05-12
> **bsmith1051 said:**
> FYI
I ended-up buying an HP PhotoSmart D7160 ... The only problem I've had is that the automatic photo-print detection doesn't work, i.e., the HPLIP driver is doing something to confuse or override the printer.  So I have to manually set the paper tray to 'Photo paper' rather than letting the printer figure it out on it's own.

hi, i also have this printer and in general, it works very well for me, although i have a hit-and-miss experience with printing from the photo tray - most of the time it gives me some annoying error on the printer about the "wrong paper size" or some such rubbish, and spits out the photo paper unprinted... really annoying :( the only time i got it to print from the desktop was when i uninstalled the hplip from the repos and reinstalled it from the .gz download from the hplip website. didnt last beyond a reboot tho... :(

also, i found that the printout i got from that was quite low quality - when i wanted to print the same picture again, i ended up having to put the file onto a memory card and load it into the 7160's handy memory card reader, and it actually printed out a hell of a lot better than doing it from the desktop! :o

---

