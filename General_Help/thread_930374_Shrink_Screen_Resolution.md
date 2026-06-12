---
title: "Shrink Screen Resolution"
date: 2008-09-26
forum: General Help
---

### Post by firefly2442 on 2008-09-26
Hello all.  

I have an Asus eeePC 1000 running Ubuntu Hardy.  The default resolution for the laptop is 1024x600.  I would like to play Kohan Immortal Sovereigns but they hardcoded the game to only support 1024x768.  I can run the game but obviously 168 pixels are missing from the screen since the resolution isn't high enough.  

Is there any way to force a higher resolution and just scale and shrink the picture so I can see everything?  Would it be possible to force this in my xorg.conf file perhaps?  Thanks. :)

---

### Post by schwieb on 2008-10-15
I am trying to figure out the same thing so I can play Spore.  I know it is possible to edit the xorg.conf file to 'scroll' beyond the resolution viewable on the small screen.  In this scenario, the screen scrolls to display the resolution as you move the mouse towards the edge of the screen.  I believe the necessary attribute is known as 'virtual' on the xorg, but I am having poor luck configuring it right.  If I figure it out or find info, I'll let you know.

---

### Post by schwieb on 2008-10-15
Well, this was much easier to solve than I thought.  The way I describe above will work, but this hardware hack will work better!

[http://forum.eeeuser.com/viewtopic.php?id=7562&p=1](http://forum.eeeuser.com/viewtopic.php?id=7562&p=1)

Hope it helps

---

### Post by Mister.Vash on 2008-10-16
I can't verify if this still works as I don't have a mode specified in my xorg.conf right now, but they way it used to work was holding down control alt and the + key on the number pad ( ctrl plus alt plus + ) that would cycle through the screen sizes that were listed in your xorg.conf file

Below is a description of the value from one of the pages on the xorg site

Modes "mode-name" ...
    This optional entry specifies the list of video modes to use. Each mode-name specified must be in double quotes. They must correspond to those specified or referenced in the appropriate Monitor section (including implicitly referenced built-in VESA standard modes). The server will delete modes from this list which don't satisfy various requirements. The first valid mode in this list will be the default display mode for startup. The list of valid modes is converted internally into a circular list. It is possible to switch to the next mode with Ctrl+Alt+Keypad-Plus and to the previous mode with Ctrl+Alt+Keypad-Minus. When this entry is omitted, the valid modes referenced by the appropriate Monitor section will be used. If the Monitor section contains no modes, then the selection will be taken from the built-in VESA standard modes.

---

### Post by firefly2442 on 2008-10-17
The hardware hack is interesting but I still don't understand why we can't just get a software hack for this.  Shouldn't there be an option in Xorg to just automatically stretch/shrink the screen based on the available size?  The LazerTag drivers seem to only be for Windows, why not a Linux version?

@Mister.Vash - I think the issue is that this isn't a "valid" mode since it's higher than the supported resolution, or maybe I just misunderstood your comment.

---

