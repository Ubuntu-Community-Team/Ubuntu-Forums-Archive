---
title: "I think I killed my printer. Can it be revived?"
date: 2005-06-28
forum: Hardware &amp; Laptops
---

### Post by derrick1985 on 2005-06-28
Hey

The other day, I decided to try my hand at sharing a printer across two ubuntu computers, one with a server install. Anyways, somewhere along the lines, I messed up my Printer and CUPS, and I can't figure out how to fix it.

The driver I'm using is for a Lexmark z25 printer, it still works ok because it works on my windows box. The driver is converted from rpm using alien.

Anyways, how can I totally get rid of everything printer related on my ubuntu system, reinstall cups and hopefully, get a working printer back again.

---

### Post by manicka on 2005-06-28
You could try uninstalling and reinstalling/restarting Cups, then remove and add your printer usng Administration--> Printing

---

### Post by derrick1985 on 2005-06-28
[QUOTE=manicka]You could try uninstalling and reinstalling/restarting Cups, then remove and add your printer usng Administration--> Printing[/QUOTE]

Tried that, still a no go.

Found out something interesting though, If for say, I choose the z22 driver included in Ubuntu, it tries to print a test page, but the paper only comes through so far, then stops, and I have to restart the printer to get the paper out. 

Now, if I choose the z35 2.0-1 driver, nothing happens. I'm beginning to think it's the driver, but i've already uninstalled it, reconverted it, and installed them again, but still a no go!

---

### Post by manicka on 2005-06-28
Lexmark have terrible driver support for linux. I have a 3 in 1 X1125 that I'd love to use but I can't even get basic printing to work at the moment. When I get a few spare bucks I'll be replacing it with a HP or somethitng else that is well supported

---

### Post by derrick1985 on 2005-06-28
I agree with that, but that still doesn't explain why it worked one second, and not the next.

---

### Post by manicka on 2005-06-29
[QUOTE=derrick1985]I agree with that, but that still doesn't explain why it worked one second, and not the next.[/QUOTE]
 okay I see what you mean. It seems there's a corrupt config file somewhere that isn't being deleted properly. I'm not quite sure where the driver config files are kept after install. Maybe you could try deleting the ppd file for the printer in in /etc/cups/ppd

---

### Post by derrick1985 on 2005-06-29
[QUOTE=manicka]okay I see what you mean. It seems there's a corrupt config file somewhere that isn't being deleted properly. I'm not quite sure where the driver config files are kept after install. Maybe you could try deleting the ppd file for the printer in in /etc/cups/ppd[/QUOTE]

No files in that directory.

I even deleted the enitre /etc/cups directory, still a no go.

I tried installind KDE today to see if I could get some more information, and i'm thinking it's an error communicating to cups. It seems, that when I try to set up a test page, it says it sent it, a box pops up for less that half a second, then disappears. Then, today when I tried through kde to configure the cups server, it gave me an error about being unable to communicate to the cups server.

Any ideas from that, i'm stumped. Also, now when I select a z22 printer, I get nothing. So, i'm REALLY beginning to think it's a cup problem, but I still can't figure out what.

---

### Post by derrick1985 on 2005-06-30
OK

Did a fresh Kubuntu install (on another computer, I don't want to get rid of this one unless I have to) and guess what, no work. So, it's not cups, it might be the driver, but then again, I don't know.

I think i might know, but tell me please if i am wrong. Has Alien been updated recently?

I hate my printer. I need a printer in linux!

---

