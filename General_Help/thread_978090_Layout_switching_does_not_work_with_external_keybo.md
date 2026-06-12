---
title: "Layout switching does not work with external keyboard"
date: 2008-11-10
forum: General Help
---

### Post by muadnu on 2008-11-10
After lots of trouble with getting layout switching to work in Hardy, I finally got it working by adding the relevant setting to my xorg.conf file:
```
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbOptions" "grp:shift_shift_toggle,compose:ralt"
EndSection

```

But now in Intrepid a new problem arose: layout switching works for my laptop keyboard but not for my bluetooth keyboard... By the way, I also have the same setting in the layout switching entry in the System->Preferences->Keyboard.

Is there any way maybe to add my bluetooth keyboard to xorg.conf? Or maybe there's some other easier way to fix this?

---

### Post by muadnu on 2008-11-11
Still no idea how to solve this... What's weird is that the layout is being set independently for both keyboards: if I use my shift+shift shortcut in my laptop keyboard to change the layout, my bluetooth keyboard still uses the English layout.

---

### Post by muadnu on 2008-11-14
Bump?

---

### Post by Emilis on 2008-11-21
I've got the same problem.

Seems it could be related to bug #289781:
[http://bugs.launchpad.net/ubuntu/+bug/289781](http://bugs.launchpad.net/ubuntu/+bug/289781)

---

### Post by muadnu on 2008-11-21
I actually solved it, and maybe works for you too. Go to System->Preferences->Keyboard. Make sure that you have the right settings for layout switching, and then on the Layout tab click "Apply System-Wide". That made the trick for me...

---

### Post by muadnu on 2008-11-25
Well, I actually I realized now that didn't solve it. The only way to get it to work now is go to Layout Options, and then change (and unchange afterwards) some preference. This seems to reload the layout switching options in such a way that now they work for my bluetooth keyboard. In Hardy the same happened, and a workaround was to run the command 'setxkbmap' (for instance when the session started). But this doesn't work in Intrepid :(.

---

