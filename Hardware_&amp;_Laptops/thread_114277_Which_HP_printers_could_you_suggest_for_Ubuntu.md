---
title: "Which HP printers could you suggest for Ubuntu?"
date: 2006-01-08
forum: Hardware &amp; Laptops
---

### Post by André on 2006-01-08
Hi everybody,

when i start Ubuntu i see that there are some HP drivers are loaded. So i guess that these printers should work well in Ubuntu.

I would like to know if you could suggest a nice HP printer with the following stats:

- Possibility to print at least at 720 dpi
- Good printout quality
- Works out of the box (or can be easily installed)
- is good at coloured printout
- is not too expensive (at most 200€ - 300€ would be nice)

I know the hardware compatibility list but i do not trust it too much because there is not enough information. For example: Right now i have a Canon S450. On the list it says everything alright. As long as you just print text that is true but when you printout a graphic the colours ain't right and the result looks terrible!

That is why i wanted to ask for your own experience about printers that fit my stats :-)

Greetings and thanks in advance
André

---

### Post by Titus A Duxass on 2006-01-08
Hi,
I've just bought a HP PSC 1610 All-in-One for just over 100€ from Mediamarkt in Germany.

Works a treat, straightfoward configuration.  All the drivers were ready and waiting.

Titus

---

### Post by Sef on 2006-01-08
Andre:  What exactly are you looking for in terms of capability for your printer?

1) Just to print text

2) print text and photos

3) print text, photos, and scan

4) Other

The PSC 1610 is a good printer.  I had to download some software through apt-get and Synaptic to get the printer and scanner to work.  It was easy; there is a thread of it that I used to get mine working.

---

### Post by André on 2006-01-08
Hi,

that's sounds pretty promising. I just want a printer, scanner is not necessary (but won't hurt me ;-)). The printer should be able to print text and sometimes photos (but at least some graphics which are embedded in the text).

Sometimes i have to hand in some stuff for university which also includes graphics and i want it to look good like when i print in Windows.

Greetings and thanks for your post
André

---

### Post by mips on 2006-01-08
The HP 6213 all-in-one works great outa the box and should be under 300euros

---

### Post by Lord Illidan on 2006-01-08
My HP psc 1110 is very cheap and works like a charm under Ubuntu and Windows..
Scanner also works.

---

### Post by André on 2006-01-08
Hi guys,

thanks for the replies. Sounds really promising :-)

Greetings
André

P.S.: How expensive are the cartdridges for these printers?

---

### Post by hentaidan on 2006-01-08
They can be very expensive, mine (for a PSC1210) cost around £20 (tri-colour and black), but can be up to £30 depending where you get them.

---

### Post by André on 2006-01-09
Are there third party cartridges which are not that expensive?

---

### Post by iraklirost on 2006-01-09
HI to all, I need to install Laserjet 1000, could anyone halp me how to do it?

I am doing in this way: 
1. I had already installed from "Synaptic Package Manager": cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data.

2. "computer > system configuration > printing
add printer>hp>select the Laserjet 1000 (it's listed)>then click "install driver" ( HP-Laserjet_1000-foo2zjs.ppd.gz from usr/share/cups/model/foomatic-ppds

but from my ubuntu OS I can not print still on HP 1000! .. (:

---

### Post by kaamos on 2006-01-09
Have you installed the hpoj, hplip and/or hpijs packages?

---

### Post by iraklirost on 2006-01-09
I install only HP-Laserjet_1000-foo2zjs.ppd.gz driver

---

### Post by hentaidan on 2006-01-10
[QUOTE=André]Are there third party cartridges which are not that expensive?[/QUOTE]

Yeah, you can get cheaper ones (seen some for £5 - £10), or you can also refill which works out quite cheap (some computer shops do it for a small fee).

Whether you trust the cheaper cartridges or not is up to you though, I personally tend to avoid them just in case.

---

### Post by André on 2006-01-10
Hi everybody,

when i print in Windows i see some additional information and tools like how much ink is left in my cartridges and the option to clean the printers header.

Is something like this possible in Linux with your HP printers? Or can you manually clean the headers at the printer (like pressing a button combination or something)?

Thanks for all you answers so far. Sounds like there is a way to print nice in Linux :-)

Greetings
Andr&#233;

P.S.: @Hentaidan: The PSC 1210 sounds nice. Can you scan and copy without problems in Linux? (Okay, copying may not depend on the OS but what about scanning?)

---

### Post by srt4play on 2006-01-10
I'll throw in another vote for the psc 1610.  I got one for Christmas and I absolutely love it.  Everything worked out of the box, and for ink level monitoring and other nifty tools , install the package "hplip" in synaptic which puts a nice gui program in system --> preferences --> hplip toolbox.

---

### Post by André on 2006-01-10
Cool,

another nice one which is not too expensive. Think i have to buy a new printer soon ;-)

Greetings
Andr&#233;

P.S.: srt4play: How is coloured printing in Linux with the 1610? Which dpis can you get with it?

I saw that it only has the colour cartridges all together. Does this not make you throw away cartridges if only one colour is gone?

---

### Post by hentaidan on 2006-01-10
[QUOTE=André]P.S.: @Hentaidan: The PSC 1210 sounds nice. Can you scan and copy without problems in Linux? (Okay, copying may not depend on the OS but what about scanning?)[/QUOTE]

