---
title: "Flash Player Plug-ins for Firefox Don't Install or Don't Workl"
date: 2009-04-26
forum: Installation &amp; Upgrades
---

### Post by zonkamatic on 2009-04-26
I'm using Firefox 3.0 under Ubuntu Linux, version 8. When I tried to install the Adobe Flash Player plug-in, the install would hang, so I tired swfdec, version 6.0. It plays SOME videos, but, when I go to a place with large files, like youtube or markfiore.com, I click on the button and it shows the "downloading" screen and just hangs there. I can't update to the latest version of swfdec--tried that, it said that I don't have the right version of libsoup even though I do (there's a dash in the name of the libsoup they're looking for but not in the one that comes with ubuntu).

There's another plug-in out there to play Flash videos. I'd try that, too, but there's no way I could find in the program OR the documentation to

                 ******** REMOVE A PLUG-IN ********* 

This does *****NOT***** mean DISABLE a plug-in. If you DISABLE a plug-in, the program won't go looking for a new plug-in the next time you try to play a video. THAT is what I NEED it to do.

And don't worry--I'm not going to whine at you about the adobe plug-in. I'm going to take that up with adobe. Wish me luck.
Extensions installed:

swfdec 6.0. Latest version is 6.2, but I can't get through the configure script for that. I tried using the Adobe Flash Plug-in, but I couldn't get it to install. The installer process just hung in the middle, and I had to kill -9 it from a terminal window just to get it the heck off my desktop.
Plugins installed:

---

### Post by zonkamatic on 2009-04-27
The issue was resolved.  I removed the swfdec package using the symantec package manager and disabled all video plug-ins.  Then, I went to YouTube and brought up the shortest vid I could find.  It brought up a "get plug-ins" menu that I was able to use to reinstall the latest deb package from adobe.  Works fine now.

---

