---
title: "setting the default system-wide cursor for Ubuntu"
date: 2008-09-06
forum: General Help
---

### Post by kestal on 2008-09-06
I need some help. My window decorator is Emerald (and I'd prefer to keep it at that) and the cursors within a window are fine, but are plain on the desktop.

Is there a way to change the system default cursors? I looked over a few articles where you had to copy over the files to a folder and the theme file in the x11 folder and update-alternatives --config x-cursor-theme, but my new theme is not present.

Any ideas?


Edit:

Gcursor does not solve this.

---

### Post by GrandpaLeaman on 2008-09-06
> **kestal said:**
> I need some help. My window decorator is Emerald (and I'd prefer to keep it at that) and the cursors within a window are fine, but are plain on the desktop.

Did you try going into the CompizConfig Settings Manager and entering your cursor theme in the general options?

---

### Post by kestal on 2008-09-06
I did try this in Compiz however I believe it would not work becuause I am using Emerald as my windows decorator. I could be wrong... but anything outside of the Window reverts the cursor back to the original one. Then if i move the cursor back in the range of my Firefox/Opera window, it goes to the one I selected, using both Appearances, and Compiz.

Any Suggestions?

Basically: If the cursor is within the firefox window, its the right cursor, if I move it out, it reverts back. The Windows decorator in Compiz is set to emerald --replace. (and that is also included in my startup session info)

---

### Post by Genius314 on 2008-09-06
The problem is that Compiz AND Gnome both have settings for the cursor theme.

Go to System>Preferences>Appearance, click "Customize," go to the Pointer tab.
Also go to System>Preferences>CompizConfig-Settings-Manager. Find the cursor theme setting (it should be a text box). (Note: I have a newer version of Compiz, so I don't think I have this option.)

Both of the cursor themes should match.

---

### Post by kestal on 2008-09-07
Hmmm, I may have inadvertently messed something up. Both of those settings are set to the same one but anything outside the window or on the desktop appears to have the default cursor.

as for the other thing I mentioned.. someone mentioned once to modify xdefault, but I am unsure how. When I update-alternative the cursor, my cursor (despite the theme file being in the folder), does not show up.

---

### Post by GrandpaLeaman on 2008-09-07
OK, here is how I have my cursor set up:

    * First I went into Appearance Preferences -> Theme -> Customize Theme -> Pointer and selected the cursor I want to use, which for me is currently DeepSky.
    * Then I went into CompizConfig Settings Manager -> General Options and put the cursor name in the Cursor theme box. Again this is DeepSky (please note field is case sensitive).

Now, in reading your description of the problem, it sounds like you have the cursor theme set up correctly in compiz but do not have it set up in your theme in appearance preferences. That would explain why you get the new cursor in a window but not on the desktop. I went in and changed my pointer setting in my theme and got the same effect. So you might want to check there.

Hope this helps!

---

### Post by kestal on 2008-09-08
Thanks for the reply.

I did fix it, and it seems to have been related to Emerald. After Emerald was installed, I was unable to change the cursor properly. I removed Emerald, applied the cursor (bingo, its everywhere now), and installed it again.

My problem was solved. Could it be something in Emerald that kept it from switching cursors?

Anyway, thanks for the replies :)

---

### Post by SPARTAN-118 on 2009-07-02
Hi, I am having the same problem as you had, but I can't fix it since my CompizConfig Settings Manager doesn't have a mouse area in the General Settings tab. 
I am using Ubuntu 9.04 Jaunty Jackalope.
Any ideas?

SPARTAN-118

PS I am also using Emerald.

---

