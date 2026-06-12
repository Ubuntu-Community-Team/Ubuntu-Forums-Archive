---
title: "What is a good network connecting printer for Ubuntu (Studio)"
date: 2017-07-27
forum: Hardware
---

### Post by jukingeo on 2017-07-27
Hello,

After tossing my piece of crap Hewlett Packard printer out the window last night...(no, not kidding, I actually did throw it out the window.  It also wasn't the first HP printer that went out the window, but it is the last as I am not buying HP any more), I am in the market for a new printer.

I would like to know what is a GOOD scanner / printer combo that is known to work on a network connection With Ubuntu (Studio), 16.04. WITH AS LITTLE HOOP JUMPING as possible.  I definitely want to get a laser printer...preferably color.   Budget is about $400.   (Yes, I want a good one this time).  Since I have more than one computer hooked up via an internet connection, I also want the printer to communicate with Ubuntu on a network level, not USB.   I also want the scanner to work via Ubuntu.

On another system I managed to get a Brother printer to work with Ubuntu Studio 14.04 over a network...however, the scanner would not work over the network...only via the USB connection.   So naturally I couldn't use the scanner over the network.

My office at work uses Brother and I am taking that this is a good brand as the printer is heavily used and hasn't failed.  That being said, I found this model:

HL-3180CDW

[http://www.brother-usa.com/Printer/ModelDetail/1/HL3180CDW/Overview?gclid=EAIaIQobChMIj6jS5sWq1QIV2D2BCh14pwl5EAAYASAAEgJ-8_D_BwE&ef_id=WPa3jQAAAc2AZ9jt:20170727224842:s](http://www.brother-usa.com/Printer/ModelDetail/1/HL3180CDW/Overview?gclid=EAIaIQobChMIj6jS5sWq1QIV2D2BCh14pwl5EAAYASAAEgJ-8_D_BwE&ef_id=WPa3jQAAAc2AZ9jt:20170727224842:s)

It is a color laser and it looks good and has wireless networking capability.   Has anyone had luck connecting this to Ubuntu 16.04 via a network connection?
[B]
EDIT:[/B]  I have since discovered the HL-3180CDW doesn't work over a wired eithernet connection as it is only meant for wifi.  So I have since moved on to the 

**MFC-9340CDW**, which is an all-in-one printer that has fax capabilities in addtion to scanning and printing.  I do not need that function, but the printer is the same price.  So why not?  I just need to know if this one will work with Linux.

Thank you!

---

### Post by bcschmerker on 2017-07-27
As far as I am aware, the only model line that WILL handle ubuntu® studio&#8480; properly over a network, on the first try, is the XEROX® Phaser® series, which not only is 10/100Base-TX and 1000Base-T4 native but also has Adobe® PostScript® v3.0 in the firmware from the outset.  The Phasers, originally developed by Tektronix for professional print shops that need near-absolute color accuracy and archival-level ink endurance, are all rather costly and therefore most often encountered at the enterprise level.  I've been using an Epson® WF-series all-in-one (good endurance at a modest price point), but the WF's, WP's, XP's, and ET's all require closed-source drivers from DownloadBZ.Epson.com.

As for the Brother® HL-3180CDW, I cannot recommend it - no direct Ethernet connection, only a USB 2.0 direct interface and 802.11b/g/n wireless.  Suspect that it, too, requires closed-source drivers.

---

### Post by vocx on 2017-07-28
> **jukingeo said:**
> Hello,

**After tossing my piece of crap Hewlett Packard printer out the window last night**...(no, not kidding, I actually did throw it out the window.  It also wasn't the first HP printer that went out the window, but it is the last as I am not buying HP any more), I am in the market for a new printer.

**I would like to know what is a GOOD scanner / printer combo that is known to work on a network connection With Ubuntu (Studio), 16.04. WITH AS LITTLE HOOP JUMPING as possible.  I definitely want to get a laser printer...preferably color.**   Budget is about $400.   (Yes, I want a good one this time).  Since I have more than one computer hooked up via an internet connection, I also want the printer to communicate with Ubuntu on a network level, not USB.   I also want the scanner to work via Ubuntu.

Ha! The only option I can really recommend is... an HP printer. HP just works! HP uses the HPLIP library to support their own brand. It's included in Ubuntu. Easy to install, and easy to use. Visit their website to check that the printer you want to buy works 100%.
[http://hplipopensource.com/hplip-web/recommended.html](http://hplipopensource.com/hplip-web/recommended.html)

Do not buy inkjet, buy laser. Maybe your last printer was an inkjet, and that's why it didn't work. Sad.

I currently have the HP LaserJet Pro MFP m127fn (USB+Ethernet). I can print and scan, remotely, with Windows and Ubuntu computers. No problems. My Ubuntu machine finds the printer by name, so it doesn't matter if the IP address changes, it will be found. The printer runs a web server, so there are some options you can look at when you type its IP address in your browser. You can also buy the HP LaserJet Pro MFP m127fw (USB+Ethernet+Wifi).

This HP printer also has a service that allows you to print over the Internet. That's right. You are at work, you send your file to the printer, and by the time you are home your document is there already printed. It's silly. Obviously you need to create an account with HP or whatever. Meh. I don't need that service, but some people may find it useful.

See here [https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post1365838](https://ubuntuforums.org/showthread.php?t=2364149&p=13658387#post1365838)
And here [https://ubuntuforums.org/showthread.php?t=2366999&p=13669363#post13669363](https://ubuntuforums.org/showthread.php?t=2366999&p=13669363#post13669363)

> 
On another system I managed to get a Brother printer to work with Ubuntu Studio 14.04 over a network...however, the scanner would not work over the network...only via the USB connection.   So naturally I couldn't use the scanner over the network.

My office at work uses Brother and I am taking that this is a good brand as the printer is heavily used and hasn't failed.  That being said, I found this model:

**HL-3180CDW**

[http://www.brother-usa.com/Printer/ModelDetail/1/HL3180CDW/Overview?gclid=EAIaIQobChMIj6jS5sWq1QIV2D2BCh14pwl5EAAYASAAEgJ-8_D_BwE&ef_id=WPa3jQAAAc2AZ9jt:20170727224842:s](http://www.brother-usa.com/Printer/ModelDetail/1/HL3180CDW/Overview?gclid=EAIaIQobChMIj6jS5sWq1QIV2D2BCh14pwl5EAAYASAAEgJ-8_D_BwE&ef_id=WPa3jQAAAc2AZ9jt:20170727224842:s)

It is a color laser and it looks good and has wireless networking capability.   Has anyone had luck connecting this to Ubuntu 16.04 via a network connection?

Thank you!

> **bcschmerker said:**
> ...
As for the Brother® **HL-3180CDW**, I cannot recommend it - no direct Ethernet connection, only a USB 2.0 direct interface and 802.11b/g/n wireless.  Suspect that it, too, requires closed-source drivers.

I haven't used a Brother laser since the days of parallel port. Yuck.
Nevertheless, nowadays I read good opinions on many Brother printers. They seem to be highly regarded for their durability in office environments. I don't know if they need proprietary drivers, but they seem to work just fine.
See here [https://ubuntuforums.org/showthread.php?t=2367154&p=13669999#post13669999](https://ubuntuforums.org/showthread.php?t=2367154&p=13669999#post13669999) (HL-3150 CDW)

---

### Post by efflandt on 2017-07-28
Any printer that supports postscript printing language should work well for printing. When my old HP4L indicated a paper jam when I could not find one, I got a Lexmark C543dn (54x series have since been discontinued) duplex (double sided) network color laser printer. It supports both HP PCL and postscript (Ubuntu uses postscript for it). Even before it was supported by Ubuntu it worked fine with an older C534 driver. It is just that default colors were a little too bold for my taste (maybe good for a brochure). So I found a reference image with lots of colors, adjusted defaults on the printer itself until it printed photo realistic that matched my screen. Those color settings on the printer itself also worked perfectly when we got the same printer for our small office at work. I would not even consider an ink jet printer because I do not print that often at home and ink jets would tend to dry up. With laser toner that is not an issue.

I also have a Lexmark X204n b&w all-in-one laser that I bought for $150 when our business HP business printer crapped out at work until we could replace the HP printer. Since it also does HP PCL (and postscript), I simply set it to the IP address that the HP printer had and it simply worked with Windows HP drivers and remotely from HP 3000 computer at our factory 1700 miles away (via VPN to our office) for printing orders, invoice copies, etc.

But scanning might be another issue. Not sure if newer Lexmark X series (all-in-one) have newer Linux scanner drivers. The Lexmark Linux (sane) network scanner driver for the X204n 32-bit version works in 32-bit 16.04 (which I only have in virtualbox) and 64-bit version works in an actual 14.04 system or virtualbox, but the 64-bit driver does not work in 64-bit 16.04 or 16.10, maybe due to the change in start up scripts. So for now if I want to scan, I need to use virtualbox with an Ubuntu version that works for it.

---

### Post by Autodave on 2017-07-28
Have to agree with vocx: I have never had a problem getting any HP printer to work with Ubuntu: going all the way back to 10.04.

---

### Post by kurt18947 on 2017-07-29
I've been shopping for a color laser printer and have pretty much settled on a Brother HL-3170CDW due to reasonable 3rd party consumable costs. I've used Brother's installer script and had good luck with it. Staples has a Canon laser on sale and Canon has linux drivers available. A set of toners would cost nearly as much as the printer though and so far limited 3rd party supply availability. Epson Eco Tank printers are interesting from a cost/page standpoint but a pretty high initial cost and I've had a couple inkjet printheads fail.

---

### Post by bcschmerker on 2017-07-30
[@vocx](https://ubuntuforums.org/member.php?u=2054517)  **Speaking of laser printers, I've a contingency for a four-toner multifunction** and anticipate an 8.5" x 14" maximum size for both originals (copy, scan or facsimile) and printouts, with 10/100/1000Base-T4 a requirement to hook up to a NETGEAR® WNDR4500 (or, should it break, a Linksys® WRT-3200AC).  I had to rule the XEROX® Phasers® out of further consideration on cost, but ultimate color accuracy is not one of my requirements.  500 sheets 28*max*# bond should be plenty of raw stock capacity in one feed tray.  Since Hewlett-Packard® does support Adobe® PostScript® v3.0 natively on select Color LaserJet® models, what model numbers should I put on the contingency shortlist?  (The current Epson® WF-3520 AiO inkjet fails the legal-size requirement but otherwise fills the role for now.)

---

### Post by jukingeo on 2017-08-05
Hello All,

Thank you for your responses.  So far it does seem like the Xerox Phasers are the top contenders here, but I have used these before and while they are beautiful, they are NOT cost effective.  VERY expensive machines.   I don't really need a printer on a production level like that.

As for HP, I know the old 1200 and 1300 printers were rock solid.  I LOVED them.  Odd looking, but solid workhorses.   Everything after those models...especially the all in ones, proved to be a disaster for me.   Granted, that is mostly the ink jet printers.  I went through three of them and I am done with HP.

Lexmark...OK, another one I am on the fence about.  While I am sure they have correct the  problem by now, I have heard these printers would just overheat and catch fire.  My father had a an ink jet Lexmark and the ink would always dry up on him very fast.

So far it seems like Canon and Brother on the top of my list.  I have a Brother on a second computer I have and I know these are rock solid.   But I have others mention they like Canon too.  

kurt18947  So you got a Brother Brother HL-3170CDW?

I will look into that one especially since it supports 3rd party toners.  That was a big problem I had with the HP ink.  They would give you so little ink and charge you out the wazoo for it.  Where as while the 3rd party stuff was reasonable, after a few pages of printing, the printer would complain that it is not the right cartridge.

I have heard of the new Epson Ecotank system they have, but as with Lexmark, I am not too familiar with them and don't see many people having them.  It does seem by and large I have mostly come across those that use HP, Xerox, Brother, and Canon (in terms of laser printers).   BUT most are using them on a Windows system, so naturally that is easier to set up.  But with me, I am mostly using Ubuntu nowadays and I want a printer that is networkable.

Vocx, that HP does sound promising even though HP has left a foul taste in my mouth.  However, that model monochrome and I am looking to see what I can get in a color laser before resorting to monochrome.

Thank you all again for you input.

Geo

---

### Post by vocx on 2017-08-06
> **jukingeo said:**
> Hello All,
...

... **Granted, that is mostly the ink jet printers.  I went through three of them and I am done with HP.**

... **My father had a an ink jet Lexmark and the ink would always dry up on him very fast.**

...**That was a big problem I had with the HP ink.  They would give you so little ink and charge you out the wazoo for it.**  Where as while the 3rd party stuff was reasonable, after a few pages of printing, the printer would complain that it is not the right cartridge.

...
Vocx, that HP does sound promising even though HP has left a foul taste in my mouth.  However, that model monochrome and I am looking **to see what I can get in a color laser **before resorting to monochrome.

Thank you all again for you input.

Geo
Why do you hate yourself? Why do you keep using inkjet printers? Why do you punish yourself buying inkjet printers? Do you like to suffer? Because buying inkjet printers is how you can get guaranteed suffering. Do you like the pain? Why, oh why?

I'm being unnecessarily dramatic, of course. But really, in all my years in school and office work, I never felt that I needed a color a printer. Everything that can be printed in these environments can reasonably be printed with a monochrome laser. You should limit your use of color.

Inkjet color printers are made for waste. They are one of the most wasteful products we use as a society. They are extremely cheap. "Did you buy a USB 100 hard drive? We will just give you this Epson (Canon, HP, Samsung) inkjet printer for free!" Inkjet printers are given away all the time because the manufacturers don't make money out of them anyway; it's the constant production and selling of ink cartridges that creates some nice revenue streams.

Getting a color laser would be a nice investment. I'd buy one if I really needed it. It's nice when the office has it. But again, I myself limit the number of colors I use to two, black and white, and gray (that's three).

---

### Post by SeijiSensei on 2017-08-06
I have an HL-3170CDW and would endorse it except that it doesn't have a scanner.  I'm sure there are Brother models equivalent to this printer but with a scanner included as well.

As for drivers, either you can set the machine to Postscript mode, or you can use the drivers that come with CUPS.  I'm on 14.04 and used the 3070CDW driver since there wasn't one for the 3170.  In Postscript mode, the printer handles manually-fed envelopes correctly.  With the default language, it would not print them in the correct orientation.

Concerning one other issue above:  The 3170 definitely has an Ethernet port which is how it is connected to my network; the 3180 apparently does not, though you can connect it over wifi.  With the Brother app for Android I can print from my phone directly as well as from client workstations.

---

### Post by kurt18947 on 2017-08-06
> **jukingeo said:**
> Hello All,

[snip]

kurt18947  So you got a Brother Brother HL-3170CDW?
[snip]
Thank you all again for you input.

Geo

Not yet, I'll probably get it this week. It and I'll bet the MFC-3180CDW do come with wired ethernet, I checked the manual on Brother's site. I avoid wifi anything to the maximum extent possible. The most common complaint I see with the Brother HL-3170 is picture & graphics quality. One review said the output wasn't suitable in their opinion for client presentations. It'll be used mostly to print pictures off the web so studio quality photos are not likely to be required. The HL-3170CDW comes with 128 MB. RAM and that's all it will support so I wonder if that's part of the reason for less than photorealistic graphics. 

I'm going to buy the machine locally so I can return it if quality is not up to snuff. I haven't configured a machine to connect to a network when the machine does not have a keypad. My devices to date have been multi-functions with keypads due to the fax function. I prefer to assign static I.P. addresses to printers so there's no problem 'finding' them. Brother does offer a linux network configuration utility though I've never used it or needed it to date.

---

### Post by SeijiSensei on 2017-08-06
I'd agree about the print quality of the 3170.  I wouldn't use it to make glossy brochures or anything like that.  For those sorts of tasks I'd use a print shop or Staples.  I think it would be fine if you were producing handouts with graphs and the like.

You set the IP address in the window with the keys.  As I recall, it wasn't very hard to do. I think you just scroll up and down for each octet.

CUPS discovers this printer quite easily, especially if you add it from the browser interface at [http://localhost:631/](http://localhost:631/).

---

### Post by kurt18947 on 2017-08-06
> **SeijiSensei said:**
> I'd agree about the print quality of the 3170.  I wouldn't use it to make glossy brochures or anything like that.  For those sorts of tasks I'd use a print shop or Staples.  I think it would be fine if you were producing handouts with graphs and the like.

You set the IP address in the window with the keys.  As I recall, it wasn't very hard to do. I think you just scroll up and down for each octet.

CUPS discovers this printer quite easily, especially if you add it from the browser interface at [http://localhost:631/](http://localhost:631/).

How about cat pictures?:grin: Thanks much for your input. It's always good to hear from a user with no ulterior motives.

---

### Post by SeijiSensei on 2017-08-06
My cat looked just fine! :D

---

### Post by kurt18947 on 2017-08-19
I got the Brother HL-3170CDW from Walmart. Refurbed for $158.50. Set a static I.P address and plugged it into a router, ran the Brother installer and I'm in business. The only problem is that the toners which come installed but with plastic covers over the rollers included 2 black and no magenta. Oops. A magenta cartridge is on its way from Brother. Contrary to what I was told by Brother's customer service, the printer will print with the wrong color toner installed so monochrome printing works and cyan and yellow work though I doubt the colors are true. The printer info sheets show the machine has printed about 150 pages hence refurbished. I have no idea why it was returned of course but it seems to work and comes with a 1 year factory warranty. The price is about the same as a good quality duplexing inkjet and I expect a longer more trouble free life from a laser.

---

### Post by jukingeo on 2017-10-14
Hello guys!

Sorry I been away from this thread for quite a while, and no I have not got a color printer yet  (I do have a monochrome one at another location I am using in the meantime).


> **vocx said:**
> Why do you hate yourself? Why do you keep using inkjet printers? Why do you punish yourself buying inkjet printers? Do you like to suffer? Because buying inkjet printers is how you can get guaranteed suffering. Do you like the pain? Why, oh why?

I'm being unnecessarily dramatic, of course. But really, in all my years in school and office work, I never felt that I needed a color a printer. Everything that can be printed in these environments can reasonably be printed with a monochrome laser. You should limit your use of color.

The main reason why I used a color inkjet printer is because I could print out photo studio quality pictures and signs for my Halloween display. Using the special glossy photo paper (and I know you can't use this on a laser printer), I could NOT tell the difference between a printed photo and a studio photo.  So I was spoiled by not having to go to the photo place to have pictures made up and paying extra for that.  I mainly printed out pictures for my parents and my wife printed out some pictures for her family.  Mainly it was pictures of our kids, particularly our increasing 'Pictures With Santa' collection and our 'A day at the Amusement Park or Great Wolf Lodge' collection.  However, over the years things changed.  I lost my Dad earlier this year and my mom in 2015 and they were the ones that most requested pictures as both were not computer literate.  My brother-in-law and most people on my wife's side of the family are computer literate and can print out their own picture if I give them a file.   So my need to have studio quality photos has changed as I no longer need to print out studio quality photos regularly anymore.  For the once in a blue moon that I need that level of clarity, I can go to Staples for that.  I still do need color printing for the Halloween work I do, but I do not need a glossy studio quality photo for this.  But there are times when I print out diagrams and electronic instructions and still do need color.   But by and far, black / monochrome printing takes up the lion's share of my work.  The resolutions also have improved much over the years and I have seen some pretty nice pictures from laser printers lately.  Again, not photo studio quality, but pretty darn close.

> 
Inkjet color printers are made for waste. They are one of the most wasteful products we use as a society. They are extremely cheap. "Did you buy a USB 100 hard drive? We will just give you this Epson (Canon, HP, Samsung) inkjet printer for free!" Inkjet printers are given away all the time because the manufacturers don't make money out of them anyway; it's the constant production and selling of ink cartridges that creates some nice revenue streams.

Getting a color laser would be a nice investment. I'd buy one if I really needed it. It's nice when the office has it. But again, I myself limit the number of colors I use to two, black and white, and gray (that's three).

I am not going to argue with you there.  Because of the rarity of using color, I became weary of having to constantly replace color cartridges that have dried out.   HP ink is very expensive too and sadly the printers are very brand specific. I thought I could use after market or recycled cartridges, but I was in for a surprise that after a few uses, I got the tell tale error, "The cartridge in the right holder is not an HP cartridge."    Yes, I have tried the reset button on the cartridge trick and what have you.  Also another issue with ink jet printers is that one time a photo that a family member sent to me got wet and the ink ran, so I had to get a replacement photo.   I found out that the colors are NOT colorfast and ANY time a picture gets wet, it is completely ruined.  This is something that doesn't happen with laser printers.

Another thing is that I have a friend that has a Xerox and he also very rarely uses color, but when  he does, it is there for him.   He hadn't printed color in a year and when he went to print a color document for me, it printed flawlessly.  So the toner doesn't dry up.

So all in all, since my needs changed, now I felt it is time to finally go laser and leave ink jets behind forever.



> **SeijiSensei said:**
> I have an HL-3170CDW and would endorse it except that it doesn't have a scanner.  I'm sure there are Brother models equivalent to this printer but with a scanner included as well.

Yes, I do need a scanner.  I do currently have a monochrome Brother All in One machine, an MPC-7440n  printer on a second computer, and it can do network printing on Linux, but not scanning.  I have to have a USB cable hooked up to the machine so I can access scanning with it.   For me, I have come to live with this as I don't scan as much as I print.  But I do need a scanner and I don't want to buy a separate machine for that.  In addition, I do use the printer as a copier...so I need the scanner.

> As for drivers, either you can set the machine to Postscript mode, or you can use the drivers that come with CUPS.  I'm on 14.04 and used the 3070CDW driver since there wasn't one for the 3170.  In Postscript mode, the printer handles manually-fed envelopes correctly.  With the default language, it would not print them in the correct orientation.

I think there were some changes in 16.04 and I am not sure how it is done there.   But I used the Brother setup utility for the Brother printer on my other machine and that one is 14.04 (If I recall right.  I might have updated that one since I moved it).

> 
Concerning one other issue above:  The 3170 definitely has an Ethernet port which is how it is connected to my network; the 3180 apparently does not, though you can connect it over wifi.  With the Brother app for Android I can print from my phone directly as well as from client workstations.

I am fine either way.  The printer will be located hear a wifi capable hub, so it doesn't need to have built in Wi-fi.  As is I currently can use my tablet to print to the MPC-7440n which doesn't have built in wifi.  

> **kurt18947 said:**
> Not yet, I'll probably get it this week. It and I'll bet the MFC-3180CDW do come with wired ethernet, I checked the manual on Brother's site. I avoid wifi anything to the maximum extent possible. The most common complaint I see with the Brother HL-3170 is picture & graphics quality. One review said the output wasn't suitable in their opinion for client presentations. It'll be used mostly to print pictures off the web so studio quality photos are not likely to be required. The HL-3170CDW comes with 128 MB. RAM and that's all it will support so I wonder if that's part of the reason for less than photorealistic graphics. 

Yes, there is a resolution limit.  I think it is 2400 lines?  As long as the printer can do photos at that level, it should look near photo quality.  Most laser printers are below 1000 lines and naturally picture quality will suffer.  So if that is the case with the HL-3170, then I need a more capable printer.  The HL-3180CDW, (which is my current contender) DOES support the 2400 lines, but I am not sure about the ethernet port.  Hopefully someone could chime in on that, or perhaps I will contact Brother myself.

> I'm going to buy the machine locally so I can return it if quality is not up to snuff. I haven't configured a machine to connect to a network when the machine does not have a keypad. My devices to date have been multi-functions with keypads due to the fax function. I prefer to assign static I.P. addresses to printers so there's no problem 'finding' them. Brother does offer a linux network configuration utility though I've never used it or needed it to date.

I am thinking the same...even though it is more expensive to get the printer from Staples than Amazon.  I like the idea of being able to return it if it doesn't work right.   I really do not know what is all involved in setting an IP address manually.   I have set up the MPC-7440n using the Brother utility and it does work with the exception of that one issue with the scanner not being able to work over the internet connection.

> **kurt18947 said:**
> I got the Brother HL-3170CDW from Walmart. Refurbed for $158.50. Set a static I.P address and plugged it into a router, ran the Brother installer and I'm in business. The only problem is that the toners which come installed but with plastic covers over the rollers included 2 black and no magenta. Oops. A magenta cartridge is on its way from Brother. Contrary to what I was told by Brother's customer service, the printer will print with the wrong color toner installed so monochrome printing works and cyan and yellow work though I doubt the colors are true. The printer info sheets show the machine has printed about 150 pages hence refurbished. I have no idea why it was returned of course but it seems to work and comes with a 1 year factory warranty. The price is about the same as a good quality duplexing inkjet and I expect a longer more trouble free life from a laser.

So you were sent a printer that had two black, a cyan and yellow cartridge?  LOL!  That is funny.  I am surprised that printer went out like that, unless they were not smart to check it before packaging.  

I am going to say that initially I was looking at Canon color inkjet printers as I was (also initially) told they work with Linux Since Canon supports their product with Linux drivers.   However, other sources say that they don't always work.  Also the color printers from Canon are HUGE!  They also cost much more than the Brother printers....so now I am back to Brother.

...I just was at the Brother site and, Bcschmerker , you are right, there isn't a wired ethernet connection for the HL-3180CDW, which the HL3180CDW DOES have.  This is what I got from the manual:

136
Interfaces
D
1
Your machine has a Hi-Speed USB 2.0 interface. The machine can also be connected to a computer that has a USB 
1.1 interface.
2
Third party USB ports are not supported.
3
For detailed network specifications, see 
Network
 on page 137 and Network User&#8217;s Guide.
Model
HL-3180CDW
USB
Hi-Speed USB 2.0 
12
We recommend using a USB 2.0 cable (Type A/B) that is no more than 6 feet 
(2.0 meters) long.
Wireless LAN
3
I

No wired ethernet spec.

However, the HL-3170CDW is no good for me because it doesn't have the scanner and can only do 600x600dpi, hence the poorer picture quality.

So as of now, what I need is something like the HL-3180CDW, but with the ethernet port.

Thank you all again.  Hopefully something comes up soon because Halloween is near and I definitely need a printer.

EDIT:

Okay guys,  this is what I have come up with:

[http://www.brother-usa.com/MultiFunction/ModelDetail/4/MFC9340CDW/Overview](http://www.brother-usa.com/MultiFunction/ModelDetail/4/MFC9340CDW/Overview)

The MFC9340CDW, it has both wired and wireless internet and it supports the 2400 dpi output.   It also has fax capabilities, but I am not in need of that.

So I am hoping this would connect as easily as the HL-3170CDW would.

Geo

---

### Post by jukingeo on 2017-11-05
Hello All,

Back again!  I ended up buying the Brother MFC-9340CDW color printer I mentioned above.  Set up was FAR easier than I thought.  I used a network connection and through Ubuntu 16.04, I used a local driver for the MFC-9320...works like a dream!  However, that is the printer section.  The scanner is not recognized and I am wondering if any of you might know how I can get the scanner recognized on the network.

This was a similar issue I ran into with the MFC-7440N and with that one, I only could get the scanner to work using the USB connection, but the printer works fine on the network too. With the MFC-7440N, I had to use the Brother install utility to get the printer to work, whereas this printer worked just by using the printer setup within Ubuntu 16.04.

So I would say this is halfway solved as I got the printer to work on two machines connected to the network (both are on Ubuntu Studio 16.04), but the scanner isn't working.

Any help would be appreciated.

Thank You,

Geo

---

### Post by pdc on 2017-11-06
so that is a brscan4 machine;

several things to check

1) [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107) ```
 sudo apt install libusb-0.1-4
```

2) [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) ```
sudo cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
``` and ```
sudo cp /usr/lib64/sane/libsane-brother4.so /usr/lib/sane
``` and ```
sudo cp /usr/lib64/sane/libsane-brother4.so.1 /usr/lib/sane
```

3) [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) ....... download file and .. ```
sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
```

4) maybe see if this opensuse post has any relevance: [https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2](https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2) ..... user needs to be part of lp group .......... one may well be in lpadmin but lp is another group!!

........... apart from that, it is all pretty straightforward !!

---

### Post by jukingeo on 2017-12-10
> **pdc said:**
> so that is a brscan4 machine;

several things to check

1) [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00107) ```
 sudo apt install libusb-0.1-4
```

2) [http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101](http://support.brother.com/g/s/id/linux/en/faq_scn.html?c=us_ot&lang=en&redirect=on#f00101) ```
sudo cp /usr/lib64/sane/libsane-brother4.so.1.0.7 /usr/lib/sane
``` and ```
sudo cp /usr/lib64/sane/libsane-brother4.so /usr/lib/sane
``` and ```
sudo cp /usr/lib64/sane/libsane-brother4.so.1 /usr/lib/sane
```

3) [http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04](http://support.brother.com/g/s/id/linux/en/instruction_scn1c.html?c=us_ot&lang=en&redirect=on#u13.04) ....... download file and .. ```
sudo dpkg -i brother-udev-rule-type1-1.0.0-1.all.deb
```

4) maybe see if this opensuse post has any relevance: [https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2](https://forums.opensuse.org/showthread.php/527893-Unable-to-communicate-with-scanner-part-of-printer-scanner/page2) ..... user needs to be part of lp group .......... one may well be in lpadmin but lp is another group!!

........... apart from that, it is all pretty straightforward !!

Will any of this disturb my printer settings?  As of now the printer is more important to me than the scanner.

---

### Post by Yellow Pasque on 2017-12-10
Hmm. An older HP Envy 5540 worked out of the box for me on 16.04.

Oh, and defenestrating a printer? That's just great.

---

