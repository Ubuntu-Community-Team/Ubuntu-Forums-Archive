---
title: "Suspend Button doesn't appear on my desktop"
date: 2008-08-20
forum: General Help
---

### Post by Zaff on 2008-08-20
Hi all,
I have a desktop computer at home and when I click on the green man I get the shutdown dialog with hibernate, restart shut down and all this but no suspend button.
Now I do have that suspend on both my laptops.
I would like to be able to use suspend because my computer makes a bit of noise and I wanna be able to turn it "on and off" quickly.
So is there a reason I don't have this button ? Can I fix that and how ?
I'm using Hardy.
Thanks in advance.

---

### Post by sdennie on 2008-08-20
Not all machines support suspend.  You may be able to force the button to appear by hitting Alt-F2, typing gconf-editor and then navigating to /apps/gnome-power-manager/general and checking can_suspend.  That should cause the icon to appear but doesn't insure the machine will actually suspend and resume properly.

---

### Post by Zaff on 2008-08-20
Okay, I will try this. It wuld be really convenient to be able to use suspend. Do you know if there's a list of hardware that support suspend somewhere ?
Thanks.

---

### Post by sdennie on 2008-08-20
I don't know of any list, no.  The best way to find out if it works is just to try it (make sure you have no apps open so, if it doesn't work, you won't lose any data).

---

### Post by Zaff on 2008-08-20
okay so I went into gconf-editor and the cansuspend check box was already checked. I still don't have the suspend button. Is there anything else I should do ? What's the command line for suspend ?

---

### Post by LateNiteTV on 2008-08-20
this is a problem with acpi support across different boards. nothing you can really do about it...

---

### Post by Zaff on 2008-08-20
okay so it's the motherboard that doesn't support it.
Thanks anyway

---

### Post by LateNiteTV on 2008-08-20
most likely. your motherboard probably does support it to some extent, but linux also may not be able to fully support it.

---

