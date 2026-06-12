---
title: "Printers that have ubuntu compatible cartridge management system"
date: 2013-10-31
forum: Hardware
---

### Post by harfin on 2013-10-31
One of the only good benefits of my old Windows XP os was that I could manage Epson printer cartridges on screen rather than manually via the printer's own hardware / buttons.

I am going to change my printer soon, and would like to get one (preferably an Epson) that enables me to do the same sort of thing under ubuntu. Things like, how much ink is left in each colour cartridge, which cartridge needs to be replaced, head clean etc

Is there a list somewhere that shows which model printers would enable me to do just that? 

Alan

---

### Post by Mark Phelps on 2013-10-31
There is an app known as mtink -- which I have used for several years now to manage three different Epson printers.

---

### Post by tgalati4 on 2013-10-31
Any HP printer that is recognized by *hpijs* has ink management.  HP ink prices will make you want to throw the printer through the window.

---

### Post by coldraven on 2013-10-31
> **tgalati4 said:**
> Any HP printer that is recognized by *hpijs* has ink management.  HP ink prices will make you want to throw the printer through the window.

I have an Epson Stylus photo R300 and for several years ran it with a Continuous Ink Supply System (CISS) with no problems. IIRC it cost £37 from eBay and came with 6 x 100ml tanks of ink. I could refill the tanks with a funnel at a cost of £12 for another 600ml of ink!
The print quality was good although they will eventually fade in bright light.
The downside is that it is difficult to move the printer with the external tanks.

When the chips in the cartridges refused to reset I bought re-fillable cartridges that have the latest resetting chips. A set of six empty cartridges is about £12 on eBay.
Pros: The printer can now easily be moved to a different room. I already had lots of spare ink.
Cons: The cartridges need refilling more often and I can never find the syringe to do it with.

My advice is before buying a printer, Google for the model and "CISS".

---

### Post by fantab on 2013-10-31
> **tgalati4 said:**
> Any HP printer that is recognized by *hpijs* has ink management.  HP ink prices will make you want to throw the printer through the window.
+1 on both the points.

HP's marketing/sales strategy seems to be higer the Printer cost lower the ink price and vice versa.

---

### Post by Zill on 2013-10-31
I have never understood why people still buy inkjet printers when laser printers are faster, more reliable *and* are far cheaper to run, even though the initial purchase price is slightly higher.  I did actually buy an inkjet printer once - never again. ;-)

---

### Post by kurt18947 on 2013-11-01
> **Zill said:**
> I have never understood why people still buy inkjet printers when laser printers are faster, more reliable *and* are far cheaper to run, even though the initial purchase price is slightly higher.  I did actually buy an inkjet printer once - never again. ;-)

Color, I suspect.  At one point - I don't know about today - the cost/page of using a color laser was about the same as inkjet.  Using refillable cartridges or continuous ink systems as coldraven mentions, inkjet cost/page is very reasonable indeed.

---

### Post by elliotn on 2013-11-01
> **tgalati4 said:**
> Any HP printer that is recognized by *hpijs* has ink management.  HP ink prices will make you want to throw the printer through the window.

+1 I also use HP printer and ink management is good

---

### Post by Zill on 2013-11-01
> **kurt18947 said:**
> Color, I suspect.  At one point - I don't know about today - the cost/page of using a color laser was about the same as inkjet...
TBH, I have no need for regular colour printing as, for example, if I wish to print a photo then it is far more cost-effective to take this on a memory card to a local outlet and use their "professional" printer.  I suspect many owners of colour inkjet printers often use them for b&w document printing, which is, IMHO, always far cheaper to do on a laser printer.

---

### Post by harfin on 2013-11-02
Thanks for that Mark. Downloaded it as it sounds ideal. Bit lost on the set-up though. 
Alan

> **Mark Phelps said:**
> There is an app known as mtink -- which I have used for several years now to manage three different Epson printers.

Thanks Mark. 
Having problems though.
The app says it cannot find my printer and refers to membership of a group 1p.  That doesn't mean anything to me.
It also wants me to point it (MTInk) to my browser (which is Chromium), but I am having difficulty doing that also, so I can't even get to the hgelp file!

Any suggestions or advice?
Alan

---

### Post by fantab on 2013-11-02
The user should belong to the group 'lp'. its [LP not 1p]

```
sudo adduser username lp
```

---

### Post by harfin on 2013-11-02
> **fantab said:**
> The user should belong to the group 'lp'. its [LP not 1p]

```
sudo adduser username lp
```

Done that now, thankyou very much.
Still cannot get the help file and, yes I have managed to point app to Chromium browser.
MTInk doesn't pick up my printer though
Does it have to be very specific to maker and model (in my case, Stylus S20) or should Epson Colour be sufficient.

---

### Post by Darren_Rose on 2013-12-18
> **harfin said:**
> Done that now, thankyou very much.
Still cannot get the help file and, yes I have managed to point app to Chromium browser.
MTInk doesn't pick up my printer though
Does it have to be very specific to maker and model (in my case, Stylus S20) or should Epson Colour be sufficient.

I ended up using

```
sudo mtink
```

in terminal

---

