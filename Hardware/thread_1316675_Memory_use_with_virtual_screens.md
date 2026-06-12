---
title: "Memory use with virtual screens"
date: 2009-11-06
forum: Hardware
---

### Post by oldmankit on 2009-11-06
I'm used to using my laptop under windows to give presentations.  I like using the 'extended desktop' - the audience sees the powerpoint presentation, and I see the 'presenter mode'.  This is so useful, as I can see the slide notes, timings, etc. etc. 

Well today I've worked it out using ubuntu.

I've just got my head around virtual screens, thanks to this great guide:
[http://wiki.debian.org/XStrikeForce/HowToRandR12](http://wiki.debian.org/XStrikeForce/HowToRandR12)

Now I have my laptop screen plus a projector screen displaying different things, placed on one big 'virtual screen'.  Well, not huge: 2560 x 1024.

I've also got openoffice working with something very similar to "presenter mode".  Actually, it's better than microsoft's version, at least visually.

Finally, my question.  When connecting extra screens, everything can be done using xrandr.  These are non-persistent changes.  However, to use a virtual desktop in the first place, the file /etc/X11/xorg.conf needs a few extra lines in:
```
    SubSection "Display"
        Virtual    2560 1024
```These are persistent changes, which I guess are called at every login.

The guide I mentioned above said that large virtual screens requires large amounts of memory.  I don't want the virtual screen to be using lots of memory when I'm not actually connected to a second screen.

Am I being super-naiive here?  Is the setting in /etc/X11/xorg.conf even relevant to memory?

Thanks,
oldmankit :D

---

