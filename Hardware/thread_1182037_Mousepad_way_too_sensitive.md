---
title: "Mousepad way too sensitive"
date: 2009-06-08
forum: Hardware
---

### Post by theturbanator on 2009-06-08
Hi everyone!

I have a Dell Vostro 1400 running Ubuntu 9.04, and my mousepad is currently way too sensitive.  I installed gsynaptics and have read that (for Ubuntu 7.04, at least -- I'm assuming it is the same for 9.04) my xorg.conf file should have the following section: 
Section "InputDevice"
       Identifier      "Synaptics Touchpad"
       Option          "SHMConfig"             "on"
       Driver          "synaptics"
       Option          "SendCoreEvents"        "true"
       Option          "Device"                "/dev/psaux"
       Option          "Protocol"              "auto-dev"
       Option          "HorizScrollDelta"      "0"
EndSection

However, my xorg.conf file does not have such a section.  Is it OK to add
it in? If it is, where can I find specific specs for my laptop and device?

Thank you!

---

### Post by s3MA00RRNY on 2009-06-08
This should be okay. When I added that section there were more options there, but they don't really matter when you're using gsynaptics to configure.

---

### Post by theturbanator on 2009-06-08
yeah so I added it, and so then I was able to go into the appropriate menu (I can't remember what it is now, and I can't access it, as I'll explain in a moment) to get into the Touchpad configuration, except that there was an error that SHMConfig had to be set to "true"...

so when i next tried sudo gedit, nothing would come up... so I had to edit it using "emacs -nw" to change it... it still wouldn't let me in so I logged out, except then there was a massive error and said that I needed to run Ubuntu in low graphics mode and that there was a problem with X server or something... which explains why the window wouldn't come up?  so I think this is because i edited my xorg.conf file....

so how do I fix this big mess now?  BTW, I am running a dual boot, and I am currently on my Vista partition... so maybe I can access my Ubuntu files??  I know that I can the other way (access Vista files from Ubuntu)

please help... my ubuntu configuration is entirely messed up now.

---

### Post by theturbanator on 2009-06-08
ok so i deleted the xconf.org file and it fixed that ... but now i don't really know if adding that section is a good idea... at least the way it is written below...

could someone tell me the proper way to add it to my xconf.org file? the stuff below did somewhat of the trick as it added the "touchpad" configuration button to my System > Preferences Menu... but after that, it all went downhill haha

---

### Post by theturbanator on 2009-06-09
any help would be much appreciated. thanks!

---

### Post by s3MA00RRNY on 2009-06-09
I used to have this set up correctly, but I've wrecked/reformatted my machine several times since then. Sorry for the trouble I caused. It "seemed" right to me.

---

