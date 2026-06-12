---
title: "External 56k Modem for 8.04"
date: 2008-05-08
forum: Hardware
---

### Post by Drakelet on 2008-05-08
Which one would you recommend?

I've read about the Actiontec here.  Does it work with 8.04?  Is this the one? [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=350055806970&ssPageName=STRK:MEWA:IT&ih=022](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=350055806970&ssPageName=STRK:MEWA:IT&ih=022)

What about these other makes?:
Zoom
Sweex
PC Line
Net-lynx
Hayes Accura
Dynamode

The sooner the reply the better, I want to get this sorted ASAP. :)

Thanks.

---

### Post by Drakelet on 2008-05-09
Oh come on!  I know some of you have external modems for dial-up.  It's not THAT hard to reply...

---

### Post by Drakelet on 2008-05-09
Anyone?

---

### Post by andrewc6l on 2008-05-09
I don't have a 56k modem on 8.04, but I do have one on an OpenBSD box. The Zoom modem works well for me - and I don't like the USRobotics ones anymore, since the last one I bought was DOA (or D after 2 hours on, at any rate).

The only problem with the Zoom modem: to update its flash, you need to connect it to a Windows box to run their installer. Once it's reflashed, all serial modems seem to Just Work.

---

### Post by Drakelet on 2008-05-10
Thanks andrewc6l.

Do you need to update the flash, or, like mobo BIOSs, is it just optional (but recommended)?

In fact, would pretty much all external modems work?

---

### Post by mickeygood on 2008-05-10
I am new with linux as os I've got an sony vaio lapto pmodel pcg-k15 
pentium 4 2.80 ghz ,512dr sdram . Beacause i live in a rural area , i use my V3 rzor celular as a modem SeArch in motorola site but there is no divers for linus available, i would appreciate any help

mickeygood

---

### Post by Drakelet on 2008-05-10
mickeygood, as yours is concerning mobile phones I would recommend making a whole new thread. :)

---

### Post by Drakelet on 2008-05-10
Bumpage. :(

---

### Post by Drakelet on 2008-05-11
I've been looking around some more and I'm very tempted to buy one of the USB Actionec ones, from
[http://search.ebay.co.uk/search/search.dll?sourceid=captaincaveman&satitle=actiontec+external+modem](http://search.ebay.co.uk/search/search.dll?sourceid=captaincaveman&satitle=actiontec+external+modem)

Surely someone has Hardy running on one!  In fact, I'm nearly certain.

EDIT: Here's a better question.  Do the mini-modems work?
[IMG]http://i12.ebayimg.com/08/i/000/ef/ac/5e5a_2.JPG[/IMG][img]http://i21.ebayimg.com/07/i/000/af/04/66ac_2.JPG[/img]

---

### Post by EmilyRose on 2008-05-11
Well, I Just upgraded from 7.10 and am very unhappy to report that my zoom mini modem is not working :( It worked perfectly on 7.10 though;)

---

### Post by Drakelet on 2008-05-11
Well, I have 8.04.  So, no Zoom Mini Modem!?  Damnit.

Thanks for the help though, possibly saved me some money. :)

---

### Post by Drakelet on 2008-05-11
Oh, another thing.  Are any drivers/software etc needed?

---

### Post by EmilyRose on 2008-05-11
Not before. It was using the generic usb modem module, which either doesn't seem to exist for 8.04 :scream: or else is broken in 8.04!! I'm now stuck trying to get the damn thing working out of my basement on my old system with 6.10!!

---

### Post by RJARRRPCGP on 2008-05-11
> **Drakelet said:**
> Which one would you recommend?

I've read about the Actiontec here.  Does it work with 8.04?  Is this the one? [http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=350055806970&ssPageName=STRK:MEWA:IT&ih=022](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=350055806970&ssPageName=STRK:MEWA:IT&ih=022)

What about these other makes?:
Zoom
Sweex
PC Line
Net-lynx
Hayes Accura
Dynamode

The sooner the reply the better, I want to get this sorted ASAP. :)

Thanks.

Zoom should be fine. The Zoom 3048 C is definitely fine. 
That's the one I used with Ubuntu when I had POTS.

---

### Post by Drakelet on 2008-05-12
> **RJARRRPCGP said:**
> Zoom should be fine. The Zoom 3048 C is definitely fine. 
That's the one I used with Ubuntu when I had POTS.
OK, thanks.  What's POTS?

