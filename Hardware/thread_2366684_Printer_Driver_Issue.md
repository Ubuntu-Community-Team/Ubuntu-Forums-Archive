---
title: "Printer Driver Issue"
date: 2017-07-20
forum: Hardware
---

### Post by rgand on 2017-07-20
i have an issue with a printer driver in the new version of Linux Mint and they suggested I ask if any Ubuntu users have the same issue to see if the problem is the driver or Linux Mint.

My printer is a Canon iX6820. The driver was downloaded from Canon as the recommended driver for Ubuntu. It works flawlessly in linux Mint 17.3 but not the newer version, 18.2.

Here's the problem.  I have a checklist created in LibreOffice Writer that is multiple columns on a landscape legal size page. When it prints from a saved .odt, .doc, or .docx file, it prints part of it sideways at the top of the page so only the center section of the text prints. My scanner won't scan a legal document so these files are shortened a bit but the part dropped off is only blank paper and you can still see what it's doing.

If I save it as a .pdf and print it, it shrinks the whole list so it fits sideways on a legal page, still oriented 'portrait' although the document is set to 'landscape'.
[ATTACH=CONFIG]276069[/ATTACH][ATTACH=CONFIG]276070[/ATTACH]

I've tried every possible setting on the printer for landscape & portrait both in each print job or in printer defaults. All other Writer files, print fine but they aren't oriented 'landscape'. This file printed fine on this computer when I had mint 17.3 on it and the same driver installed.

