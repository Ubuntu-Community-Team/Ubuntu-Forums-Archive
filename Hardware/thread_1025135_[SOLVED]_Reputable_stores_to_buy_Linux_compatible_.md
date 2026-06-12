---
title: "[SOLVED] Reputable stores to buy Linux compatible hardware"
date: 2008-12-29
forum: Hardware
---

### Post by akelsall on 2008-12-29
My Canon MP600 has reached end-of-life (btw, never buy one of these, or anything similar. If the cartridge sensor goes out, or if one cartridge runs out of ink. you **CAN NOT PRINT ANY MORE** until you've fixed the problem!!!!).

So, I'm in the market for a Linux compatible printer, and came across the Open Printer Database site ([http://www.openprinting.org/printer_list.cgi](http://www.openprinting.org/printer_list.cgi)), which seems to be a good resource for locating a Linux compatible printer.  

The problem is, I typically buy from Newegg.com, but they don't carry ANY Linux compatible printers. Can anyone recommend a company (preferrably online) that carries a Linux compatible printer? A company you've personally used several times without any problems.

Thanks,

Andy

---

### Post by 2hot6ft2 on 2008-12-29
My HP 3915 works fine and I suspect most HP printers work as well and they are available everywhere.

---

### Post by melojo on 2008-12-29
I have always had good luck with hp printers, they just seem to work.

I have an all in one hp j5780.

---

### Post by SuperSonic4 on 2008-12-29
Another vote for HP here. I got a C4580 all in one and it works perfectly, the installer was a cinch too

---

### Post by Hugh Mulqueen on 2008-12-29
I have a HP printer and it works like a charm. HP printers are offically supported by HP. 
[http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

---

### Post by ranch hand on 2008-12-29
You can check with HP to make sure the model you are thinking of getting is supported.  Most are.

---

### Post by akelsall on 2008-12-29
Supersonic4, thanks for the info. Got a few questions about it if you don't mind. 

From the images on Newegg.com, it looks like there are only 2 big cartridges. Is that right? Also, do the cartridges have sensors attached to them (to detect the ink level?). I've had issues with my old Canon (as I mentioned) and don't want another headache. It looks nice and compact for an all-in-one printer. 

Did you have to download the HPLIP software to get this printer working?

Some people on Amazon mentioned problems with the printer going into sleep mode and having to unplug it and plug it back in to get it to "wake up". Have you had this problem?

thanks,

Andy

---

### Post by mobilediesel on 2008-12-29
I bought a HP Deskjet D2460 from Newegg. It works great! I had a Lexmark before ditching Windows. I emailed Lexmark support and they said they had no interest in supporting Linux.

---

### Post by oldsoundguy on 2008-12-29
another vote for HP (I do have an Epson R1800 that also works great with the exception of color management .. close in cups, but no cigar, so my photo work gets done on a Windows box and then printed to that printer.)

---

### Post by stefanst on 2008-12-29
Go for Brother!

I got mine from Bestbuy.
Brother actually makes their own Linux drivers. So not only my printer, but also the integrated scanner/fax work!

Since they are the only company I know of who actively participate in development of Linux drivers I'd say support them!

ST

---

### Post by SuperSonic4 on 2008-12-29
> **akelsall said:**
> Supersonic4, thanks for the info. Got a few questions about it if you don't mind. 

From the images on Newegg.com, it looks like there are only 2 big cartridges. Is that right? Also, do the cartridges have sensors attached to them (to detect the ink level?). 

I've had issues with my old Canon (as I mentioned) and don't want another headache. It looks nice and compact for an all-in-one printer. 

Did you have to download the HPLIP software to get this printer working?

Some people on Amazon mentioned problems with the printer going into sleep mode and having to unplug it and plug it back in to get it to "wake up". Have you had this problem?

thanks,

Andy

Yeah, one black and one colour. There does not seem to be an option to check ink levels so I doubt it. I've checked scanning, copying and printing and all work wirelessly although you need the cable to set up wireless. 

Yeah, I did have to download the driver but it is most like an .exe file, drag and drop into terminal **as user** and follow the instructions. If you download version 2.8.12 like I did and saved it in ~/Desktop 
```
cd ~/Destkop
chmod +x hplip-2.8.12.run
./hplip-2.8.12.run
```

I've never really had the conditions to test it with waking up for I only ever turn it on when I need it and I rarely need it for more than five minutes at a time

---

### Post by jrusso2 on 2008-12-29
> **mobilediesel said:**
> I bought a HP Deskjet D2460 from Newegg. It works great! I had a Lexmark before ditching Windows. I emailed Lexmark support and they said they had no interest in supporting Linux.

Great let them know most Linux users have no interest in buying any Lexmark hardware.

Support HP as not only do their printers work with Linux they have contributed money towards Linux development.

---

### Post by dasunst3r on 2008-12-30
Unfortunately, there isn't a store that specifically sells Linux-compatible hardware and therefore you'll have to do your own research.  Narrowing down to printers, I think HP has gone downhill in terms of quality -- anything that costs less than $ 150 will not be a worthwhile investment.  Brother is the choice of printers in my circle of people as they work very well in Linux.

---

### Post by akelsall on 2008-12-30
Thanks for all the feedback. After looking at reviews on Newegg.com and Amazon.com, I was going to go with the C4580. However, I got a look at both the C4580 and C5580 at Best Buy today and thought the key layout and overall look and feel of the C5580 was beter (and it was just $10 more on sale). BUT, I just found this same printer on Newegg for $99 (including shipping!), so just waiting for it to arrive now.

I'll post again once I've set it up to let everyone know how it works. Now, I just need to figure out how to set up printer sharing so my wife can printer from her XP computer :(

Andy

---

### Post by oldsoundguy on 2008-12-30
print sharing is usually very easy.  Hook up the printer to the box, run cups to install (the printer program under system> administration> printing) and make the printer available to the network.  IF both of your computers are already networked .. just re boot.
have her  add the printer as remote and add the URI of the printer as the address of same.  Re-boot and that's it.

---

### Post by akelsall on 2009-01-09
Well, I got my HP Photosmart C5580 and, using HP's hplip software, I got it up and running with NO problems. It's noisier than the Canon I had, but I won't be printing that much, so no big deal.

Still having an issue sharing the printer with an XP box (CUPS isn't the end all for everything unfortunately). I will post a separate thread for help on printer sharing.

Concerning the HP C5580, it has a nice interface and plenty of keys on the front to make printing easy. I tried using the scanner (via SANE) it works perfectly as well. No downside to this printer. Would highly recommend (unless you'd be printing alot. In that case, you may want to look for a quieter printer).

Support HP!!

Andy

---

