---
title: "Multiple Monitors, Multiple Desktops"
date: 2008-11-17
forum: General Help
---

### Post by Mars Thrax on 2008-11-17
I have a tablet PC that I hook up to my secondary monitor whenever I'm at home, and I'd like to have a panel that contains a window list on each (so that it only shows the windows that are on that screen). Since the system will sometimes operate with a single display (when I am not home) and sometimes with two displays, I'd like to have one configuration that "just works"

The most straight forward solution I can think of is to have each display map to a separate workspace. I've been looking around, and haven't found any way to do this...is it possible with 8.10?

I have tried adding a panel to the secondary display, but it seems a bit buggy (items in the menu list only appear when the window is hovering between the two screens...if it is completely in the primary display, it shows up in that list...if it is completely in the secondary display, it disappears from both lists...if it is partially in each, it shows up in the secondary display's list).

An additional note (if it matters) is that I can't use Compiz...my system will not work in dual-screen mode with Compiz enabled.

Any ideas would be greatly appreciated!

---

### Post by easybake on 2008-11-17
> **Mars Thrax said:**
> I have a tablet PC that I hook up to my secondary monitor whenever I'm at home, and I'd like to have a panel that contains a window list on each (so that it only shows the windows that are on that screen). Since the system will sometimes operate with a single display (when I am not home) and sometimes with two displays, I'd like to have one configuration that "just works"

The most straight forward solution I can think of is to have each display map to a separate workspace. I've been looking around, and haven't found any way to do this...is it possible with 8.10?

I have tried adding a panel to the secondary display, but it seems a bit buggy (items in the menu list only appear when the window is hovering between the two screens...if it is completely in the primary display, it shows up in that list...if it is completely in the secondary display, it disappears from both lists...if it is partially in each, it shows up in the secondary display's list).

An additional note (if it matters) is that I can't use Compiz...my system will not work in dual-screen mode with Compiz enabled.

Any ideas would be greatly appreciated!

I think the solution to your problem would be to create a seperate X screen. You have your second monitor on a second workspace. Your mouse is able to move between workspaces but you won't be able to drag windows between the 2.

I have got this to work through nvidia-settings.

(I am still using Hardy so forgive me if this doesn't work)

If don't have nvidia-settings installed, install it through terminal ```
sudo apt-get install nvidia-settings
```

Once it installs run it, either through the menu listing or in terminal by typing nvidia-settings.

Select "x server display configuration", 

**highlight your second monitor**

Click configure, select "Seperate X Screen"
Click "Save To X Configuration File"
Click Apply

Restart your comp and it should work. 

That is the easiest way I have found without having to edit your xorg.conf.

---

### Post by Mars Thrax on 2008-11-17
Unfortunately, I don't have an Nvidia graphics card. I am using a Toshiba M700, which come swith an intel on board graphics...so using that utility won't really help much.

Thanks for the reply though.

---

