---
title: "[SOLVED] Mac4Lin 0.4 problem(ette)"
date: 2008-08-18
forum: General Help
---

### Post by b9k9kiwi on 2008-08-18
I have successfully installed Mac4Lin 0.4 although the top bar of any window does not display correctly until I reload the Window Manager (using the drop-down Menu of the Compiz Fusion Icon).

Why is this and/or can I get the Window Manager to reload automagically at startup?

The Compiz Fusion Icon is loaded at startup with --no-start command option and tells me that my Window Manager is Compiz and that GTK is my Window Decorator.

---

### Post by conundrumx on 2008-08-18
Could you please show us the problem?

---

### Post by b9k9kiwi on 2008-08-19
> **conundrumx said:**
> Could you please show us the problem?

The top bar (Title Bar?) of a window is transparent until I reload Window Manager, at which point the top bar adopts the Mac4Lin texture and three colour Mac like window control buttons.

---

### Post by conundrumx on 2008-08-19
Looks like Emerald is loading with the wrong engine for whichever skin, then when it snaps back to Metacity everything is fine.

Can you please confirm which decorator/WM is running in which screenshot?  The easiest way is probably through ps.  Look for emerald and compiz.

---

### Post by poodpood on 2008-08-19
I use emerald to skin the window borders, it also puts the buttons on the left.

If you downloaded the mac4lin tarball, then there should be two emerald themes included there.[IMG]http://farm4.static.flickr.com/3266/2777558709_e3dc41a992_o.png[/IMG]

---

### Post by b9k9kiwi on 2008-08-19
> **conundrumx said:**
> Looks like Emerald is loading with the wrong engine for whichever skin, then when it snaps back to Metacity everything is fine.

Can you please confirm which decorator/WM is running in which screenshot?  The easiest way is probably through ps.  Look for emerald and compiz.

The decorator/WM in both shots is Compiz/GTK (according to Fusion-Icon).  Having reloaded the WM and got the MacLike title bar, switching between Compiz and Metacity alters the window animation but does not affect the title bar.  Switching between GTK and Emerald results in a return of the transparent title bar (under Emerald) and restores the MacLike title bar (under GTK).

---

### Post by conundrumx on 2008-08-19
Select the theme in question under Emerald's settings window.  Then click the "Edit Themes" tab.  After that, try the different engines in the drop down.  One (or more) of them should cause the borders to render correctly.

---

### Post by b9k9kiwi on 2008-08-19
> **conundrumx said:**
> Select the theme in question under Emerald's settings window.  Then click the "Edit Themes" tab.  After that, try the different engines in the drop down.  One (or more) of them should cause the borders to render correctly.

As a result of the pointer in the reply from poodpood I imported the Mac4Lin theme into Emerald (I had not done so because I didn't think I was using Emerald as the Window Decorator).  Now, when a session loads the MacLike title bar is in place at the onset and the Fusion-Icon drop-down tells me that the Windows Manager is Compiz and that the Windows Decorator is Emerald.

So thanks to you and he for your time, it seems that it is fixed.

Mind you, I don't actually want the window control buttons on the left, but that's another problem :).

---

### Post by conundrumx on 2008-08-20
Take a look at the Titlebar tab under "Edit Theme"  :)

---

### Post by b9k9kiwi on 2008-08-20
> **conundrumx said:**
> Take a look at the Titlebar tab under "Edit Theme"  :)

It's really odd after years of playing and working with PCs - I used a PC before they were invented - to have to have my hand held like this :).

Thanks again - that fixed it.

---

