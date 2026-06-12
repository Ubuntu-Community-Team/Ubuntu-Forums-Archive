---
title: "Linux compatible Skype phone adaptor"
date: 2006-07-31
forum: Hardware &amp; Laptops
---

### Post by eqisow on 2006-07-31
Does anybody know of a Skype phone adaptor (such as [this]("http://us.accessories.skype.com/direct/skypeusa/itemdetl.jsp?prod=3071")) that works with Linux?

Thanks in advance.

---

### Post by eqisow on 2006-07-31
In asnwer to my own question, I've found [this](http://www.amperordirect.com/pc/c-internet-adapters/internet-phone-converter-b2k.html). The manufacturer has [Linux drivers](http://www.yealink.com/en/skypedown.asp) on their site, but I'd still like to know if anybody else has had any experience with the company or with this product in particular.

---

### Post by AmperorDirect.com on 2006-08-07
Hi,

Thank you for the mention. The product you mentioned works great in most Skype environments. However, Linux is still a work in progress. The driver/software for Linux from Yealink (manufacturer of the B2K) is not open source and only function with Fedora Core 3. 

Hope that helps a bit...

---

### Post by Jason Weiss on 2007-10-31
This post is a couple of years old, so has anyone else managed to get a USB Phone adaptor to work with skype?

Is is one of those things that just works all the time with linux so no one posts about it?

Or is it one of those things that just doesn't work with linux so no body bothers trying it?

---

### Post by phillfri on 2007-12-20
I can report that the Yealink B2K adapter works with both Skypemate software on Windows XP and the kb2kskype software on PCLinxOS 2007 on a Dell E520 intel chipset based computer. But, I also have an Asus V3-M2A690G ATI chipset based computer and the Yealink B2K will not work properly using either Skypemate on Windows XP or kb2kskype on PCLinuxOS 2007. All outbound voice has a terrible screeching sound no matter how you adjust the software. I think the the B2K adapter itself is not compatible with the ATI 690G chipset.

---

### Post by komputes on 2008-05-19
I have the B2K adapter made by Yaelink and re-sold in Canada by Voicegear.ca / Industry Dynamics. Even though the box says that it's Linux compatible, the company takes no responsability and will not come out with a debian package for the product.

I have found that this community project is the best thing you have.

[http://kb2kskype.sourceforge.net/download.html](http://kb2kskype.sourceforge.net/download.html)

Before you get all happy. Please note that this does not work exactly like skypemate of windows. I have had the
 following issues:

1) sound quality is low (echo, buzz cuts)
2) can't dial numbers from the phone (must open skype, click on "Call Ordinary Phones" and [gah! linux version] tell it what country you want to call then input the number). You can set shortcuts to contacts you saved in skype (somewhat or an annoying workarround). Beside that it does here and then.
3) Touch tones don't work well.

(1& 3 may be skype, but 2 is definitely the box)

---

### Post by altariel on 2008-05-20
> 2) can't dial numbers from the phone (must open skype, click on "Call Ordinary Phones" and [gah! linux version] tell it what country you want to call then input the number). You can set shortcuts to contacts you saved in skype (somewhat or an annoying workarround). Beside that it does here and then.


I'm very surprised at this, because on  my end it works without problems!

The only thing to remember is to add the international dial code first ... 
i.e. 0046 for a call inside sweden in my case - and then I also have to ditch the first zero in the area code as well ... but I just changed all of my SkypeOut contacts to that international format and now I only have to speed dial contactnumber# for the most used ones ... for the others 0046(0)areacode-number# works without hiccups!

---

### Post by komputes on 2008-05-20
>  2) can't dial numbers from the phone

The fact is I can only call people with shortcuts in Skype.

> **altariel said:**
> I'm very surprised at this, because on  my end it works without problems! 



Really altariel? Can you send me URLs to the packages you installed so that I may test them. Just to be clear and making sure i understand you correctly, you can pick up your phone, get a dial tone, dial number directly on the phone keypad: 

