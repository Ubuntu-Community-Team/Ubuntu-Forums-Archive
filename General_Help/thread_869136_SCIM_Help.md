---
title: "SCIM Help"
date: 2008-07-24
forum: General Help
---

### Post by lusiads on 2008-07-24
I use vi-telex input method to input Vietnamese which is supported by m17n-db package.
I can input Vietnamese in gedit and some programs by right click,  navigating Input Method, select either SCIM Input Method or SCIM Bridge Input Method (active vi-telex by press Ctrl+Space). But that menu doesn't appear in OO or Firefox. All I want is SCIM, and I didn't have to select SCIM IM or SCIM Bridge IM before, just trigger SCIM with hotkey Ctrl+Space.

I tried to follow instructions at [https://answers.launchpad.net/ubuntu/+question/38428](https://answers.launchpad.net/ubuntu/+question/38428) and [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) but neither did work.

Steps I managed to do are listed following:
- remove and reinstall scim and m17n-db package.
- "im-switch -l" show my prefered input method was scim but scim does not appear by default (since it is not active).
- "im-switch -z en_US.UTF-8 -s scim-bridge" (my locale is en_US.UTF8, also tried with scim) but that didn't work (after re-login even restart).
- tried to edit /etc/X11/xinit/xinput.d/scim, change GTK_IM_MODULE=xim to GTK_IM_MODULE=scim-bridge.

scim worked nice for me before, but now it doesn't.
I'm running Hardy 8.04.1 up-to-date.

Any suggestions?

---

### Post by lusiads on 2008-07-25
Nobody has give any suggestions yet.
Do I have to reinstall entire OS just to get scim work the right way?

---

