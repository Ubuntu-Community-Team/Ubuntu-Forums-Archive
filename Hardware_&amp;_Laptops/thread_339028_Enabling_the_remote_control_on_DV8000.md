---
title: "Enabling the remote control on DV8000"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by Dr Sketch on 2007-01-15
Sorry if this has been asked before, but I didn't see it anywhere.  I'm trying to enable the remote control that came with my laptop (HP DV8000) for multimedia use, but can't find anywhere to run the settings.  Is it supposed to be part of "Keyboard Shortcuts"?  If so, is there any way to assign multiple keys to a single shortcut (for instance, use the pause on my remote and the pause on the keyboard, depending on which I have in my hands)?  No worries if I can't use it, I just thought it would be nice since I already have it...

---

### Post by marroco on 2007-03-03
I also have a dv8000, never figured out how to configure the remote with ubuntu, the only buttons that work are the volume up and down ....

---

### Post by mctk on 2007-03-07
The remote triggers the same button presses that the keyboard does.  So, Ubuntu does not know whether you pressed the "up" key on the keyboard or the remote since the keyboard sends the same signal.

In this respect, most of the remote buttons should be working (and do work for me).  You can go to system->preferences->keyboard shortcuts to verify this.  Highlight the "play/pause" command and press the multimedia key on the keyboard.  It should say "XF86AudioPlay" or something.  Then press the play button on the remote and it will register the same command.

I have found that I cannot bind the "QuickPlay" buttons to any commands.  These are the "DVD", the little swirly thing, and the musical note button on the remote.  I haven't tried the power or the sleep button (and I'm not going to until after this post...)

So if you've verified that the "keyboards shortcuts" is registering the buttons, then it's an issue with something else.  I only have experience with Banshee.  I activated the multimedia keys plug-in, binded all my multimedia keys in the keyboard shortcuts dialog and restarted X.  That did the trick.  

If anyone has any ideas on binding the QuickPlay buttons, they would be appreciated!

---

### Post by Toolbelt on 2007-06-02
I have never gotten my HP remote to work with dv8000 out-of-the-box in Ubuntu.  Do you have anymore advice to offer us?

---

### Post by crav on 2007-06-28
Was searching for this, tried mctk's thing, and it worked flawlessly!

---

### Post by -Vampyre- on 2007-06-28
I have the same laptop and I believe the quickplay dvd features worked off of a little 255mb partition that came with the laptop. It would turn it on as a dvd player when the lid was closed. I am not sure how they worked with it on. I think it just popped up some playing software

---

