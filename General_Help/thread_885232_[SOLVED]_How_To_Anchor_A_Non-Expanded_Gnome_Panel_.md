---
title: "[SOLVED] How To Anchor A Non-Expanded Gnome Panel To A Corner"
date: 2008-08-09
forum: General Help
---

### Post by the real omni on 2008-08-09
This guide will walk you through customizing the gnome-panel so it doesn't take up so much real-estate on your screen but is still readily accessible.

A lot of panel customization can be performed by simply right-clicking on the panel and choosing "Add to panel...", "Remove from panel", or simply "Properties". More advanced configuration has to happen in the gconf-editor. We'll get to that.

First off, if you use a custom task manager such as Avant Window Navigator (see [http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu](http://www.ventanazul.com/webzine/tutorials/avant-window-navigator-ubuntu) for an example and installation walkthrough) then you can delete the bottom panel altogether. Once Avant Window Navigator is installed you can delete the bottom panel altogether - right-click on it and choose "Delete panel".

Next, you can right-click on any unwanted items in the top panel and choose "Remove from panel". You can also save space by removing the standard menus and then adding the Main Menu applet. (To add the applet, right-click on the panel and choose "Add to panel..."). The Main Menu applet puts an icon in the place of the menus that gives you access to all the menus but takes up a fraction of the screen real-estate.

Once you've removed all the unwanted panel items, right-click on the panel and choose "Properties". (Note: you'll have to right-click on an empty part of the panel, not one of the icons or status area)

Set the Orientation to the side of the screen you'd like to act as the primary anchor. This will be the side that the system tray / status area icons will spread out over, so if you want the tray to grow vertically you anchor left or right, if you want the tray to grow horizontally you anchor top or bottom. (By anchor I mean you set the Orientation setting thusly).

Next up, the size. That's up to you and relatively unimportant when it comes to the more advanced settings.

Un-tick / de-select the "Expand" option. This will shrink your panel and center it on whichever screen edge is set in the Orientation setting.

Select autohide if you'd like. If you find the hiding/showing takes too long and/or if you'd like the bar to be COMPLETELY hidden when it auto-hides we can set that up later in the advanced configuration.

Show 'hide' buttons & Arrows on 'hide' buttons: I like to select both of these. The first will put buttons on the top and bottom of a vertically-oriented panel and on the left and right of a horizontally-oriented panel. When you click the button it scoots the panel out of view so the only space it takes up on your screen is a tiny little button in the corner. 

The only problem with the Show 'hide' buttons option is that if you have Expand de-selected, your panel is centered in the screen and then has to travel all the way to the edge. This makes it a little inconvenient if all you want to do it pull up the panel, click on a menu item, and then hide the panel again.

So now we move on to the advanced configuration.

Hit ALT+F2 to bring up your trusty Run dialog.

Run 
```
gconf-editor
```

This will bring up a window that's similar to the Windows Registry (but better for two reasons: it's easier to navigate/figure out, and you don't have to run Windows to use it).

In the gconf-editor window, navigate to apps -> panel -> toplevels -> top_panel_screen0 (or whatever panel you want to configure).

If you selected Auto-hide and you want to make the bar completely hidden, change the value for "auto_hide_size" to "0".

If you want to speed up the hiding and showing of the panel during auto-hide or when the 'hide' buttons are pressed, de-select the entry titled "enable_animations" and reduce the "hide_delay" and "unhide_delay" values.

If you want to anchor the panel to a corner instead of having it centered, de-select "x_centered" and "y_centered" and then change the "x", "x_right", "y", and "y_bottom" values according to the corner you want to anchor the panel to:

To anchor the panel to the _top left_, set the following values:

```

x       : 1
x_right : -1
y       : 1
y_bottom: -1
```

To anchor the panel to the _top right_, set the following values:

```

x       : 0
x_right : 0
y       : 1
y_bottom: -1
```

To anchor the panel to the _bottom left_, set the following values:

```

x       : 1
x_right : -1
y       : 0
y_bottom: 0
```


To anchor the panel to the _bottom right_, set the following values:

```

x       : 0
x_right : 0
y       : 0
y_bottom: 0
```

---

### Post by rainwalker on 2008-08-10
Not really related to your guide, but on the off-chance that you might know:
One day, after resuming from suspend, my panels stopped un-hiding when I moused over them unless set to show 5 or 6 pixels instead of 1 (and even then they sometimes didn't unhide correctly). It only seems to happen when I'm using Compiz.
Any suggestions?

---

### Post by the real omni on 2008-08-10
Sounds like strange behavior. 

If the malfunction is only present when Compiz is running I'd say that's a good place to start your troubleshooting.

Fire up the Compiz config and look for any effects/plugins that seem like they might be responsible.

If it were me, I think the first places I'd look in the compiz config would be any plugins that are related to snapping to edges. (Wobbly windows, etc)

If you want to go through the proper troubleshooting routine like a professional technician would, the thing to do is whip open your compiz config, disable every single plugin, and see if the problem is still there. If the problem is present when compiz is running but no effects are enabled, it's likely something to do with the way compiz itself communicates with gnome. If the problem is gone when all plugins are disabled, you can start enabling plugins one by one and seeing if the problem comes back between each plugin. Eventually you'll find the one that's causing the problem and from there you can work on steps to fix the conflict (or at the very least, work around it).

Hope this helps :)

---

### Post by PsychedelicWonders on 2008-08-16
Hey im not sure what happened, but I had this thing set to the bottom right of my screen and decided it would work better at the top center because of the avn dock I am going to have.

But now my toolbar is stuck in the very middle of my screen.

What do I need to modify to get it at the top center?

thanks.

---

### Post by PsychedelicWonders on 2008-08-16
it seems I was actually able to click and drag the tool bar to the top center where I want it, but will it stay there now is the question?

---

### Post by the real omni on 2008-08-16
> **PsychedelicWonders said:**
> it seems I was actually able to click and drag the tool bar to the top center where I want it, but will it stay there now is the question?

> **PsychedelicWonders said:**
> it seems I was actually able to click and drag the tool bar to the top center where I want it, but will it stay there now is the question?

To center the bar at the top of the screen, use these settings for gconf-editor -> apps -> panel -> toplevels -> top_panel_screen_0

```

orientation : top
x           : 0
x_centered  : true (checked)
x_right     : -1
y           : 0
y_bottom    : -1
y_centered  : false (unchecked)

```

Then it should set itself centered on the top edge of the screen even after a reboot. :)

