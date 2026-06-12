---
title: "Touchpad only has problem on &quot;restart&quot;"
date: 2011-04-11
forum: Hardware
---

### Post by solarisdreams on 2011-04-11
Hi all,

I've got a problem with my touchpad on my laptop where it only does not work on warm Restarts (i.e. selecting RESTART from the shutdown menu).  The mouse cursor is just stick in the middle of the screen and I can't move it or click any of the buttons.  If I were to plug a USB mouse in, I am able to control the cursor, but the touchpad is dead.  After I shutdown, the power back up, it works fine.  I'm guessing it doesn't unload some sort of driver from memory on restart?  

Also, shutdown/cold starts, hibernates and suspends all work as they should.  I can't figure this one out for the life of me...help pls someone!

Oh, and I'm using Maverick 10.10...

tks...

---

### Post by ajgreeny on 2011-04-11
It may only be some sort of workround, but have a look at **synclient** in terminal.

Try ```
synclient -l
``` for a list of all the commands you can use, and you may find a possible command to turn on the trackpad.  The command certainly lets you change a lot of the operations of the pad, and I think it could be useful for you.

I'm on a desktop at the moment so can not look any further for you, I'm afraid, or I would look and make more suggestions as to detailed commands.

---

### Post by solarisdreams on 2011-04-12
> **ajgreeny said:**
> It may only be some sort of workround, but have a look at **synclient** in terminal.

Try ```
synclient -l
``` for a list of all the commands you can use, and you may find a possible command to turn on the trackpad.  The command certainly lets you change a lot of the operations of the pad, and I think it could be useful for you.

I'm on a desktop at the moment so can not look any further for you, I'm afraid, or I would look and make more suggestions as to detailed commands.

says:  couldn't find synaptics properties.  no synaptics driver loaded?

i ran this command with the touchpad in WORKING state...

anything else i can try?

---

### Post by solarisdreams on 2011-04-12
bump...anything I can run to see what the problem might be?

---

### Post by ajgreeny on 2011-04-12
Install **xserver-xorg-input-synaptics** for synclient.  I thought it was always installed on laptops, but perhaps that's not so.

Anyway, give it a try, there's nothing to lose.

---

### Post by solarisdreams on 2011-04-13
actually the synclient and package you referred to is already installed.  but even when the trackpad is working, synclient -l tells us, "Couldn't find synaptics properties.  No synaptics driver loaded?"

As in...I think a different driver is driving the trackpad...

---

### Post by ajgreeny on 2011-04-13
Oh well, it was worth a try.  Sorry, but I have no idea where you can go from here.

---

### Post by solarisdreams on 2011-04-16
bump

---

