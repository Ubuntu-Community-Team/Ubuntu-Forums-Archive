---
title: "No luck with getting Quicktime going..."
date: 2005-11-21
forum: General Help
---

### Post by kpm on 2005-11-21
I have followed all the instructions about video codecs, mplayer, gstreamer... but cannot seem to get Quicktime vids to play... I have installed plugin after plugin after plugin... still nothing but '(no picture)' where the Quicktime plugin should be... at least Firefox is not crashing when a Quicktime embedded web page is browsed to, but I am still unable to veiw Quicktime video... Can anyone else view Quicktime 7 files such as on this site [http://www.onegoodmove.org/1gm/](http://www.onegoodmove.org/1gm/)??  Any suggestions??
Thanks

---

### Post by bonzodog on 2005-11-21
Quicktime is not supported in linux. Most of us just learn to live with the fact that Apple don't want the linux community to have it.

---

### Post by stewski on 2005-11-21
[QUOTE=bonzodog]Quicktime is not supported in linux. Most of us just learn to live with the fact that Apple don't want the linux community to have it.[/QUOTE]

Well I know there are several issues regarding the use of codecs for propriatry formats like quicktime and windows media video etc on linux (which s why the  distro cant ship with it). But its not fair to say that you can't play quicktime on linux, Im using the mplayer mozilla plugin on ubuntu with quicktime codecs no problem.
I think I got this working by following the how to here...

[mplayer how to]("http://www.linuxforums.org/tutorials/1/tutorial-25783.html")

Thats not to say we shouldn't take the opportunity to boo apple and M$ for their stupid licencing rules "boooo boooooo boooooo" :-)

---

### Post by kpm on 2005-11-23
[QUOTE=stewski]
I think I got this working by following the how to here...
[mplayer how to]("http://www.linuxforums.org/tutorials/1/tutorial-25783.html")
[/QUOTE]

Hey thanks for that great link... I have managed to get some quicktime plugins working, but still not the ones that are using the newest version of Quicktime... (like here [www.onegoodmove.org](www.onegoodmove.org) ) but I am sure there is a solution out there and will find it when I manage to find the time to dig into it.  I am using Breezy and that tutorial is for Warty... maybe that has something to do with it... I did remove mplayer-386 and install mplayer-586 which I think enabled me to get to the point where some Quicktime embedded files worked...
cheers

---

### Post by kpm on 2005-11-23
[QUOTE=bonzodog]Quicktime is not supported in linux. Most of us just learn to live with the fact that Apple don't want the linux community to have it.[/QUOTE]

I would like to make do without Quicktime, but can't rely on content providers to offer up alternatives, and all those clips from The Daily Show on Comedy Central are Quicktime... so until I can get them to work with Linux, I have to keep my old laptop running Windows... and I really want to install Ubuntu on it... Quicktime is the only hold back (which is quite an improvement from 5 or 6 years ago I must say.)... I really want to be able to watch those clips which are otherwies scheduled past my bed time... When I learn more about alternative opensource tools and formats the content providers could use to post content instead, I will suggest it to them ad nauseum...

---

### Post by kpm on 2005-12-04
Ok, I finally got Quicktime plugins with Mplayer to work!  I did it by using this incredible Automatix script (get it here: [http://ubuntuforums.org/showthread.php?t=66563](http://ubuntuforums.org/showthread.php?t=66563)) 

I actually reinstalled Ubuntu before using Automatix, to start with a clean slate after all my mucking about... 

Anyway, I do have one more problem I will have to look into now however... When I visit the page that was my motivation for getting Quicktime files to work, ([www.onegoodmove.org/1gm/](www.onegoodmove.org/1gm/)) all of the files are embedded and on the index page and they all start playing at once!  So I have to rush through and click stop on them all and then click play on one... and then it is a bit choppy... too bad, if I can find out if that is a setting in mplayer so it does not start playing these files all at the same time, I will keep Windows off of this machine, but if I can't, alas, I will be forced to dual boot... sigh and boo to proprietary formats!

---

