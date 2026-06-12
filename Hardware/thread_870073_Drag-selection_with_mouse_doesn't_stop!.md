---
title: "Drag-selection with mouse doesn't stop!"
date: 2008-07-25
forum: Hardware
---

### Post by SpaceMaster on 2008-07-25
This is really weird.  This Dell Inspiron 9100 has a fresh load of Hardy-Har-Har Heron (as of last night, actually).  I've got everything up-to-date, restricted drivers and all, and everything's working properly... except the built-in mouse.

It's one of those dual deals - both the trackpad and the track- nub (not to be confused with the n00b running the machine =-P)  Anytime I click and hold, it begins the normal function of creating a selection box.  However, upon release, the box remains on the screen.  I can create overlapping selection boxes, even.  However, once the error begins, I cannot access all the proper functions (such as delete, etc.) from the right-click menu.  Furthermore, the left-click no longer works, either (except to create more perma-selection boxes).  I can't even left-click items such as scroll bars or menus.  The only solution I've found thus far is to Ctrl-Alt-Backspace, and restart Xserver.  Unfortunately, this forces me to close all applications, which is really annoying.

Thus far, the problem only seems to happen with the built-in mouse.  I am unable to reproduce it with a USB mouse.  However, if I create the error with the built-in mouse, the USB mouse will perform the erroneous functions as well - save for creating more of the little selection boxes THAT JUST WON'T GO AWAY! *breath* *breath*

Any help would be appreciated. ^_^

-The Space Master, who's currently navigating the universe via keyboard...
--------
edit:

tried-
  sudo apt-get install gsynaptics
after the reboot, this didn't work.

tried-
  sudo apt-get install xserver-xorg-input-synaptics
got back this this was already up-to-date

I looked around [at this thread in Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=869240&highlight=dell+mouse"), as well as [ this alternative]("http://www.linuxquestions.org/questions/fedora-35/fedora-9-how-to-enable-synaptics-touchpad-640484/#post3164577").  Following the latter, I catastrophically broke my Xserver (Actually, this didn't dissappoint me, because I haven't broken it since the upgrade to Hardy - it was about time).  After picking up the pieces, I've come back full-circle to my original problem: the trackpad buttons still behave like ill-tempered goats.  Should I just take away its candy and tell it not to play with the other children, or may there yet be hope for it?

---

