---
title: "Sound Card"
date: 2010-03-04
forum: Hardware
---

### Post by rickferd on 2010-03-04
Good Day to all. 
I am fairly new to Ubuntu. I originally dual booted windows and Ubuntu 8.04. I upgraded to 9.04 and had no problems. I then decided to get rid of windows. I wiped the hard drive and installed 9.04, but now the sound does not work. I ran lspci and get the following "00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)" but I have no idea what to do to now any help will be appreciated. Thanks

---

### Post by ajgreeny on 2010-03-04
Open a terminal and use the command ```
alsamixer
``` A mixer deck will open up and you can use the cursor keys to move from slider to slider, and to raise and lower sliders, and "M" to mute/unmute channels (those with MM showing at the bottom are muted)

Check in that terminal application that you do not have any channels set too low or totally muted, hit Esc to quit and you may find that sound has appeared.  Come back again if no good, and also look at [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449) which may have a lot of useful info for you.

---