Although I've just seen this:
[http://ubuntuforums.org/showthread.php?p=4939622#post4939622](http://ubuntuforums.org/showthread.php?p=4939622#post4939622)

Gonna test it now!  Sounds awesome!!

---

### Post by NJC on 2008-05-12
POTS = plain old telephone service.
 
I've used a USR External 56K modem with 6.0.6, 7.10 and 8.04. All worked well as serial modems are easily recognized in Ubuntu. Only program I need to work with modem is Gnome-PPP.

---

### Post by Drakelet on 2008-05-12
Thanks!  Gonna try the 536EP driver now though.

---

### Post by EmilyRose on 2008-05-12
So, I just thought I'd post back here an update... I think my modem was blown. In other words, not an ubuntu problem so much as a modem problem... I'm not entirely, 100% sure of this, but am fairly so. So... it was basicly just a wierd fact that it got blown on the same exact day I got around to upgrading! (Done at my grandparents' where they do have high speed...). Wierd. 

Anyhow I stuck it in my old system (running 6.10) and absolutely nothing happend (where as in 8.04 it said 'unknown device at least'). So... yeah. It very well may in fact work in 8.04. On the bright side, my usb-serial cable works in 8.04, so my old serial does now too!! :D

---

### Post by andrewc6l on 2008-05-12
Pretty much any serial modem should work. I had to reflash my Zoom modem because it would hang the machine whenever I'd get a RING on the serial port - I think the modem might have been driving a line high that the motherboard was interpreting as "wake on ring", and I had some software that was looking for that.

If you're in a more normal situation, you probably don't have to worry. In general serial modems are interchangeable - they all conform more or less to the Hayes / USR command set. They don't have compatibility problems the way that USB modems / WinModems do.

---

### Post by Drakelet on 2008-05-16
How do you reflash a modem?

Also, any idea if this would work?
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=290230370463](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=290230370463)
I've also seen quite a few ZOOMs about, might just get one of them.

@[RJARRRPCGP]("http://ubuntuforums.org/member.php?u=28754")
You said the 3048C would work.  Any idea about 3049?

I would still like it if someone could tell me one which will definitely work, as I'm short of money and can't really afford to waste any. :(

---

### Post by Drakelet on 2008-05-16
Well, I bought the Speedtouch.  Should it just be plug'n'play?

---

### Post by Drakelet on 2008-05-21
********.  Got it today... and it's an ADSL broadband modem.  The guy advertised it as the wrong thing.  Not happy.

So I'm looking at the Zoom 3090AF mini modem.
[http://cgi.ebay.co.uk/Zoom-3090-V-92-V-90-USB-External-Mini-Modem_W0QQitemZ150248677053QQihZ005QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/Zoom-3090-V-92-V-90-USB-External-Mini-Modem_W0QQitemZ150248677053QQihZ005QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
Look OK?

EDIT: Just done some searching:
[http://ubuntuforums.org/showthread.php?t=617623&highlight=zoom+3090af](http://ubuntuforums.org/showthread.php?t=617623&highlight=zoom+3090af)
> The 3090AF is definitely a winmodem.So it won't work!?

Bloody hell, when I bought the first one there were loads.  Now there are a lot less.  FFS.

EDIT2: Anyone know about either of the below two?  Any help welcome, I really want it to work. :(
[http://cgi.ebay.co.uk/56Kbps-External-USB-Modem-BNIB_W0QQitemZ110252035625QQihZ001QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/56Kbps-External-USB-Modem-BNIB_W0QQitemZ110252035625QQihZ001QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
[http://cgi.ebay.co.uk/External-USB-Modem-Sitecom-56k_W0QQitemZ150248814188QQihZ005QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/External-USB-Modem-Sitecom-56k_W0QQitemZ150248814188QQihZ005QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)

Here's the eBayUK search for all of them:
[http://search.ebay.co.uk/search/search.dll?sofocus=unknown&sbrftog=1&dfsp=1&catref=C6&sourceid=captaincaveman&satitle=usb+-adsl+-dsl+-broadband+-gprs+-vodafone&sacat=3692%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=EX152NH&sabfmts=1&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=1%26fsoo%3D1&coaction=compare&copagenum=1&coentrypage=search](http://search.ebay.co.uk/search/search.dll?sofocus=unknown&sbrftog=1&dfsp=1&catref=C6&sourceid=captaincaveman&satitle=usb+-adsl+-dsl+-broadband+-gprs+-vodafone&sacat=3692%26catref%3DC6&sargn=-1%26saslc%3D3&sadis=200&fpos=EX152NH&sabfmts=1&ga10244=10425&ftrt=1&ftrv=1&saprclo=&saprchi=&fsop=1%26fsoo%3D1&coaction=compare&copagenum=1&coentrypage=search)

---

### Post by Drakelet on 2008-05-21
Please, someone!!

---

### Post by Drakelet on 2008-05-21
I give up.  Just gone and bought another one.  Definitely 56k this time!  Lets just hope it works. :(

[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=110252035625](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&item=110252035625)

---

### Post by Drakelet on 2008-05-25
Great.  This one doesn't seem to work either.

It's a Smart Link SmartUSB56 Voice Modem, made by Mentor.  Any ideas?

I might just shell out the lots of money and get the Zoom. :(

EDIT: Found it on XMODEM:
[http://xmodem.org/chipsets/smartlink/smartlink_smartusb56.html](http://xmodem.org/chipsets/smartlink/smartlink_smartusb56.html)
Seems like there are official drivers.  But the official website is dead.
As for Goldberg's custom drivers, there are lots.  Which do I need?  Is it just the latest one from [http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/](http://linmodems.technion.ac.il/packages/smartlink/Ubuntu/) ?

---

### Post by Raval on 2008-05-25
I use an internal Connexant 56k PCI modem. on 8.04 worked with 7.04 and 7.10 as well. The drivers can be found on the forum and they work for a wide variety of Connexant modems.

I also have an Intel 537EP internal PCI modem and it works just as well with the modem drivers on the forum.

BTW I use to use an Actiontec external USB modem that was like $10.00

---

### Post by Drakelet on 2008-05-25
Can you give me a link to those drivers?  Although don't know if it will work, supposedly the 536EP works, but it doesn't for me.

I found the drivers for my new one (SmartUSB56) were out of date, and the company is not even making modems any more!!  Haven't been for like 2 years.

I can't find any Actiontec ones in the UK, not for under like £20, from America!!!
[http://cgi.ebay.co.uk/Actiontec-56k-V-92-USB-Serial-External-Modem-New-Sealed_W0QQitemZ280228336937QQihZ018QQcategoryZ62025QQrdZ1QQssPageNameZWD2VQQcmdZViewItem](http://cgi.ebay.co.uk/Actiontec-56k-V-92-USB-Serial-External-Modem-New-Sealed_W0QQitemZ280228336937QQihZ018QQcategoryZ62025QQrdZ1QQssPageNameZWD2VQQcmdZViewItem)

For external USB modems I assume I need one with one of the chipsets from the left column?
[http://xmodem.org/chipsets/dips/roster.html](http://xmodem.org/chipsets/dips/roster.html)

You know what?  I've just about given up on Ubuntu. :(  Seems like a LOT more trouble than it's worth.

---

### Post by Raval on 2008-05-25
> **Drakelet said:**
> Can you give me a link to those drivers?

Dell link to th version I used on 7.04 and ( for awhile on) 7.10

hsfmodem_7.60.00.**06**oem_i386.deb
[http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745](http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R155004&SystemID=INSPIRONI6400/E1505&servicetag=&os=UBLN&osl=en&deviceid=8593&devlib=0&typecnt=0&vercnt=1&catid=-1&impid=-1&formatcnt=1&libid=20&fileid=206745)

This is what I used first on 7.10 and now on 8.04 hsfmodem_7.60.00.**18**oem_i386.deb

I can't remember if I tried this one on 8.04 intel537ep-gutsy_1.0_i386.deb

Let me know if you have any problem I will walk you through as much as I can.


BTW for anyone on Xubuntu 7.10 the Conexant driver works on my GF PC.


Can't unload since files are too big. send me a PM with you email address and I will email them to you both files are under 1.5mb.

---

### Post by Drakelet on 2008-05-26
Thanks.

To be honest, I think I'm just going to try and find a cheap external fully-hardware modem.  So no drivers needed.  Now I just need to find one that will work. :(

---

### Post by Raval on 2008-05-26
> **Drakelet said:**
> Thanks.

To be honest, I think I'm just going to try and find a cheap external fully-hardware modem.  So no drivers needed.  Now I just need to find one that will work. :(

Well when it comes to modems that work under Linux you should go here I think they will be of much more help [http://linmodems.org/](http://linmodems.org/)

They have a mailing list that you can use to get help.

If you ever get a Intel 536EP, 537EP or Conexant Modem you could still ask for the drivers.

Maybe you can try modems from stores with friendly return policies so if they don't work you could return them or take an Ubuntu live CD and try the modem on one of the PCs in the store, that is, if it were possible of course.

---

### Post by Flintlock on 2008-05-26
I have been using a Actiontec Dual PC modem for years with linux with no problems at all. It is ethernet and you log in though your web browser.

It  also acts as a firewall.

---

### Post by Drakelet on 2008-05-31
Does anyone know if the 3095 mini modem works?
[img]http://img.shoppydoo.com/uk/tp_products/26/2326592.jpg[/img][img]http://www.provantage.com/ZOOA01F.GIF[/img]

Please help.

---

### Post by Raval on 2008-06-02
> **Drakelet said:**
> Does anyone know if the 3095 mini modem works?
[IMG]http://img.shoppydoo.com/uk/tp_products/26/2326592.jpg[/IMG][IMG]http://www.provantage.com/ZOOA01F.GIF[/IMG]

Please help.

Dude, try Linmodems.org its a website for modem on Linux, join the mailing list and ask there. They have the experience.

---

### Post by jessejazza on 2008-06-02
Drakelet: hang on!

I'm just looking into this myself. I was a bit miffed when i bought a Dynamode M56PCI/S-R software modem as it worked for someone using Suse 9 pro. I was using suse 10.3 and thought it'd work. It didn't i then returned to using ubuntu and started to hunt for drivers for a chipset CX11252-41. I haven't found it easy. This afternoon talking to dynamode i was gutted to find that two of their USB modems while stated as linux compliant are in fact not. He did assure me that the model M56USB-SMART was.

What some manufacturer says on a box needs to be watched! I think my modem can work and i've got to change a setting. I'll post again to confirm it. To some extent with linux it seems one has got to retain an old windows machine for a few things - one of them in my view is faxing.

The other alternative which i haven't tried yet is that ndiswrapper may work.

---

### Post by Drakelet on 2008-06-02
Thanks.  I've just suddenly realised the 3095 may not work either.  I've posted a thread, but, of course, no replies. :(

Good luck mate.

---

### Post by Raval on 2008-06-02
> **Drakelet said:**
> Thanks.  I've just suddenly realised the 3095 may not work either.  I've posted a thread, but, of course, no replies. :(

Good luck mate.

Just so you know, I'm on the net with Ubuntu 8.04 with my internal 56k pci modem. The conexant modem I spoke of earlier.

---

### Post by Drakelet on 2008-06-03
Damn you!!

Do you know the exact model/name etc?  And what about drivers - do they need to be updated often?

---

### Post by Raval on 2008-06-03
> **Drakelet said:**
> Damn you!!

Do you know the exact model/name etc?  And what about drivers - do they need to be updated often?

Never had to update the drivers, using the same driver from 7.10, used an older one for 7.04 and for 7.10. I'm sure it would work on 8.04.

I will turn off my PC and pull the card and post the chip number. Also I have used this driver on 3 Conexant modems and all worked. Mind you the brand of the modems vary but they all use Conexant chips. I have the drivers for the Intel 537EP modems too.

---

### Post by Drakelet on 2008-06-03
Thanks.  Strange thing is the 536EP drivers don't work for me.  What I really want is a hardware one, but I don't know which ones are fully hardware and not external software ones. :(

---

### Post by Raval on 2008-06-03
> **Drakelet said:**
> Thanks.  Strange thing is the 536EP drivers don't work for me.  What I really want is a hardware one, but I don't know which ones are fully hardware and not external software ones. :(

I read your post here [http://ubuntuforums.org/showpost.php?p=4951353&postcount=77](http://ubuntuforums.org/showpost.php?p=4951353&postcount=77)
so let me see if I got this right. The Intel modem would dial and then disconnect? Also did you select dev/modem under Gnome-ppp?


BTW my Conexant modem chip is CX11256-31Z

---

### Post by Drakelet on 2008-06-04
Yep, that's what I was having.  But when it was "connected" it still said there was no connection in Firefox etc.

Thanks, I'll see if I can find some cards with that chip. :)

---

### Post by Raval on 2008-06-04
> **Drakelet said:**
> Yep, that's what I was having.  But when it was "connected" it still said there was no connection in Firefox etc.

Thanks, I'll see if I can find some cards with that chip. :)

Dude, thats means the modem was working but something isn't configured properly, do you have another machine you can dualboot a fresh copy and try again? Installing the driver and Gnome-ppp. Once you D/L Gnome-ppp you have no need to config wvdial.

---

### Post by Drakelet on 2008-06-04
Done it all multiple times.  It was in Gnome-ppp it wasn't working, same thing.  Live and installed, formatted and installed multiple times.  Edited wvdial.conf, pppconfig, everything.  Spent hours and hours trying.

---

### Post by Raval on 2008-06-04
> **Drakelet said:**
> Done it all multiple times.  It was in Gnome-ppp it wasn't working, same thing.  Live and installed, formatted and installed multiple times.  Edited wvdial.conf, pppconfig, everything.  Spent hours and hours trying.



:confused: welll ehemmmm.......that sucks!

---

### Post by _duncan_ on 2008-06-04
> **Drakelet said:**
> Yep, that's what I was having.  But when it was "connected" it still said there was no connection in Firefox etc.

Thanks, I'll see if I can find some cards with that chip. :)

Did you check if Firefox is in "Work Offline" mode?

---

### Post by Drakelet on 2008-06-04
@Ravel: Yes.  Yes it does.  About to buy the external 3095, wish me luck!  I've heard it works, I think.

@_duncan_: I'm not THAT stupid (quite). ;) No, it wasn't in Offline mode.  Pidgin etc wouldn't work either.  In other words, it wasn't actually connected, or at least nothing was getting through.

---

### Post by Raval on 2008-06-05
> **Drakelet said:**
> @Ravel: Yes.  Yes it does.  About to buy the external 3095, wish me luck!  I've heard it works, I think.

[IMG]http://images.inmagine.com/img/moodboard/mb511/mwi11590023.jpg[/IMG]

---

### Post by Drakelet on 2008-06-05
And, due to dial up, I lost the auction on eBay by 20p.  Page wouldn't load fast enough.  Goddammit!!

---

### Post by zoomzoomzoom on 2008-06-07
I posted on your other thread.  No need to repeat things.  Zoom 3095 does work on linux (and works well) but you have to have driver module compiled for your particular linux kernel.  Zoom didnt make it easy for linux users. Just read other thread.  Good luck.  Simplest if you dont need the small size and convenience of mini zoom modem is to just get a usb converter cable US$5 off ebay to use with an old serial modem.  If you cant get an old serial modem for equivalent of US$10 shipped price, you arent trying.  They usually sell even cheaper at local garage sales and flea markets.  Linux users and smart windows users still on dialup are only ones really interested anymore. Oh just make sure it is 28k or better serial modem.  There are some ancient 2k and 14k and such out there.  I say 28k cause my dialup connection never goes over 24k no matter what modem.  If you can connect at better than 33k then get a 56k modem.  If like me you never connect faster than 28k, it doesnt matter.

---

### Post by Drakelet on 2008-06-08
Thanks for your help in this and the other thread zoomzoomzoom.

I don't need a USB mini one, just thought it would be easy.

Which modems do have those chips though?  I think that's my main problem, knowing which one to get.
Plus, my connection gets up to about 40kbps so I'll need a 56k one.

zoomzoomzoom's posts from my other thread so other people aren't confused:
> **zoomzoomzoom said:**
> Here is a link to my earlier posts. [http://ubuntuforums.org/showthread.php?t=711646](http://ubuntuforums.org/showthread.php?t=711646) This modem is actually a hardware modem (has an onboard controller), BUT the way they set it up acm-cdc module cant read its info. They should have come up with a patch for the acm-cdc module but instead they came up with this dumb little driver (its tiny) that lets all this happen. You have to compile this driver for a specific linux kernel or find a precompiled driver module as I mention doing in 7.10 in the link I give. 

It is a good modem and works fine in linux, just a shame Zoom wanted to make it such a pain to get working in linux.

I dont have a copy of Ubuntu 8.04 (havent had broadband access for sometime now) so cant give you step by step instructions though should be simular to steps I gave for getting it working in 7.10. Good luck.
> **zoomzoomzoom said:**
> Oh by the way if you dont need super compact modem, just need usb connection cause your new computer doesnt have a serial port, the easiest way is plain old serial modem with a cheapo serial to usb coverter cable. (They are somewhere around $5-$6 total shipped price off ebay.) I suggest getting the one with the pl2303 chip. It works better and the pl2303.ko module has been included in linux kernel for some time so will work even with older versions of linux. However from 2.6.24 and newer kernel, the cheaper ch341 chip (winchiphead) cables will work since the ch341.ko module is included. It will maybe work on older linux kernels but you have to patch the kernel to have a chance. I have one of each kind of converter cable (cause I bought the stupid winchiphead cable first not knowing...) and finally got the ch341 cable working in Puppy Linux 4.00 with 2.6.25 kernel. ch341.ko module should be in Ubuntu 8.04.

---

### Post by zoomzoomzoom on 2008-06-08
> **Drakelet said:**
> Thanks for your help in this and the other thread zoomzoomzoom.

I don't need a USB mini one, just thought it would be easy.

Which modems do have those chips though?  I think that's my main problem, knowing which one to get.
Plus, my connection gets up to about 40kbps so I'll need a 56k one.


Have what chips?  I was talking about the serial to usb converter cables with the winchiphead and prolific chipset mention.  These are sold separately from any modem though some modem manufacturers apparently use them in their usb modems.  

And if your computer still has a serial port, you dont even need the converter cable.  Serial cable on a plain old external serial modem still works just as well as it ever did.  All external serial modems work in linux and pretty much any other operating system that supports a dialup internet connection.  You dont have to look for any particular brand of serial modem , just as long as it can connect with a serial cable and is correct speed.  In your case you need a 56k version.  For me 28k and 33k versions work since I cant connect faster than 24k no matter what.

There are some softmodems that work ok in linux (some better than others), but a hardware modem will always work.  The serial-to-usb converter cable just updates the old external serial modems into modern world where serial ports no longer exist.  The converter cables can also update some (not all) other serial devices.  

Like I said, for now the only downside to the zoom 3095 modem is that you have to recompile the driver module each time you upgrade to a newer kernel.  Hopefully somebody sometime will make a patch to the acm-cdc module so zoom's driver isnt needed.

There is another mini usb hardware modem, sold in USA branded by Dell, but sold under other names in other parts of world.  Made in either Taiwan or China of course.  I've never used one, it may be natively supported dont know.  The 3095 however seems more numerous and probably cheaper.

I have seen some people promoting Dynex DX300 usb modem.  It uses the connexant driver and is definitely a software modem.  I got to try one at one point and didnt like it.  It worked but seemed sluggish.  It is cheap and some people swear by it.

I had a Smart Link pci soft modem for a while.  Linux driver for it was very good.  It was very stable and as fast as any hardware modem at least for me.

There are some pci internal hardware modems out there, but rare.  MOst are USR brand and you have to know the exact model numbers to be sure as USR also made lot of softmodems.  On ebay if the seller knows its a pci hardware modem he will ask higher price.  But sometimes if you've done your research you can find one that is being sold as a soft modem and get a good deal.

---

### Post by Drakelet on 2008-06-09
Oh, OK.

Well, I don't have a serial port so I'll need a USB/serial cable.  I'm still not sure which serial modem is fully hardware though.  That's what's confusing me.  You say about an old one, but there are a lot of old ones. :P

---

### Post by bstanley on 2008-06-09
@Drakelet:  did you wind up getting the Zoom 3095?

            If so, does it work?

            I have been trying to get help with my Zonet
            PCMCIA modem (posted a thread last week) but
            no one has responded yet.

            If the 3095 does work, I might just consider
            trying one of those instead of the Zonet.

---

### Post by Drakelet on 2008-06-10
Nope.  I was buying it off eBay, but was outbid with about 60 seconds to go.  And because I have dial up it wouldn't ******* load in time!! :(

I'm still looking out for one though.

---

### Post by zoomzoomzoom on 2008-06-10
ALL external modems that connect with a serial cable are HARDWARE modems.  There are NO software serial modems.  Any software that comes with a serial modem is to extend capabilities of the modem such as faxing or call waiting or whatever under windows.  The basic modem function will work fine with the built in PPP software nearly every linux distribution has. 

The 3095 as I say is a nice modem.  I bought my first one off ebay for like US$22 shipped price.  Then happened to see another from one of those places that resells stuff people return opened to stores.  The way they described it, thought pretty good chance of it working and for $5 sure enough it worked perfectly.  That was a gamble on my part though. They basically said in their description they didnt think it worked.  As I said before the Zoom 3095 is a good modem if you can put up with recompiling its driver everytime you upgrade linux kernels.  HIGHLY desirable for laptop users cause its so compact and doesnt need a power brick.  If you want one of these just be patient, eventually you will run into a cheap one on ebay.  I think full retail price of $40 to $60 is silly unless thats just trivial amount money to you, but for some its worth it.

I never pass up good cheap modem (especially a hardware modem) unless I already have several good ones setting around at the time.  I live on a hill and can lose several in a year from lightening.  This year so far only lost one.

---

### Post by bstanley on 2008-06-11
Hi Zoomzoomzoom!

Would you have any idea why a Zonet PCMCIA (hardware) modem

might not be working with Ubuntu 8.0.4?  I have another thread

running on this issue but have only one responder so far.

When you plug it in, the system log says it sees it as /dev/ttyS2,

but  gnome-ppp can not detect it.

The modem does work ok with  mephis 6.5 and windows of course,

so it is not a hardware issue.

---

### Post by Drakelet on 2008-06-11
> **zoomzoomzoom said:**
> ALL external modems that connect with a serial cable are HARDWARE modems.  There are NO software serial modems.  Any software that comes with a serial modem is to extend capabilities of the modem such as faxing or call waiting or whatever under windows.  The basic modem function will work fine with the built in PPP software nearly every linux distribution has. 

The 3095 as I say is a nice modem.  I bought my first one off ebay for like US$22 shipped price.  Then happened to see another from one of those places that resells stuff people return opened to stores.  The way they described it, thought pretty good chance of it working and for $5 sure enough it worked perfectly.  That was a gamble on my part though. They basically said in their description they didnt think it worked.  As I said before the Zoom 3095 is a good modem if you can put up with recompiling its driver everytime you upgrade linux kernels.  HIGHLY desirable for laptop users cause its so compact and doesnt need a power brick.  If you want one of these just be patient, eventually you will run into a cheap one on ebay.  I think full retail price of $40 to $60 is silly unless thats just trivial amount money to you, but for some its worth it.
Oh awesome.  I might as well just get a serial one then.  They'll all work right?

To be honest, although the 3095 is nice, I don't know if it's worth the hastle.  Knowing my luck it won't work with my config or something. ;)

---

### Post by stchman on 2008-06-11
Make sure any modem you get for Linux is a hardware modem.  Softmodems or Winmodems have poor support under Linux.  I believe all external modems are hardware modems sine they will not have access to CPU cycles over RS-232.

---

### Post by jessejazza on 2008-06-11
Drakelet - as i said earlier we are both at the same point. I think my conexant winmodem works but there is a setting somewhere that i haven't found. As another member said one has got to watch the kernels and compile - hardly worth the time. I bought a serial one [BT Enabler] and installed SETSERIAL from synaptic and it works. With linux one needs to stay with a serial fax modem. Non of those mini ones will be much good... i even spoke to one manufacturer who told me that 4 of their models were claimed to be linux compatible BUT weren't in practice.

We're right to try and get a softmodem working IMHO! In 2000 i got on the internet with a hardware pci modem. However two years later i changed it for a software one which i then used for the next five years - it was more reliable than the hardware one and better for faxing as it varies the flow speed. the slight drawback being that of speed (hardly noticeable).

Just testing today this serial modem has been fine faxing single sheets with efax-gtk but not so good with three. I couldn't get on dial-up!

---

### Post by zoomzoomzoom on 2008-06-11
> **bstanley said:**
> Hi Zoomzoomzoom!

Would you have any idea why a Zonet PCMCIA (hardware) modem

might not be working with Ubuntu 8.0.4?  I have another thread

running on this issue but have only one responder so far.

When you plug it in, the system log says it sees it as /dev/ttyS2,

but  gnome-ppp can not detect it.

The modem does work ok with  mephis 6.5 and windows of course,

so it is not a hardware issue.

You can either manually force it to use whatever is at ttyS2 or you can set the dialer to use /dev/modem, then create /dev/modem as a sim-link to /dev/ttyS2.  I dont know why it doesnt automatically take care of things.  I'm more old school and have no problem setting things up manually and not spending time worrying why or why not of automation scripts.  If you want more easy adjustments install KPPP, its very intuitive to use.  Modem still wont be automatically found and installed but the settings are easier with KPPP gui than wvdial config file or minimal settings options with the administration dialer.

---

### Post by zoomzoomzoom on 2008-06-11
> **Drakelet said:**
> Oh awesome.  I might as well just get a serial one then.  They'll all work right?

To be honest, although the 3095 is nice, I don't know if it's worth the hastle.  Knowing my luck it won't work with my config or something. ;)

All external serial modems will work.  Some of later ones seem rather cheap, I had one that didnt even have an on/off switch on it.  But still worked ok.  Some serial modems have a narrow connector on back of them and some have a wide connector.  The usb adapter cables all have narrow serial connector.  They will connect directly to modem where the serial cable connects if modem has narrow connector.  They will need an adapter if modem has the wide serial connector OR you can just use the original old serial cable to connect to modem and then connect the serial cable to the adapter cable.  That works fine too and gives you a long cable.  Everything has appropriate male/female ends so all fits together.

As to the 3095, if you stick to Ubuntu or other more popular versions of linux you will probably be able to find pre-compiled driver modules for this modem at site I mention in how I got zoom modem to work on 7.10.  However if you use a smaller distribution using an oddball kernel that the big distributions ddidnt use in a release then you have to compile your own driver module.

---

### Post by Drakelet on 2008-06-12
I'm actually having a hard time finding serial modems.  I've only found two so far, one is £30 ($60) and one is £15 ($30).  Here's the latter one:
[http://www.aria.co.uk/Products/Peripherals/Modems/56K+External+(Serial)+Modem?productId=6422](http://www.aria.co.uk/Products/Peripherals/Modems/56K+External+(Serial)+Modem?productId=6422)
There aren't even any on eBay! :(

Luckily I put one of the ones I bought on eBay (and didn't work) back on eBay, and already have a bid and a watcher.  If I sold it right now I would make a loss of £1-£2, which isn't too bad I suppose.

---

### Post by TopEnder on 2008-06-12
Drakelet, FYI I have a Hayes Accura 56K + FAX External modem and have used it with 6.04, 7.04 and 64bit 8.04.  No drivers had to be installed, you could say Plug & Go, works well, picked up at my local recycling centre. TopEnder

---

### Post by ezeze5000 on 2008-06-12
I have a Diamond SupraExpress 56e PRO external full hardware serial modem and it works just fin in Ubuntu 8.04.

The last time I looked they were getting kind of hard to find.


I hope this helps.

---

### Post by jessejazza on 2008-06-12
Drakelet: i can't think where you are looking on ebay. Search "fax modem" and up come more than a dozen serial hardware modems, mostly new and cost inc p&p £5. In all honesty they are cheaper than a pci modem and hassle free. These units are often new and because they no longer have a box and can't be sold by a shop they are sold on ebay.

I bought two to be on the safe side and both work fine. It was a "BUY NOW" to save me waiting till a close of auction.

---

### Post by timcredible on 2008-06-12
i've been using a cheap serial connected modem for about 7 years now, and it works with all distros since there's nothing needed driver wise.  however, since you don't have a serial port, i'm not sure what is needed, but i have a verizon usb wireless broadband modem and gnome-ppp works with it, no drivers needed, i tested an att usb wireless broadband modem which worked with no drivers also, so i would suspect that most any usb-connected modem should work.  what does gnome-ppp tell you when you configure it for the correct tty port?  also, i had to check the 'stupid mode' in gnome-ppp.

---

### Post by Drakelet on 2008-06-12
> **jessejazza said:**
> I bought a serial one [BT Enabler] 
This one?[U]
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280235141755](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280235141755)
[/U] 
> **TopEnder said:**
> Drakelet, FYI I have a Hayes Accura 56K + FAX External modem and have used it with 6.04, 7.04 and 64bit 8.04.  No drivers had to be installed, you could say Plug & Go, works well, picked up at my local recycling centre. TopEnder
That was the £30 I was saying about. :( Might see if I can find it second hand.

> **ezeze5000 said:**
> The last time I looked they were getting kind of hard to find.
You're telling me! :D

> **ezeze5000 said:**
>          I have a Diamond SupraExpress 56e PRO external full hardware serial modem and it works just fin in Ubuntu 8.04.
Like this one? :D
[http://cgi.ebay.co.uk/Diamond-Supraexpress-56e-PRO-fab-fast-56K-Fax-modem_W0QQitemZ290237138787QQihZ019QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem](http://cgi.ebay.co.uk/Diamond-Supraexpress-56e-PRO-fab-fast-56K-Fax-modem_W0QQitemZ290237138787QQihZ019QQcategoryZ3692QQssPageNameZWDVWQQrdZ1QQcmdZViewItem)
EDIT: Except it doesn't include any cables!  Damnit.

> **jessejazza said:**
> Drakelet: i can't think where you are looking on ebay. Search "fax modem" and up come more than a dozen serial hardware modems, mostly new and cost inc p&p £5. In all honesty they are cheaper than a pci modem and hassle free. These units are often new and because they no longer have a box and can't be sold by a shop they are sold on ebay.
I was searching for serial modem.  It probably doesn't help that looking through eBay takes forever due to dial up!

> **timcredible said:**
> however, since you don't have a serial port, i'm not sure what is needed
I'm pretty sure just a simple USB/serial cable should work.

> **timcredible said:**
> so i would suspect that most any usb-connected modem should work. what does gnome-ppp tell you when you configure it for the correct tty port? also, i had to check the 'stupid mode' in gnome-ppp.
I wish. :( I tried everything, it was in stupid mode, didn't work (and that includes the USB modems).

---

### Post by zoomzoomzoom on 2008-06-13
Looking on ebay.co.uk here is list of 56k external serial modems:
[http://computers.search.ebay.co.uk/56k-usb_External_W0QQcatrefZC6QQdfspZ32QQfclZ3QQfposZPostcodeQQfromZR2QQfsooZ2QQfsopZ32QQftrtZ1QQftrvZ1QQga10244Z10425QQsabfmtsZ1QQsacatZ3692QQsadisZ200QQsaobfmtsZinsifQQsargnZQ2d1QQsaslcZ3QQsatitleZ56kQ20Q2dusbQQsbrftogZ1QQsofocusZunknown](http://computers.search.ebay.co.uk/56k-usb_External_W0QQcatrefZC6QQdfspZ32QQfclZ3QQfposZPostcodeQQfromZR2QQfsooZ2QQfsopZ32QQftrtZ1QQftrvZ1QQga10244Z10425QQsabfmtsZ1QQsacatZ3692QQsadisZ200QQsaobfmtsZinsifQQsargnZQ2d1QQsaslcZ3QQsatitleZ56kQ20Q2dusbQQsbrftogZ1QQsofocusZunknown)

---

### Post by jessejazza on 2008-06-13
Drakelet: yes mine is the BT Enabler. My seller was dw05daw. He's put some more on and he does send immediately - i placed my order on sunday and by second class it was with me on Wed... good to today's GPO standards.

Getting on ebay with only dial-up is hell now... dial-up can only be used for just about reading emails these days.

---

### Post by Drakelet on 2008-06-13
You're telling me!  99% of my time online is spent waiting, it's infuriating.

Thanks all, probably going to buy one SOON!

---

### Post by jessejazza on 2008-06-14
Good luck. My use for a modem is for faxing and as a reserve in case something goes wrong with broadband. Also to read emails when on holiday - dialup still does have a use. One last thing a serial modem still requires software for the serial port available in all distros [in ubuntu it is called SETSERIAL].

My choice for the BT Enabler was largely due to my confidence in BT equipment. One other thing when you get broadband be careful of the small print about an annual contract. You may have to move suddenly (as i did when my father died last year) make sure you are allowed to continue the contract when you move. With some providers the annual contract is for that address alone and will charge a large cancellation charge if you need to cancel.

BT allow you to move and take the contract with you subject to 5 weeks notice. NOW you know why i'm a bit pro BT. [slightly off topic but thought you may like to know]:):-({|=

---

### Post by Drakelet on 2008-06-14
I've had nothing but problems and concerning BT and their internet service!  Haha.  Everyone's different I suppose.  Never had any of their products except telephones, which seemed OK.

Is this the one you have?
[http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280235141755](http://cgi.ebay.co.uk/ws/eBayISAPI.dll?ViewItem&rd=1&item=280235141755)

---

### Post by jessejazza on 2008-06-15
yes that's it.

But any of the serial hardware ones will be fine. This one i think is a series 2 which isn't as good as a series 1. But for £5 so what. The last thing you want to have to attempt is compiling for each ubuntu release.

Sorry i've been pleased with BT service!

---

### Post by Drakelet on 2008-06-15
Right, I'll probably buy that one.  I just don't want to buy ANOTHER one which won't work - I want to be 100% sure! :D

Thanks.  I would buy now, but I'm saving for a PS3 currently haha!

---

### Post by bstanley on 2008-06-25
Hi Drakelet!

If you can use a PCMCIA modem with you system,

I finally got my  Zonet 5600 PCMCIA modem to work
with Ubuntu 8.0.4.

I believe they are still available.
Try looking on  MWAVE.COM.

---

### Post by Drakelet on 2008-06-26
I've ordered a BT Enabler, it came yesterday.  Just awaiting the serial/usb cable.  I hope it's not a stupid software one...

---

### Post by Drakelet on 2008-06-26
This is getting stupid.

[img]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/FFSserialbtenabler.gif[/img]

It does detect the modem.  All the settings are correct (although changing them makes no difference, it doesn't get that far).  Stupid Mode is on.

Goddammit.

---

### Post by bstanley on 2008-06-26
Hi Draklet....


In the  ~/.wvdial.conf  file,  
try changing (via vi) the  dial command of ATM1L3DT,
to say,   ATM1L1DT.  I could not get  gnome-ppp to correctly
change my modem dial strings 

That command works with my Zonet

---

### Post by Drakelet on 2008-06-27
Trying not to sounds stupid, but how?

---

### Post by bstanley on 2008-06-27
Hi Drakelet!

If you are not used to using the 'vi' editor,
try the following:

from the gnome menus:   
       Applications --> Accessories -->  Text Editor

once in the text editor program do:
         File --> Open

then in the Open Files dialog box,  there is an icon that
looks like a piece of paper with a pencil on it,
when you place the mouse pointer on it it will display
"Type a file name".  Click on this Icon and type:  .wvdial.conf  .

I should open up the file for editing.
Look for a string in the file that starts with:
                Dial Command =

Replace the AT command to the right of the screen with
                 ATM1L1DT.
See if that dial string command will work with your modem.

The  M1L1 part of the string says to set the modem volume
at medium levle (L1 part) and turn the modem off once
connection is made (M1 part).

If need be,  try variations like  ATM0L0DT,  ATM1L0DT, etc...

---

### Post by bstanley on 2008-06-27
For clarity (after looking at my miss typing)

the file name to open is exactly:    .wvdial.conf

The string to try is:    ATM1L1DT

No trailing '.' in the file name or command.

Hope this helps....

---

### Post by Drakelet on 2008-06-27
I wasn't sure which bit I needed to change (i.e. Dial Command).  Thanks. :) Will try that soonish.

---

### Post by Drakelet on 2008-06-28
Tried a few different ones, no success.

Ima gonna PM the guy with the BT Enabler from this thread, see if (s)he can help. :)

---

### Post by Drakelet on 2008-07-03
Aaaaaaaaaaaaaaaaaaaaaaanyone?

---

### Post by zoomzoomzoom on 2008-07-03
I've never used the Gnome front end for wvdial.  When using wvdial, I use following info in my wvdial.conf file:

[Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
Carrier Check = yes
Dial Command = ATDT
Phone = <isp-phone-number>
Username = <username>
Password = <password>

With my individual isp info inserted of coursse.  Some modems especially older modems may need a different initial initialization string instead of ATZ.  Usually either ATZ or AT&F2 will initialize most modems, but I had an old Zoltex serial modem that needed its own special intitialization string.  Took bit searching on internet to find it.  

If you really want easy just install KPPP, thats by far easiest way to set up dialup connection in linux.  I even gave up on wvdial for setting up connection with my cell phone connected to my laptop with usb data cable and installed Kppp.  I just couldnt get right settings under wvdial.  Worked right away with Kppp.  Go figure.

---

### Post by zoomzoomzoom on 2008-07-03
Ok, this sounds goofy but I remember little quirk using serial to usb cable with serial modem.  Do this, create a simlink /dev/modem to /dev/ttyUSB0 or whatever node you are using.  Then use /dev/modem in your configuration file as the port for your modem. May not help, but somewhere I remember some dialer needing this indirect method.

Heck, I'll take my laptop upstairs and try it directly and post back.  Cant remember now if problem was with wvdial or gkdial.

---

### Post by zoomzoomzoom on 2008-07-03
Ok, just tried it and worked fine with wvdial set to either /dev/ttyUSB0 or /dev/modem.  Problem must have been back with Gkdial that Puppy linux used to use.

But go look at this:  [http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00728.html](http://linmodems.technion.ac.il/bigarch/archive-eighth/msg00728.html)

Person with very simular problem to yours though no answers found.  For that person modem worked correctly connected through serial port but gave error you are getting when using pl2303 serial to usb adapter cable.  You dont have a serial port to test it with serial cable, but just betcha yours is same problem.  No idea why since I have no problems with very simular setup.

I of course dont have Ubuntu 8.04 as I still havent had access to broadband to download it.  Do you have any other linux live cds just to experiment without going through an install?

---

### Post by Drakelet on 2008-07-04
Thanks zoomzoomzoom.  I'll do some research into that and try some stuff.  I'll start by trying different Inits and Dial Commands (the message suggests it's a problem with the latter).

---

### Post by Raval on 2008-07-04
> **zoomzoomzoom said:**
> Ok, this sounds goofy but I remember little quirk using serial to usb cable with serial modem.  Do this, create a simlink /dev/modem to /dev/ttyUSB0 or whatever node you are using.  Then use /dev/modem in your configuration file as the port for your modem. May not help, but somewhere I remember some dialer needing this indirect method.


My [SIZE=1][/SIZE]**** Actiontec EX560LKU needed that.

dmesg | grep USB" I was able to locate the modem at USB0

ln -sf /dev/ttyUSB0 /dev/modem

[http://ubuntuforums.org/showthread.php?t=312490](http://ubuntuforums.org/showthread.php?t=312490)

---

### Post by Raval on 2008-07-04
I just took my Actiontec EX560LKU out of the drawer and connected it to my PC with Ubuntu 8.04 load via the USB port (has a serial one too) slected USB modem under modem type in Gnome PPP and then clicked auto detect.

The modem was auto detected and I'm writing this post via the modem.

So this modem is confrimed to work with Ubuntu with no drivers.

It is not a true serial modem. They sell on Ebay for about $15 brand new. 

This is a great external modem for a laptop.

---

### Post by Raval on 2008-07-04
I found the true serial modem version on eBay.  EX560LKA (EX560LKU usb version) [http://cgi.ebay.com/Actiontec-External-56k-Modem-AOL-EX560LKA-v92-BRAND-NEW_W0QQitemZ180259268921QQihZ008QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ShippingPayment](http://cgi.ebay.com/Actiontec-External-56k-Modem-AOL-EX560LKA-v92-BRAND-NEW_W0QQitemZ180259268921QQihZ008QQcategoryZ14920QQssPageNameZWDVWQQrdZ1QQcmdZViewItem#ShippingPayment)

---

### Post by starcannon on 2008-07-04
Since the one the OP originally listed has a serial connector, while its not guaranteed, its likely that its a hardware modem, if it is (google will likely help solve the question) then it will work.

Best bet for linux, avoid winmodems(soft-modems), use hardware modems(hard-modems).

---

### Post by Drakelet on 2008-07-05
Someone in this thread has the same one and said it works.

GnomePPP auto-detects the modem, meaning it, well, is a modem that works.

The problem I think is the Dial Command.

---

### Post by Raval on 2008-07-05
> **Drakelet said:**
> Someone in this thread has the same one and said it works.

GnomePPP auto-detects the modem, meaning it, well, is a modem that works.

The problem I think is the Dial Command.

what dial command? 

BTW I'm still connected with the same modem, giving it some use before I eventually put it in the drawer.

---

### Post by Drakelet on 2008-07-05
The "Dial Command" part in wvdial.conf.

---

### Post by Raval on 2008-07-05
> **Drakelet said:**
> The "Dial Command" part in wvdial.conf.


If you're using GnomePPP you don't have to do that.

---

### Post by Drakelet on 2008-07-06
> **Raval said:**
> If you're using GnomePPP you don't have to do that.
You sure?  I thought GnomePPP still used wvdial (it was just a front)?

Well, either way, it says my Dial Command is wrong and I can't see that setting in GnomePPP.  The same problem comes up when I do wvdial in terminal.

---

### Post by Raval on 2008-07-06
> **Drakelet said:**
> You sure?  I thought GnomePPP still used wvdial (it was just a front)?

Well, either way, it says my Dial Command is wrong and I can't see that setting in GnomePPP.  The same problem comes up when I do wvdial in terminal.

When you use GnomePPP you don't have to manually edit wvdial. 

You sure it's GnomePPP your using or the default Network manager? 

You have to download and install Gnomeppp applications->add/remove

---

### Post by jessejazza on 2008-07-06
> **Drakelet said:**
> This is getting stupid.

[img]http://i268.photobucket.com/albums/jj23/JGibbins92/Ubuntu/FFSserialbtenabler.gif[/img]

It does detect the modem.  All the settings are correct (although changing them makes no difference, it doesn't get that far).  Stupid Mode is on.

Goddammit.

Drakelet: sorry to see you still appear to have problems. Looks to me if your   Setup isn't correct. Look in setup
Setup~>Modem device~>/dev/ttys0 (that's mine)

james
I bought two of these and both work ok!

---

### Post by Drakelet on 2008-07-07
> **Raval said:**
> When you use GnomePPP you don't have to manually edit wvdial. 

You sure it's GnomePPP your using or the default Network manager? 

You have to download and install Gnomeppp applications->add/remove
Yep, it's GnomePPP.  I'm not *that* stupid. :p

> **jessejazza said:**
> Drakelet: sorry to see you still appear to have problems. Looks to me if your   Setup isn't correct. Look in setup
Setup~>Modem device~>/dev/ttys0 (that's mine)
OK, I'll try that.  ttyUSB0 was auto-detected though so I assumed it was correct.

---

### Post by zoomzoomzoom on 2008-07-10
Try installing and using Kppp. Yes with serial to usb adapter cable you should be using /dev/ttyUSB0 By way the dial command is universal with dialup modems, yes even under windows.  

And look at that link I posted earlier.  Some people apparently have trouble with dial command when using the usb adapters.  I had no problems but then I am not using 8.04.  Just havent managed to get to library with my laptop and use their free wifi to download it.  

Oh by way here is maybe some info you can experiment with:

> Command modifiers define additional parameters to the modem that instruct the modem to perform certain functions automatically when dialing a phone number. They are only valid when they are contained in a dial string (that follows the D command). The commands that are used to accomplish this task are called dial modifiers, and are placed in the dial string prior to issuing the command.

Syntax: ATD{dial modifier} 1234567 [Enter]

Basic dial modifiers are:
P -- Pulse dialing. Also known as rotary dialing, this dial modifier follows the D command and precedes the telephone number to tell the modem to dial the number using pulse service. 
T -- Tone dialing. This modifier selects the tone method of dialing using DTMF tones. Note: Tone and pulse dialing can also be combined in a dial command line when both dialing methods are required. 
; -- Resume command mode after dialing. If you need to dial a number that is too long to be contained in the command buffer (45 characters for the D command), use the (;) modifier to separate the dial string into multiple dial commands. All but the last command must be end with the ; modifier. 
, -- Pause While Dialing. The comma (,) dial modifier causes the modem to pause while dialing. The modem will pause the number of seconds specified in S-Register S8 and then continue dialing. If a pause time longer than the value in S-Register S8, it can be increased by either inserting more than one (,) in the dial command line or changing the value of S-Register S8. In the following example, the command accesses the outside (public) telephone line with the 9 dial modifier. Because the comma (,) dial modifier is present, the modem delays before dialing the telephone number 5551212. Ex: ATD 9, 5551212 [Enter] 
! -- Using the Hook Flash. The exclamation mark (!) dial modifier causes the modem to go on-hook (hang up) for one-half second and is equivalent to holding down the switch-hook on your telephone for one-half second. This feature is useful when transferring calls. 
W -- Wait for a Subsequent Dial Tone. The W dial modifier causes a modem to wait for an additional dial tone before dialing the numbers that follow the W. The length of time the modem waits depends on the value in S-Register S7. The modem can be instructed to dial through PBXs (Private Branch Exchanges) or long-distance calling services that require delays during dialing. This can be done with the W command to wait for a secondary dial tone or with a comma (,) command to pause for a fixed time and then dial. Ex: ATDT 9 W 1 2155551212 [Enter] 

---

### Post by Drakelet on 2008-07-10
Uh... in English? :p  My default one was ATM1L3DT, what does that mean?  What is the 1234567?

I was wondering if maybe it was the converter - I can't get it working on Windows even.  However, the modem is auto-detected as USB0, suggesting that it does work.  I don't see why it shouldn't to be honest.

---

### Post by Drakelet on 2008-07-12
Tried more things.

sudo wvdialconf finds the modem and sets everything up.  But adding in my phone, username and password and I get the same error: "Invalid dial command" for ATDT[phone number].
The Inits work, which are ATZ and... a really long fancy one.

I tried "echo ATDT0001112222 > /dev/ttyUSB0" and nothing happened.

:(

I might make a separate Invalid Dial Command thread.

EDIT: Maybe it's my phone number that is the problem?  I'll try and contact my provider sometime.

---

### Post by zoomzoomzoom on 2008-07-14
> **Drakelet said:**
> Uh... in English? :p  My default one was ATM1L3DT, what does that mean?  What is the 1234567?

I was wondering if maybe it was the converter - I can't get it working on Windows even.  However, the modem is auto-detected as USB0, suggesting that it does work.  I don't see why it shouldn't to be honest.

Assuming you have dial tone phone service, use ATDT<yourphonenumber>  The 1234567 represents a generic telephone number, substitute your own.  I am not paying enough attention, M1 and L3 are not options in the ATDT dial command.  Thats why you are getting error.  As I posted above the options are either ATDT or ATDP and you can add ; , ! M   nothing else.  The M1 and L3 belong up in the ATZ line I believe but for now dont use them, just try to get it to dial, dont worry about how loud it is.  Try editing the /etc/wvdial.conf file and just using ATDT08089933315 if thats your actual phone number and you are using dial tone phone system.  Leave out the M1 and L3.

---

### Post by zoomzoomzoom on 2008-07-14
Your /etc/wvdial.conf file should look simular to this:

> [Dialer Defaults]
Modem = /dev/modem
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 S11=55 +FCLASS=0
Carrier Check = yes
Dial Command = ATDT
Phone = <isp-phone-number>
Username = <username>
Password = <password>

See the dial command line, just plain "Dial Command = ATDT"  Wvdial adds your phone number to that.  The M1 and L3 commands would go up in the Init1 line so something like ATZ&M1&L3  but I wouldnt bother with that.  Keep it simple to just get it working, then experiment with modem volume using modem initialization string if you desire.

---

### Post by zoomzoomzoom on 2008-07-14
And you can just run wvdial directly by opening a terminal and typing wvdial instead of using Gnome front end for wvdial if the Gnome thing is confusing.  Both ways are going to use same /etc/wvdial.conf file for the settings.  The front end is just supposed to make things simpler for those not used to editing configuration files directly.

If using terminal, just type wvdial to connect and close terminal window to stop the connection.  I personally never saw the point in running front end gui for wvdial but each to their own.  If wvdial wont do it for you then install Kppp.  It does offer more settings and very friendly for those used to gui interface.  As I mentioned earlier, I had to use Kppp when connecting to internet with data cable from my cell phone.  It offered settings not available in wvdial that I needed to set.

---

### Post by Drakelet on 2008-07-14
ATDT (by itself) doesn't work.  That's the problem. :(  My wvdial is identical to that (except a lower baud, wvdialconf auto detected lower, think I've tried higher though).

So in other words, the error is either in the Dial Command (ATDT), which it shouldn't be, or the telephone number, which I didn't think it would be.
I'll try telephoning my ISP sometime and seeing if they can help.

Thanks again everyone for all your help!

---

### Post by earlycj5 on 2008-07-25
> **Drakelet said:**
> Does anyone know if the 3095 mini modem works?
[img]http://img.shoppydoo.com/uk/tp_products/26/2326592.jpg[/img][img]http://www.provantage.com/ZOOA01F.GIF[/img]

Please help.

Yes, I made this entry in the linuxquestions.org hardware compatibility list.  [http://www.linuxquestions.org/hcl/showproduct.php/product/4166/cat/500](http://www.linuxquestions.org/hcl/showproduct.php/product/4166/cat/500)

Now I need to set it up with my Unbuntu installation.

---

### Post by candtalan on 2008-08-02
drakelet: I have just had to use a 56k external serial connected dial up modem at my inlaws, and I have sympathy with you.

however I seem to have found success.

1)  any serial connected, that is, external modem (hayes compatable) will work. not usb external, since usb connected modems will probably need drivers i think.

2)   using ubuntu 8.04.1 as follows. note that the 8.04.1 has added updates so the straight 8.04 non updated with no internet connection may have different functionality.

3) i noted that pppconfig and wvdial were both installed by default by looking in synaptic package manager

4) i used pppconfig to set up the configuration, choosing pap type, this was no good for my isp (waitrose) so i later changed it to chap again using pppconfig.

5) the dialling was done with wvdial and i had to manually edit and insert text into the wvdial file as required first

6) things did not work even then until i made a link (symlink) between the 
/dev/ttyS1 and /dev/modem

sudo ln -s /dev/ttyS1 /dev/modem
(i think, please check?)


note my particular serial connection was seen in pppconfig as being /dev/ttyS1
also note the upper case s.

7) i was using a terminal to run pppconfig and wvdial, also to edit the wvdial fil and also to create the symlink. i cannot check details just now, hopefully i can check details here later. (different machine).


hth

---

### Post by Drakelet on 2008-08-02
The only thing of that I didn't try was the symlink.  Please can you check the code (I'm not a code monkey :)), because if so it MAY work (not likely though...).  EDIT: Haven't tried 8.04.1 actually.

---

### Post by ModelM on 2008-08-02
I'm coming into this thread very late, so I may be covering old ground here. If ATDT is rejected as an invalid dial command, you might try ATDP for pulse dialing instead.

---

### Post by candtalan on 2008-08-02
> **Drakelet said:**
> The only thing of that I didn't try was the symlink.  Please can you check the code (I'm not a code monkey :)), because if so it MAY work (not likely though...).  EDIT: Haven't tried 8.04.1 actually.


LOL nor am i a code mokey :-)
mine did not work at all without the symlink because the package i think wvdial, not sure, kept giving errors suggesting it did not find /dev/modem
so i knew from the error messages that it could not find /dev/modem even after pppconfig had been configured and had offered the particular serial port ttyS1 (on your machine it might be different, say ttyS0  ??)

I can confirm that the creation of the symlink needs (in my case)
sudo ln -s /dev/ttyS1 /dev/modem

this symlink does not seem to stick as permanent, i had to make it again this morning afresh, still it works and i am learning.....

other code items i needed were, in approximate sequence

sudo pppconfig
(then do the configuration)

sudo gedit /etc/wvdial.conf
(add in the correct text information)

sudo wvdial
dials up, hooray!

hope that helps, you certainly deserve it

---

### Post by Drakelet on 2008-08-03
Hmm, well my modem WAS detected.  Don't think it is the symlink then.  ********.

Maybe it's 8.04.1 that fixed it?  What were the updates concerning networking/dial up between the first release and the current?

---

### Post by candtalan on 2008-08-05
> **Drakelet said:**
> Hmm, well my modem WAS detected.  Don't think it is the symlink then.  ********.

Maybe it's 8.04.1 that fixed it?  What were the updates concerning networking/dial up between the first release and the current?

I am not sure it is a modem detection problem though (I am no expert anyway) but whether the /dev/modem usefully points to your detected modem. 

As I understand it, that is the benefit of the symlink.

My modem was detected as being on ttyS1 for example, but this was unrelated to /dev/modem. The symlink apparently sorted that.

If you have not already tried it, consider trying  the symlink with your appropriate details anyway.

8.04.1 - there are a lot of updates included and if 8.04 does not work I would, not hesitate to go with 8.04.1 anyway, particularly with internet access problems. Even with dialup connected, the updates will be heavy using dialup.

---

### Post by Drakelet on 2008-08-07
> **candtalan said:**
> I am not sure it is a modem detection problem though (I am no expert anyway) but whether the /dev/modem usefully points to your detected modem. 

As I understand it, that is the benefit of the symlink.

My modem was detected as being on ttyS1 for example, but this was unrelated to /dev/modem. The symlink apparently sorted that.

If you have not already tried it, consider trying  the symlink with your appropriate details anyway.
Oh, OK.  I might do that (if I can be bothered to load/install Ubuntu AGAIN!).

> **candtalan said:**
> 8.04.1 - there are a lot of updates included and if 8.04 does not work I would, not hesitate to go with 8.04.1 anyway, particularly with internet access problems. Even with dialup connected, the updates will be heavy using dialup.
That's why I have a mate.  Downloaded it yesterday, took him like 5 mins for the 700MB.  I hate him.

---

