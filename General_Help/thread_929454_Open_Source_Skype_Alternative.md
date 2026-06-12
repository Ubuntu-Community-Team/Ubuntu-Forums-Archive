---
title: "Open Source Skype Alternative"
date: 2008-09-25
forum: General Help
---

### Post by FeraTech on 2008-09-25
I was wondering if there were any Open Source alternatives to Skype that had compatible hardware phones.

I am also looking for software that has the ability to use call forwarding and be able to have dial in number.

---

### Post by styfle on 2008-09-25
I think Ekiga is similar but skype is available for linux so I don't know why you wouldn't use it.

---

### Post by Sef on 2008-09-25
Check out [Wengophone]("http://www.openwengo.org/").  It is in the universe (community maintained) repository.

---

### Post by FeraTech on 2008-09-25
Yes I've looked into all those but it does not seem like there are hardware phones available for them and they lack a lot of features...

---

### Post by ben2talk on 2009-03-10
> **Sef said:**
> Check out [Wengophone]("http://www.openwengo.org/").  It is in the universe (community maintained) repository.

Wengophone appears to be sleeping - you cannot create a new account with them, and the Ekiga Softphone in the repositories is a pig to set up - I gave up. Twinkle had problems with ports.

Open Source isn't very Open a lot of the time!

---

### Post by zerubbabel on 2009-11-09
There is also Gizmo5, which works very well. I've been using it for six months or so. But the latest and saddest (in my opinion) news is that Google just acquired Gizmo in order to compete with Skype. I suppose that will eliminate any hopes of secure communication with Gizmo, since Google will doubtless scan every communication for keywords so as to fuel its advertising engines. 

So does anyone know of any other chat/voip/file-transfer alternative to Skype and Gizmo?

---

### Post by julianb on 2009-11-09
> **zerubbabel said:**
> 
So does anyone know of any other chat/voip/file-transfer alternative to Skype and Gizmo?

Does Ekiga work for you?

---

### Post by zerubbabel on 2009-11-10
Well, I'm trying to figure out how to get Empathy to work through a SIP gateway for calling and receiving calls from regular phones. That's Karmic's answer to Skype, so I'm going to give it a whirl. Has anyone got it work with voipdiscount.com?

---

### Post by gradinaruvasile on 2009-11-10
I tried Emathy and couldnt use it at all with a SIP account (local SIP server).

By hardware phones you mean Skype/SIP protocol compatible phones or just regular PSTN phones?
And you mean a SIP provider that has a call out service. Usually this a paid service AFAIK. Maybe some providers have free ones, but i dont think u can call everywhere and anytime - just the fact that regular phones calls are not free by nature.

Using SIP protocol may (and usually does, at least for me) cause problems over NAT/firewalls (internet in general). Sometimes you cannot hear the other, sometimes the other way around. It is suited to be used in offices/through VPNs that are routed well, but over the Internet it has its problems. My experience at least.

On the other hand the only thing that guarantees (well, sort of) that your communication is not recorded/listened to is peer to peer encryption (ZRTP/OTR  (pidgin)/etc) - you know all services have servers attached to them and the software on them permits eavesdropping - its really up to the people who administer them. And peer to peer encryption is only supported by a handful of applications and certainly cannot be used to call regular phones (well at least i havent heard of it).

P.S. Skype is implemented just right under Linux. Why not use it? I use it and works perfectly (every single time, not as flaky as SIP is sometimes) and interoperates with the Windows version 100%. Anyways its more secure than Yahoo.

I too would like to see a Skype/Yahoo like open source thing, but anything that is adopted and grows big is bound to become just another Skype/Yahoo - money is needed to support the infrastructure everywhere...

---

### Post by zerubbabel on 2009-11-10
Sorry, I meant regular phone *numbers*, not phones. The reason I don't like Skype is because they reserve the right to use your computer as a relay server and I don't want someone else's traffic going through my computer. 

I realize that security depends on the discretion of the server administrator, but Google's clearly stated mode of operation is to glean advertising hints from its message streams. They maintain a profile on each user so as to more accurately target their advertising. That's why all their services are "free". I'd rather not participate.

