---
title: "GetLive configuration problems"
date: 2009-05-08
forum: Installation &amp; Upgrades
---

### Post by mercury80 on 2009-05-08
Hey!
I've been trying to install GetLive to import my hotmail to evolution. Can't find any decent tutorials or help on the mater. The most helpful one so far is a [French one]("http://babelfish.yahoo.com/translate_url?doit=done&tt=url&intl=1&fr=bf-home&trurl=http%3A%2F%2Fdoc.ubuntu-fr.org%2Ftutoriel%2Fhotmail_getlive_evolution&lp=fr_en&btnTrUrl=Translate").

When i install it with, it is dependent on postfix and procmail, i get to a part where i am supposed to configure postfix, and i got no clue what to do there... "No configuration", "Internet site", "Internet with smart host", "satellite system" and "local only". if i try anything but "No config" i have to type a "system mail name". Don't know what is correct. 

the /usr/bin/getlive confiuration-file is obsolete aswell. so i tryed to replace it with this [GetLive.pl file]("http://getlive.cvs.sourceforge.net/viewvc/getlive/GetLive/") as well.

And then there is Evolution... I tied to add it as an acount, using the /usr/bin/getlive as a configuration path. Not sure what to use as a server type, I'm guessing "local delivery", but i tried "standard UNIX mbox file" aswell... when i try to fetch my mail, it just says complete straight away.

I have no idea what's wrong. Anyone know this stuff?

---

### Post by ooolongT on 2009-05-19
I would like to get GetLive working too.  Does anyone have any idea how  to configure GetLive?  I just started using mutt, but any GetLive info would be helpful.


#=========================================

I am 90% of the way there, I am going ot start another thread about my problem though since this one seems dead.

---

### Post by mercury80 on 2009-05-21
I am surprised no one knows how-to, or the whereabouts of a manual, for GetLive. It is in the repository and maintained by Ubuntu MOTU Developers. So... is there a way I can bump this in to the spotlight?

---

### Post by ooolongT on 2009-05-22
Good news!!!  You do can now hack your way around the use of getlive!

Check out this article:
[http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/](http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/)

Problem solved!

---

### Post by mercury80 on 2009-05-23
SWEEEEEET! about frkn-time... i used to have that back in the day. (if it hadn't been for the fact that i've had that account since hotmail started, i would have swaped it over years ago...) Pitty tho... it  doesn't look like it was about to come to norway any time soon... now the question is: what is their devious reasons for asking our home-address?

---

### Post by ooolongT on 2009-05-23
Ah, I am in the same boat as you.  I have used that stupid address for as long as there has been Hotmail, and at the time that was the only free email I knew about.  I would LOVE to ditch it, but I can't.  

My feeling on why they are asking for the home address is, "Don't know, don't care."  I am sure they would say they are tailoring advertising to you, but they wouldn't need to know your precise address for that.  And, as I discovered, there is no need to put something that precise in the form.  Filling it out exactly as they do here: [http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/](http://www.mydigitallife.info/2009/01/22/hack-to-enable-hotmail-pop3-and-smtp-support-instantly-for-all-countries/)  is enough for me to be able to use it. That is all I care about!  

Did you get it to work?

---

### Post by mercury80 on 2009-05-23
no such luck... The "register information link" is not available in my hotmail-account...

---

### Post by ooolongT on 2009-05-23
Ah man, that's lame.  Are you sure you're looking in the right place?  

If its really not there, I guess this is a poor solution but you could always forward it to another hotmail account that you create in England, Canada or wherever? 

Alternatively, you can also have gmail grab it, and then filter it on the TO line.

---

