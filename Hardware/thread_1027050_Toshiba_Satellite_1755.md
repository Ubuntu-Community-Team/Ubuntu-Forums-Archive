---
title: "Toshiba Satellite 1755"
date: 2008-12-31
forum: Hardware
---

### Post by EMCGFX on 2008-12-31
Hi I have Toshiba Satellite 1755 Laptop with the following specs listed bellow. I can't seem to install Xubuntu 8.10 Final on it, I get some kind of error. Is there any other version or linux distro that will work fast with my laptop? It had Windows ME on it, but its very slow. I want to try linux on it. Please help, thank you.

[URL="http://www.csd.toshiba.com/cgi-bin/tais/support/jsp/modelContent.jsp?ct=DL&os=&category=&moid=1073792274&rpn=PS170U&modelFilter=1755&selCategory=3&selFamily=1073768663&selModel=1073792274|PS170U"]
Specs Source[/URL]

Intel Celeron 700MHz Processor
64MB SDRAM, expandable to 192MB
10GB Hard Drive
24X max speed CD-ROM, 8x max speed DVD-ROM
13.3" TFT active-matrix display
4MB SGRAM external video memory
Built-in 3.5", 1.44MB Floppy drive
Crystal 4281 PCI bus Sound Chip
Integrated V.90/56K modem (Mars 3, Lucent)

Also, I have the following wireless cardbus adapter, which I can't seem to get it working with windows. D-Link AirPlus 2.4GHz DWL-650+

If you have simular laptop your self, or know anything about laptops please reply. Any suggestions and comments are welcome. Thank you.

---

### Post by EMCGFX on 2008-12-31
I've done some digging and one site right here > [http://www.geocities.com/linopak/](http://www.geocities.com/linopak/) recommands to use Red Hat 8.0 ;-) It even gives nice guide for each hardware part. Will defently try that. Any other suggestions besides Red Hat 8.0 ?? Can any one recommend any working older version of Xubuntu for this laptop?

Edit: I've just ordered another 128mb ram for it, so cheap lol $11 bucks ;-) Now will have 192mb I hope it will be enough to install Xubuntu 8.10 or at least 7.10 now =)

---

### Post by WiFlag on 2009-01-10
How ironic. I have the same laptop and I just dissected it to make a kitchen computer. I was looking up the video specs while reinstalling Xubuntu when I came across this post.

I run Xubuntu on it, but I had to use the alt CD to reliably get the install to run (I also have mine upgraded to 192M, but it's just not enough for the live CD install). I would also recommend burning the ISO for the alt CD as slow as your burner will let you - the DVD drive on mine is a little flaky, and if you're seeing install problems, maybe yours is too.

I also have the same pcmcia card (are you my twin brother or something?) and I will tell you that it is a beast to get working. It stopped being autodetected on install sometime back around 7+ and I don't think it's come back yet. If you have anything else to use, I would recommend you do so. That is not an option for me, however, so once I figure it out I'll post back here with how I did it. I have some good leads.

My final caveat is that while I "run" Xubuntu, I only use it for surfing the web, so if you're trying to get more than that out of it, your mileage may vary. If you decide to install, or if you try something else, let me know. I'd be happy to run another distro, but this is for my wife and I'm trying to keep it familiar for her - and alternatives that looked promising like U-lite and fluxbuntu don't appear ready for full operation yet. (Fluxbuntu looked very nice, only 64M ram needed, but they haven't finished 8.10 yet).

---

### Post by EMCGFX on 2009-01-10
Hi WiFlag =)

> How ironic. I have the same laptop and I just dissected it to make a kitchen computer. I was looking up the video specs while reinstalling Xubuntu when I came across this post.

What do you mean you dissected it to make a kitchen computer? Did you take it appart, like screen, keyboard and the body of the laptop...

> I run Xubuntu on it, but I had to use the alt CD to reliably get the install to run (I also have mine upgraded to 192M, but it's just not enough for the live CD install). I would also recommend burning the ISO for the alt CD as slow as your burner will let you - the DVD drive on mine is a little flaky, and if you're seeing install problems, maybe yours is too.

Yes, I've managed to install Xubuntu 8.10 final in graphical mode, ones I've added 128mb of ram to it. It looks like I can take out the 64mb ram in my model and try adding another 128mb stick =) 

Will try it and let you know if it works for me. As for burning dvd with low speed I did not see any problem, so I burned it at max default that cd has. But you are right it spinned the cd like crazy. Ones you wrote that I realized that I should of burned it at 8x speed at least.

> I also have the same pcmcia card (are you my twin brother or something?) and I will tell you that it is a beast to get working. It stopped being autodetected on install sometime back around 7+ and I don't think it's come back yet. If you have anything else to use, I would recommend you do so. That is not an option for me, however, so once I figure it out I'll post back here with how I did it. I have some good leads.

LOL Yeah, I'm your twin brother. Did you not know ? I'm your twin brother from another mother =) I could not install my card yet. I use **3Com Megahertz 10/100 Network X-Jack PCMCIA 3CXFE575CT** on mine is like $10 on ebay. Works very well, but of course its not wireless... So I would need wireless card some day.

