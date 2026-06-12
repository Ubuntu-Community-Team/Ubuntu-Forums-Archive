---
title: "Firefox touchpad event problem"
date: 2006-12-23
forum: Hardware &amp; Laptops
---

### Post by beanbrain on 2006-12-23
Hello,

Here's some more touchpad weirdness. I'm generating an event in Firefox that I can't figure out how to turn off. It only occurs when I accidentally double-click in the upper-right corner of my (Alps) touchpad; when I do this the browser attempts to redirect to a URL based on whatever text happens to be under the cursor (e.g., if "Thread" is highlighted when I double-click the upper-right corner of the touchpad, the browser attempts to load "Thread.com").

This does not seem to be the horizontal scroll-click event that is discussed in so many other threads, because I can click anywhere else on the touchpad--bottom-left, top-left, middle, bottom-right--without this occurring, and I've already disabled this using about:config.

Does anybody know what event is this and why it's occurring? I'd like to disable it, and I've been fighting the problem for the last few days.

Thanks!

---

### Post by beanbrain on 2006-12-24
An update: I think I finally figured out which setting to change. There's a setting called "middlemouse.contentLoadURL," and it seemed like that's exactly what was happening--when I tapped in the upper right corner of the touchpad, Firefox would try to load either a site previously visited or whatever "content" was highlighted by the cursor. Changing this setting to "false" seems to eliminate this behavior (I toggled the setting back and forth a few times for testing purposes).

---

### Post by rking on 2006-12-30
Thank you!  This problem has been bugging me for days!  Now to fix the other nine million items on the list of things-to-be-done-before-I-can-dump-windows... :)

---

### Post by beanbrain on 2007-02-04
rking,

I'm a bit late on my response, but am glad this helped. Like you I'm a "switcher" and haven't gone back to XP since dumping it in December. I did have to make some compromises, but overall I'm happier with my tools and computing life in general now.

---

