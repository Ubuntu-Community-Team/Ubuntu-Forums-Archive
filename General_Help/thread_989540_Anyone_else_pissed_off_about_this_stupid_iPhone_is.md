---
title: "Anyone else pissed off about this stupid iPhone issue?"
date: 2008-11-21
forum: General Help
---

### Post by EmanresuusernamE on 2008-11-21
Ok, I work for a Technical Sales and Services company, (glorified tech support), and we have a handfull of customers with iPhones.  Now normally I wouldn't care at all about what phone these people use, however the proprietaryism of Apple has severely pissed me off.  These customers use an Exchange server, which simplifies life quite a bit for them as it was meant to be; the issue, is with the iPhone's ability to use the Exchange server.  If we setup the phone to use the server first, before connecting it to a computer, everything works out beautifully, and almost convinces me that Apple can be a good company, and that I should buy stock.  However if the user connects their iPhone to their PC first, the iPhone will then whole heartedly refuse to connect to the Exchange server and will only send/receive email when the computer is on, running Outlook and on the internet.  This in it's entirety defeats the point of the Exchange server all together.

My question is, after a phone has been married to a computer, is there any way to break up this relation ship and cause a horrible divorce between the two?  I don't care if they won't speak to each other again as long as their emails and such will work.  The Windows PCs are whores anyways and will accept practically anything else over and over again, while the iPhone is the completely faithful little git that believes in the sanctity of marriage and won't leave the side of the PC for any reason.  LITERALLY.  We flashed the stupid phone, and tried to restore it to the factory default, this crashed and burned horribly and made the iPhone useless.  We then had ATT restore the phone for us, we didn't connect the phone to the PC, and yet it STILL would not receive emails without the PC being up and all that.  Talk about a die hard faithful relationship, wish I could find a wife like this.

We've already deleted and added the Exchange profile several times, we've removed the Exchange account from the Outlook client the phone was attached to.  We have SSL on the server already, I followed the instructions on the Apple website to enable the Virtual Directory so that the phones didn't require the use of secure log ins.  

I've heard that there's a file that you can send to the iPhone from like a Gmail account or such that you can use to help it get past all of this.  I'm assuming that it's the server's SSL certificate, but I'm wondering WHY do you have to send it from Gmail in the first place when you can go without SSL on the iPhone.  Fact is the stupid phones can be so cranky that you have to consistently switch between using SSL and no SSL sometimes to get them to work.  This is not a viable Enterprise solution that Apple is trying to ploy off on everyone, like their advertisement is leading people to believe.  I'm honestly tempted to go buy an iPhone so that I can do this and then sue them for false advertisement.

Does anyone have any help they can offer, or even some opinions and comments?

---

### Post by EmanresuusernamE on 2009-02-06
Hmmm, well it looks like this is solved.  I didn't fix it myself, but I'm glad it was fixed.  Turns out that there was a setting in the Cisco router that was causing an issue with this.  The keep alive time needed to be set at the maximum of like 9 minutes for the iPhone to properly work with the server.  As well as a few other registry tweaks on the server from what I was told.  I need to get a full run down of what all we had to do.

---

