---
title: "Help me set up a printer server... Thing?"
date: 2015-08-21
forum: Hardware
---

### Post by nathan84 on 2015-08-21
I have no idea what to call this, but if I can get it set up correctly it will be worth everything to have a working wireless printer. I have a Canon Pixma 2920 which from every source I have gathered on Google is completely unsupported by Linux... I'm definitely not up for the task of creating my own drivers so I thought up something that I think could be possible. Basically I am going to load Windows XP onto an extra laptop I have laying around, install the printer drivers onto it, and I want to use that laptop sort of as a "server" that will receive the print requests from my Ubuntu Mate installation here on my desktop. So it would go Desktop -->Laptop --> Printer. Any ideas how to do this? Please keep in mind I'm fairly new to Linux (Well, kind of, I used it for about a year but never really did much and that was back when I sort of just had to) and I don't know just how complicated this process is going to be... But if I can get a working printer then I would be grateful. :)

---

### Post by TheFu on 2015-08-22
My advice.
Sell the Pixma, buy a linux-friendly printer and all these issues go away.  Seriously, I did exactly this for my Mom about 5 yrs ago. Made life much easier and we got her off the expensive ink over to cheap laserprinter toner. Thing the printer cost $55 back then.  I had tried and found proprietary solution for the Pixma drivers ... they wanted $50 ... When the kernel changes from 1 major release to the next, sometimes these drivers aren't compatible and another $50 would be needed.  Yep - buying a new printer was the better answer.  Get one that supports postscript with IPP as the protocol and it will work.

I did not look up if your specific printer does postscript or IPP. You should do that first.

---

### Post by nathan84 on 2015-08-22
Alright, I'm going to try and make arrangements to sell it, until then I'm going to just use a virtual machine for my printing needs. :)

---

### Post by Bucky Ball on 2015-08-22
*Thread moved to **Hardware**.*

Brother and HP are generally Linux-friendly. :)

---

### Post by TheFu on 2015-08-22
> **Bucky Ball said:**
> *Thread moved to **Hardware**.*

Brother and HP are generally Linux-friendly. :)

Mom got a Brother.  It was easy to get working - think I just plugged it into Mom's Lubuntu system and it was recognized. Mom printed 20+ pgs a day. She like to read email on paper.

I have a Samsung. Had to download a driver and follow some less than clear instructions to get it working. Haven't tried hard to make it work after the 14.04 update. It worked on 10.04 and 12.04, however.  Even if I need to run a tiny, tiny, tiny VM just to support the printer, I will. Don't feel I've gotten my $55 out of it the last 8 yrs. Still on the 2nd toner cartridge.

Some Cannon printers are supported by Linux as well. If you care about inkjet color control I think the Pimax line has some great printers ... are you certain this model doesn't support postscript? If the goal is a network printer - just get one that supports postscript and IPP.

---

### Post by QIII on 2015-08-22
Hello!

As far as I know, without installing some software to make your XP an actual print server, the best you can do with XP is ***share*** a printer.  This would mean that any client machine, i.e.: your Ubuntu machine, would need to have the appropriate driver installed.

What I have found by rooting around the web is that all the articles talking about making XP a "print server" are actually just about sharing the printer.  That's fine in a Windows network where all the machines can be provisioned with a Windows driver.

Unfortunately, that means we may not be able to help you.  Don't panic just yet, of course.  There may yet be some Forum denizen much brighter than I (which wouldn't take much) who can provide just the right solution for you.

---

### Post by weatherman2 on 2015-08-22
> **nathan84 said:**
> I have no idea what to call this, but if I can get it set up correctly it will be worth everything to have a working wireless printer. I have a Canon Pixma 2920 which from every source I have gathered on Google is completely unsupported by Linux... 

Hmm - people here seem to have had success:

[https://www.reddit.com/r/linuxmint/comments/2hd335/canon_pixma_mg2920_driver/](https://www.reddit.com/r/linuxmint/comments/2hd335/canon_pixma_mg2920_driver/)

I use two other Pixma printers in Ubuntu (not the 2920) and they work quite well now with native drivers - don't even use Canon's drivers anymore.

---

### Post by vandammes on 2015-08-22
I think the lazy person's way would be to put Teamview on both machines, and just copy documents from Ubuntu to the XP machine, paste them into Microsoft Turd, and print from that.

---

### Post by weatherman2 on 2015-08-22
vandammes, that sounds like way too much work to me.  I would setup Windows in a virtual machine on my Linux box before doing that, then install the printer drivers in Windows.  Then I wouldn't have to have a second computer running just to print!  In fact, I have done exactly this in the past when I needed to (already had XP in a virtual machine, so it was easy to use it for occasional printing).

---

