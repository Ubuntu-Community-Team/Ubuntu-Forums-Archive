---
title: "applets and keys"
date: 2008-09-09
forum: General Help
---

### Post by evaristegalois on 2008-09-09
I have two unrelated questions:

(1) I accidentally deleted the time/calendar applet on my gnome desktop (top right corner). How can I get it back?

(2) Whenever I usb plug in my external keyboard my laptop keyboard switches to 'numlock on' which messes it up. I know how to change this (type gconf-editor on the command line, search for numlock and change the respective keys) but how can I change these keys without using gconf-editor (which is GUI). Ideally, I'd write a little perl script or shell script to change the keys back to 'numlock off'.

---

### Post by bmac on 2008-09-09
To add the time & date back into your panel.

Right click on panel and select "ADD To Panel" then select "Clock" and click on the "ADD" button.

Can't help with the keyboard script. Hopefully, someone else will respond to that issue.

Hope this helps....

---

### Post by unutbu on 2008-09-09
The best solution would be to stop the gnome device manager from auto-enabling the numlock. Unfortunately, I don't know how to do that. It might involve editing a HAL policy file in the /etc/hal/fdi/policy directory. I don't know the details to such a solution however.

Since you know how to turn it off using gconf-editor, however, you are just a hop away from a CLI solution:

When you type gconf-editor and navigate to the numlock off item, note the Keyname. It might look something like this:
```

/desktop/gnome/accessibility/keyboard/numlock_enable

```
(I'm making this up because I couldn't find numlock myself!)

Given the keyname, you can assemble a command like this:
```

gconftool-2  --type bool /desktop/gnome/accessibility/keyboard/numlock_enable  'false'

```
to turn it off.

---