> My final caveat is that while I "run" Xubuntu, I only use it for surfing the web, so if you're trying to get more than that out of it, your mileage may vary. If you decide to install, or if you try something else, let me know. I'd be happy to run another distro, but this is for my wife and I'm trying to keep it familiar for her - and alternatives that looked promising like U-lite and fluxbuntu don't appear ready for full operation yet. (Fluxbuntu looked very nice, only 64M ram needed, but they haven't finished 8.10 yet).

Ones I've installed Xubuntu I've noticed that its very slow on this laptop, I've checked memory and it runs on 128mb its very heavy for this. I've also seen the Fluxbuntu but its very old version and the new one have not been released yet, and I have no idea when it will be released. 

So that leaves me with two other options. Install just base of xubuntu without gui and then install flux on it or use ubuntu server edition install that stop/uninstall all the servers and install flux gui. The second one is most likely what I will do.

There is also Arch Linux, which can be installed without gui and the add flux. But I am not familiar with arch linux that good. I've only installed ones and it was without gui.

Will update this post ones I get my laptop working as fast as I can with bare minimal resources. Sorry for any spelling, I try =))

---

### Post by oilchangeguy on 2009-01-10
you can alos try puppy linux, or damn small linux.

---

### Post by EMCGFX on 2009-01-11
> you can alos try puppy linux, or damn small linux.

Yes, I've tried Puppy Linux and DSL before. I did not like it because it runs from cd. I think puppy linux can be installed on hdd. I don't know about DSL.

I've tried installing Ubuntu Server 8.10 + Fluxbox without any success yet. I had some kind of "xserver can not start" error, even do I've installed it. I've followed this post > [http://ubuntuforums.org/showthread.php?t=233278](http://ubuntuforums.org/showthread.php?t=233278)

Right now I am trying to install Fedora 10 on it, with LXDE, XFCE and GNOME. Will test it and see how it works. :-\"

---

### Post by WiFlag on 2009-01-13
> **EMCGFX said:**
> What do you mean you dissected it to make a kitchen computer? Did you take it appart, like screen, keyboard and the body of the laptop...

Yeah I ripped it apart. I plan to put a wood frame around it and hang it in the kitchen for my wife to use. (wireless keyboard and mouse so they can be out of the way).

I haven't had much time to work on it thanks to deadlines at work, but the PCMCIA card has been giving me a lot of grief. Considering it's only 802.11b I really should just upgrade, but I'm cheap so I'll be at least giving it a shot (once work winds down a bit next week).