The issue is not a corrupted file because I created a whole new document using text boxes instead of columns and the result is the same (that's the document in the photos).

I can put the file on a flash drive and print it fine on my wife's computer still with Mint 17.3 Cinnamon.

Thanks for any input on this. RG

---

### Post by pdc on 2017-07-20
I have replied to the post on the Mint forum that you left for this topic:

---

### Post by QIII on 2017-07-21
pdc, would you care to post here rather than make the Ubuntu Forums Community wonder?

---

### Post by pdc on 2017-07-21
certainly; if I post the link, as it has images from the initiator; and several posts in this thread 

[https://forums.linuxmint.com/viewtopic.php?f=6&p=1344787&sid=035549d9d1dc638b2ca329e4db8f0617#p1344787](https://forums.linuxmint.com/viewtopic.php?f=6&p=1344787&sid=035549d9d1dc638b2ca329e4db8f0617#p1344787)

---

### Post by rgand on 2017-07-21
Thanks for the informational post, pdc. I'll try your suggestions.

For some reason I'm not getting notifications of replies on this thread. I'll have to go check my account settings.

EDIT: I couldn't figure out what to do in my settings but I subscribed to this thread so that should take care of it.

---

### Post by uwe-bungto on 2017-07-21
Canon make great printers; their drivers are a real pain in the ass
I do not know if this will help.
sudo add-apt-repository ppa:rolfbensch/sane-git
sudo apt-get update

---

### Post by pdc on 2017-07-21
"their drivers are a real pain in the ass" ...... said with passion, but perhaps not totally correct these days .............. for all the inkjets that Canon sell these days, they offer source code; and rpm; and debian packages; in 32bit and 64bit variants; they update their drivers as new releases of ubuntu evolve; they provide essentially one driver now that works for all their inkets; let's be just a little bit fair; even if it not so much fun; I would say it is HP printers that cause the most posts in ubuntu/Mint these days for problems;

---

### Post by uwe-bungto on 2017-07-22
I used HP for about 15 years, but got away from them when they started to compete in the garbage market along with Epson and Canon. Their cartridges have expiry dates  after that the printer would not function. I discovered that by accident when I bought 4 sets of ink cartridges at Costco  for a ridiculously low price only to have 2 sets fail because of an expiry date. I had Epson all in one , much easier and Linux friendlier than a Canon, they are ink hogs, 3 sets of cartridges is the price of a new printer. It had a printer head clog and never to work again.  I bought  an Canon IP7220 (2 sets of ink is the price of the printer) to replace the printing part of the epson. Finally scraped the Epson and bought a Canon MX922 all in one. Since the first day I got warnings printer not found, printer off line, printer waiting for job to complete. That is both with the Linux drivers and the Turbo Print drivers. 

When I installed the Canon MX922 the printer worked;  but kept getting a warning scanner at 192.xxx.xxx.xxx not found. I finally found a PPA for drivers that might work.
sudo add-apt-repository ppa:rolfbensch/sane-git
That broke the installed sane package.

Now the Canon works sort of. There is no way I know of to print DVDs which it is capable of.

---

### Post by vocx on 2017-07-22
> **pdc said:**
> "their drivers are a real pain in the ass" ...... said with passion, but perhaps not totally correct these days .............. for all the **inkjets **that Canon sell these days, they offer source code; and rpm; and debian packages; in 32bit and 64bit variants; they update their drivers as new releases of ubuntu evolve; they provide essentially one driver now that works for all their **inkets**; let's be just a little bit fair; even if it not so much fun; I would say **it is HP printers that cause the most posts in ubuntu/Mint these days for problems**;
What? HP has excellent support with the "hplip" collection of drivers and utilities. I honestly don't know how people install their systems that they cannot make them work. I think many HP printers work out of the box although not with everything they are capable of, that's because they can use generic drivers. However, if the users had bothered to install their printers with "hp-setup", they may have seen that most functionality works.

> **uwe-bungto said:**
> I used HP for about 15 years, but got away from them when **they started to compete in the garbage market along with Epson and Canon**. Their cartridges have expiry dates  after that the printer would not function. I discovered that by accident when I bought **4 sets of ink cartridges** at Costco  for a ridiculously low price only to have 2 sets fail because of an expiry date. I had Epson all in one , much easier and Linux friendlier than a Canon, they are ink hogs, 3 sets of cartridges is the price of a new printer. It had a printer head clog and never to work again.  I bought  an Canon IP7220 (2 sets of ink is the price of the printer) to replace the printing part of the epson. Finally scraped the Epson and bought a Canon MX922 all in one. Since the first day I got warnings printer not found, printer off line, printer waiting for job to complete. That is both with the Linux drivers and the Turbo Print drivers. 

When I installed the Canon MX922 the printer worked;  but kept getting a warning scanner at 192.xxx.xxx.xxx not found. I finally found a PPA for drivers that might work.
sudo add-apt-repository ppa:rolfbensch/sane-git
That broke the installed sane package.

Now the Canon works sort of. There is no way I know of to print DVDs which it is capable of.

Oh, I see what your problem is now. You guys are buying inkjet printers. Don't buy injekt printers! Buy laser. It's much better. I get it, you have to do some photography work, so you need the color. I don't need it. So, for me, a laser printer is much better, and they work fine for scanning and printing. And if I really want to treat myself, I can buy a color laser as well!

By the way, adding a repository of "sane" affects the "sane" program, no the drivers for your printer. Don't be confused. The solution to a printer not working properly is with the drivers for that printer, not the "sane" component, which is just a backend that does the actual scanning.

---

### Post by pdc on 2017-07-22
> What? HP has excellent support with the "hplip" collection of drivers and utilities. indeed; but if you were to look at what driver is installed; you may well find that it is an open-source foomatic driver that is actually in the MAKE & MODEL line; in the PROPERTIES for the printer;

One actually needs to run ```
hp-setup
``` ...... to get the benefit of all the good work that the folks at HP put into hplip; but one can only comment that in there repeated posts asking for help with HP printers; that do not auto-configure ..... yes, I know they should ..... yes, I know everyone believes that they do .... yes, I know everyone always say they work all the time ..........

In summary, we all appreciate the good work that Printer Companies do to support those using linux: Brother; Canon; Epson; HP and Samsung are those that come to find where folks ask for advice and one can point them to the linux drivers they make available; it was said that rpm was the common package in Japan 10 or more years ago; so many drivers came in that format; we have come a long way in so many ways in linux now; now debian packages are widely available, which is greatly appreciated; all best wishes to linux users everywhere

---

### Post by uwe-bungto on 2017-07-22
> **vocx said:**
> What? HP has excellent support with the "hplip" collection of drivers and utilities. I honestly don't know how people install their systems that they cannot make them work. I think many HP printers work out of the box although not with everything they are capable of, that's because they can use generic drivers. However, if the users had bothered to install their printers with "hp-setup", they may have seen that most functionality works.



Oh, I see what your problem is now. You guys are buying inkjet printers. Don't buy injekt printers! Buy laser. It's much better. I get it, you have to do some photography work, so you need the color. I don't need it. So, for me, a laser printer is much better, and they work fine for scanning and printing. And if I really want to treat myself, I can buy a color laser as well!

By the way, adding a repository of "sane" affects the "sane" program, no the drivers for your printer. Don't be confused. The solution to a printer not working properly is with the drivers for that printer, not the "sane" component, which is just a backend that does the actual scanning.

My first laser printer was a HP laser jet III remember them.

---

### Post by uwe-bungto on 2017-07-22
It is not a matter of printer drivers but scanner  drivers

---

### Post by rgand on 2017-07-31
For some reason I'm still not getting notifications for this thread. Anyway, here's an update.

At  pdc's suggestion, I downloaded TurboPrint and installed it. It works  great with no issues. When my 30-day trial runs out, I guess I'll fork  over the fee for the driver.

> **uwe-bungto said:**
> Canon make great printers; their drivers are a real pain in the ass
I do not know if this will help.
sudo add-apt-repository ppa:rolfbensch/sane-git
sudo apt-get update
Thanks for the reply. I'm still a novice at working in the terminal. I think it would download something called rolfbensch but what is that? If it'll make the Canon driver work, I may give it a try.


Thanks for all the input on this.

---

### Post by pdc on 2017-07-31
what uwe-bungto gave you was a link to a SCANNER file: .....not a printer file 

Sounds like Turboprint is working well as the printer driver; glad to hear you are pleased with it: it is a very good product; they support it well; do keep in touch with them; you get huge control over file printing; and for inkjets, ink levels etc

---

### Post by rgand on 2017-08-01
Thanks, pdc. Yes, Turboprint is working fine. It's easy to use and gives good control over the print functions.

I sent them an email with a question last week but haven't heard back from them yet. Do they typically take a while to respond?

---

