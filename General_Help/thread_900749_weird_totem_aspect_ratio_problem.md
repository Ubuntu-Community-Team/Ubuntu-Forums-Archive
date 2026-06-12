---
title: "weird totem aspect ratio problem"
date: 2008-08-25
forum: General Help
---

### Post by tramir on 2008-08-25
For a couple of days, I have this weird problem: when I try to play a movie in Totem (xine), the image is squeezed as if it uses the reverse aspect ratio. I can't post a screenshot because it doesn't show the video being played. Anyway, think of an image stretched vertically (everybody looks really thin and tall :))

I deleted Totem's configuration file (both in .config and in .gconf) and re-installed totem, totem-common and totem-xine, but to no avail. VLC plays movies without any problem, it's only totem that behaves like this.

My configuration is: Hardy (all updates), ATI fglrx, totem-xine. Problems playing anything: AVI, DVD etc. If anybody has any idea, please let me know. Eternally grateful... :D

---

### Post by prince_niceguy on 2008-08-25
remove .xine or related folders in your home directory. that should fix the issue. i too use fglrx and use totem-xine and it works perfectly for me.

---

### Post by tramir on 2008-08-25
I removed .xine and everything else I could find related to that. No change. 

It used to work fine for me too (for more than a year). It did happen before, but it went away on its own after a restart. But now it's still here after a restart. Any other idea?

---

### Post by cooke77 on 2008-08-26
The 'squeezed' effect is due to the Ratio having been set at 16.3.
To UNDO, reset this Ratio to 4.3. (This will give you back the 'normal size'.)

---

### Post by tramir on 2008-08-26
The aspect ratio is set to "auto" and changing it does not solve the problem. This was my first thought too. The video really looks as if totem switched the dimensions somehow (height for width)...

---

### Post by tramir on 2008-08-27
A bit more testing: 

[LIST=1]
[*]uninstalled totem-xine and installed totem-gstreamer - same behavior
[*]installed gxine - same behavior
[/LIST]

Also, the video resize options behave weird. Nothing happens until I choose 2:1, after which the image gets stuck in a double-size (but still half-width, relatively) layout.

Again, VLC plays the videos fine, but totem shows them with half the width. Literally. What could make totem halve the width? Any idea? Any help would be greatly appreciated...

---

### Post by tramir on 2008-08-27
Is there any file/place where totem could save some settings that might affect how it displays videos? It seemed to me like it automatically creates a xine preference file,and maybe that's why gxine was affected as well. Does anybody know where I could find the settings related to video playback?

---

### Post by tramir on 2008-08-27
No idea, anybody?

---

