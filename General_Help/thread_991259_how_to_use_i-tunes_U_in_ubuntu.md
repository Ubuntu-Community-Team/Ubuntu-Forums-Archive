---
title: "how to use i-tunes U in ubuntu???"
date: 2008-11-23
forum: General Help
---

### Post by rakan_dr on 2008-11-23
hey guys,
i'm trying to use the itunes U services to watch and download some videos from some universites but i don't know how to do that, because while loading a web page from itunes U, firefox asks me to select a software to run the videos or something. I chose rythmobx, but nothing happened!

this is the page that i was trying with it:
[http://deimos.apple.com/WebObjects/Core.woa/Browse/mit.edu]("http://deimos.apple.com/WebObjects/Core.woa/Browse/mit.edu")

---

### Post by rbmorse on 2008-11-23
Does iTunes U require iTunes, by any chance?

---

### Post by rakan_dr on 2008-11-23
> **rbmorse said:**
> Does iTunes U require iTunes, by any chance?

I don't know, maybe, did you check that link??

---

### Post by jimmy the saint on 2008-11-23
I am not positive, but I would think that if it is an itunes streaming server of any sort it would use the itunes streaming protocols.  That would mean it is a DAAP server.  Rhythmbox has a daap plugin, but does not work with video.  Unless I am mistaken, Banshee (another player) has a daap plugin and plays video.  I would say that is a good place to start.

---

### Post by jimmy the saint on 2008-11-23
Well after clicking the link provided I would say that your issues are deeper than any of that.  Unless you can connect directly to the server (skip the webpage) You may not be able to do that.   Contact your IT dept and ask them for the ip and port of the daap stream, if that is even what it is, and you should be able to use that. 

Otherwise, it looks like you need itunes.  Maybe you could use a virtual machine with VBox and use a windows guest.

---

### Post by rakan_dr on 2008-11-26
> **jimmy the saint said:**
> Well after clicking the link provided I would say that your issues are deeper than any of that.  Unless you can connect directly to the server (skip the webpage) You may not be able to do that.   Contact your IT dept and ask them for the ip and port of the daap stream, if that is even what it is, and you should be able to use that. 

Otherwise, it looks like you need itunes.  Maybe you could use a virtual machine with VBox and use a windows guest.

thnx man, but i'm not an MIT student :( so which dept should i contact??
That web page and other videos on itunes are free to use, so anybody should use it freely and without problems with itunes application *i think*.

any other suggestions??

---

### Post by rakan_dr on 2008-11-28
anybody!

---

### Post by rakan_dr on 2008-11-30
hello!!

---

### Post by rbmorse on 2008-11-30
You need iTunes to view that link. iTunes is owned by Apple Computer. They do not make a Linux version of iTunes.  

If you want to use iTunes on a Linux machine, your options are (in my order of preference):

1.  Install Windows XP (SP2 or later) along side of your Linux installation in a dual-booting arrangement. You can use Linux for important things, but you will have to leave the session and reboot the machine into Windows to use iTunes. I prefer this option because in my experience this is the most stable and trouble-free way to use iTunes, especially in conjunction with an iPhone3G or late model iPod;

2. Install Windows (XP SP2 or later) into a virtual machine manager and install iTunes into that;

3. Install the WINE Windows compatibility layer and hope iTunes will work under that (last time I checked, it didn't but it's been awhile since I tried it).  

You could also ask MIT for the name of the genius who locked this particular service into a proprietary and expensive single-vendor arrangement.  When you find it give it a swift kick in the shins.

---

### Post by rakan_dr on 2008-12-02
> **rbmorse said:**
> 

You could also ask MIT for the name of the genius who locked this particular service into a proprietary and expensive single-vendor arrangement.  When you find it give it a swift kick in the shins.

he must be a nerd who doesn't know anything except studying ;)

---

### Post by Mr. Picklesworth on 2009-02-13
Just thought I should bump this...
iTunes U is a beautiful interface. I agree it would be nice to have that in a free format! (MiroGuide, anyone?)

However, my suspicion (correct me if wrong) is that this just aggregates Open Courseware. For example, MIT provides Open Courseware quite nicely :)

Here is the Open Courseware Consortium: [http://www.ocwconsortium.org/](http://www.ocwconsortium.org/)
Here is MIT's material: [http://ocw.mit.edu/index.html](http://ocw.mit.edu/index.html)

---

### Post by celticbhoy on 2009-02-13
As far as I know itunes will work under wine if it is version 7.4.

---

### Post by NoBugs! on 2009-02-14
Did you try the podcast section of this [help page]("https://help.ubuntu.com/community/RestrictedFormats/iTunesMusicStore")? It should work.

---

### Post by Mr. Picklesworth on 2009-07-26
Bumping this thread with a solution!
First of all, this works best with Miro, which you can download from Ubuntu's repositories.

Here's a blog post:
[http://www.greenhughes.com/content/enjoying-open-university-podcasts-miro](http://www.greenhughes.com/content/enjoying-open-university-podcasts-miro)

Here is OpenUniversity, which feeds iTunes U:
[http://podcast.open.ac.uk/](http://podcast.open.ac.uk/)

You can subscribe to that site's RSS feeds or use the Add Site feature in Miro.

---

### Post by NoBugs! on 2009-08-25
Thanks for the info! That's great that OU is putting this online, but I don't think most colleges offer this. This should work for the other itunesu sites:
[http://www.fritscher.ch/blog/2009/05/13/browsing-itunesu-without-intalling-itunes/](http://www.fritscher.ch/blog/2009/05/13/browsing-itunesu-without-intalling-itunes/)

---

### Post by liamgh on 2009-08-25
You might also be interested to know that OU podcasts are available through Boxee too, see: [http://www.greenhughes.com/content/rising-boxee-developer-challenge-open-university-app](http://www.greenhughes.com/content/rising-boxee-developer-challenge-open-university-app) :) (As is OpenCourseWare).

---

### Post by steve.dake on 2011-01-21
Here is an app that will work:
[http://www.ubuntugeek.com/tunesviewer-itunes-university-media-and-podcasts-in-linux.html](http://www.ubuntugeek.com/tunesviewer-itunes-university-media-and-podcasts-in-linux.html)

---

