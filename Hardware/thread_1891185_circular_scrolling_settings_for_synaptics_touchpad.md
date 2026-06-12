---
title: "circular scrolling settings for synaptics touchpad are reset after logout"
date: 2011-12-05
forum: Hardware
---

### Post by attam on 2011-12-05
I noticed this option a while back, but never figured out how it works...but today, after seeing a [demo]("http://www.youtube.com/watch?v=rkh9OE6mZVQ") on youtube, realized its usefulness and decided to take advantage of it...at least until I logged off.:confused:

I can enable and use circular scrolling on my ubuntu 11.10 system using gpointing-device-settings, but when I log out, the setting reverts to disabled (actually, the option is checked, but the trigger region is not selected, so it doesn't work). In order to re-enable it, I have to disable circular scrolling by unchecking it, close and restart gpointing-device-settings, then re-enable it and select the trigger zone. After this, it works again, but only until the next logoff.

Using: gpointing-device-settings and gsynaptics version 1.5.1-5ubuntu1

would appreciate any suggestions on how to fix this...

---

### Post by BC59 on 2011-12-05
If you search the word gsynaptics on Ubuntu Software Center, you see two options of software to manipulate touchpads.

---

### Post by attam on 2011-12-06
thanks for the reply...
update: I have removed the transitional package gsynaptics and the problem still occurs as described above. ie, the circular scrolling works if set, but is disabled on logoff. more precisely, the trigger zone is reset (the circular scrolling checkbox remains checked)

---

### Post by attam on 2011-12-08
After searching the forum again, I found this response by rp88 which solved my problem...[http://ubuntuforums.org/showpost.php?p=9727751&postcount=8](http://ubuntuforums.org/showpost.php?p=9727751&postcount=8)
That was easier than I thought...:smile:

---