As far as Empathy goes, it works fine as a Jabber client, interacting with my Gizmo5 contacts, at least in text mode, but when I set up a SIP account, it claims to connect, but I hear nothing.

---

### Post by zerubbabel on 2009-11-12
I've settled on using Empathy as a Jabber client and Twinkle for VOIP, and everything is working fine. Twinkle is very nice, with an interface to DiamondCard, a reasonably cheap and responsive SIP provider. It would have been nice to be able to use Empathy for both, but as far as I can see, Empathy's user interface for VOIP is non-existent.

---

### Post by ngage on 2009-11-13
hey,

sorry to butt in but i am having trouble integrating my google voice and gizmo5 accts.  I have been able to verify my gizmo5 sip number in google voice and i can receive calls now.  The problem is that i can't call out, and i think you are supposed to get 3 free minutes.

I explain my problem in depth here: [http://ubuntuforums.org/showthread.php?t=1324934](http://ubuntuforums.org/showthread.php?t=1324934)

My problem seems topical in light of voip options discussed.  Thanks in advance.

---

### Post by metalf8801 on 2009-11-13
> **zerubbabel said:**
> There is also Gizmo5, which works very well. I've been using it for six months or so. But the latest and saddest (in my opinion) news is that Google just acquired Gizmo in order to compete with Skype. I suppose that will eliminate any hopes of secure communication with Gizmo, since Google will doubtless scan every communication for keywords so as to fuel its advertising engines. 

So does anyone know of any other chat/voip/file-transfer alternative to Skype and Gizmo?

but is gizmo5 open source? if so what license does it use?

---

### Post by crys on 2009-11-13
You might also consider Linphone. In my opinion, it's the most stable SIP soft phone. I tried Ekiga which didn't work for me; it has problems in getting its bugs fixed.
Try the most recent version, which is here:
[http://savannah.inetbridge.net/linphone/stable/sources/](http://savannah.inetbridge.net/linphone/stable/sources/)

Chris

---

### Post by zerubbabel on 2009-11-13
No, Gizmo5 is not open source, but it is free and supports open standards like SIP and Jabbar.

---

### Post by brucewagner on 2010-03-04
What about for VIDEO too...  not just voip.

We are looking for the standards-based, open source, non-proprietary Best alternative to Skype....  

But we want it to handle video (web cam) calls well too.

Any news on what works best?

Skype is closed and proprietary.  Skype for Linux doesn't seem to work with all our web cams.  It also does not seem to have been updated in at least 2 years?

Gizmo5 is not open source, and it's not even allowing new accounts.

What about the others?   Is there a standard for VIDEO?  Does the SIP standard handle video?

Empathy?

---

### Post by Zill on 2010-03-04
[QuteCom]("http://www.qutecom.org/") (formerly WengoPhone) is good for VOIP/SIP video chat and can be easily installed on Linux, Mac and Windows.  Not much documentation around but it is fairly intuitive (my wife uses it to see our grandson). :-)

If you want a free SIP account to go with QuteCom then I recommend [IPTel]("http://www.iptel.org/service").  However, if you want to also dial landlines then you may need a different provider as I believe IPTel only provide VOIP connections.

Both QuteCom and IPTel are open-source applications.

---

### Post by VanillaMozilla on 2010-03-17
There is a thread here, with my summary of what I found: [http://ubuntuforums.org/showthread.php?t=1408679&page=3](http://ubuntuforums.org/showthread.php?t=1408679&page=3) on VoIP programs. The only one I have gotten working completely (for making calls) is Twinkle, with Diamondcard for computer-to-phone calls.  Some people had excellent luch with SIP-Communicator.

Ekiga has numerous problems, which may or may not be caused by sound packages (ALSA and others).

---

### Post by Docaltmed on 2010-07-13
> **VanillaMozilla said:**
> 

Ekiga has numerous problems, which may or may not be caused by sound packages (ALSA and others).

Ekiga's sound quality is awful on my machine. Qutecom, on the other hand, is easy and excellent. I'm using it in combination with nomado.eu for phone service.

---

