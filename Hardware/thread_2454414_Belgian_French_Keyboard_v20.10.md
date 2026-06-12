---
title: "Belgian French Keyboard v20.10"
date: 2020-11-29
forum: Hardware
---

### Post by woutz on 2020-11-29
Hi,

Does anyone know how to use a Belgian French keyboard with Ubuntu 20.10? Tried all possible listed French keyboard layout versions in Settings  -  Region & Language  -  Add Input Sources, but no luck.

[IMG]https://upload.wikimedia.org/wikipedia/commons/thumb/9/93/Belgian_keyboard_layout.png/1200px-Belgian_keyboard_layout.png[/IMG]

Maybe just me looking at the wrong place?

---

### Post by CelticWarrior on 2020-11-29
Welcome.

Have you tried French (AZERTY)?

---

### Post by woutz on 2020-11-29
Thanks a lot for your swift reply.

And, yes, thanks, I did try 'French (AZERT), - amongst many others :-) . But the French AZERTY layout (of France) - and all the other standard layouts listed in the standard drop down list are all  different than the Belgian one.

However, I just stumbled upon this post here: [https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en](https://help.ubuntu.com/stable/ubuntu-help/keyboard-layouts.html.en) - and think that does the trick.

Added' French' as additional language and executed the recommended command *gsettings set org.gnome.desktop.input-sources     show-all-sources true* - and now 'Belgian French' is figuring in the drop down list!

---

