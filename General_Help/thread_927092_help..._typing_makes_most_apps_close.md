---
title: "help... typing makes most apps close"
date: 2008-09-22
forum: General Help
---

### Post by KnightOnline on 2008-09-22
my ubuntu has gone mad.


most applications close if i start typing something, any keystroke will make them close, wordpad, console, etc, but oddly enough, firefox and vmware are fine.

also, my caps lock, shift, ctrl and alt keys don't work.

when i reboot the problem disappears for a bit, but after a few minutes its back.

this is a fresh install of hardy 8.04.1, all i did was install the latest updates, apply my theme, and install vmware.

can anyone help me?

Edit: it seems that logging off and then back on also fixes the issue, but only for a few minutes

---

### Post by oldos2er on 2008-09-22
Which keyboard layout are you using?

---

### Post by thetillster on 2008-10-30
Hi Knight,
I have the same problem. So does my colleague. I don't know whether it is related to VMWare, that's is at least what we suspect. I have a workaround: You don't need to log out, which works as you mentioned. You can change your keyboard layout to any arbitrary layout then change it back to the original one in the Presferences->Keyboard menu. You don't even have to close this menu after having switched to the new one. As a test you can use the specified input box in the menu. It will close just like any other app if it didn't fix it. Other than that I'm still lokking for the solution.

---

### Post by thetillster on 2008-10-30
I found a solution that works for me. It was pointed out in the rather lengthy debate about this bug in [https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/195982"). Create a launcher application that just executes the command [COLOR="Yellow"]setxkbmap[/COLOR].

---

