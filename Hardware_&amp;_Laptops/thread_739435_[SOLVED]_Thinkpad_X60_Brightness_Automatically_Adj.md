---
title: "[SOLVED] Thinkpad X60 Brightness Automatically Adjusts"
date: 2008-03-29
forum: Hardware &amp; Laptops
---

### Post by ilych on 2008-03-29
Hello,

I recently installed Xubuntu on my Lenovo Thinkpad X60. The Fn+Home and Fn+End brightness adjustment keys did not work, so I installed the Gnome desktop, essentially changing my Xubuntu to Ubuntu, which did fix the problem.

However, while I can adjust my brightness with the function keys, **the brightness periodically (often after about one minute) restores to its maximum value automatically**, without my permission. How do I fix this problem? It is also mentioned in this [thread]("http://ubuntuforums.org/showthread.php?t=350562").

On a side note, if there are other X60 users out there, what other things do I need to install to make my X60 functional in Ubuntu. I'm not sure if I need the ThinkVantage button anymore. If I do, how do I install that?

Thanks for any help,
ilych

---

### Post by ilych on 2008-03-30
Sorry, I didn't search enough on the forums. This [post]("http://ubuntuforums.org/showpost.php?p=3648590&postcount=2") contains the solution:

[QUOTE=volanin]1. Press ALT + F2 to open the run dialog.
2. Type gconf-editor and press ENTER, to open the gnome "registry".
3. Navigate to APPS -> GNOME-POWER-MANAGER -> BACKLIGHT
4. Uncheck the item named enable
5. Close the window.[/QUOTE]

---

