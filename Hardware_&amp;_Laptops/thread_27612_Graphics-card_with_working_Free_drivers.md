---
title: "Graphics-card with working Free drivers?"
date: 2005-04-16
forum: Hardware &amp; Laptops
---

### Post by Reverie on 2005-04-16
Closed source nvidia and fglrx drivers freezes the computer, happens to me, my brother, and a friend. It worked fine with xfree, but I'm finally too fed up trying to fix these problems, so instead, my question is this:

Does anyone know of an okay 3d graphics card with full FREE driver-support, e.g. included with x.org. It doesn't have to run Doom3, just have okay (not super) 3d support so we can play with experimental free software and take the occasional shot at games for lan-parties. The only non-ati/nvidia card I have tried was a Matrox (years ago), and it was great except for it's closed source requirement for some things (HAL?), what is it with these guys? Do hardware manufacturers hate F/OSS?

Have any of you had any good personal experiences, or have some links handy that provides this information? I currently use the free 'nv' drivers and it gives me a nice giddy feeling, I like that, but [we] want 3d and are willing to pay for a new card.

Also, keep up the good work, Ubuntu GNU/Linux is the best distrobution I have ever seen, hope you can get rid of the need for closed drivers some day, good luck with the next release.

---

### Post by skwid on 2005-04-16
[QUOTE=Reverie]Closed source nvidia and fglrx drivers freezes the computer, happens to me, my brother, and a friend. It worked fine with xfree, but I'm finally too fed up trying to fix these problems, so instead, my question is this:

Does anyone know of an okay 3d graphics card with full FREE driver-support, e.g. included with x.org. It doesn't have to run Doom3, just have okay (not super) 3d support so we can play with experimental free software and take the occasional shot at games for lan-parties. The only non-ati/nvidia card I have tried was a Matrox (years ago), and it was great except for it's closed source requirement for some things (HAL?), what is it with these guys? Do hardware manufacturers hate F/OSS?

Have any of you had any good personal experiences, or have some links handy that provides this information? I currently use the free 'nv' drivers and it gives me a nice giddy feeling, I like that, but [we] want 3d and are willing to pay for a new card.

Also, keep up the good work, Ubuntu GNU/Linux is the best distrobution I have ever seen, hope you can get rid of the need for closed drivers some day, good luck with the next release.[/QUOTE]
 I've never seen nvidia or fglrx drivers totally lock a pc up...   I am not sure about an alternative 3d video card.  Might check with the MESA people and see what they support.

---

### Post by Buffalo Soldier on 2005-04-16
Reverie,

Silly question from me. Which driver did you install? From repository or nvidia website?

---

### Post by denzilla on 2005-04-16
I'm running a ti4600 with the repository drivers. no issues :)

---

### Post by Reverie on 2005-04-17
Hmm, I didn't find much useful material on the mesa or dri websites, what I'm looking for I guess is a list (personal experience preferred) of Ubuntu-friendly 3d graphics cards with open source drivers, "why?" I see you ask, and the reason is simple, these are the problems you get with closed source drivers (taken from your own forums):

[http://www.ubuntuforums.org/showthread.php?t=27440](http://www.ubuntuforums.org/showthread.php?t=27440)
[http://www.ubuntuforums.org/showthread.php?t=27272](http://www.ubuntuforums.org/showthread.php?t=27272)
[http://www.ubuntuforums.org/showthread.php?t=24703](http://www.ubuntuforums.org/showthread.php?t=24703)
[http://www.ubuntuforums.org/showthread.php?t=24982](http://www.ubuntuforums.org/showthread.php?t=24982)
[http://www.ubuntuforums.org/showthread.php?t=24033](http://www.ubuntuforums.org/showthread.php?t=24033)

The problem is that you have no way of knowing what the actual problem is when using closed source drivers, only way to debug is to do random stuff until the problem goes away (with help from forums and google), fixing these issues usually takes a few (desperate) hours trying all sorts of crazy stunts, and then start over on your friends and families boxes. So instead of wasting a hundred hours (I'm a geek) every year "fixing" these problems, I would like to start buying and recommending good and F/OSS friendly graphics cards. 

Unfortunately there doesn't seem to exist such a card, and you can no longer buy the old cards that are well supported in the stores, please tell me I'm wrong though, please. Some of you must have faced the same troubles.


skwid: I'm afraid that's the case, but thanks for the reference, it gave me something to go on, albeit it doesn't look good ):
Buffalo: I've tried them all, if I spend more hours trying I'm sure I can find a fix, my point is I don't want to anymore.
denzilla: I'm happy for you ;)

---

### Post by moopere on 2005-04-17
[QUOTE=Reverie]...The only non-ati/nvidia card I have tried was a Matrox (years ago), and it was great except for it's closed source requirement for some things (HAL?)...[/QUOTE]

Upon reading your post I immediately thought of Matrox.  However, the snippet above has me wondering.  Are you sure about this?  I was completely unaware of any closed source requirement when using Matrox cards.  I use them frequently at work (not Parhelia cards though) and they seem to be speedy and stable and install just fine using drivers that come with Debian (free) or Ubuntu (possibly not free, maybe in restricted??? I've not actually checked this)

Matrox cards can be hard to find on the shelves thee days, probably because the major mind share in the gaming PC world is with Nvidia or ATI, but they are around and are reasonably priced and good performers.

Cheers,
Craig

---

