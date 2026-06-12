---
title: "Workplace switcher doesn't work with Compiz Fusion?"
date: 2008-09-09
forum: General Help
---

### Post by gldearman on 2008-09-09
Hi,

When I need to move an open window to another workspace, I usually just grab it in the workplace switcher (the mini-representations of workspaces that appear on the bottom panel), and drag it to the workspace I want it in.

When I enable Compiz Fusion, though, that no longer works.

Am I having an issue, or is that the way this is supposed to work?  Is there any way I can get that feature back without disabling visual effects?

I know that there are a whole host of other ways to move a window to another workspace (keyboard shortcuts, right-clicking and using the menu, etc.).  But I kinda liked that one.

Any help?

Thanks

---

### Post by Infinite Indefinite on 2008-09-09
Have you got the Compiz-Switch?  You can get it at:

[http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

Using the Compiz-Switch, then you can easily turn the Advanced Visual Effects on or off. When they're off, you can move open windows using the workspaces.  Then use the switch to turn the effects back on.

Alternatively, just drag the open window itself to the edge of the screen as I've done in the screenshot.

---

### Post by gldearman on 2008-09-09
So, it's not a bug I'm having, then?  That's the normal behavior?

Thanks for telling me about the Compiz-switch.  I had no idea.  For this particular use, that's probably too much trouble -- but I'm sure I can find another use for it.

I think probably my best substitute for dragging windows on the workspace switcher is probably zooming out with Expo and then dragging in that view.

In terms of dragging an open window to the edge of the screen as in your screenshot -- do I need to enable a special plugin to do that, or is it enabled by default? (I can't just check, since I'm not at home).

Thanks

---

### Post by tuxxy on 2008-09-09
Just drag the window to the screen edge so it starts to overlap, then it auto switch to the next face.

Or setup some key bindings so you can flip the screen without using the mouse for example ALT + left/right

---

### Post by Lizard_King on 2008-09-09
I have an even stranger problem with Workspace Switcher. When I right click on the workspace box and choose properties, I only have Colums: and rows: options. I would like to name my workspace boxes.

Thanks in advance.

---

### Post by Lizard_King on 2008-09-09
Testing, testing, is this thing on?

---

### Post by gldearman on 2008-09-09
> **Lizard_King said:**
> When I right click on the workspace box and choose properties, I only have Colums: and rows: options. I would like to name my workspace boxes.

Try disabling visual effects.  Then, right-click on workplace switcher, name your workspaces, and re-enable visual effects.  Do the names stick?

---

### Post by Lizard_King on 2008-09-09
I've decided to just reinstall Windows XP Pro, I've had nothing but trouble with Ubuntu and out of 40,000 members no one has any answers about how to fix any of the hundreds of problems I've encountered thus far, my second day using Ubuntu.

---

### Post by gldearman on 2008-09-09
> **Infinite Indefinite said:**
> 
Alternatively, just drag the open window itself to the edge of the screen as I've done in the screenshot.

Wow!  That works!  Cool!

But -- my original question:

With Compiz Fusion enabled, I cannot grab a window in workplace switcher and drag it to another workplace. Does anyone know if:

a)  This is the way it is supposed to work?
b)  I am having a fix-able problem (and, if so, how to fix it)?
c)  This is a bug with no known fix?

Can anyone answer this question?

Thanks, and thanks for all the help I've already gotten.  This forum has been an amazing source of help.

---

### Post by frogotronic on 2009-05-17
> **Lizard_King said:**
> I've decided to just reinstall Windows XP Pro, I've had nothing but trouble with Ubuntu and out of 40,000 members no one has any answers about how to fix any of the hundreds of problems I've encountered thus far, my second day using Ubuntu.


All you have to do is make sure that the VIEWPORT SWITCHER plugin is on and then configure its behaviour.  Not too difficult.

):P

---

### Post by lariosa42 on 2009-08-16
Bump!

---

### Post by chris1950 on 2009-08-17
I have the problem as Lizzard_King.

