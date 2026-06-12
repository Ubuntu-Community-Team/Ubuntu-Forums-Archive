---
title: "[SOLVED] Compiz not allowing me to add a second virtual desktop(can only have one)"
date: 2008-09-13
forum: General Help
---

### Post by Predator106 on 2008-09-13
Hello, I am using GNOME with Compiz, I want to add another virtual desktop, I used to have 2 total virtual desktops. But in Compiz General Settings->Desktop Size-> Number of desktops, it is locked at 1. Locked as in it won't let me up the value what-so-ever. This also means, that since I can only "have" one virtual desktop, that the applet: Workspace Switcher, will not let me use the second one that I have listed, in other words, it's grayed out.

The settings above the one that I mentioned are set to 2 for Horizontal virtual size, and set to 1 for Vertical virtual size. I also have tried setting all of them to high values, in hopes that the one control would "become" enabled, but that didn't work.

I have also tried resetting the window manager(compiz). I have Compiz, I also have Emerald.

Also note that I did used to have a second monitor attached (dual-monitor setup), but I didn't like it. But prior to this, I could always use my virtual desktops (and I did, often).

Do you think that Ubuntu thinks, in a remote way, that I still have my second monitor attached.

---

### Post by billgoldberg on 2008-09-13
> **Predator106 said:**
> Hello, I am using GNOME with Compiz, I want to add another virtual desktop, I used to have 2 total virtual desktops. But in Compiz General Settings->Desktop Size-> Number of desktops, it is locked at 1. Locked as in it won't let me up the value what-so-ever. This also means, that since I can only "have" one virtual desktop, that the applet: Workspace Switcher, will not let me use the second one that I have listed, in other words, it's grayed out.

The settings above the one that I mentioned are set to 2 for Horizontal virtual size, and set to 1 for Vertical virtual size. I also have tried setting all of them to high values, in hopes that the one control would "become" enabled, but that didn't work.

I have also tried resetting the window manager(compiz). I have Compiz, I also have Emerald.

Also note that I did used to have a second monitor attached (dual-monitor setup), but I didn't like it. But prior to this, I could always use my virtual desktops (and I did, often).

Do you think that Ubuntu thinks, in a remote way, that I still have my second monitor attached.

You only need to change the horizontal size.

The number of desktops needs to remain 1.

I don't know why it doesn't work for you.

Try using 4 instead.

---

### Post by Predator106 on 2008-09-13
No, I tried doing both, and each individually, the virtual and the horizontal. I even tried to max them out, still nothing. I set the horiz. to 4 and the vertical to 1 and it's still the same problem. Also note that I have set the applet to 2 columns by 1 row, but the other one is greyed out and I can't use it.

---

### Post by RobbMeex on 2008-09-13
Me too. Clicking on the other desktops do nothing. 4 horizontal 1 vertical. other desktops are useless now :(

EDIT: reenabled desktop wall, and they are back. of course the cube is undone.

---

### Post by Predator106 on 2008-09-13
UPDATE: Apparently it is actually compiz that's doing it. When I switch it to metacity, they work fine....

EDIT: Well, I've figured out that it is with my profile, it must be screwed up.... but I don't want to lose the information in my profile. If I create a new profile (default) and use it, it works fine....

---

### Post by Predator106 on 2008-09-13
Yeah, you were right, that would explain everything, the Desktop Wall was disabled for some reason, you do need the cube disabled, but since the desktop wall is kind of built into the cube it doesn't really matter, even though I don't use the cube and like the other way better.

Problemo has been solved....o.

:)

---

