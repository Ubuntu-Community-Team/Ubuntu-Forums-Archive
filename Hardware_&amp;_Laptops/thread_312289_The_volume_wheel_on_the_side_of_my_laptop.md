---
title: "The volume wheel on the side of my laptop"
date: 2006-12-04
forum: Hardware &amp; Laptops
---

### Post by stoffe on 2006-12-04
Got a Fujitsu-Siemens Amilo M3438G. On the side of it, there's a small wheel for volume control, which works in Windows but not in Ubuntu (other volume controls, such as with Fn-buttons work). If someone has a fix, that'd be awesome, but all I really hope for is to file a bug. :)

So, does anybody have any idea how to give more specific information that might help the devs? Or even better, know a fix, of course. :)

Thanks!

---

### Post by nsleiman on 2006-12-31
if you get it worked please let me know :)

---

### Post by stoffe on 2007-01-07
> **nsleiman said:**
> if you get it worked please let me know :)

Love to, but as you see I don't know where to start. :)

---

### Post by tweedledee on 2007-01-09
> **stoffe said:**
> Love to, but as you see I don't know where to start. :)

Run xev in a terminal, then (while your cursor is over the xev window), move the wheel and see what event is output.  You can then map whichever button it is outputing (assuming you get one) to a keyboard shortcut for adjusting the volume up/down (you can set those for metacity, I don't know what command metacity is outputing to actually do the work).  See here for somewhere to start: [http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441)

---

### Post by stoffe on 2007-01-10
> **tweedledee said:**
> Run xev in a terminal, then (while your cursor is over the xev window), move the wheel and see what event is output. 

There is no output from xev when doing this, I suspect that if there was, it might already have been fixed. :)

---

### Post by tweedledee on 2007-01-10
> **stoffe said:**
> There is no output from xev when doing this, I suspect that if there was, it might already have been fixed. :)

Check /etc/X11/xorg.conf (make a backup before changing!) to see what it says under the mouse section (and input device section with driver "mouse") for the "protocol."  If it's already set to "ExplorerPS/2" then your wheel is probably just not supported at all.  If it says something different, you could try changing the protocol and seeing if you can get any output from xev.

---

### Post by stoffe on 2007-01-10
> **tweedledee said:**
> Check /etc/X11/xorg.conf (make a backup before changing!) to see what it says under the mouse section (and input device section with driver "mouse") for the "protocol."  If it's already set to "ExplorerPS/2" then your wheel is probably just not supported at all.  If it says something different, you could try changing the protocol and seeing if you can get any output from xev.

Now I'm not following you... should I need to change my mouse protocol to get output from my volume control knob? If I was unclear about this: xev does output a lot of stuff for mouse and other stuff, but not for the volume knob. Using volume buttons on keyboard etc *does* work and is properly supported, both for external keyboard and built-in laptop fn stuff. However, nothing happens in Linux (not to sound, not in GUI) when turning this little wheel, while it does in Windows.

If I've misunderstood something about this, then please explain further, I appreciate it. For the record, protocol is already "ExplorerPS/2" and there's no other troubles with that.

Also, I'm fine with there being no support at the moment because I don't *need* it, but for the sake of complete support I'd like to at the very least file a bug, and to do that, I'd like to be able to give some pointers and data to any friendly dev that happens by. :)

Thanks!

---

### Post by nsleiman on 2007-01-11
> **tweedledee said:**
> Check /etc/X11/xorg.conf (make a backup before changing!) to see what it says under the mouse section (and input device section with driver "mouse") for the "protocol."  If it's already set to "ExplorerPS/2" then your wheel is probably just not supported at all.  If it says something different, you could try changing the protocol and seeing if you can get any output from xev.

with xev i can map all keys but not the volume wheel :(

---

### Post by tweedledee on 2007-01-13
> **stoffe said:**
> Now I'm not following you... should I need to change my mouse protocol to get output from my volume control knob? If I was unclear about this: xev does output a lot of stuff for mouse and other stuff, but not for the volume knob. Using volume buttons on keyboard etc *does* work and is properly supported, both for external keyboard and built-in laptop fn stuff. However, nothing happens in Linux (not to sound, not in GUI) when turning this little wheel, while it does in Windows.

If I've misunderstood something about this, then please explain further, I appreciate it. For the record, protocol is already "ExplorerPS/2" and there's no other troubles with that.

Also, I'm fine with there being no support at the moment because I don't *need* it, but for the sake of complete support I'd like to at the very least file a bug, and to do that, I'd like to be able to give some pointers and data to any friendly dev that happens by. :)

