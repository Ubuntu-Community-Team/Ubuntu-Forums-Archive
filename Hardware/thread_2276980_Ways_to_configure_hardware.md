---
title: "Ways to configure hardware"
date: 2015-05-06
forum: Hardware
---

### Post by Sethox on 2015-05-06
Hello !

So I've been using ubuntu distro for quite some time now and I noticed that it's kind of dependant on the search engine for applications, that's kind of alright but the main issue I have with how this is presented makes things so cluttered.

Example:
[LIST]
[*]AMD Catalyst configure application, is a separate application that isn't in the "All Settings" application/window (I don't know if Nvidia's graphic cards configure application/window shows there)
[*]Mouse configuration is lacking in settings and alternative ways to use your mouse (no acceleration, configure DPI, if more buttons found in the mouse you should be able to reconfigure them, etc)
[*]Compiz, why is this a hidden setting application? As a new user you don't really get to find out that this application exist, shouldn't this great toolbox be in the 'All settings' Application/window?
[/LIST]

My point being, we should be able to see all available setting possible (with your hardware) what you can do and put on display on the settings (in it's own category) and have less cluttered configures/applications scattered everywhere for you to search for.
If I search for mouse configurations, I want all the settings available (counterpart of the terminal way to set things up).

So my question is, why so little settings in the GUI:s?

---

### Post by dino99 on 2015-05-06
What you wish is what was the default some years back. But the devs were tired by users trying/tweaking a bit too much the default settings (which are chosen for a smooth experience) and then were complaining about broken things and reporting false issues. So now what is hidden is for a real reason. System Settings is the main place where to find the most current needs. Dconf (dconf-editor) is also available to change the default settings; but users need to understand what they are doing.

---

