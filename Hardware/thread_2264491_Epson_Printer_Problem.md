---
title: "Epson Printer Problem"
date: 2015-02-07
forum: Hardware
---

### Post by Bob_Pennington on 2015-02-07
I purchased a new Epson WF-7620 printer after my HP Printer died; which was working perfectly under Lubutu.  Downloaded the latest driver from Epson for linux & installed.
Now, anything that I print; turns out **DIM**, like the printer is running out of ink.  Not the case.  Wife's window box works fine; but my printing does not.
Would anyone have any ideas about this.  Thanks in advance.

---

### Post by Mike_Walsh on 2015-02-08
Hallo, Bob.

I don't think this is a software problem; more of a 'settings' problem, and I think it's one I've run into myself before now.

I have a 4-yr old SX218; a 'baby brother' to the WorkForce series (uses the same drivers, anyroad). I think this is more to do with your colour profiles. I'm doing this entirely from memory, since I haven't had a Windows install for the best part of a year now, but...

If you go into the status monitor in Windows, and... I think it's the second or third tab along (forget what it's called....it's the one that deals with your colour settings and stuff like that), you'll see, over on the right-hand side, a button with a toggle, giving either 'Epson Vivid' or 'Adobe RGB'. I was CONSTANTLY having to reset this under XP.....but I rather think my install was getting corrupted; it was over 10 years old, and had never been re-formatted or re-installed, which, I've found since, is essential for a Windows install to keep behaving itself.

I digress.

You can find the same setting control in CUPS. This is what runs ALL printers 'under the hood' in Linux, but you don't often see it; certainly the 'buntu flavours give you a nice GUI to play with. The GUI doesn't give you this button, but the CUPS web interface will.

Go into your browser, and enter 'localhost:631' into your address bar....this will bring up the web interface for CUPS. Click on the end tab, 'Printers'; you'll find your printer listed. Click on that, and it'll open the 'Administration' tab, with your printer details. Click on the 'Administration' box on the left-hand side, and select 'Set default options'. Click on 'Colour Management' in the top bar of the next page, and then, make sure you've got 'Epson Vivid' showing; if not, select it. 

When you've done that, either have a play with the colour, brightness, contrast controls as well, or just click on 'Set Default options' at the bottom. That will set it as the standard option.

You've also got the colour, brightness & contrast controls in the GUI in Lubuntu; you can have a play with them there. I will tell you this much; Epsons DO like the brightness set high, and the contrast pretty low. Mine does, anyway....but my previous one was much the same.

My personal settings are as follows:-

Bright: +15
Contrast: -10
Saturation: -5
C:+5
Y:-2
M+1

Try the brightness, contrast & saturation at those levels initially....then adjust to suit yourself.

Let us know if that helps.


Regards,

Mike.

BTW: Of course, I may be on completely the wrong track, here.... ;)

---

### Post by Bob_Pennington on 2015-02-09
Thanks Mike for the info.  Followed your info; but unfortunately there is no option for "Color Management" to be found anywhere under "Admin/Set Defalt Options" or anywhere else under Cups for the printer.  Does this option relate to distro version, as I'm running 12.04 LTS?  Any other info would be greatly appreciated.

---

### Post by Mike_Walsh on 2015-02-09
Hi, Bob.

No, I don't think this is anything to do with distro version. It's looking like it IS a driver problem, to be honest. I'm guessing you downloaded the generic 'escp/r' filter/driver from Epson, didn't you?

I'm asking, because that particular one is a bit short on features; in fact, it's VERY basic, and barely lets you make any adjustments at ALL. I can't get onto the Epson download site at the moment, as it appears to be down for maintenance. Bear with me though, 'cos I'm going to try and see if I can dig you out a more suitable one. They ARE there, but Epson do NOT make it easy for Linux users to find them.....and this is despite them being members of the Linux Foundation, which in theory means they've signed up to trying to provide as much material to the Linux world as possible; yeah, r-i-i-i-ght!

Watch this space, and I'll do my best to try and get you sorted with this.


Regards,

Mike. ;)

---

### Post by Bob_Pennington on 2015-02-09
Problem solved! Thanks Mike for your help.  Although I did not find "color management" under CUPS; I did some playing around (click fields & look....duh) and found under "Set Default Options", setting "Media Type" to "plain papers-Standard-Vivid" solved the problem of DIM printing.  Thanks again Mike.

---

### Post by Mike_Walsh on 2015-02-09
Fair enough! Glad I was able to give you a few pointers in the right direction.

Do remember, for future reference, that you can usually do quite a bit more, settings-wise, via CUPS itself. Most people, as I said, aren't aware of its existence, but it's a very handy way of fixing printer woes.

I don't usually bother with the 'escp/r' generic driver; I much prefer the specific one for my printer, since it gives me a LOT more control over the finish of my graphics projects.....but of course, it all depends on what you use it for. For mostly text output, the 'escp/r' driver is fine; and I DO remember now, that 'Media Type' IS one of the options for that driver......I don't have that in the one I use, but DO have several other bells & whistles instead!


Regards,

Mike.

---

