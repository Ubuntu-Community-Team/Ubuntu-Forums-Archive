---
title: "[SOLVED] fglrx instead of mesa"
date: 2008-07-21
forum: General Help
---

### Post by Archimedes0212 on 2008-07-21
Hey All -

I'm having INCREDIBLE difficulties getting fglrx working instead of mesa on my ubuntu Hardy system.  I've installed fglrx several ways and none seem to work (I've done it from the terminal AND from Envy).  Everytime that I check my graphics, using fglrxinfo, it tells me I'm still using mesa.  

Compiz and my regular graphics work fine, but the problem comes when I want to watch a movie in fullscreen or in a size that is larger than half the size of my monitor.  Everything slows down and my video/audio gets desynchronized.  (I know the problem isnt in the video file because it works fine on my Windows XP system).

Does anybody have any ideas how to get my system to use fglrx or to fix my media watching problems??  

Many thanks in advance.

---

### Post by rbmorse on 2008-07-21
I'm sort of surprised that Envy didn't work.  

What's your hardware?

---

### Post by jocko on 2008-07-21
> **Archimedes0212 said:**
> Hey All -

I'm having INCREDIBLE difficulties getting fglrx working instead of mesa on my ubuntu Hardy system.  I've installed fglrx several ways and none seem to work (I've done it from the terminal AND from Envy).  Everytime that I check my graphics, using [COLOR=Red]fglrxinfo, it tells me I'm still using mesa.  [/COLOR]

[COLOR=Red] Compiz and my regular graphics work fine,[/COLOR] but the problem comes when I want to watch a movie in fullscreen or in a size that is larger than half the size of my monitor.  Everything slows down and my video/audio gets desynchronized.  (I know the problem isnt in the video file because it works fine on my Windows XP system).

Does anybody have any ideas how to get my system to use fglrx or to fix my media watching problems??  

Many thanks in advance.

If fglrxinfo claims you use mesa, but compiz works, your problem is that fglrxinfo is wrong. There is no way you can get compiz working with mesa and fglrx.
I bet you have xgl installed? That usually causes fglrxinfo to *incorrectly* claim that mesa is in use instead of fglrx.
Uninstall xserver-xgl unless you need it (since about a year ago, ati's drivers support compositing and aiglx, so there is no need for xgl if you use hardy. I you use gutsy with the repo version of fglrx, you need to keep xgl if you want compiz to work).

---

### Post by Archimedes0212 on 2008-07-21
I have an ati graphics card, don't know anymore, sorry running on an IBM Thinkpad T60.

And yes, I do have xgl installed.  So you're saying that I don't need xgl period.  I can have compiz and everything work perfectly fine even if I uninstall it?


Thanks for the responses guys (or gals).

---

### Post by Archimedes0212 on 2008-07-21
thanks, it worked

---

### Post by Archimedes0212 on 2008-07-22
Okay, new problem branching off the old one.

So it's using my ati graphics now - I uninstalled xserver-xgl and am using the gnome session instead of the gnome + XGL.  

When I logged in the first time, my keyboard was really screwed up.  I went to keyboard layout and changed it back to 'us basic'.  This morning when I turned my system on again and logged in, my keyboard was messed up again.  I went to the layout manager and it still said 'us basic'.  I clicked apply and then okay and it went back to normal.

Do any of you know a way to keep this from happening??  Thanks.

---

### Post by chalewa on 2008-07-22
> **Archimedes0212 said:**
> Okay, new problem branching off the old one.

So it's using my ati graphics now - I uninstalled xserver-xgl and am using the gnome session instead of the gnome + XGL.  

When I logged in the first time, my keyboard was really screwed up.  I went to keyboard layout and changed it back to 'us basic'.  This morning when I turned my system on again and logged in, my keyboard was messed up again.  I went to the layout manager and it still said 'us basic'.  I clicked apply and then okay and it went back to normal.

Do any of you know a way to keep this from happening??  Thanks.


i don't think that this would have anything to do with your graphics card tho. 

but i don't know how to solve your problem. did you do some searches for keyboard problems?

---

### Post by danwood76 on 2008-07-22
You need to change it in the xorg.conf file.

so:
```

sudo gedit /etc/X11/xorg.conf

```
And make sure unde rthe keyboard section the correct layout is set.

---

### Post by Archimedes0212 on 2008-07-22
thanks danwood.  I'll do that when I get home.

---

### Post by danwood76 on 2008-07-22
Oh by the way you can do a little menu based config of the xorg.conf file with:
```

sudo dpkg-reconfigure xserver-xorg

```
You may then need to make fglrx reinstall its settings in there:
```

sudo aticonfig --initial -f

```

---

### Post by Archimedes0212 on 2008-07-23
thanks danwood.  I modified the xorg.conf and it's perfectly fine now.

---

### Post by QuimNuss on 2008-11-05
Waho... I've been going with this issue since Hardy...
However, resetting the keyboard layout didn't work for me. Any hint on how to do it?

I'll try to figure it out, however, Deeply thanks for solving this issue! (I feel a bit dumb as it only was an unnecessary packet)

---

### Post by QuimNuss on 2008-11-06
I've just found a workaround by now... using the command
```
setxkbmap -model pc105 -layout es -variant basic
```

sets my layout to spanish catalan variant. (you should use the option you'd like for that). I have to put the command on the session startup... I don't like it, but it works by now.

Any clue on how to solve the flickering? It only happens when I run compiz. It's not critical as I already used another user for playing, but yet...

---