---

### Post by PsychedelicWonders on 2008-08-16
alright that all seemed to work.

Now let me ask you a few more questions regarding this situation:

When I open programs, i.e. opera, etc. it doesnt open in a full screen, but instead seems to allow space at the top and the bottom as if the tool bars were actually there.

1) So how do I set it up that when i open programs, they open full screen?

2) Can I move the icons as I choose?  It doesnt seem that way?

3) right now they are on the right, can I push them all to the left by my name?

4) Will it always show my name at the top between those two bars?

5) is there any way to have a clock always visable regardless of what is up on the screen, be it toolbars or open programs?

6) And maybe put all of the "open" programs between those bars instead of my name so it kind of "highlights" at a quick glance what is actually open?

Does this all make sense?

---

### Post by the real omni on 2008-08-16
> **PsychedelicWonders said:**
> alright that all seemed to work.

Glad to hear it. :)

> Now let me ask you a few more questions regarding this situation:

Most of these questions can be answered by simple google searches. In case you're unfamiliar with how to use Google.com, I'll provide example search terms I would start with in order to research the individual questions:

> 1) how do I set it up that when i open programs, they open full screen?

This one is a 2-part answer.

1) The gnome panel at the top. 

The space that's created at the top is for the gnome-panel that is centered on the top edge of the screen. If you set the panel to auto-hide, it will remove the space so your maximized application windows will hug the top edge of the screen. Your gnome panel will slide up under the top edge of the screen and you'll just see the edge of it. Hover the mouse over the edge, and the full panel will slide down. 

Unfortunately I haven't found any way to have a non-expanded panel visible at all times and not reserve the desktop real-estate of an expanded panel. I suppose it's just a gnome shortcoming. If you really really need to have the panel visible all the time and you really really need to have the desktop real-estate available all the time, I'd suggest creating a new Bug Report on the Ubuntu Launchpad page. ([https://launchpad.net/ubuntu](https://launchpad.net/ubuntu))

2) The AWN dock:

The space at the bottom of the screen is created by the AWN dock. Essentially it's the same situation as the top gnome panel space, but luckily AWN has more ability to control how the space is handled.

- Click on any icon in the dock and the top option in the context menu should be "Dock preferences". Choose that option to bring up the Preferences dialog.

- In the Preferences dialog, look at the options in the Bar Behavior section of the General page. The setting that makes AWN reserve the entire bottom of the screen as blank space is the setting "Maximized windows don't cover the bar (requires restart)". Ensure this setting is _de-selected_ and restart if needed.

> 2) Can I move the icons as I choose?  It doesnt seem that way?

You can. 

Google:
```
ubuntu gnome panel how to move icons
```

and

Google:
```
ubuntu avant window navigator how to move icons
```
(Note that using the -TRUNK version of AWN disables the "Refresh" button in the Launchers page of the AWN manager, so once you've arranged your AWN launcher and applet icons you'll have to log out then back in.)

> 4) Will it always show my name at the top between those two bars?

Google:
```
ubuntu gnome panel how to remove items
```

> 5) is there any way to have a clock always visable regardless of what is up on the screen, be it toolbars or open programs?

Google:
```
ubuntu standalone clock
```

(standalone means a program that runs on its own instead of being anchored to the gnome panel or a dock like AWN.)

NOTE: For pretty much ANY kind of software installation, the best thing to do is hunt through your Add/Remove... option in the Applications menu on the gnome-panel. There's a search function, so you can just type in "clock" or "clock standalone".

> 6) And maybe put all of the "open" programs between those bars instead of my name so it kind of "highlights" at a quick glance what is actually open?

Well AWN puts an icon on the dock for any running application, but if you want a windows-like taskbar as well, you can always add that to the gnome panel.

Google:
```
ubuntu gnome panel how to add item
```

As you can see there's a general trend to getting precise results from google.

If you're researching something for ubuntu, always start with 'ubuntu' as the search term (or 'kubuntu' or 'xubuntu' or 'edubuntu' or whatever flavor you use). 

Next, if it's specific to the gnome panel or to avant window navigator or to evolution calendar or nautilus file manager or whatever application/desktop element you're researching, make that your next search term.

Finally, add terms specific to the task you're trying to perform.

If you find you get a lot of results specific to older versions of Ubuntu, add "8.04" or "hardy" to the search terms.

Last tip: if you don't get the links you're looking for on your first search, don't just give up and go right to the forums. I often have to search four or five times with different sets of terms in order to find a result that solves my problem - but nine times out of ten I *can* find a result if I stick with it... Then if I've exhausted every term and combination of terms I can think of, I post a message for help on the forums or on the ubuntu launchpad (or both).

Hope this helps you get more comfortable with google and working through troubleshooting situations! :)

---

