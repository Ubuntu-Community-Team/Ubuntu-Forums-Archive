---
title: "Newbie Wacom Bamboo tablet owner - How to get this working?"
date: 2008-12-28
forum: Hardware
---

### Post by Applegeek on 2008-12-28
OK...I need some warm human feelings here about getting Hardy to work with my daughter's new Wacom Bamboo tablet that she got for Xmas.

Here's what's been done:

Go to Synaptic Package manager, download and install xorg wacom driver and the wacom-tools packages.  Restart the PC, and plugged in the tablet.  Both the tablet and mouse are working, but Gimp doesn't recognize the tablet as an extended device.  The buttons on the pen are only recognized as the alternate and middle mouse buttons, and the tablet pen pressure isn't recognized.

The package manager tells us wacom-tools is supposed to allow the user to configure the tablet, but I don't know where to find this desirable feature.

So there is some life, sorta, but its not working 100% yet.  Nothing has frozen, and the mouse continues to operate normally. Moving the pen on the tablet moves the cursor also, albeit very slowly.

Any clues?  I'm assuming this involves editing Xorg.conf...but "how" is what I need help with.

PS - This is a prime example where some of the features and options inside Ubuntu are a little less than "human".

---

### Post by Rohan Kapoor on 2008-12-29
try running in the terminal ```
wacom-tools
```. It may also be under system-preferences.

---

### Post by Applegeek on 2008-12-29
In terminal: 
wacom-tools = command not found.  

Its installed, according to synaptic.

Now if this gave me any clue as to how to configure the tablet, or how to run it...

---

### Post by igknighted on 2008-12-29
> **Applegeek said:**
> In terminal: 
wacom-tools = command not found.  

Its installed, according to synaptic.

Now if this gave me any clue as to how to configure the tablet, or how to run it...

The command is 'wacomcpl', not 'wacom-tools'.  It should run from the CLI just fine.

---

### Post by Rohan Kapoor on 2008-12-29
> **igknighted said:**
> The command is 'wacomcpl', not 'wacom-tools'.  It should run from the CLI just fine.
That's plain odd, it's works on my computer.

---

### Post by Favux on 2008-12-29
Hi Applegeek,

Please consult Loic2's wiki and its associated thread and resources at:

[https://help.ubuntu.com/community/Wacom]("https://help.ubuntu.com/community/Wacom")

Hope this helps.

---

### Post by Applegeek on 2009-01-03
I got it to work!!  I followed this:

[http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom](http://ubuntuforums.org/showthread.php?t=765915&highlight=wacom)

I don't know how I missed this before...but it works perfectly now!!

Thanks!!!

---

### Post by Favux on 2009-04-03
Hi Applegeek,

If you don't have all the buttons working yet in Intrepid, Gemnoc in post #7 on this thread can help:

[http://ubuntuforums.org/showthread.php?t=1098822]("http://ubuntuforums.org/showthread.php?t=1098822")

---

### Post by ranch hand on 2009-04-04
I have no idea about the OP but I thank you for the link.  I would like to get one of the little buggers and now I just might.

---