```

0046086924600 #
```

and the phone will start ringing and you will be connected with the Swedish Newspaper Publishers' Association. Can you try it just to make sure. If this works please let me know which exact packages/instructions you followed.

---

### Post by altariel on 2008-05-21
> Really altariel? Can you send me URLs to the packages you installed so that I may test them. Just to be clear and making sure i understand you correctly, you can pick up your phone, get a dial tone, dial number directly on the phone keypad:

Code:

0046086924600 #

and the phone will start ringing and you will be connected with the Swedish Newspaper Publishers' Association. Can you try it just to make sure. If this works please let me know which exact packages/instructions you followed.

well, since I am the package builder in this project ;) I just use the very same packages which I then hand over to the programmer/maintainer which then uploads them to sourceforge. 

[http://sourceforge.net/project/showfiles.php?group_id=186708](http://sourceforge.net/project/showfiles.php?group_id=186708)

In this case I'm using the 7.10-packages on a 7.10-computer. 

* I start Skype, 
* after a while (SLOW computer, Dell Latitude c840) I start kb2kskype 
(I have had an automatic script in .kde/Autostart and might get back to that again if I start using the SkypePhone more regularily again - just need to figure out the correct sleep-time on my end before starting kb2kskype) 
* doublecheck in the Skype setup options that all sound devices are set to VOIP Phone  
(have some USB-things that sometimes claim/gets the sound devices instead)
* and by that point it really is as easy as 

--- lifting the handset, (skype reacting directly!)
--- getting a dial tone, 
--- dialing a COMPLETE international number and 
--- pressing the # key ... 
--- with Skype popping up the appropriate SkypeOut connection or popping up about "calling number x" 

oh, and speed dials are speed-dial-number# 

what doesn't work though, understandably, is calling services where you have to use your phone for choices and the like in meny structures ... 

A package for 8.04 will get built whenever I come back home next (which might be this weekend)

---

### Post by komputes on 2008-05-21
I'm running the 7.10 Packages on Hardy, I'll try it on Gutsy to see if I can fully dial numbers. By the way, which version of Skype are you currently using?

In my current situation here's what works and what doesn't:

--- lifting the handset, (skype reacting directly!) -< YES
--- getting a dial tone,  <- YES
--- dialing a COMPLETE international number and  pressing the # key <- NO. Does not dial unless it's a shortcut/speed dial. need to click on Dial out or on Contact.
--- with Skype popping up the appropriate SkypeOut connection or popping up about "calling number x" <-YES
--- Touch Tones <- NO

---

### Post by bluenova on 2008-05-21
I have the box and used to run it on a laptop with Windows XP. This laptop was purely for running the Skype phone and was the only Windows installation in the house. After I moved house I didn't bother setting it up again. I have never heard of kb2kskype before, but will certainly be giving it a try now!

---

### Post by altariel on 2008-05-21
> **komputes said:**
> I'm running the 7.10 Packages on Hardy, I'll try it on Gutsy to see if I can fully dial numbers. By the way, which version of Skype are you currently using?
Beta 2.0.0.43 
on Kubuntu 7.10 on an old Dell Latitude C840 laptop ... 
and even connected to an USB hub - several people seemed to have troubles with audio distortion when plugging the telbox into a NOT powered USB hub on some motherboards at least ... but even that does work on this old Dell at least ... 


> **komputes said:**
> 
--- dialing a COMPLETE international number and  pressing the # key <- NO. Does not dial unless it's a shortcut/speed dial. need to click on Dial out or on Contact.
--- Touch Tones <- NO
what are Touch Tones? 

I have double and triple checked this today, no problems here to dial SkypeOut numbers NOT in my contact list :confused: :confused:

so please do doublecheck with a gutsy version - should work to just boot the gutsy live CD and install skype, usbb2k-api and kb2kskype I hope ... 

could you please give some more details on your hardware?
and what kind of telephone? tone dialling or pulse dialling?

---

### Post by altariel on 2008-05-21
ah ... I think I get what you mean by touch tones ... 
:) 
(wikipedia is great)

