---
title: "[SOLVED] [Firefox] Dark themes look BAD"
date: 2008-11-05
forum: General Help
---

### Post by fiddler616 on 2008-11-05
Hello,
I've been playing around with Darkroom (on GNOME) and Dusk (on Xfce), and I like it...except for buttons and scrollbars in Firefox--it looks terrible having random squares of darkness.

I've set Firefox to not use the system colors...but the problem persists.

I've already seen this thread: [http://ubuntuforums.org/showthread.php?t=791076](http://ubuntuforums.org/showthread.php?t=791076)
which tells me I'm not the only one, but they couldn't solve it.

Thanks in advance

---

### Post by nufros on 2008-11-11
I'm having the same problem... it seems that firefox adopts the window background color from my theme for the dropdown menus... can be very hard to read... but it looks too nice everywhere else to change the whole desktop just for firefox... there's gotta be a way to fix this, it's so friggin annoying lol

---

### Post by transmition on 2008-11-11
Although I do not know how to do it, I believe modifying the userchrome.css in the .mozilla folder would allow you to change some color settings. 

I may be misunderstanding you, but you do want to alter the buttons and scrollbars, I find that the heaven cube theme [https://addons.mozilla.org/en-US/firefox/addon/8218](https://addons.mozilla.org/en-US/firefox/addon/8218) works for me.

---

### Post by nufros on 2008-11-11
I haven't looked into modifying the userchrome.css yet, but I tried the theme you suggested. And it does looks great, but I'm still having the same problem... dropdown menus seem to have a color selected by firefox independant of whatever firefox theme I've installed.

Here's a screenshot of what I'm talking about... notice how dark the dropdown menus are? They'll always match whatever color I choose in System>Preferences>Appearance to be my window background color...


-------------------------------------------------------------------------


***UPDATE: I think I might have figured out a workaround with Greasemonkey.

[Color Corrector2.1 (http://userscripts.org/scripts/show/36850)]("http://userscripts.org/scripts/show/36850")


It's not perfect, but it works for me :guitar:
(see the before and after screenshots)

---

### Post by element_G on 2008-11-11
Another method is found in my How-to; it's a bit more involved, but you end up with nicer looking forms boxes than the above greasemonky script. 

[http://ubuntuforums.org/showthread.php?t=873486](http://ubuntuforums.org/showthread.php?t=873486)

---

### Post by nufros on 2008-11-13
maybe, but for a more basic user (such as myself :redface:) that's pretty labor-intensive... (+ I find having to edit forms.css every time Firefox updates a little tedious)

personally, I prefer to have something that I can turn on and off easily in case I decide to change themes to something light...


new >>> I've updated the script now so that you can customize the colors and shape of each form

---

### Post by philinux on 2008-11-13
I'm using new wave. [http://www.gnome-look.org/content/show.php/New+Wave?content=87134](http://www.gnome-look.org/content/show.php/New+Wave?content=87134)

The only problem I've seen is the drop down google suggestions being white on grey. But I can live with that as I like it a lot. And I've never been a fan of dark themes at all.

---

### Post by fragos on 2008-11-13
IMHO it's unfortunate that Firefox doesn't adapt to the Gnome theme. That is one of the reasons I changed to Epiphany which is completely integrated into Gnome. It's also faster than Firefox but has a much limited set of extensions when compared to Firefox. Epiphany can also run with the Gecko or Webkit renering engine. The great thing about Linux is that you have choices.

---

### Post by nufros on 2008-11-18
Hopefully the makers of Firefox will address this issue in a future update [-o<

---

