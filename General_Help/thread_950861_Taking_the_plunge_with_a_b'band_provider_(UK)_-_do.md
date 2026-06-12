---
title: "Taking the plunge with a b'band provider (UK) - do I understand correctl?"
date: 2008-10-17
forum: General Help
---

### Post by SomethingFishy on 2008-10-17
Hi

I'm new to linux and making tentative progress but not yet convinced I've made the right move.  Perhaps you can help me sort out my Internet connection and start to convince me.

Having trawled through the websites of many of the UK's main ISPs it seems pretty clear I'm not gonna find one that supports Ubuntu for an entry-level monthly subscription.  However I think I've established that as if I can find one that provides Internet access via an ethernet connection (such as Virgin) all I need to do is plug it in.  That is, as long as Ubuntu is recognising my network card.  Please tell me, is that right, and how can I be sure my network card is OK?  I'm reluctant to gamble cos of other problems I'm having (see post on monitor resolution prob, if you like :))

Cheers.

---

### Post by sparky-steve on 2008-10-17
Hello,

Any ISP will work with Ubuntu with a bit of - but not much - effort.

Virgin will work out of the box via ethernet; I would strongly recommend that if you go down that route you will need a firewall (applied to any O/S). In linux firestarter is a great GUI firewall, though I prefer & use shorewall, which also allows me to share the internet with the family, and furthermore have the kids internet filtered through DansGuardian via Squid (content filtering).

For the ADSL providers, you would need either an ADSL PCI card (or equivalent) or an ADSL modem with ethernet port. ZyXel make some great products that will either NAT your LAN (thus you would not "need" a firewall) or bridge the connection as if it were an ethernet provided service.

I would be willing to help on any of the above issues if you need more information.

SS

---

### Post by sparky-steve on 2008-10-17
Oh - and you've SO made the right choice; My move to linux was turbulent some years ago, but it's come on SO much in that time, and ubuntu is a gift from above so far as installation / ease of use.

Stick with it for a while and you'll see.

SS


PS: Try starting a new thread about your monitor resolution problems. More people will see it. You also need to give more information, such as graphics card make/model, and the exact problem you're having.  If it's Intel or Nvidia I might be able to help you. ATI and I dont get along ;-)

---

### Post by ww711 on 2008-10-17
> **SomethingFishy said:**
> Hi
Having trawled through the websites of many of the UK's main ISPs it seems pretty clear I'm not gonna find one that supports Ubuntu for an entry-level monthly subscription. 
Cheers.

Your ADSL ISP only provides you a connection to the Internet. 

Majority of ADSL ISPs bundle a package with a wireless router, e.g [https://www.bethere.co.uk](https://www.bethere.co.uk)

It does not matter what operating system you use; Linux, Windows, Mac OS, etc.

---

### Post by Elfy on 2008-10-17
I've had the same deal with isp's not supporting linux - basically they don't have the cheat sheets for the call centre staff.

Don't tell them what you're using when you have problems - as long as you can get past the initial reluctance to even talk to you and can provide suitable responses you will get 'some' help - or at least I have.

All you really need them to do is to support the connection to the router.

I never managed to get anywhere with linux until I had a router and used the ethernet connection.

Unfortunately atm I'm using talktalk - who will at least help - especially via the forum, where there are people who use linux and ubuntu, but AOL were not helpful and tiscali hung up. 

I would imagine the netwrok card will be ok - but if you give us the name/model you'll get a better answer.

---

### Post by jerome1232 on 2008-10-17
I actually worked for 2wire (contracted by at&t to build wireless adsl/routers) and yeah nobody will support Linux but honestly it's bad enough memorizing OSX 10.4 10.2, win 2k3, xp, and vista so that you can guide someone who can't double click, through menu upon menu without being able to see their screen, but I still would trouble shoot things that are os indepentent (router, pppoe in the router, physical connections, adsl signal issues, and etc...) 

As long as you get a service that you can stick a router between you and the internet I see no issues. ppoe connections can be done in the router.

---

### Post by PocketDog on 2008-10-17
My next door neighbour's on TalkTalk. I changed his router's MTU to 1432, silly sod still had the default 1500.
My laptop zips along after

```
sudo ifconfig eth1 mtu 1432
```

I assume - if he's using Windows - his laptop won't be as fast as mine ;-)

---

### Post by SomethingFishy on 2008-11-05
Thanks again + a quick update:  I've just got online tonight, and it was as easy as the forum said. I signed up with "talk talk", who sent me a router, I plugged it all in, connected the ethernet cable and I was online immediately.  Thanks to those who encouraged me to go for it.

Incidentally talk talk seems a good deal: land line rental, up to 8 meg speed and 40 gig monthly download limit for less than 16 quid a month.  Sweet.

---

### Post by scouser73 on 2008-11-05
I'm with Virginmedia and although they don't support Linux you should have no problems connecting to the internet. I deleted Windows XP and installed Ubuntu 7.10 when it came out and I've had no problems with the internet connection apart from downtimes (which is due to Virginmedia).

---

