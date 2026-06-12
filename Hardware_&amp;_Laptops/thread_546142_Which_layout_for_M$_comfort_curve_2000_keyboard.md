---
title: "Which layout for M$ comfort curve 2000 keyboard?"
date: 2007-09-08
forum: Hardware &amp; Laptops
---

### Post by jek on 2007-09-08
I upgraded to Feisty and have had difficulties getting my M$ comfort curve keyboard 2000 to work via vncserver.

My searching turned up these links with partial information:

Similar vncserver problem: 
 [http://ubuntuforums.org/showthread.php?t=34135](http://ubuntuforums.org/showthread.php?t=34135)

Solution for that person that doesn't seem to work for me: 
 [http://www.petersblog.org/node/878](http://www.petersblog.org/node/878) 

Another person with kbd difficulties and no answer: 
 [http://ubuntuforums.org/showthread.php?t=372762](http://ubuntuforums.org/showthread.php?t=372762)


I find that one bizarre partial workaround was to start my desktop with vncserver and then connect using Vino to that.  Somehow, the mapping was improved but not perfect.  Not sure just why this worked.

In any case, I can use the preferences/keyboard/layouts tool to select keyboards and it does change the mapping.  But none of the obvious candidates seem to work properly.  I tried all of the US version layouts but none worked directly with vncserver.  The best layout through Vino was "English".  But asdf maps to abfh when connected directly to vncserver

It is very weird what is going on.

I'm suspicious that I need to edit /etc/X11/xorg.conf but it isn't at all obvious what/how to do there.
It currently has this in xorg.conf:
```
Section "InputDevice"
        Identifier      "Generic Keyboard"
# See [http://blog.odonnell.nu/38.html](http://blog.odonnell.nu/38.html)
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection
```

which seems to have some description here:

[http://www.xfree86.org/current/XKB-Config2.html](http://www.xfree86.org/current/XKB-Config2.html)

I tried changing the option to:
```
        Option          "XkbModel"      "microsoft,microsoftinet,microsoftprousb,pc104"
```
but that didn't seem to help.

It seems to be a bit of a "twisty passages, all different" situation...

I'm using Windows XP with RealVNC version 4.1.1 as the client.  It was working fine with dapper and this happened after a dapper->edgy->feisty upgrade yesterday.

Suggestions?

---

### Post by jek on 2007-09-08
More searching yielded some more results:

This site has more info on the confusion:
[http://blog.benjolo.com/archives/2007/04/25/arrrrgh-ubuntu-704-upgrade-confused-gnome-keyboard-settings-for-vnc/](http://blog.benjolo.com/archives/2007/04/25/arrrrgh-ubuntu-704-upgrade-confused-gnome-keyboard-settings-for-vnc/)

and the comments have a link to this:
[http://ubuntuforums.org/showpost.php?p=2539412](http://ubuntuforums.org/showpost.php?p=2539412)

This link has you intentionally break the gnome selection of keyboard type and that works for me!
Something is broken about gnome keyboard support.

Weird.

Another interesting link:
[http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/](http://www.movingtofreedom.org/2007/02/16/howto-remote-desktop-with-vnc-in-ubuntu-edgy-gnu-linux/)

---