Thanks!

The protocol does regulate how many buttons the mouse is recognized as having.  For example, the basic 'PS/2" protocol only recognizes 3 (I think) buttons, no matter what else you do.  The "ExplorerPS/2" protocol is the most general one right now; presumably something coded in there does not recognize the output being generated by your mouse when you move the wheel, and so it is ignored (and hence xev and the rest see no event).

So I think you're stuck with an unusual wheel for now, unless someone with expertise in recognizing hardware events directly wants to chime in, or someone knows something else really obscure I've not found.

You perhaps should file a feature request rather than a bug report - I think this is a case of a missing feature rather than a bug, unless you've seen reports of other people getting a similar setup to work.  My guess is some code needs to be added to the mouse protocol.

---

### Post by stoffe on 2007-01-13
> **tweedledee said:**
> The protocol does regulate how many buttons the mouse is recognized as having.  For example, the basic 'PS/2" protocol only recognizes 3 (I think) buttons, no matter what else you do.  The "ExplorerPS/2" protocol is the most general one right now; presumably something coded in there does not recognize the output being generated by your mouse when you move the wheel, and so it is ignored (and hence xev and the rest see no event).

So I think you're stuck with an unusual wheel for now, unless someone with expertise in recognizing hardware events directly wants to chime in, or someone knows something else really obscure I've not found.

You perhaps should file a feature request rather than a bug report - I think this is a case of a missing feature rather than a bug, unless you've seen reports of other people getting a similar setup to work.  My guess is some code needs to be added to the mouse protocol.
But it is not a mouse wheel, it's the volume wheel on my laptop. My mouse wheel works just fine.

---

### Post by tweedledee on 2007-01-13
> **stoffe said:**
> But it is not a mouse wheel, it's the volume wheel on my laptop. My mouse wheel works just fine.

I seem to have confused myself.  I was operating under the assumption that the volume wheel was associated with the mouse on the laptop - which I think comes from answering unrelated threads at the same time.  Ignore my last 2 posts.

I think this qualifies as "unsupported hardware" and you should file a bug with the Ubuntu Launchpad.  There's also a thread or two around about unsupported hardware for Edgy, you could post there and/or see if someone has gotten something similar working.  You could also check the Fujitsu-Siemens support website and see if they provide any Linux support.  If they don't, you could complain to them as well.

If go via Launchpad, people more knowledgeable than I should will probably get involved and you may find a solution.

---

### Post by stoffe on 2007-01-14
> **tweedledee said:**
> I think this qualifies as "unsupported hardware" and you should file a bug with the Ubuntu Launchpad.  There's also a thread or two around about unsupported hardware for Edgy, you could post there and/or see if someone has gotten something similar working.  You could also check the Fujitsu-Siemens support website and see if they provide any Linux support.  If they don't, you could complain to them as well.

If go via Launchpad, people more knowledgeable than I should will probably get involved and you may find a solution.

Yep, I know, and that's where I started with this post - on my way to launchpad, but being a "good netizen" I wanted to check here first in case I could provide better data right away to the devs.

Thanks for the effort. :)

---

### Post by stoffe on 2007-01-14
Update: found a probably relevant bug that says it may be an ALSA bug: [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/59582](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/59582)

It's another FJS laptop, so it's quite probable it's the same issue.

Added a "me too" there, instead of filing something new. Posting here in case anyone else is looking for the same info later.

---

### Post by Enalia on 2007-03-17
Any updates on this problem?

---

### Post by stoffe on 2007-03-17
Not apart from what is said at the bug report, no. At the moment I'm waiting for more instructions on how to provide data, if that's possible.

---

### Post by morryis on 2007-09-04
hi, for Amilo M3438g i have found a solution: [http://www.amilo-forum.de/topic,17541,-Feisty-Fawn-M3438G.html]("http://www.amilo-forum.de/topic,17541,-Feisty-Fawn-M3438G.html")

short summary in english:

you need to compile Alsa as described in this tutorial: [https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")

after compiling you have to add the following line to the alsa-base file: 
options snd-hda-intel model=fujitsu

---

### Post by _Stevie_ on 2007-12-22
did anyone try this if it works?
i have a amilo xa 1526 and im pretty new to linux.

EDIT:
okay i tried it and it doesnt work with my Xa1526.
too bad.

---

### Post by _Stevie_ on 2008-05-29
i filed a bug report for the xa1526:
[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/235890](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/235890)

feel free to sign in!

---