Bump:guitar:

---

### Post by Gorgapor on 2010-04-20
I have the same problem. This is definitely a bug.

Lucid Lynx beta 2, with the default install, using compiz (the default)

In the workspace switcher, mouse over a mini-window. A tooltip pops up saying "Click to start dragging <window name>".

Click and drag, nothing happens when you release the button.

Turn off compiz, and everything is fine.

---

### Post by deepclutch on 2010-06-02
^Same.I am experiencing the same problem.This is,as if Work Space Switcher is Freezed/locked.I tried ccsd Desktop options.but that neither helped.

EDIT:Resolved after Enabling Desktop Cub Options.

---

### Post by autonomy on 2010-06-08
I'm having the same problem. I have normal visual effects on. If I switch it off, then I can move an application from another workspace to this one by clicking its shape in the workspace switcher and dragging it to the present workspace. With normal visual effects on, I'm taken to the other workspace upon release of the mouse button. Enabling cube didn't help.

---

### Post by NTL2009 on 2010-06-11
> **autonomy said:**
> I'm having the same problem. I have normal visual effects on. If I switch it off, then I can move an application from another workspace to this one by clicking its shape in the workspace switcher and dragging it to the present workspace. 
...

Same here. I noticed this in 9.10 and it is still in 10.04. The Workspace Switcher works like a charm with System / Preferences / Appearance / Visual Effects: set to _NONE_. Any other setting breaks the drag feature (reported by many users).

Searching, searching...** it IS a bug** (and it does not look like it will be fixed soon):

[https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/150690](https://bugs.launchpad.net/ubuntu/+source/libwnck/+bug/150690)

I'm no coder, but it sounds like Compiz has a different take on what a 'workspace' is from how metacity defines them, so things just are not going to work the same. I'm pretty new to Linux/Ubuntu (and liking it), I don't know if it would help to add to the chorus there in launchpad to raise priority on this, or if that would distract from their efforts.

So this relates to my following related issue:

**Anyone have a work-around for Screen-Zooming with Visual Effects OFF?** - With Visual Effects set to NORMAL I was able to set the mouse to zoom the screen in/out  (SUPER-Key + Scroll). But if I set Visual Effects to NONE so I can use the drag feature between Workspaces, I lose the zoom capability.

Anyway to get Screen Zoom with Visual Effects set to NONE?

TIA - NTL2009

---

### Post by _nikolaos on 2010-06-12
> **gldearman said:**
> Try disabling visual effects.  Then, right-click on workplace switcher, name your workspaces, and re-enable visual effects.  Do the names stick?

They don't stick, when switching back to Compiz.

My own way to bypass, but NO way fix, the problem was the following, as Compiz effects are working:

[LIST]
[*]I have installed a Cairo-Dock at the bottom and kept the Panel at the top as well.
[*] I removed the Workspace Switcher from the Panel and put it on the Cairo-Dock.
[*] I renamed the Workspaces on the Cairo-Dock.
[/LIST]

In functionality terms, it's almost the same: I can see the Workspace names when mouse hovers over the squares. However, it's a subjective way to work, because I like Cairo-Dock.

And the strange problem is that, whenever I turn off the Compiz effects, and right-click on the windows' title, "Move to Another Workspace" option shows my modified names, but the same option retains original names "Workspace 1", "Workspace 2" and so on when I return to Compiz.

It seems like Compiz and metacity keep different lists of workspaces, and switching between them switches the lists as well. The obvious thing to do, provided that I am correct, is to change names on both lists in a corresponding way.

But, although it's frequently mentioned in this forum how to change the metacity's workspace names list (gconf-editor etc.), I can't find the similar way to change the Compiz list.

[http://ubuntuforums.org/showthread.php?t=825590](http://ubuntuforums.org/showthread.php?t=825590)

Any suggestions?

(P.S. if someone could tell me how the names can stick on the squares of the workspace-switcher as labels?)

---

