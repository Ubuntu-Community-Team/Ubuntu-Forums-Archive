---
title: "Video card - ATI - Rage Fury 128 Pro"
date: 2007-05-07
forum: Hardware &amp; Laptops
---

### Post by kulus1969 on 2007-05-07
Hi,  I've given up on trying to get this card to work.  I now use a NVidia Card.

However, I would like to try again because I really liked this card in Windows.  I was disappointed when it didn't work properly in Ubuntu.

As far as I can tell, it has the following problems:

1. 3D Acceleration doesn't work
2. Video In/Video Out doesn't work.

That prevents it from playing any of the more interesting games ie. 3D Games as well as showing any slideshows, games, etc..  on the tv.  It also prevents me from recording from my VCR/DVD player to my computer.

As far as I can tell there is no known solution to these problems yet.

How do I let the development team know about this and ask them to work on a fix for this?

Kev

---

### Post by Kir360 on 2007-05-24
Hey!!!I've the Same Problem....But I'm Disappointed 2 know there's no Soln 4 this...

---

### Post by stephenlittleton on 2007-06-17
:popcorn:

I dont have any clue why the ati doesnt work either.  I even used an old tnt2 card in place of it... model 64, But neither work.  This sucks, I wish I wouldnt have sold my video card... Anyways, the card works for 3d accelleration in windows, as good as you can get without T&L... so maybe thats the problem, we cant support T&L so therefore nothing works.  Who knows, not me yet.

Gonna pop some popcorn and wait for some replies... it might be a minute

---

### Post by Dan Hammond on 2007-06-19
I have that video card and i can't get it to work either, it was fine with windows but when i switched to ubuntu all the 3d stuff it used to do stopped, i did try different drivers for it but alas no luck, i had to reconfigure X 'cos they didn't work and i messed it up. Can't believe its impossible but it doesn't seem there are many answers to the problem.

---

### Post by Dan Hammond on 2007-06-19
Reading this made me go hunting for drivers again, something i had largely given up, i managed to found this and just installed it >> [http://downloads.vnunet.com/download/33679.html](http://downloads.vnunet.com/download/33679.html) i hope it works but i have yet to restart X 'cos i still need my computer for a little while. I will let you know if it works or not.

Ok i said that i would let you know if it works, it doesn't, i had to reinstall xserver-xorg-video-ati in the command line when i restrted X, that driver works the best i think.

---

### Post by Kubunteando on 2007-06-19
I have 3D acceleration with that card using the Open Source drivers.

Check:

[http://dri.freedesktop.org/wiki/](http://dri.freedesktop.org/wiki/)

The TV input and output I have not tested it, try to have a look at GATOS:

[http://gatos.sourceforge.net/](http://gatos.sourceforge.net/)

The software is in the repositories. There is a note saying that at the moment is not compatible with Direct Rendering (HW 3D acceleration)

---

### Post by stephenlittleton on 2007-06-26
Man, i have been installing on and off for so many days trying to get it going... I got some open gl stuff to work, such as screen savers and compiz, but other than that beryl and emerald and the wobbly windows dont work!!! ARG!

---

