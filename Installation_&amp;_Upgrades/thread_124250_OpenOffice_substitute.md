---
title: "OpenOffice substitute"
date: 2006-02-01
forum: Installation &amp; Upgrades
---

### Post by qwazert on 2006-02-01
It seems as though OpenOffice won't work for me, so I have removed it.
Can someone suggest an equivalent word-processing app that I could try instead of Oo writer? 

Abi-word works (and prints), but it has a few quirks...I'm just curious what all is "out there" as far as office software goes.

---

### Post by MartinG on 2006-02-01
[QUOTE=qwazert]It seems as though OpenOffice won't work for me, so I have removed it.
Can someone suggest an equivalent word-processing app that I could try instead of Oo writer? 

Abi-word works (and prints), but it has a few quirks...I'm just curious what all is "out there" as far as office software goes.[/QUOTE]Do you mean you just don't like OpenOffice, or is there some problem that others could help with if you posted about them? 

As to what else to use, it depends on your needs, but there's not some wonder-app out there waiting to be discovered, or we'd all be using it instead of OpenOffice. For a more-or-less full-featured word processor there's Abiword and KWord from the Gnome and KDE camps, then there's paid-for stuff like TextMaker or ThinkFree Office.  Some people say something like Emacs or Vi is all they need, or there's LaTeX.

---

### Post by qwazert on 2006-02-01
OpenOffice was unable to print documents for me - but that's a whole other story!

I'm not too set on specifics, I'm just searching for options. I tried Kword and don't like it, so I'll give LaTex a try and see how it fares.

For the time-being, I will use Abiword until I find something a bit more "MsWord'ish".

---

### Post by taurus on 2006-02-01
Just so you know, emacs and vi are basic text editors...  Back to your problem with OpenOffice.  Are you able to print from other apps except OpenOffice?  Make sure you pick the right printer from OpenOffice's print menu or it will just dump it into some generic printer!

---

### Post by qwazert on 2006-02-01
Apparently there is a "bug" in Ubuntu that prevents my printer from printing in Oo writer. I've tried everything short of a re-format. All other applications print but that one, so I doubt that it is a flaw in my printer or my set-up.

After some reading, it seems that LaTex is a bit of overkill for what I want. Kword wasn't bad but it had some real limitations. Has anyone ever tried ***Pathetic Writer***?

---

### Post by towsonu2003 on 2006-02-01
does the pdf viewer print your stuff correctly? if so, you can export your document as pdf in openoffice, open it in your pdf viewer, and print it (3-5 mouse clicks). 

I tried abiword and koffice (kword is part of it) but they can't really read MS documents... there is something called star office?

also, if you register / login to linuxquestions.org, this poll and its answers may help: [http://www.linuxquestions.org/questions/showthread.php?t=409039](http://www.linuxquestions.org/questions/showthread.php?t=409039)
The poll won't be visible if you don't login / register :-k  I believe most of their suggestions are apt-gettable in ubuntu.

---

### Post by qwazert on 2006-02-01
The PDF viewer prints...EVERY OTHER APP in Ubuntu prints except for OoWriter.
According to what I had been reading, the LATEST version of Oo was supposed to have fixed this bug but apparently it didn't.

I'll continue to examine other WP's until I find one I like...otherwise I'll reload Oo and print from PDF...:-k

---

### Post by qwazert on 2006-02-01
I re-installed Oo2 today and now OoWriter **IS** printing documents with  no problems!
I don't understand what happened, but I am thankful that it works PROPERLY now!





*Still on the lookout for some really cool software! \\:D/

---

### Post by towsonu2003 on 2006-02-01
[QUOTE=qwazert]I re-installed Oo2 today and now OoWriter **IS** printing documents with  no problems![/QUOTE]
i'm really glad that worked out nicely :)

just out of curiousity (and bc I have some problems with the beta Ooo2), which one did you re-install? oo2 in the repositories (beta) or the one from openoffice.org (not beta). if you did the later, could you link the guide you used (if any) as I would like to install the non-beta one. The small glitches in this beta bother me while writing my thesis ;)

check out the software in the parent of that linuxquestions.org poll link I posted for some more cool stuff. ;)

---

### Post by qwazert on 2006-02-01
Most of the LINUX software I install is from the Repository.
Having said that, I should also mention that I installed this particular app via the LATEST version of Automatix.

The version of Oo is the same as before, but I noticed in the Help/About section that it specifically mentioned *Breezy*:
***Openoffice.org2-core 2.0.1-0Breezy1 Sat. Jan7 01:11:04 UTC***

All of my settings were the same as before; fonts, spacing, etc. But this time when I went to PRINT, a different screen came up than before and my printer reacted immediately.

Hope this helps?
:confused:

---

### Post by landotter on 2006-02-02
I have OOo installed and it's great, but for really basic WP duties, I really like Abiword. Seems it's finally gotten pretty stable--it was a crashing annoyance even a year ago. It uses amazingly few system resources.

For spreadsheets, I like the light footprint of gnumeric, but my spreadsheets are beyond basic, just using a few sums. :P I hear it's quite decent for moderate use as well.

OOo is heavy, but it's powerful as well. It's what I fire up to design business cards and similar heavily formatted work.

---

### Post by gamma on 2006-02-02
I really want to switch to Koffice, but it doesn't want to open powerpoint files and some .doc files. Or if it does open them it renders them weird... OO for me.

---

### Post by qwazert on 2006-02-02
And I found Kword to be rather simplistic.
Now that Oo is FULLY functional for me, I find it to be an acceptable substitute for MSOffice.

---

### Post by towsonu2003 on 2006-02-02
[QUOTE=qwazert]
The version of Oo is the same as before, but I noticed in the Help/About section that it specifically mentioned *Breezy*:
***Openoffice.org2-core 2.0.1-0Breezy1 Sat. Jan7 01:11:04 UTC***
[/QUOTE]
oh I see. Automatix got you the stable version. the one in the breezy repos -thus the one I'm using- is the beta oo2 (version is 1.9.129). may be I should start searching for a howto now (I was too lazy for the last couple of weeks for oo2 ;) ).
thanks for the reply :) .

---

### Post by MartinG on 2006-02-03
[QUOTE=towsonu2003]oh I see. Automatix got you the stable version. the one in the breezy repos -thus the one I'm using- is the beta oo2 (version is 1.9.129). may be I should start searching for a howto now (I was too lazy for the last couple of weeks for oo2 ;) ).
thanks for the reply :) .[/QUOTE]Just add this repository:
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./

---

### Post by towsonu2003 on 2006-02-03
[QUOTE=MartinG]Just add this repository:
deb [http://people.ubuntu.com/~doko/OOo2/](http://people.ubuntu.com/~doko/OOo2/) ./[/QUOTE]
that's easy enough ;)

---

### Post by ace2005 on 2006-02-05
OO is very good, i use it on Kubuntu and i take it with me for use at school:

[http://portableapps.com/apps/office/suites/portable_openoffice](http://portableapps.com/apps/office/suites/portable_openoffice)

Abiword also has a portable version, so check out that too

---

### Post by towsonu2003 on 2006-02-05
[QUOTE=ace2005]
[http://portableapps.com/apps/office/suites/portable_openoffice](http://portableapps.com/apps/office/suites/portable_openoffice)
[/QUOTE]
I wish they had it for linux as well. but it seems anything tat gets picked up by windows users looses its developer support in one way or antoher in linux.

---

