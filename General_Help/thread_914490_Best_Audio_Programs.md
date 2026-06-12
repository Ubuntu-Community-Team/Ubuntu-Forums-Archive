---
title: "Best Audio Programs?"
date: 2008-09-08
forum: General Help
---

### Post by lotharjade on 2008-09-08
**What are the best audio programs out there for Ubuntu or Linux? ** I am looking for a fairly full featured program that would be comparable to Winamp, possibly with new more advanced features such as web 2.0 tech (tags would be lovely).  The programs that came with Ubuntu seemed a bit wanting to me, and I have been looking for more.  :-k

I know XMMS had some link to Winamp awhile back, but I keep seeing indications that is either not up to date, or the development of the project is falling behind.

Also, the current audio video programs seem to have a fit if you try to drag the slider/progress bar accross to a further position in the song or video while playing, which typically ins't a big deal in windows.  Anyone know what that is all about?

(I keep wishing someone would smash Winamp, Del.icio.us, and Pandora together into a online/offline program for managing all our music and sharing, in web 2.0 fashion, our thoughts of same.  But, sadly I lack the programming skills)

---

### Post by tuxxy on 2008-09-08
Banshee, Rythmbox, VLC

---

### Post by ryanhaigh on 2008-09-08
Although it isn't something I use personally I think songbird might be what you are looking for in terms of web integration. Other big names in the linux audio player universe are Amarok, Banshee, Exaile, Rythmbox (google will find you MANY articles comparing these). As far as I know Banshee is the only one of these that also supports video.

Personally I like decibel audio player for its simplicity, the only 'web 2.0' feature it has is last.fm integration and I don't use that. I keep my music organised in directories and don't have the time to make sure tags are all correct so it works well for me. Does one thing and does it well.

VLC is a great video app on any platform but unfortunately the linux version (at least in 7.10) opens a new instance whenever you open a file rather than adding it to the current playlist.

You might also want to take a look at the linux port of XBMC or the boxee (not sure if thats the spelling) fork which supposedly makes it a 'social' media player.

---

### Post by mb_webguy on 2008-09-08
For music, I think Amarok is probably the best app available.  I used Winamp for years in Windows, and like Amarok at least as much.  Your comment about "Web 2.0" features is a bit vague, but Amarok does have quite a few plugins that interface with various websites, such as grabbing lyrics from various websites or integrating with last.fm.  

Amarok doesn't support video like Winamp, but that's why god made VLC...

---

### Post by OutOfReach on 2008-09-08
Banshee, or Rhythmbox.

---

### Post by cybrsaylr on 2008-09-09
I use all 3, Amarok, Banshee, and Rhythmbox.

---

### Post by kpkeerthi on 2008-09-09
There is also audacious, if you prefer winamp-like.

---

### Post by lotharjade on 2008-09-13
> **mb_webguy said:**
> For music, I think Amarok is probably the best app available.  I used Winamp for years in Windows, and like Amarok at least as much.  Your comment about "Web 2.0" features is a bit vague, but Amarok does have quite a few plugins that interface with various websites, such as grabbing lyrics from various websites or integrating with last.fm.  

Amarok doesn't support video like Winamp, but that's why god made VLC...

Thank you for all your suggestions.  I am now looking into and comparing the various players.

  As for the web 2.0 bit, I guess I am refering to a social media player.  Basially I want to have all of Del.icio.us's features, just slightly skewed to a media palyer, with the inclusion of a five star rating system. 
 
  You see with Delicious I can bookmark a website, leave tags of my own making (no standard required, just whatever I want) or suggested tags, and a comment message about what I think about it.  Now if you haven't used the system you might think, there is nothing social about that, but thats where the fun starts.  If you make that bookmark public other people can not only see, but search for your bookmark.  You can go to your bookmarks and see a number of how many other people posted that same bookmark, but also see all the comments for other people who posted public bookmarks for that page.  Quite often they are really interesting.

  [COLOR="DarkRed"][SIZE="4"]What does that have to do with Audio/Video?[/SIZE][/COLOR]  Well, I basically want all those features for every CD and video I have on my computer, online, or (if possible) streaming videos and anything like that.  At that point I can see what everyone else thinks of songs, and add to it my self.  It gives me a way to comment about songs, music, and videos, but also find out a lot of info about music, video, etc...

  You see, I spent three and a half years working as a DJ at a college radio station up here in Alaska.  One of the tasks of the program manager and staff was to listen and review every cd that came into the station and both rate the CD, but also every song on it with comments.  It was a low tech version of what I am talking about, and was very enlightening when searching for music that you hadn't heard before.  You all might not be that interested in such a system (as I know some linux users push toward minimalism in things), but for some of us such a system is a little piece of happiness.

  I really appreciate your help and suggestions.  Thank you.  :biggrin:

---

### Post by loboc on 2008-09-13
Banshee Rhytmbocx and Amarok have last.fm intergration built in.  Last fm is a social music rating site, once you start scrobbling your tracks last.fm can play you songs that people with similar tastes are listening too, 

i prefer amarok because the ease of its scripting language allows some sweet plugins like lyrics look up through google instead of one or two lyrics databases

---

### Post by WRDN on 2008-09-13
> **ryanhaigh said:**
> Although it isn't something I use personally I think songbird might be what you are looking for in terms of web integration. Other big names in the linux audio player universe are Amarok, Banshee, Exaile, Rythmbox (google will find you MANY articles comparing these). As far as I know Banshee is the only one of these that also supports video.

Personally I like decibel audio player for its simplicity, the only 'web 2.0' feature it has is last.fm integration and I don't use that. I keep my music organised in directories and don't have the time to make sure tags are all correct so it works well for me. Does one thing and does it well.

VLC is a great video app on any platform but **unfortunately the linux version (at least in 7.10) opens a new instance whenever you open a file rather than adding it to the current playlist.**

You might also want to take a look at the linux port of XBMC or the boxee (not sure if thats the spelling) fork which supposedly makes it a 'social' media player.

Regarding the VLC issue (see bold quote), you can use the following script to ensure only one instance of VLC is allowed to start:

```

#!/bin/bash

kill -TERM $(pidof vlc)

vlc "$1"

```

This closes any instances and opens a new one when you open a file.

---

### Post by dualpretop on 2008-09-17
Amarok, Listen, Qmmp...

---

