---
title: "Multiple Desktops"
date: 2008-10-18
forum: General Help
---

### Post by dontgetshocked on 2008-10-18
I did have multiple desktops at one time and unchecked or disabled it and now I need it back.I have Compiz installed as well.Where do I go and what do I do to get this working?

Thanks,

---

### Post by pdub on 2008-10-18
sudo apt-get install compizconfig-settings-manager

System->Preferences->Compiz Config Setting Manager->General->Desktop Size

Change the Horizontal Virtual Size to 4, the rest should be one.

---

### Post by dontgetshocked on 2008-10-18
I have it set already and nothing has changed.

---

### Post by brianfreytag on 2008-10-18
> **dontgetshocked said:**
> I did have multiple desktops at one time and unchecked or disabled it and now I need it back.I have Compiz installed as well.Where do I go and what do I do to get this working?

Thanks,

Several questions I have:

What graphics card do you have?
Do you have proprietary or opensource graphics drivers installed for that card?
If you go to System -> Preferences -> Screen Resolution, is one of the options a very large screen resolution?  For example, mine is 3360 x 1050 (I have a 20" Dell monitor with a native 1680 x 1050 and a 17" Westinghouse monitor with a 1280*768)  If you have a large screen resolution, select that one.  This is for an ATI Radeon 4850 with the ATI Catalyst 8.10 proprietary drivers.

---

### Post by pdub on 2008-10-18
Do you have the Workspace Switcher on your top or bottom panel?

If you do, try right-click preferences and set the # of desktops

If you do not, then right click on the top or bottom panel, choose Add to Panel and add the Workspace Switcher applet.

Columns are the # of workspaces.

---

### Post by dontgetshocked on 2008-10-18
That did the trick, adding the workspace switcher.

Thanks,

---

### Post by geovino on 2008-10-31
> **pdub said:**
> sudo apt-get install compizconfig-settings-manager

System->Preferences->Compiz Config Setting Manager->General->Desktop Size

Change the Horizontal Virtual Size to 4, the rest should be one.

My multiple desktops is set at one and I can't change it to 4. What needs to be changed so I can create 4 desktops for the cube?

---

### Post by geovino on 2008-10-31
> **dontgetshocked said:**
> That did the trick, adding the workspace switcher.

Thanks,

Where is workspace switcher? I don't see it here in 8.10.

---

### Post by geovino on 2008-11-01
> **brianfreytag said:**
> Several questions I have:

What graphics card do you have?
Do you have proprietary or opensource graphics drivers installed for that card?
If you go to System -> Preferences -> Screen Resolution, is one of the options a very large screen resolution?  For example, mine is 3360 x 1050 (I have a 20" Dell monitor with a native 1680 x 1050 and a 17" Westinghouse monitor with a 1280*768)  If you have a large screen resolution, select that one.  This is for an ATI Radeon 4850 with the ATI Catalyst 8.10 proprietary drivers.

I have a Nvidia Geforce 5200 card and the Nvidia-glx-173 is installed.

---

### Post by geovino on 2008-11-01
Got the cube working. Thanks :)

---