Well, almost. Scanning works fine, copying works fine as well, but I seem to be having problems printing in pure black; it seems to be using the colour cartridge for some reason. Think I might have broken it though, it always used to work fine. I havn't had the time lately to find out why.

I've got a feeling the PSC1210 has been superceded though. By the 1310?

---

### Post by srt4play on 2006-01-10
[QUOTE=André]Cool,

another nice one which is not too expensive. Think i have to buy a new printer soon ;-)

Greetings
André

P.S.: srt4play: How is coloured printing in Linux with the 1610? Which dpis can you get with it?

I saw that it only has the colour cartridges all together. Does this not make you throw away cartridges if only one colour is gone?[/QUOTE]

It is excellent in both black and color printing.  I've never had any concern about dpi at all, never crossed my mind because I just do basic printing.  But taking a look at the printer settings in system --> administration --> printing, I see multiple DPI options for 300, 600, and 1200.

About the color cartridge, yeah I guess you'd have to replace the whole thing even if just one color is out... but I've done a good amount of color printing and the color ink levels have all gone down in the same amount.

Hope this helps

---

### Post by André on 2006-01-10
@srt4play:

Does scanning work well for you? If this works well and without problems the 1610 might the first choice so far :-)

Greetings and thanks to anyone
Andr&#233;

---

### Post by srt4play on 2006-01-11
Yes everything works really well including scanning.  The memory card slot on the front of it works good too.

---

### Post by André on 2006-01-11
Okay, we have a choice here ;-)

Will get a 1610 ASAP. Thanks for all you answers srt4play (and sure thanks to you other guys too!). I hope i did not get disturbing... but it is so hard to beleive that everything works so fine :-)

I will get this one and think my money is well spend.

Thanks again
André

---

### Post by gosh on 2006-01-11
Just my 2 cents

I use a Ofiicejet 6110 All-in-One without any problem.

---

### Post by André on 2006-01-11
Hi gosh,

thanks for your reply. I think that the 6110 may be a bit too expensive for me right now.

Does it have any benefits above 1610? What's the difference?

Greetings
André

---

### Post by gosh on 2006-01-12
I don't know what the actually differences are, but I have my 6110 for over two years now and it works without any problems.

A quick glance at hp's website tells me that the 6110 has a fax (who uses one nowadays?) and a sheetfeeder (which comes in handy when I have to copy a bundle of papers). The 1660 has an interface for your photo memory cards (I connect my camera directly to my pc).

As fas as prices are concerned, I don't know what the difference is but you might google around for that.

---

### Post by lex on 2006-01-13
Hi, I have a HP Photosmart 2610 all in one, it prints fine and was easy to install with Foomatic-GUI printer configuration tool, from Add Applications.
Could anyone please tell me how to use the scanner? I'm a newbie so please make it easy, if possible. Or advise me of a good thread.
Thanks
Lex

---

### Post by André on 2006-02-02
Hihi,

so here comes my vote. The 1610 works really well. I just got mine yesterday and everything works out of the box!

Thanks to anyone for the tips
André

---

### Post by DrBair on 2006-02-02
I have an HP 1315, same as the 1310 but with pictbridge which I am yet to use.  I got the printer pretty cheap at staples a while back and I'm still on the original cartridges, which is great because the cartridges for HPs are expensive!  

Scanning and printing both worked out of the box without any hassles.  The only thing that sucks is that if you try to print when the printer is off you then have to go into the printer control section in KDE and start the printer up again.  

On a side note this will probably be the last printer I buy.  I've had and seen far too many issues with printers dieing only after one year with normal use.  Not to mention the highway robbery with the print cartridges, it costs more for new cartridges that it does for a new printer in some cases anymore.  

So seeing that I *maybe* print two hundred pages a year and I can print PDFs for about 10cents a page down at the local copy shop, the printer deal just isn't working out for me.

---

### Post by Jeffery Mewtamer on 2006-02-03
[http://hpinkjet.sourceforge.net/install.php#HPLIP](http://hpinkjet.sourceforge.net/install.php#HPLIP)

Thats the guide I used to install my PSC 1610 printer, and it seems to be valid for a large number of HP printers. Also I think that it being linked from the HP website says something for it's reliablity.

P.S. Fellow PSC 1610 owners: How do I access the scanning software?

---

### Post by tim15856 on 2006-02-03
[QUOTE=iraklirost]HI to all, I need to install Laserjet 1000, could anyone halp me how to do it?

I am doing in this way: 
1. I had already installed from "Synaptic Package Manager": cupsys, cupsys-bsd, cupsys-client, cupsys-driver-gimprint, and cupsys-driver-gimprint-data.

2. "computer > system configuration > printing
add printer>hp>select the Laserjet 1000 (it's listed)>then click "install driver" ( HP-Laserjet_1000-foo2zjs.ppd.gz from usr/share/cups/model/foomatic-ppds

but from my ubuntu OS I can not print still on HP 1000! .. (:[/QUOTE]

The LJ 1000 seems to be a strange printer. See if this helps [http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000](http://www.linuxprinting.org/show_printer.cgi?recnum=HP-LaserJet_1000)

---

### Post by Joey French on 2006-02-17
I have had nothing but good luck with my hp deskjet 5650 printer under ubuntu. Installed and works perfectly, no fuss, no problem. And, it looks good with my box...

:D 

Joey French

---

