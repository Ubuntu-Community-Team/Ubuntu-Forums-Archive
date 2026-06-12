---
title: "If you happen to have trouble with SiS graphic"
date: 2008-12-27
forum: Hardware
---

### Post by Dennis Schulmeister on 2008-12-27
Hi friends,

I know there is quite a lot of discussion on the Internet on how to get SiS graphic chipds running under Ubuntu and Linux in general. While some distros (like Fedora) seem to get them running ok out of the box with other distros it might take some tweaking. It even gets worse because up to this day the manufacturer SiS refuses to release Linux drivers on a regular basis and they especially refuse to release drivers which enable hardware accelaration.

In order to collect all available wisdom and files I started a page on my personal wiki some months ago. This page has been quite a success and got more hits than all other pages of the wiki together. So it soon outgrew my wiki. Thus I decided to migrate all gathered information to its dedicated wiki.

Here it is::guitar:

[http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)
or [http://sis-wiki.homelinux.net](http://sis-wiki.homelinux.net) for short (but with dynDNS ads:()

Please update your existing bookmarks and tell all your friends who happen to have SiS graphic cards about the wiki. Please continue to help me to keep the available information up to date.

Thank you and have a happy new year,
Dennis Schulmeister

---

### Post by zivley on 2009-01-15
> **Dennis Schulmeister said:**
> Hi friends,

I know there is quite a lot of discussion on the Internet on how to get SiS graphic chipds running under Ubuntu and Linux in general. While some distros (like Fedora) seem to get them running ok out of the box with other distros it might take some tweaking. It even gets worse because up to this day the manufacturer SiS refuses to release Linux drivers on a regular basis and they especially refuse to release drivers which enable hardware accelaration.

In order to collect all available wisdom and files I started a page on my personal wiki some months ago. This page has been quite a success and got more hits than all other pages of the wiki together. So it soon outgrew my wiki. Thus I decided to migrate all gathered information to its dedicated wiki.

Here it is::guitar:

[http://ncc-1701a.homelinux.net/~linux-sis/](http://ncc-1701a.homelinux.net/~linux-sis/)
or [http://sis-wiki.homelinux.net](http://sis-wiki.homelinux.net) for short (but with dynDNS ads:()

Please update your existing bookmarks and tell all your friends who happen to have SiS graphic cards about the wiki. Please continue to help me to keep the available information up to date.

Thank you and have a happy new year,
Dennis Schulmeister


I really need this one, but it seems the links you gave us are no longer available, is there a way to get this howto from somewhere else?
Perhaps you can just post it here?
Thanks

---

### Post by Dennis Schulmeister on 2009-01-16
Hi,

if the links don't work this is related to my internet connection. Either it broke down for some unknown reason (unfortunately this happens once in a while) or you tried during just those 5 minutes during night (GMT+1) where it is not available.

The bottom line is the links should still work. Just try it again. If it really doesn't work drop me a message to "dennis (*) windows3.de"

Best, Dennis

---

### Post by zivley on 2009-01-17
You're right, the links still work, it was aparently a temporary problem.
Anyway, none of the solutions worked for us, we still have a problem getting this darn graphic card diplay resolution higher than 800x600, I guess it's not a software problem, perhaps the card is not what we think it is...
I have another PC with the same hardware and I remember fixing it very easily, I can't remember exactly how, and the PC is now disconnected and sitting somewhere, if we can't find another solution, I'll have to plug it in and see how I fixed it there.
Thanks anyway!

---

### Post by Dennis Schulmeister on 2009-01-17
How about the VESA driver? At least this one should work. It might be that you have to add information about HorizSync and VertSync to /etc/X11/xorg.conf but otherwise it should work.

See here: [http://ncc-1701a.homelinux.net/~linux-sis/?page=VesaDriver](http://ncc-1701a.homelinux.net/~linux-sis/?page=VesaDriver)


Best, Dennis

---

### Post by zivley on 2009-01-18
I wasn't sure which one of the drivers I need to download, so I decided to use your guide and give the VESA driver another try, I understood the last time didn't work because I didn't set the Hsync and Vsync. This time it worked!
Thanks a lot!

---

### Post by Dennis Schulmeister on 2009-01-18
Great. I'm glad it worked. :)

Best, Dennis

---

### Post by Dennis Schulmeister on 2009-06-09
Hi people,

this is just to let you know that the wiki still exists and is continously maintained by me. So be sure to check back if you find yourself in trouble with your SiS graphics. :)

Best,
Dennis

---

