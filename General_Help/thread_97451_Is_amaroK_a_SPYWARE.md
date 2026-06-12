---
title: "Is amaroK a SPYWARE?"
date: 2005-12-01
forum: General Help
---

### Post by freedom on 2005-12-01
Recently I accidentaly discovered that amaroK is stealing 1-2kbps of my modem internet connection. I like to monitor the speed of transfering something and yesterday when downloads of some files are finished I notice that on the graph still are some transfer going wich are cleverly disguised because transfer never goes over 2kbps. I'm sure it's amaroK cause when I quit amarok transfer stops.:confused: 
Does someone getting this too?

---

### Post by magnusbb on 2005-12-01
Yes, it is spyware in the way that it takes the names from your mp3 files and get information about them on the internet - to provide you with more information on the album, the lyrics, and more.

I guess with KDE's configurability, you can turn this off.

---

### Post by supenguin on 2005-12-01
I am running into the same problem... I looked around the amarok settings and could not find anything about connecting to the internet. I checked the help files and forums and didn't have any luck there either.

The only time I want amarok connecting to the internet is when I import tracks off a new CD. I want it to get track info from CDDB and album cover art. After that - no more getting anything off the internet.

---

### Post by claydoh on 2005-12-01
afaik, amarok is not supposed to connect to wikipedia or to the lyrics database, or the cover manager until you click on the appropriate tab. An option to try is to uncheck all the options on the last.fm section in the configuration setup . It seems that even if you don't have an account it may be connecting there to help with the suggested songs feature, which as it states does not require an account or profile with last.fm.

---

### Post by freedom on 2005-12-02
[QUOTE=claydoh]It seems that even if you don't have an account it may be connecting there to help with the suggested songs feature, which as it states does not require an account or profile with last.fm.[/QUOTE]

You're right.
It is about to fetch similar artists from lastfm wich does not require account.
This option is enabled by default and I didn't go to lastfm tab cause I don't have account and really don't need it. :KS

---

### Post by daller on 2005-12-02
[QUOTE=supenguin]I am running into the same problem... I looked around the amarok settings and could not find anything about connecting to the internet. I checked the help files and forums and didn't have any luck there either.

The only time I want amarok connecting to the internet is when I import tracks off a new CD. I want it to get track info from CDDB and album cover art. After that - no more getting anything off the internet.[/QUOTE]

Just interested... Is amarok capable of cd ripping?

And to the spyware-thing - OpenSource Applications can't be (isn't) spyware - It's that simple!
Spyware is a ClosedSource-thing (assuming that people aren't dumb!)

I can promise you that nothing in the repositories is spyware!

---

### Post by GoldBuggie on 2005-12-02
You can rip files from CD in amarok yes...it goes about it the same as konqueror if I remember correclty.

---

### Post by daller on 2005-12-02
[QUOTE=GoldBuggie]You can rip files from CD in amarok yes...it goes about it the same as konqueror if I remember correclty.[/QUOTE]

Well, how do I do it?

If it's as simple as KAudioCreator, shouldn't "we" consider removing KAudioCreator from the default installation?

IMO as few different applications as possible is the best!

---

### Post by GoldBuggie on 2005-12-02
like from konqueror..just do a drag and drop from the mp3 dir or ogg dir etc.

---

### Post by samx on 2005-12-02
[quote=daller]If it's as simple as KAudioCreator, shouldn't "we" consider removing KAudioCreator from the default installation?[/quote]
No.
I can't find any functionality to rip CDs in AmaroK.
I think GoldBuggie meant that built-in function in KDE/Konqueror, that you see an mp3 and an ogg folder when you open an audio CD and you can copy these files as if they're really there.
I took some time for me to realize that these are virtual files. Perhaps some people like this "feeling", but I'm more old-style in that matter, I want a "real" application where I can change settings and so on and not special "magic".

---

### Post by GoldBuggie on 2005-12-02
I do mean the functionalty that konqueror provides but I'm pretty sure that when I wnter a CD and open it in Amarok I get about the same structure of choosing mp3/ogg etc as in konquerer. 

You can change the settings for the ripping at *kcontrol->Sound & Multimedia->Audio CD->(MP3 Decoder or Ogg Vorbis Encoder)*

And it uses internet database to lookup the cd and names the file accordingly.

When I found this I removed KAudioCreator.

I'll try a CD with Amarok when I get back from going out.

---

### Post by asimon on 2005-12-03
Amarok sends information which songs you play to "an independent server". But AFAIK it's disabled by default. See [Amarok FAQ: last.fm](http://amarok.kde.org/amarokwiki/index.php/FAQ#last.fm_FAQs).

---

### Post by samx on 2005-12-03
@GoldBuggie
Yes, but all that functionality comes from konqueror (even the CDDB lookup) or more exactly from a special plugin which is used by konqueror, too. So if you want to rip CDs, you can do it with konqueror and the result is identical.
I just wanted to say that I would like to have KAudioCreator in the standard installation.

---

