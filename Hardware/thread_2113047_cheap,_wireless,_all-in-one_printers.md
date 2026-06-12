---
title: "cheap, wireless, all-in-one printers"
date: 2013-02-06
forum: Hardware
---

### Post by grizdog on 2013-02-06
I realize that there are a lot of threads on this subject, including the sticky compatibility thread, but I have looked around, and unfortunately, this information has a short shelf life - like so many things in computing.

I am looking for a new printer to replace the HP all-in-one that I just had to discard.  It was and HP all-in-one, and it was great except it was impossible to get spare parts for it, and it needed new rollers.  That has left me a little irritated with HP.

That said, from experiences in the office and elsewhere, I have come to believe that three best manufacturers are HP, Canon, and Epson, and would like to stay with one of those.  Moreover, HP seems to have the best reputation for compatibility with Linux, so I don't want to cut off my nose to spite my face - if HP is the best choice, I will go with them.

I think my requirements are pretty common - I don't use a printer much, and don't need much, but I want to be able to scan and copy, too.  I don't need photo quality, and no speed is too slow.  I don't need two-sided printing, I can just run the paper through a second time - just a basic printer - well, a basic all-in-one, with wireless. And color.  a color inkjet all-in-one, with wireless.

Price is a secondary consideration - I can afford a printer, but I rebel at paying for a whole bunch of things I will never use, including high speed, card reader, all sorts of software, and other bells and whistles.

Also, a big issue has been Linux (Ubuntu) compatibility.  Canon has a nice collection of Linux drivers on their Canon-Europe site, but unless I am missing something, most of the models listed over there are not available over here in the US - I may well be missing something, I have a feeling I wasn't seeing everything on the site.  But I want a printer that will work with wireless both for printing and for scanning.  I don't mind doing a little configuration, but I would like something that is likely to survive the next Ubuntu upgrade.

Finally, it has to be a printer that I can actually buy in the US.  My local computer store where I like to go is limited pretty much to business machines, high speed laser printers and the like.  I don't like the big box stores, but I will go into one if I have to, and I don't like buying things online if I think there is a high probability that I will have to return them.

I think there are a lot of Ubuntu users out there with similar requirements, I would think someone would want to serve this niche.  So, what should I buy, and how should I configure it?

Thanks

---

### Post by kurt18947 on 2013-02-06
Canon's European drivers work in the U.S. too.  Models may not be exact but 'families' drivers usually work.  HP has an excellent rep for being Linux friendly.  Definitely stay away from Lexmark and Dell (rebadged Lexmark).  Lexmark's consumer grade linux hardware support sucks and they're getting out of the inkjet printer biz this year.   

I've had very good luck with Brother.  Their hardware and ink are pretty reasonably priced and they're available at most chains like Staples, Office Max, Best Buy etc.  Wired and wireless printing and scanning work reliably.  They use CLI installers and offer .rpm & .deb files.  A lot of their "do this before installing" stuff is obsolete though, it was written around the time 8.04 was released and hadn't been updated the last time I looked.  Most of it no longer applies to modern *buntu releases.  I use their installer script for printers found here:

[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_prn.html#f00104)

Installing the scanner is a little more involved, particularly if you're running a 64 bit O.S. but the tricks are documented.

  [http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/faq_scn.html)

I think Epson has pretty good linux support but I have no experience with it.

---

### Post by coffeecat on 2013-02-06
> **grizdog said:**
> just a basic printer - well, a basic all-in-one, with wireless. And color.  a color inkjet all-in-one, with wireless.

<snip>So, what should I buy, and how should I configure it?

Thanks

I bought myself a HP Deskjet 3520 e-all-in-one a couple of weeks ago. It feels a bit cheap-n'-cheerful but it does its job well, although I haven't tested photo-quality printing yet. Both printer and scanner work out of the box in 12.10 and work in 12.04 if you install the latest hplip drivers from the hplip website. 

As far as setting up is concerned, you configure wireless by connecting the printer via USB at first, as weird as that sounds. Wrongly assuming that I could only do this in Windows or MacOS, and because the install CD was missing from the packaging, I downloaded the Windows setup utility and used Windows for the initial configuration. I needn't have bothered. Since doing this I discovered the command line hp-setup utility which launches a GUI which *should* be able to configure wireless for you - but I haven't tested this.

Also - I discovered a useful seemingly undocumented feature. If you find out the LAN IP address of your configured and wireless connected printer and connect to that in a browser, you get a web configuration page. This includes a wireless setup wizard which is a bit eccentric seeing as you have to setup the wireless first in order to use the web-based wireless setup wizard. No doubt it might come in useful! :)

---

### Post by kurt18947 on 2013-02-06
> **coffeecat said:**
> 
............
 This includes a wireless setup wizard which is a bit eccentric seeing as you have to setup the wireless first in order to use the web-based wireless setup wizard. No doubt it might come in useful! :)

That may have been thought up by the brother of the guy who recommended to download the latest wireless driver to the person who couldn't establish an network  connection of any type. :rolleyes:

---

### Post by jessesimp on 2013-05-08
hey guys I was just hoping for a little advice from some people that probably know a lot more than me about this stuff. I've never bought a printer and I'm not entirely sure what I'm looking for, but I know I want a good all-in-one printer and I don't want to spend a million bucks, just like anybody right? I found this site [http://www.squidoo.com/best-all-in-one-printers2](http://www.squidoo.com/best-all-in-one-printers2) and I'm leaning towards the Epson Expression Home XP-400 Inkjet Printer, I've read a lot of reviews but I was hoping to get some instant feedback from you guys about Epson or that exact printer and let me know what you guys think before I make the purchase? Thanks a lot!

---

