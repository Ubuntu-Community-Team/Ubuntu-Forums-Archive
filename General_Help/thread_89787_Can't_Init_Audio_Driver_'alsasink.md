---
title: "Can't Init Audio Driver 'alsasink"
date: 2005-11-13
forum: General Help
---

### Post by derek19 on 2005-11-13
When i go to this site:

[http://football.myfantasyleague.com/2005/home/32026](http://football.myfantasyleague.com/2005/home/32026)

I get this error:

Can't init audio driver 'alsasink' - trying another one....

Then comes back and tell me it can't find one then closes KDE

Anyone have any idea?

---

### Post by mlomker on 2005-11-13
Do you mean that it closes your web browser?  I just opened it in Firefox without a problem.

---

### Post by derek19 on 2005-11-13
After i posted, i opened it in firefox but i didn't have any sound.

---

### Post by joakim2 on 2005-11-13
Happens to me every time I try to view a video clip with Konqueror - both with 3.4.3 and 3.5...

---

### Post by Rob2687 on 2005-11-14
Yeah I get the same thing whenever I try to view a wmv or quicktime video on a website in konqueror 3.5

---

### Post by lerrup on 2005-11-14
I would suggest that it is [this bug]("https://bugzilla.ubuntu.com/show_bug.cgi?id=15270").

If you want to add any comments it might help with finding what the problem is.

---

### Post by skyboy on 2005-11-14
worked great both on Konqueror and Firefox and I even had  Amarok playing music (xine sound server) at the same time. 
I use Breezy with KDE3.5rc1

---

### Post by skyboy on 2005-11-14
Sure you didn't have another application (like skype) blocking the sound server ??

---

### Post by lerrup on 2005-11-14
[QUOTE=skyboy]Sure you didn't have another application (like skype) blocking the sound server ??[/QUOTE]

I don't, but I do have Gnome installed as well.

Can anyone else give me the info about their setup so we can try and work this out?  If you have a crash are you running KDE exclusively or do you have other WMs installed?

---

### Post by joakim2 on 2005-11-14
Switching from the Gstreamer engine to Xine did it for me. Now video clips appear to be playing (only tried a few so far). I still have some major issues with one of my favorite sites that I use to listen to the radio during the work day :)

[http://www.sr.se/p3/webbkanaler/](http://www.sr.se/p3/webbkanaler/)

First of all I had to change the browser identification for sr.se to I.E to even get it to stop complaining that I wasn't accepting cookies (go figure.. bad site design I suppose). But clicking on any of the links that say "Lyssna" crashes Konqueror to no end...

EDIT: switching engines that Kaffeine uses, that is

---

### Post by lerrup on 2005-11-18
Still not working for me...

Weirdly, the realplayer problem is Konqueror only as it works fine as a standalone or embedded in firefox/epiphany.

Any Konqueror experts out there?

---

### Post by André on 2006-02-27
Hi,

sorry for bumping this but did you guys finally find an answer to this?

Konqueror is such a nice browser but this bug really scares me...

Any ideas finally?

Andre

---

### Post by tate on 2006-02-28
i'm still having this problem as well. 

using KDE 3.5.1-0ubuntu0breezy1

konqueror gives the same set of errors and then closes.

any new news here?

---

