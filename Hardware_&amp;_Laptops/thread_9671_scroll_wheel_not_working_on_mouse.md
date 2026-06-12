---
title: "scroll wheel not working on mouse"
date: 2004-12-30
forum: Hardware &amp; Laptops
---

### Post by Datchew on 2004-12-30
I saw a couple similar posts, but they had different problems. 
In (GASP) windows, when i hold down the mouse scroll wheel, I can scroll around in a spreadsheet, etc, just by moving the mouse. 

That feature doesn't work in Ubuntu. 
I'm about 4 days into this Linux stuff and love it so far... but go easy on me. 
Keep it simple please... spoon feed me.   :mrgreen: 
Thanks much.

---

### Post by Mira on 2005-01-01
Hack no...you take the spoon and I'll tell you where you're plate is! ;-)

You are gonna need a good text editor for this...just one you feel comfy with. That'll be your spoon. Advanced Text Editor/Kwrite is my fave one.
Now open /etc/X11/XF86Config-4....or something with that kinda name.
You see the huge amount  of text in it? Good! Find the stuff that says "Mouse",
check that you have /dev/psaux for driver and IMPS/2 for protocol.

Surprise! Mice have protocols! And they're often set wrong for wheelmice, which is pretty much amazing with so many people using wheelmice and those wheels being so addictive...

---

### Post by Datchew on 2005-01-29
did that. 

i put the /dev/psaux stuff in quotes like everything else was. 
still not working. 

any other ideas?
thanks much .

---

### Post by poofyhairguy on 2005-01-31
[QUOTE=Datchew]I saw a couple similar posts, but they had different problems. 
In (GASP) windows, when i hold down the mouse scroll wheel, I can scroll around in a spreadsheet, etc, just by moving the mouse. 

[/QUOTE]

Ok. It took me reading your post a couple times to get what you were saying. 

I know the feature you are talking about. I've looked myself, and I have found nothing like this in Linux. 

Sorry for the negative, but at least it is an answer.

---

### Post by az on 2005-01-31
So i gather two things:
1- You got X working.
2- Your scroll button scrolls, but you would like it to click and hold your botton and get a two-dimentional scroll thing?

Is this correct?

If so, there used to be some plugins for mozilla that would do that.  Other apps can do it too.  There is not a system-wide feature like that.

---

### Post by maverick340 on 2007-08-10
I dunno about 6.10 but some have faced this prob in 7.04 too. My self incuded. WEll i use Opera Web Browser. In that , go to Tools>Preferences >SHortcuts > Middle Click Options.
In Set Middle Click Options, check the start panning option. Done !

---

### Post by Fireman_DJ on 2007-10-04
My god, I could kiss you. If you were a girl and we were in the same part of the world.
I've been thru the Opera shortcut options. Completely missed the little middle click button there.

Opera + Ubuntu rules.

---

