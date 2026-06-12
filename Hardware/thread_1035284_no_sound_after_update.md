---
title: "no sound after update"
date: 2009-01-09
forum: Hardware
---

### Post by xjgnsdof on 2009-01-09
I recently updated 8.10, including the kernel (2-6-27.11). Now, whenever I try to change the volume, I get the following: 

[I]The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu.[/I]

When I try to enter Sound Properties, I get the following: *No volume control GStreamer plugins and/or devices found.*

Is anybody else experiencing this after the update from January 8, 2009?

---

### Post by gettinoriginal on 2009-01-09
Hope these help:  :P

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)
[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)
[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by xjgnsdof on 2009-01-09
Thanks, but I posted this problem so I didn't have to read all of those (some of which I read already). I'm low on Ubuntu-fixing time at the moment.

---

### Post by markbuntu on 2009-01-09
If you just upgraded to Intrepid then you should follow this guide, it is quick and easy and will hopefully get you fixed up right away

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

### Post by xjgnsdof on 2009-01-10
I didn't just upgrade to Intrepid. I did a fresh installation of it weeks ago, and sound was working fine until I updated. How do I fix this?

When I input "aplay -l" I get an error saying that there are no sound cards, so your guide won't work.

---

### Post by xjgnsdof on 2009-01-12
up

---

### Post by xjgnsdof on 2009-01-12
I broke down and reinstalled Intrepid. Sound is working just great. I must have botched an ALSA installation, and the update just made my mistake stick. If anybody has a more elegant solution, please post it.

---

