---
title: "Any Music Players that Handle Classical?"
date: 2005-11-21
forum: General Help
---

### Post by Ubuntist on 2005-11-21
Are there any Linux music players out there that are designed to cope with classical music?  In other words, players that can
[LIST=1]
[*]Organize tracks into pieces and pieces into albums, and
[*]Keep track of both composer and performer?
[/LIST]

---

### Post by jmh on 2005-11-21
Tha bundled Mplayer does that - for some of my CDs it even pulled out all the necessary composer and title info and populated it's database. For others you edit it by hand.

I did find (not used it on Breezy) I had to grab a OGG tag editor to alter the tags on some ripped tracks, but that was easy.

---

### Post by Ubuntist on 2006-03-09
Sorry for the long delay, but just after I posted my question, sound stopped working on my Ubuntu installation and I've only recently got it working again.

I've looked at Mplayer (and its website), but I can't figure out how it solves my problems.  Let's say I have a CD called "Holst - The Planets -- Britten - Enigma Variations" which contains both Holst's "The Planets" and Britten's "Enigma Variations," and I have loaded the CD onto my hard disk.  What I want is a player that will allow me to identify the whole CD by its name but will also allow me to identify the piece called "The Planets" and another piece called "Enigma Variations".  Is there any player that can do that?

---

### Post by phetre on 2006-05-08
Hi Ubuntist.  I'd just like to put in my two cents for Quod Libet.  After about a week of use, I prefer it to Rhythmbox, Amarok, Banshee, XMMS, and Listen.  It has excellent music-management features, runs on the standard GStreamer engine, and it's FAST!  I have a fairly large library (~15,000 songs), and searches just fly, even on my low-end computer.
But more relevant to this thread, it supports the Composer tag.  I'm in the process of retagging my classical albums right now to take advantage of this.

---

### Post by enopepsoo on 2006-05-08
Like much maligned gstreamer has some decent classical streaming stations.
I have been happy enough with it to never look for another streaming audio client.

---

### Post by hugmenot on 2006-05-09
Quod Libet works exceptionally well for any music library that is a little more involved than the usual pop music collection.
This is mostly due to its commitment to rich meta-data (vulgo: tags). Rich meta-data means that you are free to use any tags you wish and you can configure the display to reflect your preferences.
I find it very pleasant to tag everything to my standard, it supports all formats that I need and it supports Replaygain which is useful for &#8220;classical&#8221; music, because dynamic variance is often very high across albums.
I think this screenshot is able to illustrate what QL can do:

---

### Post by ex00r on 2006-05-09
i'm very pleased to hear that i'm not the only one here who listen to classical music.

anyway. I will check out quod libet. I already checked out amarok, listen, XMMS, BMP, rhythmbox and some more. But non of them were good enough for managing classical music. amarok were just great, but since i run gnome...

what also anoyes me, is, that you can't sort your library by composer. This is really frustrating. If there is somebody who knows how to do it or which player to use, go ahead and tell it :)

PS: Wagner is the best! :D

ex00r

---

### Post by hugmenot on 2006-05-09
[QUOTE=ex00r]i'm very pleased to hear that i'm not the only one here who listen to classical music.

anyway. I will check out quod libet. I already checked out amarok, listen, XMMS, BMP, rhythmbox and some more. But non of them were good enough for managing classical music. amarok were just great, but since i run gnome...

what also anoyes me, is, that you can't sort your library by composer. This is really frustrating. If there is somebody who knows how to do it or which player to use, go ahead and tell it :)[/QUOTE]

The Album List mode you see in my screenshot doesn't offer a sort by composer option (but this would be a really trivial to implement feature request to the devs) but other browser modes like, yes, Browser can be configured to have a pane for composer. Also you can use the powerful search do stuff like composer = "Richard Wagner" anywhere.

> 
PS: Wagner is the best! :D


fair enough, or not...

---

### Post by Ubuntist on 2006-06-06
I'd given this thread up for dead; I'm glad to see there's life in it yet.

Thanks for suggesting Quod Libet, everybody.  I've just installed it and will try it out.  It does look pretty good, though it's not obvious to me that it can group individual tracks (corresponing to movements for classical music) into pieces.