I've toyed with the idea of just doing a debian install to ease up the RAM, and I may resort back to that yet. Ubuntu is just so damn easy to use though, I'd hate to give my wife a debain box...
I'll probably just try to tweak Xubuntu to get it down a little more in RAM. You raise an interesting point on the RAM, I didn't even think about tossing the 64M and putting another 128M stick in...

---

### Post by EMCGFX on 2009-01-14
Nice, I did not think of taking laptop apart lol I won't take it apart as I need it like it is. But I will add another 128mb ram and a bigger hard drive maybe 40gb, if I find a cheap one on ebay. The memory that I've used is [eBay Link]("http://cgi.ebay.com/128MB-SDRAM-SODIM-100Mhz-PC-100-Kingston-KTT-SO100-128_W0QQitemZ120354959390QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item120354959390&_trksid=p3286.c0.m14&_trkparms=66%3A2|65%3A15|39%3A1|240%3A1318") its cheap with free shipping and works great =) I will buy another from the same source.

At first I thought that my 64mb ram is build in, like on some models you can't take it off (I know its stupid). But by looking at it you can take it away and put in another 128mb stick =) If the systems detects the memory successfully then I will have 256mb ram =) that would be more then enough to run at least xubuntu. Which is fine by me on this laptop.

As for the WiFi card, I did not have any luck yet. As of right now I am running "Damn Small Linux" on it. Which works very well and uses under 30mb ram, I have plenty ram left to use for other applications. I've noticed that firefox takes massive amounts of ram. Since Damn Small Linux is based on Knoppix and Knoppix based on Debian you can easily use deb's and install what you need =) So if you havent tried "Damn Small Linux" yet, I suggest you do. It works very well.

Have fun with your laptop, and let me know if you figure out something with WiFi card. I will do the same =))

---

### Post by Dreaduk on 2009-01-14
Guys,

for what my tuppence worth is worth, I have a Toshiba Satellite S1800-712.....a complete pig to get anything other than XP running on it (assuming you have the correct drivers) and I have tried to install Ubuntu on it with no success, it wont detect the correct screen resoloution and the Belkin PC wireless card is just not worth the trouble trying to get up and running.

I did, however, have a great deal of success with Mandriva Linux, popped the disk in and booted from it and hey presto everything except the wireless card was working properly. The wireless card was a doddle to install as well as Mandrake seems to have an automatic wrapper that takes all the command line nonsense out of it.

Tragically I found Mandriva very clunky compared to Ubuntu and when it eventually crashed I didn't bother recovering it but re-installed XP. Bizzarely the machine ran far better than with the original XP installation. I just put it down to the original XP installation being bogged down with extranious background stuff running but I did the same thing with a Dell and it ran faster as well. It seems that a Windows formatted disk benefits from a Linux formatting prior to an XP installation.

I don't suppose this will help either of you much but it might give you some ideas.

---

### Post by WiFlag on 2009-01-17
> **EMCGFX said:**
> The memory that I've used is [eBay Link]("http://cgi.ebay.com/128MB-SDRAM-SODIM-100Mhz-PC-100-Kingston-KTT-SO100-128_W0QQitemZ120354959390QQcmdZViewItemQQptZLH_DefaultDomain_0?hash=item120354959390&_trksid=p3286.c0.m14&_trkparms=66%3A2|65%3A15|39%3A1|240%3A1318") its cheap with free shipping and works great =) I will buy another from the same source.

You might be out of luck - recent research I've done seems to suggest that the max ram the mobo can handle is 192M. I'd be very interested to hear if you find differently.

---

### Post by EMCGFX on 2010-04-06
I've installed OpenBSD 4.6 on it now, without GUI. Works very well.

---

### Post by EMCGFX on 2010-04-27
Hey WiFlag, I've managed to install 512MB memory in it. It needs to be PC100 :-) It worked like a charm. This is the memory I used for it > [http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170357094272](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&item=170357094272)  It says PC133, but it supports PC100 too.

---

