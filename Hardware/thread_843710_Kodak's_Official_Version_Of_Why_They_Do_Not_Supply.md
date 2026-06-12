---
title: "Kodak's Official Version Of Why They Do Not Supply Drivers For Linux"
date: 2008-06-28
forum: Hardware
---

### Post by daytonageeks on 2008-06-28
This letter was sent me today after many requests for a straight answer as to why Kodak does not support Linux with drivers for their 5100 AIO printer........

Greetings james ,
 
Thank you for your recent visit to the Kodak Web site and question about Linux drivers for the Kodak EasyShare 5100 All-in-One printer.
 
We are quite concerned over your experience, and are sorry for any inconvenience or frustration this has caused you.  We will do our best to help you.

Thank you for visiting the Kodak web site and your inquiry regarding Kodak support for Linux operating system with Kodak products. Currently there is no support for Kodak products on the Linux OS by Kodak. Our Kodak software engineers are well aware of the Linux operating system. We appreciate your concern for this operating system and interest in enabling Kodak products to work with it.

Kodak continues to follow the Linux Operating system. We noted, as far back as March 30, 1999, that Linux announced support of a Linux-USB driver that only worked with UHCI controllers. Since UHCI controllers represent only a portion of the PC market, Linux-USB was very limited and was very preliminary even six months ago.

We had the same situation in the past with preliminary Microsoft-USB drivers and now version 2 USB as well. Sometimes, the availability of these drivers simply does not match our product release dates. Even after the support is there, as is the case with Microsoft version 1, we still have to update our Kodak web site with the latest driver patches to keep in step with Microsoft-USB patches. In addition, Kodak has worked very closely with the USB IF Working Group on the USB standard participating in numerous USB "Plug Fests" where we test out our hardware and software on a variety of computers with various "chip sets".

In the past, prior to the release of Microsoft Windows 98, Kodak worked intensely with the staff at the Windows Hardware Quality Labs (WHQL) to achieve "Windows Logo". This was no small feat with the USB technology forming the basis of the DVC323 and later products and the Windows 98 operating system. As a result, the DVC323 passed all USB compliance testing with Windows 98. I am not sure that there is such a rigorous test standard for Linux-USB. If not, this has serious implications on our technical support staff and the cost for providing a Linux-USB driver.

We understand the issue with devices based on the CPiA chip set and once again are faced with a problem with Linux-USB support in that isochronous transfer is not yet fully implemented. There is a distinct difference when a company claims "USB support" it does not always mean "full USB support". Kodak relies on full support for UHCI and OHCI host controllers as well as their corresponding USB transfer types. The support for this simply is not there yet.
As Linux-USB becomes fully implemented and released with the Linux OS, Kodak may investigate the technical feasibility of developing Linux-USB drivers for future products. I am confident that our technical teams would be able to provide support once Kodak analyzed the business case for such support.

We are glad to be of service and are here for you if you need us in the future. Please reply to us "with history" if you need to respond to this email.

For more information, you can visit the FAQ section in our website at [www.kodak.com/go/aiosupport](www.kodak.com/go/aiosupport). You will find helpful tips and upgrades.

Best Regards,

