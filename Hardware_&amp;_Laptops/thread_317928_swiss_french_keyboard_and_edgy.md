---
title: "swiss french keyboard and edgy"
date: 2006-12-13
forum: Hardware &amp; Laptops
---

### Post by Psykotik on 2006-12-13
Hi,

Since my upgrade to edgy (but I suspect it is related to the Xorg update), the configuration for my keyboard switched to a french one. Under Gnome everything works and fully usable, but it is not when switching to the console.

Here is the xorg.conf related part to keyboard :

```
Section "InputDevice"
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    #Option	   "XkbModel"	"pc105"
    Option         "XkbModel" "logiink"
    Option         "XkbLayout" "ch"
    Option         "XkbVariant" "fr"
EndSection

```

Since I know I am no only swiss person here, some of you had to change this part... to what ? How to obtain the swiss french keyboard ?

---

### Post by xyz on 2006-12-13
Salut,
I don't know if this will help (I'm still on Dapper)...but Edgy no longer has 
Preferences > Keyboard > Add ?? M.....alors!
This looks promising:
[Ubuntu edgy and swiss french keyboard]("http://www.stgraber.org/?p=5")
**by Stéphane Graber**
> As you may have seen if you tried to install the alternate (non-live) CD of Ubuntu/Kubuntu/Edubuntu, there is only one keyboard for the whole switzerland (it’s called “Switzerland”) which is in fact the swiss german one.

The bug was reported and a patch was done and will be added for the next CD (probably with Feisty), if you can’t wait and need a “swiss french” alternate cd, I did these isos for you.
Let me know if it works...ciao Geneva!

---

### Post by xyz on 2006-12-13
Hi again,
I started a new thread [Using Swiss French keyboard? ( Edgy) Beware of this...]("http://www.ubuntuforums.org/showthread.php?p=1880832#post1880832") in the Ubuntu Café.
You may want to check on that thread once in a while as someone might just come up with another solution.
Bonne chance!

---

### Post by Psykotik on 2006-12-13
Well, thank you very much xyz, but my problem doesn't affect gnome, which recognizes perfectly my swiss french keyboard (yes, you'll still find the keyboard preferences in Edgy :) ).

The problem occurs only when switching to the console (ctrl+alt+f1, f2, f3, and so on). Thanks anyway.

Anyone else ?

---

### Post by stgraber on 2006-12-13
The problem is only with the keymap used by the installer and then set as default for the ttys, it doesn't really affect the X server where you can manually set your keymap to swiss-french in the Gnome GUI or by editing the xorg.conf file manually.

I didn't search, but there is of course an easy way to fix this keymap issue for ttys as well, but I thought it was easier to make a fixed iso and share it than writing a doc on how to fix that :)

Anyway, this issue is now fixed in Feisty (I have posted a bug report and a fix on launchpad).

---

### Post by Psykotik on 2006-12-13
Salut Stéphane,

Is it a complex task ? I'm not going to upgrade to Feisty right now, as I'm not going to reinstall an all new Edgy to get the advantage of the new keymap :cool: 

Can you explain how to patch ? It would be a double benefit, I'll learn something about the keymaps, and I'll be able to confortably use my keyboard again.

TIA

---

### Post by stgraber on 2006-12-14
I think that's the way to fix on a classical Edgy :
Edit /etc/default/console-setup as root

At the end of it you should see some keyboard related line, make them to look like that :
XKBMODEL="pc105"
XKBLAYOUT="ch"
XKBVARIANT="fr"
XKBOPTIONS="lv3:ralt_switch"

Then reboot and tell me if you now have the swiss-french keyboard when in console mode.

Stéphane

---

### Post by Psykotik on 2006-12-14
Merci beaucoup, Swiss friend. It works like a charm. I do not feel anymore like a old clerk with arthritis when I switch to the console :)

---

