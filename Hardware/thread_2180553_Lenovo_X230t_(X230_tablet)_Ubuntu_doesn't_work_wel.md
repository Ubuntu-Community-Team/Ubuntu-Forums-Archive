---
title: "Lenovo X230t (X230 tablet) Ubuntu doesn't work well. Should I work on 13.04 or 13.10?"
date: 2013-10-13
forum: Hardware
---

### Post by cpbl on 2013-10-13
I have got a Lenovo X230t which is their 12" convertible tablet. Unfortunately, despite the optimistic references to this thread, [http://ubuntuforums.org/showthread.php?t=2074106](http://ubuntuforums.org/showthread.php?t=2074106), numerous key features are not supported under Ubuntu 13.04 (tablet mode, keyboard light, fingerprint reader, ...).   I would love to see an up to date account from anyone for how an unsophisticated user can make use of this machine. 

My question here, though, is that given that a lot of the documentation seems to be for 12.04 or X220t, and I have an X230t, should I be trying to work with the (still beta and generally buggy) 13.10 or with 13.04 (or even the older LTS)?

---

### Post by cpbl on 2013-10-24
I've tried to put a summary and status of my troubles with the Lenovo X230T and Ubuntu 13.04/13.10 here: [http://cpbl.wordpress.com/2013/10/24/ubuntu-13-04-and-13-10-on-lenovo-x230x230t-convertible-tablet/](http://cpbl.wordpress.com/2013/10/24/ubuntu-13-04-and-13-10-on-lenovo-x230x230t-convertible-tablet/)

Overall, this hardware is NOT compatible with Ubuntu yet.

---

### Post by Favux on 2013-10-24
Hi cpbl,

I guess assesment of compatability depends a bit on perspective.  When I started really using linux about 5 years ago many laptops were non-functional.  This was due to lack of OEM support of course.  So if you can load the linux Distro on it and use it as functioning laptop to me that counts as compatible.  I would not expect some extra features of the laptop to be necessarily supported though.  But I would hope for a "simple" work around.  I don't consider it reasonable to expect the Distros to support every laptop model's every feature.

For example at the heart of Martin Ueding&#8217;s think-rotate package's think-rotate script is this line:
```
rotation="$(xrandr -q --verbose | grep 'connected' | grep "$internal" | egrep -o '\) (normal|left|inverted|right) \(' | egrep -o '(normal|left|inverted|right)')"
```
This happens to be almost identical to the line in my Rotation HOW TO that I started 5 years ago (11/2008) when I was a newbie of only a few weeks.  See method 1 scripts:  [http://ubuntuforums.org/showthread.php?t=996830](http://ubuntuforums.org/showthread.php?t=996830)  Notice the auto script in method 2.  Anyway although I was still climbing the command line learning curve (still am for that matter) I was already able to handle rotation for my tablet PC.  There is an updated [Rotation HOW TO]("http://forums.linuxmint.com/viewtopic.php?f=42&t=110395").  Where you'll also find tips on getting the bezel buttons working.  You probably saw links to this on the thread you reference.  That stuff is admittedly more involved.

By the way thanks for pointing out Martin's package.  I was unaware of it.  Ordinarily I would have referred you to Magick Rotation:  [https://launchpad.net/magick-rotation](https://launchpad.net/magick-rotation)  But starting with Raring (13.04) Ubuntu's Unity desktop implemented the App Indicator spec. for the System Tray.  Which Magick didn't comply to so Magick wouldn't appear in the System Tray any longer.  I finally go around writing a App Indicator for Magick in the last couple of days.  As I sort of suspected from what I had seen (documentation very scarce to non-existent) following the App Indicator specification cripples some of Magick's functionality.  I'll probably load an alpha test version to the devel branch in a few days where you could get a tar to test.

As far as multi-touch goes these are still early days.  The kernel and the X Server only got real multi-touch support within the past year or two basically.  This Linux Wacom wiki page discusses Wacom multi-touch and how it interacts with the Ubuntu Unity desktop's mult-touch support:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Multitouch)  As should be coming clear part of the environment is navigating the various UI design choices of different segments of the community including  Canonical's.  Canonical continues to do a lot of mult-touch work for its mobile initiative and that should be coming into the Desktop at some point.

---

### Post by cpbl on 2013-10-24
Hi Favux. Thanks for reading and for your thoughts.

I appreciate your view, and tolerance, but I really don't see the need for ambiguity in labels. If something is marked as fully compatible, one would expect the hardware to work. If the X230 works but the tablet features don't, don't call the X230T compatible. If a significant hardware feature like backlighting doesn't work, that's fine that there's demand for it as a Linux machine anyway, but the situation shouldn't be summarized by saying it works.

Beyond thinking more detailed information is better, I actually think (completely naively) much higher standards would be enormously productive. Right now, the value of having your hardware certified is not very much, since it means nothing. If as you claim, most machines don't work *really* well with Linux, then that should mean that if someone like Canonical or Lenovo made sure one or a few did, they would sell like hotcakes among the niche market. In fact, the situation is that if one wants to buy a newish computer and know in advance how it will work, it's still nearly impossible.

I think tolerance for crappy support should be decreased, which would put more pressure on manufacturers and distributions to cooperate. I have been using mostly Unix and Linux since 1991, but not as a hobby. I now have money to throw around, yet don't know where to spend it to just get a good production machine and OS that doesn't need the professional user to be a part-time hacker. I think the software is so great that this makes me sad. 

Anyway, this was not meant to be a rant or to be sad, as I am optimistic enough about the X230T that I'm using it. And as I mentioned in my post, there is LOTS that works out of the box, of course (though I didn't mention yet all the troubles with power consumption performance).

Thanks again, especially for your code contributions! 
Chris

p.s. [Edit:] I see my post is nearly completely off-topic now; sorry. Since it is, already, let me add: I wish there was a culture of solving much more of our open-source problems through crowd funding. I've been waiting expectantly for that for a decade! If something is broken on an X230, there must be enough users willing to pitch in to pay someone somewhere to really solve it! And such output would naturally be open.

---