Nancy R
Kodak Information and Technical Support
[http://www.kodak.com/go/aio](http://www.kodak.com/go/aio)

Now, with this in hand, will someone please tell me if this makes sense, or is doubletalk?
Thanks and Blessings,
                      Daytonageeks (Jim)

---

### Post by ciascuno on 2008-08-04
Actually, I'd just like to bump this as I'd be very interested to hear the opinion of someone with a better understanding of kernel USB support than I have - how valid are their concerns?

Thanks to daytonageeks for successfully obtaining this detailed response!

---

### Post by greenstar on 2008-08-12
Unfortunately, I don't have the answer, but I am interested to see if anyone else does.

Great job in obtaining a response, daytonageeks. Persistence pays off.

Greenstar

---

### Post by ciascuno on 2008-08-12
After a post onto the linux-usb list, pointing to your message and providing some excerpts, a couple of the devs very helpfully commented - thanks to balbi and greg k-h particularly: [http://thread.gmane.org/gmane.linux.usb.general/8221](http://thread.gmane.org/gmane.linux.usb.general/8221)

The general consensus seems to be that these suggestions are rather outdated and Kodak hardware has no difficulty with the USB part of the process on Linux. This seems to be a frequently trotted-out reply (signed by different support staff) - see, for example, the following:
 [http://osdir.com/ml/multimedia.gphoto.user/2007-02/msg00003.html](http://osdir.com/ml/multimedia.gphoto.user/2007-02/msg00003.html)
 [http://ubuntuforums.org/archive/index.php/t-501652.html](http://ubuntuforums.org/archive/index.php/t-501652.html)
 [http://jaredrobinson.com/blog/?p=105](http://jaredrobinson.com/blog/?p=105)
 [http://castor.igrin.co.nz/pipermail/northlinux/2006/000039.html](http://castor.igrin.co.nz/pipermail/northlinux/2006/000039.html)
 [http://linux.derkeiler.com/Newsgroups/linux.redhat/2004-03/0104.html](http://linux.derkeiler.com/Newsgroups/linux.redhat/2004-03/0104.html)
- the earliest of which is dated March 2004 and I wouldn't be surprised if there are copies even before that.

---

### Post by greenstar on 2008-09-18
If you still need help getting Ubuntu to recognize your camera, try the suggestion given [here]("http://ubuntuforums.org/showpost.php?p=4814036&postcount=4"). If that doesn't work, get a USB card reader for your memory card and upload pictures that way. You can get one for under $10.

HTH.
Greenstar

---

### Post by Yoshokatana on 2008-11-14
Hey, I'd like to weigh in on this.

I'm a tech support guy at Kodak, and I'm working in the printers division. I was wondering about Kodak's stance on linux after reading that letter, and talked to my supervisor. Well, now he and I are working to get Kodak to be more linux-friendly, both internally (using SugarDRM and Zimbra rather than LotusNotes) and externally.

Awhile ago, I read a blog post by one of our dev guys out in San Diego, that he was working on linux drivers. My supervisor knows him personally, so he'll try to get in touch and hopefully see what's happening with them. We know that the drivers have been working since March, so they're hopefully doing internal testing right now. I think the dev team that works on the OSX driver are contributing the relevent *nix-friendly code.

I'll post whenever the dev guy gets back to me. Hopefully they'll release the beta code if I ask.

---

### Post by jdzitro on 2008-11-14
THANKS Yohokatana! Looking forward to it.

---

### Post by jakie18064 on 2008-11-15
I am glad to hear that Kodak is working on a driver to use with Ubuntu. 

I was just on the [[COLOR="Blue"]www.winehq.org[/COLOR]]("http://www.winehq.org") site to see if there was a way to use the printer with Ubuntu and Wine. No such luck.:sad:

I have one PC that is capable of booting to XP or Ubuntu. There are two reasons that I still have XP on a PC. One is the Kodak 5300 printer and the other is work. I need to be using XP or Vista as my home operating system so I can remote into my desktop PC.

If Kodak provides a driver for the printer, I'll just forgot about logging into my work PC from home. :) Who needs to check up on work when they are home anyway?

---

### Post by mgmiller on 2008-12-10
```
I need to be using XP or Vista as my home operating system so I can remote into my desktop PC.
```

I have been remote desk-toping into windows for the last few years without any problems.

Applictions > Internet > Terminal Server Client

To connect to a WinXP pro box that is running its standard remote desktop, configure the one in Ubuntu as follows:

GENERAL TAB:
Computer: you can use the ip address or if it has an assigned domain name, you could use that.  Just put in the number, no www or anything.  Same for the domain name, you would enter foo.com, not [www.foo.com](www.foo.com)

Protocol:  RDPv5

User Name:  Whatever the user name you use on the windows machine you want to log onto is.

You can leave the rest of the fields blank.


DISPLAY TAB:

I had the best results with "Use specified screen size"  I have mine set to 1280x960, but make sure its a size that's smaller than the resolution of your Ubuntu machine.

Colors:
Use specified color depth....High Color (16 bit)


LOCAL RESOURCES TAB:

The only one that's important here is the Keyboard.  Make sure it is for your keyboard, mine is set to "en-us".

PROGRAMS TAB:

You don't have to set anything here


PERFORMANCE TAB:

This can also be left unchanged, although "Enable bitmap caching" seems to speed things up a bit for me.


That's it, just click connect and you should see your windows logon screen with the user name you entered in the first tab.  Just type in the appropriate password and away you go.


Exiting the session is the same as from a windows RDP session.  Click Start and then Disconnect.

---

### Post by jaypmcwilliams on 2009-01-04
In response to daytonageeks letter from kodak- It is TRULY double talk explanation of why they DO NOT want to work with LINUX. After deep research, we've found that the LINUX kernel DOES in fact recognize the printer hardware & the protocols needed to communicate with it. However, they said it themselves, *"MICROSOFT WINDOWS"*. They have an EXTENSIVE contract for windoze licensing but Kodak wanted & needed to keep a corner in the market so they went with a design that would specifically PREVENT development, by others, trying to circumvent paying for Kodak. Kodak actually had issues like Microsoft, "OURS ONLY & PAY FOR OURS OR YOU DON'T EXIST" theory. Texas Instruments did the EXACT same think with there All-in-one media card readers. Devolopers convinced TI to open up. Yet still fight. We have notified Kodak of there yearly lose of MILLIONS from the LINUX community. ATI learned from it's mistakes & now AMD holds them. WOW! now ATI's are wonderful. We are going to try a Kodak ESP series All-in-One & if it fails, so will Kodak sales! We will keep you posted on this. Thank You, Jay

---

### Post by jaypmcwilliams on 2009-01-05
> **jaypmcwilliams said:**
> In response to daytonageeks letter from kodak- It is TRULY double talk explanation of why they DO NOT want to work with LINUX. After deep research, we've found that the LINUX kernel DOES in fact recognize the printer hardware & the protocols needed to communicate with it. However, they said it themselves, *"MICROSOFT WINDOWS"*. They have an EXTENSIVE contract for windoze licensing but Kodak wanted & needed to keep a corner in the market so they went with a design that would specifically PREVENT development, by others, trying to circumvent paying for Kodak. Kodak actually had issues like Microsoft, "OURS ONLY & PAY FOR OURS OR YOU DON'T EXIST" theory. Texas Instruments did the EXACT same think with there All-in-one media card readers. Devolopers convinced TI to open up. Yet still fight. We have notified Kodak of there yearly lose of MILLIONS from the LINUX community. ATI learned from it's mistakes & now AMD holds them. WOW! now ATI's are wonderful. We are going to try a Kodak ESP series All-in-One & if it fails, so will Kodak sales! We will keep you posted on this. Thank You, Jay



OK. We contacted Kodak about this & we got the same ALL around Double Talk AGAIN. With the introduction of Kodaks' NEW line Of All-In-Ones's, there is NO WAY they could not have see this market! Here's the response we got;  


[I]Greetings Jay ,

 

Thank you for visiting the Kodak web site and your inquiry regarding Kodak support for Linux operating system with Kodak products.

 

Currently there is no support for Kodak products on the Linux OS by Kodak. Our Kodak software engineers are well aware of the Linux operating system. We appreciate your concern for this operating system and interest in enabling Kodak products to work with it.


We are glad to be of service and are here for you if you need us in the future. If you do reply, please be sure to include any previous e-mail so we may assist you better.

Regards,

Eric H.

Kodak Information and Technical Support

[http://www.kodak.com/go/aio](http://www.kodak.com/go/aio)[/I]



This is the SAME response they have given for the past 5 years pertaining to ANY of there equipment. It seems Kodak is acting like the Microsoft of the new millennium. END

---

### Post by Maheriano on 2009-01-05
Wow. Just lost respect for Kodak.

---

### Post by Yoshokatana on 2009-01-05
Hey, I'm still following the thread.

The dev guy hasn't responded, and none of my contacts know anything about this. I know we do have linux drivers internally, and I'm actively trying to get them released.

I'd give it about a month more. I'll see what I can do, but if I can't get the drivers released, then I'm quitting. The problem is, Kodak doesn't know what it's doing. They barely know about linux, and I'm having to guide them through their support options.

I'll check back when there are responses, or if anything happens. Let's all hope for the best.

---

### Post by Dfairlite on 2009-01-11
I really hope kodak releases these drivers soooooon!!! my vista partition will no longer boot! so if not its out the window with the kodak and in with a brother!

---

### Post by Pipps on 2009-01-11
Another Kodak ESP3 owner here - amazed that my new printer doesn't work in Ubuntu - and hoping that something will happen sometime very soon to allow me to use this basic piece of hardware with one of the most popular operating systems in the world!

May I join the queue of those all waiting with bated breath?

---

### Post by electrogeist on 2009-01-11
because they were too lazy / cheap to support POSTSCRIPT

---

### Post by Andre-D on 2009-01-16
FYI: It's about one year ago that I stopped buying hardware that does not have Linux drivers, even hardware for use in windows-enviroment @work.

I simply do not support hardware manufacturers that do not support opensource.

---

### Post by Pipps on 2009-01-17
I have returned the Kodak ESP3.

I cannot have any respect for a so-called 'manufacturer' who does not support linux.

Kodak are a joke. A sad joke.

---

### Post by PoopLoops on 2009-01-19
Gah, this sucks.  I am just now playing around with my Ubuntu partition after leaving it for the past few months, and in that time getting a new printer (ESP3).  I knew it was a POS right out of the box, but I figured whatever, as long as it prints.  Yeah.  No more Kodak for me and I suspect I will have to buy a new printer shortly.

---

### Post by Yoshokatana on 2009-01-19
Well, I suppose it has been a month.

Because of Kodak's inaction and obtuseness in the face of both external and internal inquiries for linux support, I guess we can reasonably say...

**It is Kodak's official position that it doesn't, and will never, adequately support Linux or Open Source.**

Because of this mind-numbing move on Kodak's part, I have left the company. I recommend any hacker or user to NEVER use Kodak hardware, as it is effectively obsolete. When a company shows such a blatant disregard for the realities of the tech community, it loses all credibility.

Goodbye, Kodak. Requiescat in pace.

---

### Post by jamesdb on 2009-01-19
I am another victim of Kodak ESP3. I'm a novice with Linix/unbuntu and did not check to see if the printer was compatible with unbuntu. I bought the printer just after Christmas and have held on to it hoping that either Kodak or someone in Linux would provide a driver. I guess this is not going to happen from reading this thread. I am going to attempt to return it and get another printer. Does anyone have a suggestion for a good 3 in 1 printer that costs around what the Kodak printer cost $100 - $150. My old printer is an Epson 660 and it works ok but it is very slow on linux.

Thanks
JamesDB

---

### Post by yyyc186 on 2009-02-02
I ordered a KODAK ESP 7 printer today before finding this support forum.  Given that Ubuntu is taking over corporate desktops as companies abandon Microsoft in favor of OpenOffice and Open Document Format, I didn't even think about the driver issue.  It is simply unthinkable that any hardware manufacturer could believe supporting Microsoft was enough to stay in business.  Obviously they haven't heard about Microsoft's massive layoff and severe downsizing.

Oh well, I'm in the process of canceling this order.  Will let you know if I manage to get it canceled before they ship.

---

### Post by yyyc186 on 2009-02-02
This story just keeps getting better.

I called to cancel my order.  You cannot cancel an order with Kodak.  You have to stand around and wait for the shipment to arrive so you can refuse it.  If UPS just drops it on your doorstep they consider it sold.

No place on their Web site does it say they only support Microsoft.

My first call is to Visa to contest the charge.  My second call is to the Attorney General's office.

This isn't just a bad business policy, this is criminal wire fraud.

---

### Post by stchman on 2009-02-02
It sounds like they spent a great deal of time to earn their little Windows logo and ignored Linux.

What they are also trying to say is that they feel that Linux users make up a small minority so they are going to do nothing as their is not enough profit involved.

I would email them back and say F-off, you will spend your money on HP and also recommend to all you know that they do not spend their money on Kodak products.

Easiest way to hurt a company is to buy their competitors products.

I really despise inkjets anyway as they are a complete drain on your pocketbook with their crappy little inkjet cartridges.

---

### Post by drpaul on 2009-02-02
jamesdb:

No one seems to have answered your question. My experience is that HP has great support for Linux printing/scanning and the latest software even does fax for me. I'm using a hp 6110xi, not the latest hp model, but I would think that they have pretty broad support for their products in their software.

HTH

Paul

---

### Post by Pipps on 2009-02-03
I certainly went and bought a HP printer after finding this great thread. And I have never been happier!

---

### Post by ham213 on 2009-02-03
I am an ESP 7 owner who, unfortunately, **DID NOT** check to see if the printer worked in Linux. Stupid me just assumed it would work without difficulty the way my Epson RX500 and my networked HP 4600DN color laserjet did.

It's a little frustrating when I have to send a pic or a document across the network to a machine that is running an inferior O/S like Winbloze and THEN to my networked printer in order to get a print made.

It really is a shame, because for the price the KODAK ESP series of printers really work well, have good prints AND a low cost of ownership (minus the frustration).

Here is another spot of information from a tech at KODAK about the lack-of-driver issue. It can be found here: [http://johnmanard.pluggedin.kodak.com/default.asp?item=2191668]("http://johnmanard.pluggedin.kodak.com/default.asp?item=2191668")

Here is the relevant part of the post:
> 

Posted By: Ron Baird (1/29/2009)

Comment: Greetings Jerry, I hear you, and so does a good portion of the software team. Actually, we are very clear about not providing a Linux driver and this is clearly noted on the packaging of our printers. We are sorry that you did not note this information upon making your purchase. If you need Linux drivers, and you are within the return date option you may want to consider it. I am afraid; however, there simply is not enough time and resources to bring a set of drivers for the operating systems other than Windows and Mac. They are the leading two operating systems by far and though Linux is coming along, it seems to me that dedicating resources to bring drivers forward is not prudent. I do know that there are plans for them in the future, but that project is on hold while more needy software issues are addressed. As the world turns and things improve, that situation will likely change. At present, however, we are not going to provide Linux drivers. Things were looking up for a while there but with the down turn of the economy, more jobs are being lost which makes it quite hard to justify drivers for Linux. Thanks for understanding.


I'm just really disappointed that they didn't spend much effort at all on this. I know the Linux community is small, but we are growing in force every day. I just don't see how they can say that they can't dedicate resources to this because of the economy.

I personally have found that the economy being the way it is has had a very positive effect on turning people on to Linux (especially UBUNTU). I install Ubuntu on a bunch of new computers as a dual boot with Winbloze and some even as a primary because people just don't want to pay almost $200 to get a full featured operating system.

---

### Post by DonaldJ on 2009-02-03
Hey!  If Kodak doesn't want the $millions a Linux pipeline would generate, then watch'em Squirm when windows has gone to its grave, and Linux has taken the scene...  

This Kodak boycotting Linux might be their undoing...  
If Kodak wants to attach itself to a dying horse.. we can spend our money on other camera brands...  Not a prob.. there are many to choose from...  

It makes me wonder about Kodak, given that I see Windows as being a part of 
"hell on earth"...  

Last time I spent a penny on Kodak stuff, I can't recall...  I vaguely recall that I bought a roll of Kodak highspeed 35-mil color, about 23-years ago..? 
Next time I spend a penny on Kodak stuff, might never happen...

---

### Post by Barney Oatmeal on 2009-04-05
Sorry for bumping (not really) This subject is near and dear to me.
Are there any new opinions or developments on the subject????

Blessings,
           Barney Oatmeal

---

### Post by GreyGeek on 2009-04-05
> **drpaul said:**
> jamesdb:

No one seems to have answered your question. My experience is that HP has great support for Linux printing/scanning and the latest software even does fax for me. I'm using a hp 6110xi, not the latest hp model, but I would think that they have pretty broad support for their products in their software.

HTH

Paul

I bought an HP OfficeJet 5610 All-in-One printer awhile back.  It worked great with Mandriva 2009 PWP and it works great with Kubuntu jaunty.

---

### Post by Yoshokatana on 2009-04-06
Barney,

Kodak isn't going to offer linux support. They refuse to release the drivers they've *already* developed, even when I suggested they simply not offer support. They remain tight lipped.

I would suggest trying Epson or HP. That is all.

---

### Post by Pipps on 2009-04-09
I would strongly recommend HP. They have the most pro-linux attitude to hardware compatibility that I have ever seen!

I think all linux users should boycot Kodak as a matter of principle.

---

### Post by mister_playboy on 2009-05-14
I also have an Kodak ESP3, and I have used it successfully (both printing and scanning) in the past by running it from an XP VM in Virtualbox before.  It's not working in my new VM on 9.04, and I have yet to figure out why.  The printer is recognized and all that, but it fails to respond went I send a job to it.

---

### Post by dmdornctusa on 2009-05-25
I just purchased a Kodak ESP 7 this weekend, my primary usage is as a WiFi printer for my Mac and PC.  However I did notice in the driver list a UNIX driver.

Has anyone tired this in Linux. 

I tried using my HP Photosmart A826 on my Linux box but could not get satisfactory results when trying to print from the Linux version of LightZone.

So far LightZone in the only item of my photo workflow software that  works in directly in Linux (and better and faster than it does in WindowsXP) but with no way to print I am at a dead end triy to run my workflow exclusive in Linux.

David

---

### Post by Yoshokatana on 2009-05-26
> **Barney Oatmeal said:**
> Sorry for bumping (not really) This subject is near and dear to me.
Are there any new opinions or developments on the subject???
Not exactly. Kodak's dev team has an internal driver, but they don't want to pay to support it. They don't generally hire the best tech people, and the people they do hire are generally not savvy enough to support linux (even ubuntu). I doubt anything will change in the near future.

Unless Kodak decides to release the driver without support (possible, but unlikely) or someone reverse-engineers the driver from the OSX driver (unlikely, kodak printers aren't that important) nothing will happen.

HP printers are looking pretty nice right now.

---

### Post by brawd on 2009-07-07
Well I just emailed them to complain.
Judging from the tone of the discussion here I seriously doubt that it will help - but I feel better.

brawd.

---

### Post by jaw838 on 2009-10-14
Any news on compatibility and possible drivers for the Kodak ESP printer range within the new release folks?

---

### Post by jaypmcwilliams on 2009-10-15
[COLOR="Red"]I keep getting the same on phone & email response from Kodak, " We do NOT currently support LINUX but our programing & technical departments are working on it." Well, I'm working on it too. I went out & got a Canon Pixma MP620 All-In-One WiFi/Network Scanner/Photo Printer for the SAME price & the cartridges are the SAME price at Wal-Mart. SCREW KODAK!!!!! And ANY company that refuses to design hardware that could loose BILLIONS in additional revenue. Kodak's lose !!!! This company, dedicated to FREEdom, is moving on and away from Kodak products OFFICIALLY! Jay P. McWilliams Co-Owner/Certified Technician of [http://www.Lin-U-Over.com](http://www.Lin-U-Over.com) Thank You.[/COLOR]

---

### Post by ztomic on 2009-10-15
This is really more complicated than it looks. Kodak is in business to make money and I'm sure they don't need to support linux in order to make money.

I agree that it's sad we Linux users cant get proper support for hardware. I constantly fight with hardware. I spent 5 hours at my Moms house over the weekend trying to get a Epson cx9400 to print decent photographs... I gave up. It works great in Windows though. Other Epson printers have been well supported. Another poster in this thread commented that ATI is great with Linux but that hasn't been my experience. I have struggled with many different flavors of ATI.

Don't get me wrong. I love my Linux. The fact is that Kodak doesn't have to support Linux. I have my problems with Microsoft as well but I wont state them here. But users want something easy to use and that's what they get with Kodak on Windows. The driver CD comes with a great picture printing program. You don't see great picture printing programs in Linux even with hardware that's well supported. But I don't print pictures so it's no big deal to me except that I have to help Mom out.

So where does that leave us. Welp, when Mom went to buy a new printer, I told her to get an Epson 'cause I have had good luck in Linux with them. Not the case with the cx9400. I tried to steer her right but it bit me in the butt. Either way, you just do the best you can to find the hardware that works good in Linux.

Anyway, thats my two bits... take it or leave it.

---

### Post by jaypmcwilliams on 2009-10-15
While I do have to agree that Windows is easier in some aspects, It's not cheap in the long or short term. I REALLY do NOT want to get into a conversation or argument about which is better or worse, it's more of a matter of " What I can do". To the point, IF you know what you're doing, GIMP & other LINUX programs actually print better photographic DPI that Windows can IF the correct printer & drivers are used. ATI video cards are the same way. To the matter, Kodak, like so many others, have been pressured by Microsoft & concerns with hardware costs gone to more proprietary hardware. They are usually warned by development departments NOT to do this for closing out markets, yet THEY choose this route & with that choose to loose. To close, with the money LINUX users have saving money NOT having to pay for SO MUCH software, we have more to spend on extra's INCLUDING 2 printers vs 1. For the record, I was a DIE-HARD Windows user, tester, programmer for years but wanted FREEdom more than throwing my money away. While the Kodak ESP printers are wonderful & cheap, they're not functionally versatile for the REAL world. UNIX servers & LINUX servers make up over half the worlds networks & those networks use printers that Kodak's new ESP's are NOT compatible with. Think about it, Kodak IS loosing BILLIONS. FREEdom sometimes has a small price/work to pay/do. We " the LINUX world " are here to help you be FREE. My name is Jay, & I AM FREE!  :) :KS

---

### Post by Nickedynick on 2010-01-03
I think a lot of people on this thread are throwing out far too much hyperbole in claiming that Kodak will loose billions by not supporting Linux.

HOWEVER, I came across this thread just in time to cancel an order for a ESP 3250 - so thanks to all of you, and no thanks to Kodak! It seems stupid and arrogant to say that they're an inferior company for not offering this support, but whatever real reason they have for this decision they've still lost customers. If they decide to release drivers for the Linux community in the future then I'll go straight back to them, but for now I'm passing.

---

### Post by jpryde on 2010-01-28
One way to get connected to a Kodak printer would be to use a print server.  There are several on the market from $60 upward.  That is what I am planning.  Using two printers and three PCs.One new printer using USB and an older HP895 using parallel cable.

---

### Post by jaypmcwilliams on 2010-01-29
> **jpryde said:**
> One way to get connected to a Kodak printer would be to use a print server.  There are several on the market from $60 upward.  That is what I am planning.  Using two printers and three PCs.One new printer using USB and an older HP895 using parallel cable.

My apologies for my ignorance, but that has to be the most expensive & troublesome way to do something just for a printer. The idea of these posts are specifically for fixing &/or creating a driver for LINUX. Or, at least, compile sufficient printing methods. Your route seems to be one of executive failure. I, as I'm sure others feel, your answer is indeed NOT one of resolution to this matter. If we start to go in this direction, then Kodak will KNOW & LEARN to continue on their path of non-compliance with open-source development & discontinue the open path KNOWING that the printers will sell to anyone with a dollar. Whether they work or not. It seemed to me that Kodak was giving me the run around as so to expire the return dead-line. Well, I refused to play that game. I returned ALL Kodak equipment for FULL refunds. This driver issue has been NON-ADDRESSED for YEARS. BAD BUSINESS on their part. The LINUX/Open-Source community saves BILLIONS by NOT buying windows software. Kodak needs to grow up & realize a lost, renewable, income.

---

### Post by MeeMaw on 2010-01-29
Yes, I just read all this on another forum....

I lucked out in 2005.... I was starting to experiment with live disks and discovered my Kodak printer would not work in Linux no matter what.... it was already three years old so I figured it would die soon anyway, which it did.... In 2006 I bought a used HP DeskJet 5550, installed Linux to my computer and I've never looked back.

I do have a Kodak camera but the only way I EVER download the pictures is with a card reader..... 

I don't even use EasyShare on the Windows computers I have to use at work..... I hate the program....

I think they _will_ start losing money on this -- heck there are at least 6 of you here that have ordered something else....  $150 x 6 is $900 (a small start but a good one)..... and I'm sure there are many more using other distros who have done the same.

---

### Post by jaypmcwilliams on 2010-01-30
> **MeeMaw said:**
> Yes, I just read all this on another forum....

I lucked out in 2005.... I was starting to experiment with live disks and discovered my Kodak printer would not work in Linux no matter what.... it was already three years old so I figured it would die soon anyway, which it did.... In 2006 I bought a used HP DeskJet 5550, installed Linux to my computer and I've never looked back.

I do have a Kodak camera but the only way I EVER download the pictures is with a card reader..... 

I don't even use EasyShare on the Windows computers I have to use at work..... I hate the program....

I think they _will_ start losing money on this -- heck there are at least 6 of you here that have ordered something else....  $150 x 6 is $900 (a small start but a good one)..... and I'm sure there are many more using other distros who have done the same.



Interestingly, I bought a Canon Pixma MP620 & after some serious reworking with files & command line, Got printing, photos, scanning, OCR, bluetooth, network & wifi working. Canon does support LINUX ( TO SOME EXTENT ). But the drivers are REALLY HARD to find on their site. ALL of my Canon cameras work with LINUX too.

I'm closing out my help on this Kodak thread due to the fact that I now REFUSE to purchase any more Kodak products. 

---------** jaypmcwilliams CLOSED OUT on this thread **----------

---

### Post by Malakai on 2010-01-30
6 months ago linux only worked with UHCI ? I don't think so hehe.

I smell a ******** technobabble answer.

---

### Post by ibuclaw on 2010-01-30
> **Malakai said:**
> 6 months ago linux only worked with UHCI ? I don't think so hehe.

I smell a ******** technobabble answer.

You have to realise that the canned response was written circa 1999, about the time when Linux had a big boom of interest among companies.

Such interest has stagnated in recent times, with only Ubuntu really recapturing the energy of the 1990s, at least, among users.

---

### Post by crc294 on 2010-02-12
Hi all,

I discovered this thread the other day while searching for support for my new Kodak AiO printer. Looks like getting native Linux support from Kodak is a dead end.

I had another idea, and maybe someone here can tell me if it is possible or if it already exists. I have a comp running Windows 7 on the network, and I tried sharing the Kodak printer from it, thinking I could forward print jobs through Windows 7 to the printer. This doesn't work, you still need to install a driver in Ubuntu.

But this gave me an idea - is there a "faux printer" that you can install in Windows, that accepts PostScript jobs or something, and just forwards them on to another printer using the Windows driver? It would work something like this:

1) Install faux printer in Windows, set it up to forward print jobs to Kodak printer using Windows driver.
2) Share faux printer on home network
3) Set up faux printer in Ubuntu via samba and a PostScript driver
4) Print to faux printer from Ubuntu. Job is sent in PostScript. Faux printer turns around and prints to Kodak printer using Kodak driver.

What does everyone think? Does this exist, or could it be made?

---

### Post by paulnewall on 2010-03-17
I've written a cups driver for the kodak ESP 5250.
It's working on my ubuntu 9.10 system.
 
You can download it from sourceforge - search for kodak and you should find it.
 
If you get it working with another OS or for another ESP printer it would be very nice to hear that.

---

### Post by dalee on 2010-03-17
Hi,

I'm trying your driver for the Kodak ESP 5250 version 2. I'm trying to compile it on an eeePC 1101HA running 9.10 Karmic, Xbuntu variant.

I am getting this error at make:

# Dependencies...
#
# ... OK!
#
cc -O2 -Wall   -c -o c2esp.o c2esp.c
c2esp.c:31:23: error: cups/cups.h: No such file or directory
c2esp.c:33:23: error: cups/i18n.h: No such file or directory
c2esp.c:34:25: error: cups/raster.h: No such file or directory
c2esp.c:35:30: error: cups/sidechannel.h: No such file or directory
c2esp.c:69: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
c2esp.c:70: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
c2esp.c:71: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
c2esp.c:94: error: expected declaration specifiers or '...' before 'ppd_file_t'
c2esp.c:94: error: expected declaration specifiers or '...' before 'cups_page_header2_t'
c2esp.c: In function 'DoLog':
c2esp.c:104: warning: implicit declaration of function 'fprintf'
c2esp.c:104: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:104: error: 'LogFile' undeclared (first use in this function)
c2esp.c:104: error: (Each undeclared identifier is reported only once
c2esp.c:104: error: for each function it appears in.)
c2esp.c: At top level:
c2esp.c:108: error: expected ')' before '*' token
c2esp.c:115: error: expected ')' before '*' token
c2esp.c: In function 'FlushBackChannel':
c2esp.c:127: error: 'cups_sc_status_t' undeclared (first use in this function)
c2esp.c:127: error: expected ';' before 'status'
c2esp.c:132: error: 'status' undeclared (first use in this function)
c2esp.c:132: warning: implicit declaration of function 'cupsSideChannelDoRequest'
c2esp.c:132: error: 'CUPS_SC_CMD_DRAIN_OUTPUT' undeclared (first use in this function)
c2esp.c:133: error: 'CUPS_SC_STATUS_OK' undeclared (first use in this function)
c2esp.c:135: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:135: error: 'stderr' undeclared (first use in this function)
c2esp.c:140: error: 'CUPS_SC_STATUS_TIMEOUT' undeclared (first use in this function)
c2esp.c:140: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:141: error: 'CUPS_SC_STATUS_IO_ERROR' undeclared (first use in this function)
c2esp.c:142: error: 'CUPS_SC_STATUS_NOT_IMPLEMENTED' undeclared (first use in this function)
c2esp.c: In function 'GoodExchange':
c2esp.c:159: error: 'PrintFile' undeclared (first use in this function)
c2esp.c:159: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:161: error: 'stdout' undeclared (first use in this function)
c2esp.c:162: warning: implicit declaration of function 'fflush'
c2esp.c:167: warning: implicit declaration of function 'cupsBackChannelRead'
c2esp.c:171: error: 'stderr' undeclared (first use in this function)
c2esp.c:172: warning: implicit declaration of function 'strncmp'
c2esp.c:172: warning: implicit declaration of function 'strlen'
c2esp.c:172: warning: incompatible implicit declaration of built-in function 'strlen'
c2esp.c: In function 'Setup':
c2esp.c:202: warning: implicit declaration of function 'DoOutSend'
c2esp.c:202: error: 'stdout' undeclared (first use in this function)
c2esp.c: At top level:
c2esp.c:233: error: expected declaration specifiers or '...' before 'cups_page_header2_t'
c2esp.c: In function 'SetPaperSize':
c2esp.c:237: warning: implicit declaration of function 'strcpy'
c2esp.c:237: warning: incompatible implicit declaration of built-in function 'strcpy'
c2esp.c:239: error: 'header' undeclared (first use in this function)
c2esp.c: At top level:
c2esp.c:287: error: expected ')' before '*' token
c2esp.c:344: error: expected declaration specifiers or '...' before 'ppd_file_t'
c2esp.c:344: error: expected declaration specifiers or '...' before 'cups_page_header2_t'
c2esp.c: In function 'StartPage':
c2esp.c:349: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:349: error: 'stderr' undeclared (first use in this function)
c2esp.c:350: warning: implicit declaration of function 'DisplayHeader'
c2esp.c:350: error: 'header' undeclared (first use in this function)
c2esp.c:362: warning: implicit declaration of function 'DoOut'
c2esp.c:362: error: 'stdout' undeclared (first use in this function)
c2esp.c:374: error: 'CUPS_CSPACE_CMYK' undeclared (first use in this function)
c2esp.c:391: warning: implicit declaration of function 'fputs'
c2esp.c: In function 'EndPage':
c2esp.c:405: error: 'stdout' undeclared (first use in this function)
c2esp.c: In function 'Shutdown':
c2esp.c:422: error: 'stdout' undeclared (first use in this function)
c2esp.c: In function 'output_jbig':
c2esp.c:624: warning: implicit declaration of function '_cupsLangPrintf'
c2esp.c:624: error: 'stderr' undeclared (first use in this function)
c2esp.c:624: warning: implicit declaration of function '_'
c2esp.c:651: warning: implicit declaration of function 'memcpy'
c2esp.c:651: warning: incompatible implicit declaration of built-in function 'memcpy'
c2esp.c: At top level:
c2esp.c:670: error: expected declaration specifiers or '...' before 'FILE'
c2esp.c: In function 'write_plane_stripe':
c2esp.c:681: error: 'stderr' undeclared (first use in this function)
c2esp.c:691: error: 'fp' undeclared (first use in this function)
c2esp.c:692: warning: implicit declaration of function 'fwrite'
c2esp.c:692: warning: incompatible implicit declaration of built-in function 'fwrite'
c2esp.c:693: error: 'PrintFile' undeclared (first use in this function)
c2esp.c:710: warning: incompatible implicit declaration of built-in function 'fwrite'
c2esp.c: At top level:
c2esp.c:720: error: expected declaration specifiers or '...' before 'FILE'
c2esp.c: In function 'pbm_page_bands':
c2esp.c:840: error: 'fp' undeclared (first use in this function)
c2esp.c:896: error: too many arguments to function 'write_plane_stripe'
c2esp.c: In function 'main':
c2esp.c:916: error: 'cups_raster_t' undeclared (first use in this function)
c2esp.c:916: error: 'ras' undeclared (first use in this function)
c2esp.c:917: error: 'cups_page_header2_t' undeclared (first use in this function)
c2esp.c:917: error: expected ';' before 'header'
c2esp.c:919: error: 'ppd_file_t' undeclared (first use in this function)
c2esp.c:919: error: 'ppd' undeclared (first use in this function)
c2esp.c:932: error: 'LogFile' undeclared (first use in this function)
c2esp.c:932: warning: implicit declaration of function 'fopen'
c2esp.c:933: warning: implicit declaration of function 'setbuf'
c2esp.c:934: warning: incompatible implicit declaration of built-in function 'fprintf'
c2esp.c:938: error: 'stderr' undeclared (first use in this function)
c2esp.c:943: warning: implicit declaration of function '_cupsLangPuts'
c2esp.c:967: warning: implicit declaration of function 'strcmp'
c2esp.c:978: warning: implicit declaration of function 'strerror'
c2esp.c:985: warning: implicit declaration of function 'cupsRasterOpen'
c2esp.c:985: error: 'CUPS_RASTER_READ' undeclared (first use in this function)
c2esp.c:1008: warning: implicit declaration of function 'ppdOpenFile'
c2esp.c:1011: warning: implicit declaration of function 'strcat'
c2esp.c:1011: warning: incompatible implicit declaration of built-in function 'strcat'
c2esp.c:1013: error: 'PrintFile' undeclared (first use in this function)
c2esp.c:1029: warning: implicit declaration of function 'cupsRasterReadHeader2'
c2esp.c:1029: error: 'header' undeclared (first use in this function)
c2esp.c:1047: error: too many arguments to function 'SetPaperSize'
c2esp.c:1048: error: 'CUPS_CSPACE_CMYK' undeclared (first use in this function)
c2esp.c:1063: error: too many arguments to function 'StartPage'
c2esp.c:1076: warning: implicit declaration of function 'cupsRasterReadPixels'
c2esp.c:1103: error: 'dfp' undeclared (first use in this function)
c2esp.c:1109: warning: incompatible implicit declaration of built-in function 'fwrite'
c2esp.c:1113: warning: implicit declaration of function 'fclose'
c2esp.c:1119: error: 'stdout' undeclared (first use in this function)
c2esp.c:1119: error: too many arguments to function 'pbm_page_bands'
c2esp.c:1133: warning: implicit declaration of function 'ppdClose'
c2esp.c:1138: warning: implicit declaration of function 'cupsRasterClose'
make: *** [c2esp.o] Error 1

What am I doing wrong or missing from my install to get it to compile. I have build essentials installed.

Thank you for your effort!

dalee

---

### Post by paulnewall on 2010-04-08
The errors you are getting from make are due to some packages that need to be installed first. I may forget some, but you should install:
build-essentials
cups
cupslib2-dev (or maybe it's libcups2-dev)
 
 
Sorry about the long delay in replaying, but I don't monitor this forum.
You could get a quicker reply by using the help forum here
[http://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085](http://sourceforge.net/projects/cupsdriverkodak/forums/forum/1107085)

---

### Post by dalee on 2010-04-23
Hi,

I too had forgotten about this thread. I have just retried compiling it. It now works perfectly with Lucid.

Thank You for what you have accomplished!!

dalee

---

### Post by pricetech on 2010-04-23
Glad somebody got it to work, especially for those who already own kodaks and are stuck with them.

I personally loathe kodak and have for a very long time, for reasons that have nothing to do with Linux support.

I never recommend anything but HP printers for use under Linux, though I have a Brother that works perfectly.

---

### Post by bwallum on 2010-06-09
I've never made a driver in my life so ask first if this could work on a Kodak ESP 3 AiO?

EDIT
--- but I have now, thanks paulnewall! mmmmmmmmmmmmmhhhhhhhhhhhhhh!

I've paraphrased what I did on [http://ubuntuforums.org/showthread.php?p=9453827#post9453827]("http://ubuntuforums.org/showthread.php?p=9453827#post9453827")

---

### Post by Trent T on 2010-08-22
Hi all--
MANY thanks for the Kodak CUPS driver!  It works GREAT with my Kodak ESP 7250 Printer from Linux 9.10!

Here's a link to the SourceForge location for the driver:

[http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_08-1_i386.deb/download](http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_08-1_i386.deb/download)

The name of the driver is
c2esp_08-1_i386.deb

After downloading and installing, I was able to activate the driver in the usual way through System/Administration/Printing.  

It printed a color test page the first time I tried it (My printer is hooked up as a wireless device)

Very impressive performance-- Thanks again to all!

Trent T.

---

### Post by Mister_Ron on 2010-09-05
> **Trent T said:**
> Hi all--
MANY thanks for the Kodak CUPS driver!  It works GREAT with my Kodak ESP 7250 Printer from Linux 9.10!

Here's a link to the SourceForge location for the driver:

[http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_08-1_i386.deb/download](http://sourceforge.net/projects/cupsdriverkodak/files/c2esp_08-1_i386.deb/download)

The name of the driver is
c2esp_08-1_i386.deb



It also works with my Kodak ESP 7 AiO and Ubuntu 10.04.1.  Hooray!  Thanks much!
.................
Update:  It only partly works.  It's OK for basic stuff, but the colors are slightly off, and it does not recognize the auto-duplex feature.

---

### Post by houndi on 2010-09-05
Awhile ago, I read a blog post by one of our dev guys out in San Diego, that he was working on linux drivers.

---

### Post by Mister_Ron on 2010-09-06
> **houndi said:**
> Awhile ago, I read a blog post by one of our dev guys out in San Diego, that he was working on linux drivers.

How long ago?  There's an earlier post that mentioned that almost two years ago.

---

### Post by Adrian Challinor on 2011-01-18
So, now I can print. 

But has anyone managed to scan? Neither SimpleScan or SANE recognise the sanner as being there. 

HELP!

---

### Post by Adrian Challinor on 2011-01-18
OK, so I have downloaded the sourceforge drivers and I have a printer. 

But has anyone managed to work out how to get it to scan? 

Neither SimpleScan nor XSANE recognise the device as a scanner. Does it have to be plugged in?

---

### Post by paulnewall on 2011-01-29
You can't scan.
We have the same problem as with printing - someone has to write a SANE backend for the Kodak ESP.
I have got as far as aquiring a scan from the Aio, but I can't make any sense of the data, which I think is compressed - so you can't just look at it and easily deduce the format.

---

### Post by ShinobiTeno on 2011-03-01
Ahaha, I had similar sitation with esp5250.
The sales manager in saturn has assured it has CUPS and support linux(it supports macosx btw).

Yeah, it didn't. Great respect for the hacker that wrote PPD driver.

But I simply just returned this garbage back to the store. TWO of it. And took HP B209 - now everything works and officially. 

So throw away the garbage.

---

