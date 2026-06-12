---
title: "X be busted?"
date: 2006-01-16
forum: Installation &amp; Upgrades
---

### Post by DirtDawg on 2006-01-16
Goodness I'm having troubles. 

I just installed Breezy on My Dell after some trouble, but there's no GUI. I get a message that X Window System won't load, gives me some info which I cannot understand, then jets me to a command line.

It tells me to "restart when GDM is configured correctly" (how rude!). 
I'm using a Nvidia GeForce FX 5500, if that has something to do with it?

Any help would be appreciated. I've been digging through the forums, but no luck yet. 

Thank you.

---

### Post by DirtDawg on 2006-01-16
Okay, nobody's responded or even looked at this post, so I'm going to update.

From a few posts I found, I figured out to enter:
sudo dpkg-reconfigure xserver-xorg
I did this. However, most of the questions I had *no idea* what the thing was asking so I found myself just pressing Enter a lot. 
When it asked about my graphics card, I told it I had a vesa (I believe. The name started with V anyway). I read in a post it was considered a kind of "generic" driver. 

Anyway, now I have a GUI, but I'm pretty sure I faked my way into getting things to work. And who knows if I screwed something up while I was "answering" all those questions. 

So I wondered if anyone could clue me in as to what exactly I did, if there may be some subtle consequences for my actions which I am not aware of yet and, if so, how might I fix them?

Thanks again.

P.S. So far, I LOVE it!

---

### Post by newuser111 on 2006-01-16
what you did seems fine, using vesa is fine but no hardware acceleration

i recommend installing the nvidia drivers

[http://makuchaku.info/amnesty/#installnvidiadriver](http://makuchaku.info/amnesty/#installnvidiadriver)

---

### Post by DirtDawg on 2006-01-16
Excellent. Thank you.

---