well, I DO hear them in the telephone end!

which leads me to think there is some miscommunication between skype and the telephone?
... on the other hand stuff DOES seem to work apart from two issues? ??? hmmm ... 

how do your options look like? 
* x11 and dbus enabled under public api? 
* B2K_connector under allowed programs in the same public-api-part of the skype options?
* all three sound-devices set to VOIP Phone in the sound devices part of the skype options? 

or your soundserver?
what sound is your skype set to? 
is this another of the problems existing with pulse audio in hardy? 
:) guessing wildly as you might see ... 

will point the developers/programmers of the software to this thread too :)

---

### Post by simon_6162 on 2008-05-22
Hi,

Start Skype and login, then start kb2kskype from the command line using 

```
kb2kskype --debugmessages
```

If you don't have a PSTN line connected to the box you need to have the b2k box in USB mode, If you do have a PSTN line then you need to be in PSTN mode and dial a (*) to switch to SKYPE mode before dialing a number.

Then dial 0046086924600# or your own house number!

Hang up before you annoy them !
post the output that appears in the lower window of kb2kskype. (remove your friends user names from the post though)

One thing to note on the later versions of skype is that if you change user or start kb2kskype before logging into skype you have to go to the contact tab of kb2kskype and click refresh to connect to Skype.

---

### Post by komputes on 2008-05-22
@simon
Please note that I don't and have never used PSTN mode.


@altariel
Touch tones are the sounds the keypads make. I don't think this is the phones fault because, clicking on the numbers in skype gives me the same mistakes. I have no idea what you're asking me about the api and sound server, but I will try it on gutsy to see if I can dial numbers from the phone in USB mode.

---

### Post by komputes on 2008-05-23
Running "kb2kskype --debugmessages" on Ubuntu 7.10 (Live CD) with usbb2k-api-mod2.8, kb2kskype-0.3.7 and skype-2.0.0.68-1 I get the following result:

```
Skype instance found, window id 52428926
NAME B2K_CONNECTOR (sent to skype) 
PROTOCOL 7 (sent to skype) 
OK (message from skype) 
PROTOCOL 7 (message from skype) 
CONNSTATUS ONLINE (message from skype) 
CURRENTUSERHANDLE komputes (message from skype) 
SEARCH FRIENDS (sent to skype) 
USERSTATUS ONLINE (message from skype) 
USERS bob, megan, sue, toby, lary, fred, cedric (message from skype) 
USB Device Found (from telbox) 
SWITCH USB (from telbox) 
(from telbox) 
Unknown Key: 01 f6 (from telbox)
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
CALL 12125551212 (from telbox) 
CALL 12125551212 (sent to skype) 
ERROR 92 CALL: Unrecognised identity (message from skype) 
Skype: ERROR 92 CALL: Unrecognised identity 
HANDSET OFF (from telbox) 
SET CALL STATUS FINISHED (sent to skype) 
MINIMIZE (sent to skype) 
ERROR 19 Invalid call id (message from skype) 
Skype: ERROR 19 Invalid call id 
OK (message from skype) 
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
HANDSET OFF (from telbox) 
MINIMIZE (sent to skype) 
OK (message from skype) 

```Perhaps this may help in understanding why I cannot dial out. I will try with Kubuntu 7.10 although it is not my default environment.

---

### Post by komputes on 2008-05-23
I just tried it on Kubuntu 7.10 (Live CD) and it seems to do the same thing, except for this part:

```
USB Device Found (from telbox) 
SWITCH USB (from telbox) 
(from telbox) 
Unknown Key: 00 00 00 00 01 f6 (from telbox) 
```

Do you guys get an "Unknown Key"? This has always been the case for me, although it is usually "Unknown Key: 01 f6 (from telbox) ", even in Kubuntu.

---

### Post by altariel on 2008-05-24
yes ... 

