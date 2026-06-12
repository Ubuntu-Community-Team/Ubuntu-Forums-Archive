---
title: "Dot is switched to comma in dot key!"
date: 2008-11-15
forum: General Help
---

### Post by jpmelos on 2008-11-15
Hi everyone

When I press the dot key in my keyboard, it inputs a comma
I'm using VAIO VGN-FZ250AE, Ubuntu 8-10 fully updated
This bug appeared after the updates of today (November, 15)
Could anybody help me?

Thank you very much, and sorry for the dot-less post LOL

/edit: ABNT2 layout keyboard (Brazilian layout)

---

### Post by nikgare on 2008-11-15
Which keyboard do you have configured in Ubuntu?

Try **System->Prefences->Keyboard**

---

### Post by manuquadros on 2008-11-16
I have exactly the same issue on an Acer Aspire 5050-3233,

Also an ABNT2 layout keyboard (Brazilian layout),

A difference is that I'm using Xubuntu 8,10, also fully updated, On the Keyboard Preferences, the option that is marked is "Use X configuration",

---

### Post by Mardoct909 on 2008-11-16
Are you sure your keyboard is a Brazilian layout? It might very well not be. I'm in Canada, but I have as of yet to see a Canadian layout keyboard. It's always US.

---

### Post by manuquadros on 2008-11-16
> **Mardoct909 said:**
> Are you sure your keyboard is a Brazilian layout? It might very well not be. I'm in Canada, but I have as of yet to see a Canadian layout keyboard. It's always US.

Yes, I am,

Anyway, it was working perfectly before the last upgrade,
Is there any way to undo the last batch of upgrades I did? At least I would be able to do some decent typing until the issue was solved,

---

### Post by manuquadros on 2008-11-16
It seems to be a problem with xkb-data version 1.3-2ubuntu4.1. To have your dots back, you have to revert to version 1.3-2ubuntu4. It worked for me. (see my dots! :P)

---

### Post by carloshiga on 2008-11-16
Create a script keymap.sh like this:

```
#!/bin/bash

xmodmap -e "keycode 129 = period"
xmodmap -e "keycode 60 = period greater"
xmodmap -e "keycode 62 = Shift_R"
xmodmap -e "keycode 46 = l"
```

and then

```
sudo sh keymap.sh
```

It works for me but there is a little problem: every time I boot my computer I have to run the script again. I tried to put it in /etc/init.d/ and use update-rc.d like this

```
sudo update-rc.d keymap.sh defaults
```

but it didn't work. Any idea to run this script while booting?

---

### Post by wingnux on 2008-11-17
I'm having the same problem and it really scared the **** out of me :P Gonna revert to the previous version of xkb-data then, thanks for the tip! ;)

---

### Post by rogeriovinhal on 2008-11-19
Until yesterday I had this problem, but only on the numeric pad. But with yesterday's updates, the actual period button (on comma's right) started working like a comma also.

What kind of fix not only doesn't fixes the problem but makes it worse?

And then we can't have Openoffice 3.0 because it isn't "tested" yet...

---

### Post by pingflood on 2008-11-19
It's an ond and well known bug, (<- this comma should be a DOT!)
It's reported (more than one time), the team know the problem and the solution, but until now there's no package fixed in repositories,,

[https://bugs.launchpad.net/bugs/272606](https://bugs.launchpad.net/bugs/272606)

I never been so sad with a bug in [K]Ubuntu like I am now,
Not because the bug itself (there are many other bugs in Kubuntu and I don't care), but because seems the team doesn't care about it,

---

### Post by rafaelcapanema on 2008-11-20
Wow, same here, (this also is supposed to be a dot)
Ubuntu seems quite buggy lately,
Since I've upgraded to Intrepid, I've been having problems with Compiz, Firefox and now this,,,

---

