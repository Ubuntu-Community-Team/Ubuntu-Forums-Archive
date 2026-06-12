---
title: "Multimedia key repeat killing gnome panel etc.."
date: 2008-11-04
forum: Hardware
---

### Post by fewt on 2008-11-04
I have a Compaq r4125 that I've just upgraded to 8.10, and I am seeing weird behavior when using my multimedia keys.  When I hit Volume Down, it will continue to drive my volume control down to 0, and when I press Volume up, it will send it to 100%.

I've done some troubleshooting, including backing out to 2.6.24 but the behavior persists.  I've used these keys every day, and have never had this issue before (I upgraded from 8.04).  This issue also occurs on a clean install (tried that too).

If I jump over to a terminal, and run showkey all of the keys indicate a press and release event except volume up and down.

keycode  46 press
keycode  46 release
keycode 114 press
keycode 115 press
keycode  28 press
keycode  28 release


This same action on other computers with 8.10 shows those keys press and then release.  Has anyone run into this one?  If not, I'll open a bug report on it.  My searches came up empty, which never happens..

Thanks in advance..

---