I had become pretty comfortable with amaroK.  I run Gnome rather than KDE, but amaroK still seemed to work pretty well.  Having given up on finding a player that could handle composers, I had simply started using the artist tag to hold the composer in the case of classical music, although I have also populated the composer tag.

All in all, at this point it's a contest between Quod Libet and amaroK.  On XP, I use Media Monkey.

---

### Post by phetre on 2006-06-06
[QUOTE=Ubuntist]It does look pretty good, though it's not obvious to me that it can group individual tracks (corresponing to movements for classical music) into pieces.[/QUOTE]
That is a great idea.  I've never seen a player with that capability -- does Media Monkey do that?  I can think of two ways to hack this into Linux.
[B][U]
OLD METHOD:[/U][/B]
The MusicBrainz "solution" is to tag every track name with the name of the work and movement:  "Symphony No. 9 in D minor: I. Allegro ma non troppo"

From what I can tell, that has three drawbacks:
[LIST=1]
[*]The work is not an object in the library, but only a pattern in the track title.
[*]The track title ends up being too long for most portable players to display reasonably.  On my rockbox'd iRiver, most classical music requires a lot of scrolling to display both the movement and the work.
[*]Roman numerals look stupid for works with a lot of tracks, like the Goldberg Variations, or the Bartok Violin duets, etc.
[/LIST]
That said, it is easy to search, and it's a consistent system, so when a better solution comes along, it will be easy to convert things automatically (cross fingers). 

**_NEW IDEA:_**
Using Quod Libet / Ex Falso, you can create a "work" tag and apply it to tracks belonging to multimovement works.  That should make it possible to group tracks according to work and album.  I guess you could also create a "mvmtnumber" tag for ordering within a work, if for some reason "tracknumber" isn't sufficient.  I haven't tried this, so caveat emptor.  (That said, you can just delete the tag if it doesn't work.)

This would seem to have several benefits, compared to the old method:
[LIST=1]
[*]The "work" is now an object in the library, at least as much as "artist" or "album."
[*]It should be easy to configure any reasonably robust player to display "work" and "[movement] title" in separate fields.
[*]Er, no Roman numerals?  :)
[/LIST]
The main drawback, obviously, is that not many players support this kind of rich metadata, so it might be a little tricky to export your library from Quod Libet, should the need arise.

---

### Post by hugmenot on 2006-06-06
You&#8217;re free to use whatever suits you for subcategorization or markup (that was what I meant with rich meta-data).
In this case you could use the tag <part> which is semi-standard (if at all), but QL accomodates for it in the default UI. You can have it in the lists and it shows in trackinfo display, popups etc.
If you use movement you can add a column for it and add it to the config strings. Here&#8217;s the one I use:```
\<span weight='bold' size='large'\><title>\</span\> - <~length><version|
\<small\>\<b\><version>\</b\>\</small\>>
<artist|\<small\>von \</small\> <artist>><conductor|,\<small\> Dir. \</small\><conductor>><composer|,\<small\> Komp. \</small\><composer>><performer|
\<small\>Int. \</small\>\<i\><performer>\</i\>|<album artist|
\<small\>Int. \</small\>\<i\><album artist>\</i\>>>
<album|\<b\><album>\</b\><discnumber| - Disk <discnumber>><part| - \<b\><part>\</b\>><tracknumber| - Titel <tracknumber>>>
```

It&#8217;s a little involved; you have to discern musical tags in <> and markup tags in \<\>. Conditionals are made with pipes: <if | then | else>. Watch the newlines, they prevent empty lines in case the rule doesn&#8217;t match.

For the columns, if you enter a &#8220;tied tag&#8221; like album~part, it will append the part to the album if present. This way is better than MusicBrainz-style concatenation because they are really two fields, backwards compatibility is better, searchability etc.

BTW I like tagging with an instrumentation field and with performer having one tag per performer. Oh, and I also use composer for <artist> because that&#8217;s most useful in simpler players. Others prefer performer, though.

---

### Post by Ubuntist on 2006-06-07
[QUOTE=phetre]That is a great idea.  I've never seen a player with that capability -- does Media Monkey do that?[/QUOTE]

Apparently Media Monkey does allow one to merge tracks together into a single object, but I've never taken the time to figure it out.  Making use of this feature would have the drawback that you'd no longer be able to play individual movements if you wanted to.

---