here's my output, edited for numbers and my skype handle ... 

```
Skype instance found, window id 67108947
NAME B2K_CONNECTOR (sent to skype) 
PROTOCOL 7 (sent to skype) 
OK (message from skype) 
PROTOCOL 7 (message from skype) 
CONNSTATUS ONLINE (message from skype) 
CURRENTUSERHANDLE //{removed}// (message from skype) 
SEARCH FRIENDS (sent to skype) 
USERSTATUS DND (message from skype) 
USERS //{bunch of users removed}// (message from skype) 
USB Device Found (from telbox) 
SWITCH USB (from telbox) 
(from telbox) 
Unknown Key: 01 6f (from telbox) 
HANDSET ON (from telbox) 
FOCUS (from telbox) 
FOCUS (sent to skype) 
OK (message from skype) 
CALL //{some number - in full}// (from telbox) 
CALL //{some number - in full}// (sent to skype) 
CALL 454 STATUS UNPLACED (message from skype) 
CALL 454 STATUS ROUTING (message from skype) 
CALL 454 RATE 0 (message from skype) 
CALL 454 RATE_PRECISION 3 (message from skype) 
CALL 454 RATE_CURRENCY SEK (message from skype) 
CALL 454 STATUS EARLYMEDIA (message from skype) 
CALL 454 VAA_INPUT_STATUS FALSE (message from skype) 
HANDSET OFF (from telbox) 
SET CALL 454 STATUS FINISHED (sent to skype) 
MINIMIZE (sent to skype) 
CALL 454 STATUS CANCELLED (message from skype) 
OK (message from skype) 
CALL 454 STATUS CANCELLED (message from skype) 
```


one thing I -did- notice was that my full number looked like 004650xxxxxx
whereas your full number starts with 1212 ... could be that very problem rearing its head again with international numbers in different countries, Simon?

[http://en.wikipedia.org/wiki/List_of_international_call_prefixes](http://en.wikipedia.org/wiki/List_of_international_call_prefixes)
[http://www.itu.int/oth/T0202.aspx?parent=T0202](http://www.itu.int/oth/T0202.aspx?parent=T0202)
[http://www.wtng.info/wtng-cod.html](http://www.wtng.info/wtng-cod.html)

komputes: have you tried to include a 00 at the very beginning of your number just to check if it makes any difference? or maybe 011 according to this [http://www.wtng.info/wtng-1-ca.html](http://www.wtng.info/wtng-1-ca.html)
if the logic is correct that is ... 
Sweden: 00 = international prefix & 46 = country code --> so I dial 0046(0)50xxxxxx
Canada: 011 = international prefix & 1 = country code --> so maybe 0111-somenumber would work?
as far as I can tell a call from Canada to Sweden (i.e. full number) would start with 01146(0)50xxxxxx

---

### Post by komputes on 2008-05-25
Ok, so I can make calls, I was just unaware that a prefix needed to be included.

To call in the USA or Canada dial the following numbers using your phone

```

&#9556;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9574;&#9552;&#9552;&#9552;&#9552;&#9559;
&#9553;OUT&#9553;PREFIX&#9553;AREA CODE&#9553;PHONE NUMBER&#9553;SEND&#9553;
&#9553;011&#9553;  1   &#9553;   212   &#9553; 555 -1212  &#9553;  # &#9553;
&#9562;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9552;&#9577;&#9552;&#9552;&#9552;&#9552;&#9565;

```This is true for all numbers on the NANP system (for the uninitiated the NANP is the numbering plan for the Public Switched Telephone Network for Canada, the US and its territories, and the Caribbean). 
For all area codes check this page out: [http://www.bennetyee.org/ucsd-pages/area.html](http://www.bennetyee.org/ucsd-pages/area.html)

Thanks to atariel for packaging this and helping me figure this out.

Full solution posted here: [http://ubuntuforums.org/showpost.php?p=5040812&postcount=4](http://ubuntuforums.org/showpost.php?p=5040812&postcount=4)

---

