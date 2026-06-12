---
title: "Vertical Panels"
date: 2008-07-16
forum: General Help
---

### Post by arigram on 2008-07-16
I have been experimenting with my desktop panels in vertical position. My desktop resolution of 1920x1200 gives plenty of space in the horizontal and I have been using only one panel to fit almost everything at the top. Yet, this novel orientation at the sides is quite attractive. I am forced to split the panels in two, but I don't feel like I am losing space.
The left panel has the application selectors and information and the right the workspace and window selectors.

There are some problems though as the option to have the panel on the sides gets very little use and is not very developed.

- The Menu applet of "Applications, Places and System" should allow:
    - Icons instead of Text Labels on the main categories on the panel
    - Customizing the orientation of the main categories (so I could have for example Applications at the top instead at the bottom)
- The Window Switcher should allow the use of Icons instead of text labels because as it is, I can't read the labels and can't distinguish the windows unless I get a preview from compiz.
- The Window Switcher also has a bug where when the panel background color is semi-transparent, the window buttons save for the one selected are invisible.
- Some applets could have a vertical orientation, such as the System Monitor applet which could show the graphs vertically and the Window Switcher should also display the window names vertically like all the other labels.

It works fine apart from those things.

---

### Post by scragar on 2008-07-16
hmn, I'll have to try vertical panels at some point, my monito's on the 1280 res, so I've got a lot more free space on the sides than the top(it's almost 50px for both panels, which is a fair bit when you think about it(50px/~1000px = 1/20th of the screen!))

---

### Post by Krydahl on 2008-07-16
Yeah I tried this for a while and gave up. I just found too many applets hadn't been designed with the vertical orientation in mind - windows switching being one of the worst (next to useless). 

Hope someone looks at this.

---

### Post by arigram on 2008-07-16
I think I will go with this single panel for now (with the window selector menu), until the applets get more developed or move to KDE.

---

### Post by arigram on 2008-07-16
I also discovered that Compiz is affected when changing the workspaces in the workspace selector applet. That means that if I am changing the display of let's say four workspaces from the horizontal to the vertical (rows and columns in the preferences) it changes the actual orientation and number of workspaces in the "compiz space". The Expo displays the workspaces vertically and the cube ceases to work. So, that makes the Workspace applet useless in the vertical.

---

### Post by Krydahl on 2008-07-16
I see this too, but can't get too worked up about it. The workspace switcher seems almost useless in the vertical configuration (workspaces shown too small to use) and configuring it as you suggest doesn't seem to make it any better.

Personally I change workspace either via keyboard shortcuts, expo or mouse rotation and don't feel the need to use the panel applet.

---

### Post by arigram on 2008-07-16
Krydahl, I also use the Cube and Expo of Compiz, but the applet is useful to check if I am "forgetting" any open applications or windows on another workspace and switch with just a click of the mouse.

If only the Windows Selector Applet would change to show icons (not unlike what the Windows Selector Menu does or the applet in XCFE), then it would really be perfect. I have room for lots of window icons in the vertical and the Menu applet doesn't make sense in this configuration (you can't see or select a window unless you click to open the menu - good for small screens only).

---

### Post by Krydahl on 2008-07-16
I agree, the window selector applet is the real problem with this setup. I have used the menu version, but it introduces an extra a click and you can't see what's going on at a glance. 

I wonder who we'd have to contact to put in a feature request? Gnome devs, presumably.

---

### Post by scragar on 2008-07-16
why not use

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)

```
wmctrl -s 2
``` etc in a line of launchers? that way the real config would say they are horizontal, yet you get to keep the line vertical. Not a perfect solution, but a working one.

---

### Post by arigram on 2008-07-16
> **Krydahl said:**
> I wonder who we'd have to contact to put in a feature request? Gnome devs, presumably.

Whom, indeed.
Anyone know how to file a bug/feature request?
(although I did find a request in Brainstorm)

Ok, I found the Gnome Applets in Launchpad:
[https://launchpad.net/ubuntu/+source/gnome-applets](https://launchpad.net/ubuntu/+source/gnome-applets)

---

### Post by Krydahl on 2008-07-17
Saw your bugs. Good work. Something I should do more often.

---

### Post by arigram on 2008-07-17
> **Krydahl said:**
> Saw your bugs. Good work. Something I should do more often.

I did already receive a response which is a great sign.
Icons in the Window List has been filed already from what I was told (even if I didn't find a reference by searching), so if Window List will display the icons of applications/windows, then we're all set!

---

### Post by arigram on 2008-07-17
> **scragar said:**
> why not use

[http://www.sweb.cz/tripie/utils/wmctrl/](http://www.sweb.cz/tripie/utils/wmctrl/)

```
wmctrl -s 2
``` etc in a line of launchers? that way the real config would say they are horizontal, yet you get to keep the line vertical. Not a perfect solution, but a working one.

Thank you.
That takes care half of what the applet is for, although I could use the display of windows inside each workspace thumbnail to remind me what's there.

---

### Post by scragar on 2008-07-17
I don't think it's possible to do that without writing an applet for the purpose(and there's already an applet for that very reason, I'm sure there'll be an official fix at some point). Someone else might be able to help you out with that though(I think you might be able to get a script to edit images based on the windows or whatever which might work)

---

### Post by Krydahl on 2008-07-28
I'm currently trying to do without a windows selector (the main thing stopping me using vertical panels) and trying out using the scale plugin in compiz instead. I'm not sure whether I can get into the habit, but we'll see.

---

