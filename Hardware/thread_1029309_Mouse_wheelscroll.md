---
title: "Mouse wheel/scroll"
date: 2009-01-03
forum: Hardware
---

### Post by Lupinus on 2009-01-03
Hi All,

I just installed Ubuntu 8.10 and love it thus far.  However, I've run into a bit of a snag trying to configure, of all things, my mouse.

Mouse works, the wheel works when I roll it, but when I click the wheel I don't get the same feature as I did on XP (not sure the right term, click you get the four arrows, move pointer, screen scrolls automatically)

I've tried google and a search on the forum but not seeing anything.

Is there a way on 8.10 to make that happen?  Also is there a way to get new pointers?  

I've gone into System>Preference>Mouse and only have two tabs General and Accessibility, neither of which seem to cover this.

Sorry if this has been asked already

---

### Post by Rohan Kapoor on 2009-01-03
> **Lupinus said:**
> Hi All,

I just installed Ubuntu 8.10 and love it thus far.  However, I've run into a bit of a snag trying to configure, of all things, my mouse.

Mouse works, the wheel works when I roll it, but when I click the wheel I don't get the same feature as I did on XP (not sure the right term, click you get the four arrows, move pointer, screen scrolls automatically)

I've tried google and a search on the forum but not seeing anything.

Is there a way on 8.10 to make that happen?  Also is there a way to get new pointers?  

I've gone into System>Preference>Mouse and only have two tabs General and Accessibility, neither of which seem to cover this.

Sorry if this has been asked already
You should search [www.gnome-look.org](www.gnome-look.org) for pointers. They can be installed by going to system->preferences->appearance. About your mouse issue, I'm not sure if that feature is supported in Ubuntu, I don't believe it is. Personally, I'm surprised that you want it because most people hate it.

---

### Post by Lupinus on 2009-01-03
Thanks Darth.  I mostly use it when scanning forums but can live without it.

Thanks for the tip on the pointers

---

### Post by Rohan Kapoor on 2009-01-03
Your welcome!

---

### Post by matt.cohenprice on 2009-01-05
I'm having the same issue. My Kensington Pilot Mouse works and scrolls, but autoscroll does not, nor can I find any way to assign a task to clicking the scrollwheel.

I tried binding different Compiz actions to "button 3" and "4" and on up, but the scroll click seems to not be associated with any of them.

Any ideas?

---

### Post by Rohan Kapoor on 2009-01-05
> **matt.cohenprice said:**
> I'm having the same issue. My Kensington Pilot Mouse works and scrolls, but autoscroll does not, nor can I find any way to assign a task to clicking the scrollwheel.

I tried binding different Compiz actions to "button 3" and "4" and on up, but the scroll click seems to not be associated with any of them.

Any ideas?

I would like to repeat what I said earlier:

This mouse wheel click is not supported in ubuntu and as far as I can tell it will not be implemented anytime soon.

---

### Post by innactpro on 2009-03-25
> **darth-vader said:**
> I would like to repeat what I said earlier:

This mouse wheel click is not supported in ubuntu and as far as I can tell it will not be implemented anytime soon.

It works for me. What I haven't found yet is how to control the amount of scroll the wheel controls. For some of my apps it scrolls way too much.

---

### Post by mcduck on 2009-03-25
> **matt.cohenprice said:**
> I'm having the same issue. My Kensington Pilot Mouse works and scrolls, but autoscroll does not, nor can I find any way to assign a task to clicking the scrollwheel.

I tried binding different Compiz actions to "button 3" and "4" and on up, but the scroll click seems to not be associated with any of them.

Any ideas?

The wheel button (or middle mouse button if you have a 3-button mouse without a wheel) is "button 2".

There is no system-wide support for autoscrolling, but for example Firefox still supports it, if you just enable it in Firefox settings:

Enter "about:config" as the address, then use "scroll" as the filter and find the key called "general.autoScroll". Right-click that and select "Toggle" to set the key's value to "true". Now you have autoscrolling in Firefox.

---

### Post by Rohan Kapoor on 2009-03-25
> **mcduck said:**
> The wheel button (or middle mouse button if you have a 3-button mouse without a wheel) is "button 2".

There is no system-wide support for autoscrolling, but for example Firefox still supports it, if you just enable it in Firefox settings:

Enter "about:config" as the address, then use "scroll" as the filter and find the key called "general.autoScroll". Right-click that and select "Toggle" to set the key's value to "true". Now you have autoscrolling in Firefox.
I stand corrected then :D!

---

### Post by mcduck on 2009-03-26
> **darth-vader said:**
> I stand corrected then :D!

Yeah, actually the middle  ouse button is pretty much a Unix/Linux thing, we had it long before Windows.. :D

In the old days Mac had one mouse button, Windows had two and Unix had three.

The standard copy/paste-method in Unix/Linux depends on having a middle mouse button (select what you want to copy, and middle-click to paste it). You can also resize windows from any point in the window with Alt+Middle button. And many window managers use it for rather important functions, for example to switch between windows and access your minimized windows in Openbox you'd middle-click on desktop to open a popup that lists your desktops and windows (Openbox desn't have any panels).

Probably the reason why auto-scrolling with middle mouse button isn't enabled by default is that it's traditionally used for so many other purposes.

(Bit of a same thing with the "windows-button", originally called "Super" or "Meta", which appeared first on Unix machines and was marked with a diamond, definitely not Windows logo :D)

---

### Post by NoBugs! on 2009-03-31
If you go to Firefox preferences, advanced, there is a check to enable Autoscrolling (middle click scroll), and enable smooth scrolling (for middle-scroll).

---

### Post by Rohan Kapoor on 2009-03-31
> **NoBugs! said:**
> If you go to Firefox preferences, advanced, there is a check to enable Autoscrolling (middle click scroll), and enable smooth scrolling (for middle-scroll).
I feel dumb, How did I completely miss that?

---

