---
title: "Canon i450 Driver"
date: 2005-04-30
forum: Hardware &amp; Laptops
---

### Post by Runewalsh3 on 2005-04-30
Hey, I was wondering if anyone knew of any drivers that are compatable with the Canon i450 bubblejet printer. I have checked on LinuxPrinting.org, but the i450 is not listed. I remember using a different canon driver when I used Mandrake 10.0, but I dont know which one.

---

### Post by sethmahoney on 2005-05-02
I'd be interested in the answer, too.

---

### Post by Seth on 2005-05-02
[QUOTE=sethmahoney]I'd be interested in the answer, too.[/QUOTE]
 Try BJC-7000 (gimp-print) :)

---

### Post by Raven-sb on 2005-05-02
Well I'm not sure if the i450 driver already exists for linux, but if you can't find one you can always try Turbo Print.  [http://www.turboprint.de/english.html](http://www.turboprint.de/english.html) 

They do have a free version of their driver for the i450 which you may find suitible. Otherwise you can always buy the commercial version which has added features.

Personally I'm very impressed with Turbo Print's product, without it I wouldn't be able to print at all with my Canon i320.

Hope this helps,

Raven

---

### Post by Ozitraveller on 2005-05-02
[QUOTE=Runewalsh3]Hey, I was wondering if anyone knew of any drivers that are compatable with the Canon i450 bubblejet printer. I have checked on LinuxPrinting.org, but the i450 is not listed. I remember using a different canon driver when I used Mandrake 10.0, but I dont know which one.[/QUOTE]


Is this similar to Canon i550? I use Bjc-7100 or Bjc-80 if that's any help.

---

### Post by David Haas on 2005-05-03
I'm not familiar with Canons, but in looking at the PPD files in Gimp-Print (/usr/share/cups/model/gimp-print/4.2) I see listed this PPD file: bjc-s450.ppd.gz. Might this work if you selected it in the Printer GUI setup? 
David

---

### Post by sethmahoney on 2005-05-26
[QUOTE=Ozitraveller]Is this similar to Canon i550? I use Bjc-7100 or Bjc-80 if that's any help.[/QUOTE]

The Bjc-7100 does work for the Canon i450!  Yay!

---

### Post by Ozitraveller on 2005-05-26
Excellent!

---

### Post by YaAqoB on 2005-05-26
What about the i320? I tried the turbo print thing but I had their logo printed on my pages all the time so I gave it away.

---

### Post by sethmahoney on 2005-05-26
[QUOTE=YaAqoB]What about the i320? I tried the turbo print thing but I had their logo printed on my pages all the time so I gave it away.[/QUOTE]

Have you tried the 7100 driver?

---

### Post by YaAqoB on 2005-05-27
I tried it just now and it don't work :( Thanks though.
When i say print, the light on the printer starts flashing but nothing else happens.
Anyone got any other ideas?

---

### Post by Jenda on 2005-05-27
The BJC-7100, BJC-80 don't work on my i455... any ideas?

---

### Post by Ozitraveller on 2005-05-27
I've checked out the forums, and found many users of Canon iXXX printer are finding success with the 7000 drivers.

---

### Post by Jenda on 2005-05-28
[QUOTE=Ozitraveller]I've checked out the forums, and found many users of Canon iXXX printer are finding success with the 7000 drivers.[/QUOTE]
 No luck there yet. Anyone any ideas? Please?

---

### Post by Acesomeone on 2005-05-31
Does anyone know a driver for my Canon i905D??? Turbo Print has this dreadful advert on every page :(

---

### Post by Acesomeone on 2005-05-31
Seemingly the 'BJC 7000' (note the SPACE, not DASH) works fine for i905D

---

### Post by Seti on 2005-05-31
If you installed Turboprint be advised that it is NOT free software, it is only a demo and you need to purchase a license to use it withought the adverts being printed over your document. So if you really need to get your canon ixxx running and can't  get the linux driver to work, I think they charge about $35. 
My personal experience is that these printers kinda suck, and to have to shell out the extra money for Turboprint ( which I have) is almost not worth it. Probably better to save up and just get a better printer that is supported by the open-source drivers.

---

### Post by Acesomeone on 2006-06-17
[QUOTE=Seti]My personal experience is that these printers kinda suck, and to have to shell out the extra money for Turboprint ( which I have) is almost not worth it. Probably better to save up and just get a better printer that is supported by the open-source drivers.[/QUOTE]
I wouldn't say my i905D printer sucks, on the contrary, I've always liked it, just want to it to work under Linux. Question was whether anyone had an opensource driver working for this particular printer (i905D).

Thanks,
Ace

---

### Post by taykpk on 2006-08-05
> **Jenda said:**
> No luck there yet. Anyone any ideas? Please?

A little late, but with my i455 I'm using the BJC 7100, although it prints HUGE.

---

### Post by Jenda on 2006-08-05
Thanks, taykpk - it is indeed a little too late :)
It was for a Canadian friend, but I'm no longer in Canada. I will, however keep it in mind for future reference.

---

### Post by moospeed on 2006-08-13
Busy converting from WXP SP2 to Dapper Drake. I also have a Canon i450 and have used the BJC-7100 driver (as recommended at top of this thread).

It prints the basics but the quality is pretty poor, it also lacks any of the proper head alignment and maintenance features of the Windows driver. The Win driver has a pretty good setup in terms of functionality, page preview, etc.

As I'm new to linux would it be worth waiting for a driver to be written or is that unlikely to happen ? (won't be deleting that xp partition just yet ;)  );)

---

### Post by Platinum89 on 2007-02-20
> **moospeed said:**
> Busy converting from WXP SP2 to Dapper Drake. I also have a Canon i450 and have used the BJC-7100 driver (as recommended at top of this thread).

It prints the basics but the quality is pretty poor, it also lacks any of the proper head alignment and maintenance features of the Windows driver. The Win driver has a pretty good setup in terms of functionality, page preview, etc.

As I'm new to linux would it be worth waiting for a driver to be written or is that unlikely to happen ? (won't be deleting that xp partition just yet ;)  );)

I kept my Win98SE as a dual boot for several purposes and the maintenance program for the Canon i450 was one reason. I know the older models work rather well (such as the BJC2000 series) as I set up Ubuntu and his two Canon printers for him. His other one is an older BJC series. In the printer properties, there are settings that may help with the print quality, but I haven't had time to check them out yet.

---

### Post by sethmahoney on 2007-03-29
I just had to do a fresh Edgy 6.10 install and my i450 is no longer working correctly.  The bjc800 driver prints the whole page, but tiny, in the upper left hand corner, and the gutenprint driver prints the page in the correct size, but it is very light.  Any suggestions?

The [OpenPrinting database]("http://openprinting.org/show_printer.cgi?recnum=Canon-i450") says to use the bjc800 driver, but that "You have to adjust the resolution values in the ppd to the correct values: 150x150, 300x300, 600x600 and 1200x1200."  It doesn't look like I can do that in the GNOME configuration utility - any ideas what that might mean (and if it might work)?

---

### Post by junjan on 2007-05-07
Canon i450
I have been trying several combinations, and selecting the BJC-7000 model with the Gutenprint CUPS driver (expert) and tweaking a bit the color controls gives a quite good result.
;)

---

