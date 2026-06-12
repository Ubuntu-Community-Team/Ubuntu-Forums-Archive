---
title: "my only two problems with ubuntu"
date: 2005-07-24
forum: Hardware &amp; Laptops
---

### Post by woedend on 2005-07-24
Ubuntu is a great 'project', but seems to throw me a couple problems that prevent me from using it full time.  The first is a strange problem...when my monitor goes into standby/suspend mode, and I bring it back up by moving the mouse, the ubuntu screen is too big for the monitor...the X on maximized applications is out of view, as with the scrollbar...over the period of about 5 minuetes it slowly shrinks itself back onto the screen.  Weird.  The other...sound.  I've searched for this problem and found it a million times...static'd out sound when pcm is full blast.  why?  I use fedora core 4 mainly now only because of those 2 problems...and they do not exist in fedora at all.  Anyone point me in the right direction here?

---

### Post by varunus on 2005-07-24
The first one, I have no idea.  That sounds really strange...The fact that it shrinks back means it probably isn't the software directly, but more Ubuntu is triggering something on your monitor...I don't know, though.

For the second problem, what sound card do you have?  The problem could be card dependent.

Part of the solution comes from the fact that Fedora Core 4 has a newer ALSA than Ubuntu, if I'm not mistaken.  Breezy will have the same version, I think.  One way to get around this is to just not max out the sound; I've never needed to go up that high (my laptop has a hardware spinner for sound, and I leave PCM at 60% since any louder I lose the control I want over the volume).  ALSA 1.09 is going to be great; automatic dmixing of sound streams for cards that need it, and much better driver support from what I've seen.

---

### Post by woedend on 2005-07-24
[QUOTE=varunus]The first one, I have no idea.  That sounds really strange...The fact that it shrinks back means it probably isn't the software directly, but more Ubuntu is triggering something on your monitor...I don't know, though.

For the second problem, what sound card do you have?  The problem could be card dependent.

Part of the solution comes from the fact that Fedora Core 4 has a newer ALSA than Ubuntu, if I'm not mistaken.  Breezy will have the same version, I think.  One way to get around this is to just not max out the sound; I've never needed to go up that high (my laptop has a hardware spinner for sound, and I leave PCM at 60% since any louder I lose the control I want over the volume).  ALSA 1.09 is going to be great; automatic dmixing of sound streams for cards that need it, and much better driver support from what I've seen.[/QUOTE]
 thank you for your reply...on the first one...that is strange...but onto the second.  I use my computer as an alarm clock.  Not only is the static bad at high volumes, it doesn't sound all that loud because of it.  I need at least 85% pcm, and thats about when it starts to get nasty.  Can I put newer alsa on ubuntu?  if so how?

---

