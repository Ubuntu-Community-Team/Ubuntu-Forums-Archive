---
title: "Notification not legible in notifications w/ Darkroom theme"
date: 2008-11-10
forum: General Help
---

### Post by Daimoneze on 2008-11-10
See image below. I know I can change the color of the text but that has other implications. This doesn't appear to be considered a "tooltip" as those appear correctly and as set in "Appearance". It seems the text is the correct color but the background should be darker (like the windows). Such is the case on another machine I have running same environment (ubuntu 8.10, compiz, darkroom).

[IMG]http://farm4.static.flickr.com/3234/3019892026_a5cd75885c.jpg[/IMG]

---

### Post by Daimoneze on 2008-11-10
bump?

---

### Post by Daimoneze on 2008-11-24
It just dawned on me to ask: is the above a tooltip? Tooltips are set with a dark background/light foreground and when hovering over objects they appear correctly. Is it possible to alter the color of notifications like the above?

---

### Post by Daimoneze on 2008-12-17
Time past = bump

---

### Post by Daimoneze on 2008-12-24
This must be a tough one.

---

### Post by JECHO on 2008-12-24
I've used that theme before and haven't had any problems with the notification area... no idea how to help you. sorry :-/

---

### Post by Ivo Moelans on 2008-12-24
Try this:

Start gconfig (*Application&#8594;System Tools&#8594;Configuration Editor* or type in terminal *gconf-editor*) an go to* Apps&#8594;Notification Daemon*. In the pane on the right change *theme* into *normal*. Notifications should now conform to your theme. You can also change the location where the notification pops up (if not determined by the app).

Hope this helps

***Edit:***
In Intrepid there seem to be only two notification themes: *standard* or *ubuntu*.
But you could look in *CompizConfig Settings Manager* in category *Accesibility*, *Opacity, Brightness and Saturation*. Make sure that in the tab *Opacity* there is no item containing *Notification*.

---

### Post by nikolardo on 2009-02-11
I have the same problem.  I've somewhat traced it to the fact that the notifications take their forecolor from the window forecolor (preferences -> appearance, customize, colors) and their background color from input boxes.  In the darkroom theme, input boxes are light in background and dark in foreground, whereas windows are dark in background and light on foreground, and while I don't know why the notification daemon takes its colors from two different places, that's why it's light on light.

This (for me) does not change when I change between "ubuntu" and "standard" in gconf editor for the notification daemon, and neither do I have opacity, saturation, and brightness enabled in compiz fusion.  Can I make the notification daemon refer to "input boxes" or "windows" for both background and foreground?

---

