---
title: "KDE 3.5rc2: Konqueror seems really unstable"
date: 2005-11-28
forum: General Help
---

### Post by elempoimen on 2005-11-28
Has anyone else noticed that Konqueror seems really unstable when in web browser mode?

Does anyone have any tips for solving this problem?  It seems to happen most often on multimedia pages, but not necessarily ones calling the same plugins...so I can't blame a particular plugin.

---

### Post by Wizzard on 2005-11-28
What do you mean by "seems to be unstable"? I have KDE 3.5 RC2 and it is quite stable, but sometimes a little slow.

---

### Post by elempoimen on 2005-11-28
Literally unstable.

Konqueror (and only Konqueror) crashes all the time while web browsing.

---

### Post by shakin on 2005-11-28
[QUOTE=elempoimen]Literally unstable.

Konqueror (and only Konqueror) crashes all the time while web browsing.[/QUOTE]

I have noticed that it can crash when viewing some embedded video, but not all. I'll get two or three alert windows that I need to click 'ok' on and then the app shuts down.

I only have this problem about once a week when I'm goofing off at work, but if you  happen to visit a lot of pages with embedded video I'm sure it must be frustrating.

---

### Post by elempoimen on 2005-11-28
Just one, really--CNN.  It is frustrating.  What video player are you using? I've tried both kmplayer with the mplayer backend and the mozilla mplayer plugin.  Just for giggles, I'm about to try kmplayer with Xine, which is actually my preferred mp anyway.

---

### Post by hvbakel on 2005-11-28
I'm having the same problem, I don't think it's related to the video player though. If you go to the video page directly via [http://edition.cnn.com/video/player/player.html](http://edition.cnn.com/video/player/player.html), there tends to be a lot less crashing. I've already submitted a bug report on this at: [http://bugs.kde.org/show_bug.cgi?id=117142](http://bugs.kde.org/show_bug.cgi?id=117142), feel free to vote for it :)

---

### Post by elempoimen on 2005-11-28
You're absolutely right.  And I've voted.  Thanks!

---

### Post by Brando569 on 2005-11-29
isnt konqueror based off of the mozilla code? (or i could be wrong) if so v1.5 is in beta right now, and i have the same bugs you guys seem to be having

---

### Post by Wizzard on 2005-11-29
[QUOTE=shakin]I have noticed that it can crash when viewing some embedded video, but not all. I'll get two or three alert windows that I need to click 'ok' on and then the app shuts down.

I only have this problem about once a week when I'm goofing off at work, but if you  happen to visit a lot of pages with embedded video I'm sure it must be frustrating.[/QUOTE]

Just one offtopic question, where did you find KMplayer? It is not in official repository, is it?

---

### Post by victorche on 2005-11-29
3.5 Final is out ;)
[ftp://ftp.kde.org/pub/kde/stable/3.5/kubuntu](ftp://ftp.kde.org/pub/kde/stable/3.5/kubuntu)

---

### Post by getaceres on 2005-11-29
3.5rc2 and final are the same, so the same bugs are present.
Well, for the konqueror bugs. I had it all the time when I was using the kaffeine package provided by kubuntu. Now I have downloaded and compiled the last version of kaffeine and it's much much more stable.
When it fails in a multimedia page, it usually is because of a bug in the media player  (by the way, most multimedia applications are less bogus when you compile they by yourself).

---

### Post by elempoimen on 2005-11-29
[QUOTE=Brando569]isnt konqueror based off of the mozilla code? (or i could be wrong) if so v1.5 is in beta right now, and i have the same bugs you guys seem to be having[/QUOTE]No.  And the KHTML developers would probably shoot you if they knew you thought that. ;) Konqueror/KHTML is a completely separate work from Mozilla, with no shared code AFAIK.  The rendering engine for Mozilla is Gecko, and the rendering engine for Konqueror is KHTML, which is also the same engine upon which Apple's Safari browser is based.

And I did see that they upgraded rc2 to final--and there's only 4 packages that are different.  Unfortunately, none of them are Konqueror. :(  But there is a new Kmail, which is good because the old one had some issues as well.

---

