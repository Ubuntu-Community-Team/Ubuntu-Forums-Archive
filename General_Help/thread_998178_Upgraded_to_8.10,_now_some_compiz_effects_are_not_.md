---
title: "Upgraded to 8.10, now some compiz effects are not working"
date: 2008-11-30
forum: General Help
---

### Post by lsutiger on 2008-11-30
I upgraded to 8.10 from 8.04 today. I have been playing with compiz/beryl for over a couple of years now, so this is not completely foreign to me. This is the first time I have come across this problem. EX: I have the burn animation set for closing a window, but when I close a window, it just closes. My minimize is set to magic lamp, but the action it is taking is the default action (I forget the name of it - but it is the default out of the box when you run compiz). But I changed my open animation to dream, ad it works.

So I am confused. Can someone help me out in trying to solve this problem?

---

### Post by Forlong on 2008-12-01
Most of the "intense" effects are now in a separate plugin called **Animations Add-On** – enable that to get those animations back.

---

### Post by Wartender on 2008-12-01
if that doesn't work (if you already have it enabled) just click the little brush icon to reset the settings to default and set it again, that worked for me when my animations stopped working when i upgraded to 8.10

---

### Post by lsutiger on 2008-12-01
Thanx Wartender, that worked for the initial problem. But there are some other bugs I have found. 

One, which is really aggravating, is when I click on an icon in AWN that is on another desktop, it does not go to that desktop. I have to click it several times to get to the right one.

I think I may go back to 8.04

---

### Post by Wartender on 2008-12-01
you're welcome :), i'm not sure about that awn problem though, maybe a reinstall? (of awn)?

---

### Post by lsutiger on 2008-12-01
Thanx for the quick reply! I tried a complete removal, restart, then instal of AWN and still having the same problem :(

---

### Post by lsutiger on 2008-12-03
Here's another quirk I can not figure out. I have the minimize animation set to magic lamp, but when I recall a minimized application, the glide animation is used....HUH? I thought minimize and restore were controlled by the same animation (beryl had a separate animations).

Can anyone explain this to me?

---

### Post by Forlong on 2008-12-04
Works here as expected, when minimizing to the window list applet of the GNOME panel.

What are you minimizing to?
I know applications that minimizie to tray are using the open animation on restore.

---

### Post by lsutiger on 2008-12-04
Minimizing to Avant Window Navigator. I do not have glide set to the open animation, but to the dream animation, but glide is what is being used to restore a window.
Thanx for all the input!

---

### Post by Forlong on 2008-12-04
What's the output of
```
gconftool-2 -a /apps/compiz/plugins/animation/screen0/options | grep Glide
```

---

### Post by lsutiger on 2008-12-06
I got nothing...sooo, I downgraded back to 8.04, but compiz is acting wacky here too!!

Is there a way to reset all of the settings to a "default"? I would rather do that than fool around with the settings all day.

---

### Post by Forlong on 2008-12-06
> **lsutiger said:**
> Is there a way to reset all of the settings to a "default"?
In case you're on GNOME:
```
gconftool-2 --recursive-unset -a /apps/compiz
```

---

### Post by lsutiger on 2008-12-06
Thanx Forlong!

---

