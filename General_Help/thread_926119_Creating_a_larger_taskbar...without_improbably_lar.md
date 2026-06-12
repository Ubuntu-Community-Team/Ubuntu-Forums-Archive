---
title: "Creating a larger taskbar...without improbably large icons"
date: 2008-09-21
forum: General Help
---

### Post by Pontifex on 2008-09-21
[Semi-experience user converting from Windows]

I'd like to increase the size of my taskbar (vertically) to increase the amount of windows I can have an overview of while working.

This is pretty easy in Windows, click and drag to increase my taskbar real estate.

I knew it wouldn't be as simple or intuitive in Linux, but i did find a rather easy solution for increasing the size of the taskbar:

Right Click on Taskbar &#8594; Properties &#8594; Size = 75 Pixels

Which lines up quite nicely with three rows of taskbar window icons.  Though really it should be something other than pixels in the default config dialog, perhaps "rows" would be a better measurement?

My problem turns out to be that all the icons I have on the taskbar are **enormous** (see screenshot).  My networking icon, time and main menu are all unaffected (apart from some formatting changes; E.g. my time is centered and multi-lined where it was a simple line of text), but my Tomboy notes, sound and update reminder are gigantic.

_How do I fix this?  How do I return them to their original size?_

I would like it very much if the answer were something other than editing hidden configuration files or going to the command line, I'm shooting for simplicity with setting up.

---

### Post by dmartin on 2008-09-21
There is one way I can think of, though I admit it isn't very pretty.  You can create many docks, where you go to each one's properties and uncheck Expand.  I just tried it myself and it does work, but it isn't clean at all.  

Otherwise, you might want to look at KDE 4.1.  It's applet design is that any applet can either be attached a dock or on the background desktop.  It's quite nifty.  I ran it for two weeks as a test, and I still cannot stand most of the KDE apps.  If the QT GTK theme worked well, that would be no big deal, but it doesn't.  And so I had to go back to Gnome.  But, that's a whole other topic I suppose.

Also there's XFCE (Xubuntu), which my memory is fuzzy on, but might give you what you want. 

I know the *box DEs can be configured how you want, but if you don't like config files, the *box desktops aren't for you.

---

### Post by Pontifex on 2008-09-21
> 
There is one way I can think of, though I admit it isn't very pretty. You can create many docks, where you go to each one's properties and uncheck Expand. I just tried it myself and it does work, but it isn't clean at all.


You're right, that makes me wince a little inside.  Good creative suggestion though. =)

> 
Otherwise, you might want to look at KDE 4.1...


> 
Also there's XFCE (Xubuntu)...


I'd rather not install a new window manager at this stage.  I've [got]("http://lifehacker.com/5049947/tasque-manages-to+dos-with-remember-the-milk-integration") [a]("http://lifehacker.com/software/featured-linux-download/supercharge-your-right+click-menu-with-nautilus-scripts-269043.php") [few]("http://lifehacker.com/367714/run-windows-apps-seamlessly-inside-linux") [things]("http://lifehacker.com/5048628/make-your-linux-desktop-more-productive") I want to install, setup and get used to, before I go switching around anything big like the window manager.

I'll keep it in mind though, thanks.

> 
I know the *box DEs can be configured how you want, but if you don't like config files, the *box desktops aren't for you.


I'm _okay_ with "config files", I just don't want to mess with them if I don't have to.

There's a couple of reasons I'm going through this process:
[LIST]
[*]I **really** like virtual desktops.
[/LIST]
Linux and MacOSX are the best at "true" virtual desktops.  The Windows solutions I've tried - for lack of a better word - "suck ***", so I need a solution to get work done that use the programs I'm passably familiar with and are in my price range.  Since I already use OSS almost exclusively on my Windows install and I can hardly pay rent...

Here we are.
[LIST]
[*]I'm part a LUG and we're trying to figure out how to make a usable Linux desktop for our "converts".
[/LIST]
This is quite a challenge as most people know.  I'm doing it the "config file"-less way because that's the optimum path to teaching new people how to use their new system.  To try to help them not pitch it in a bin when things get rough.
[LIST]
[*]I want to get up and running as quickly as possible.
[/LIST]
I have tasks and projects I want to get running.  I simply have too many things to keep track of and that I want to pursue, to do it any other way besides working with virtual desktops in Linux.

So I'm spending some time trying to get things working in Linux and the way to do that the quickest, from my previous experience setting up Linux, Is to use the graphical tools first;  Then try to the guess-and-check-method of: browsing the forums, looking and asking for help and finding that single answer that worked out of the 20 or so that I found that didn't.  Usually the later method involves using the command line and editing configuration files.

Using the command line and editing configuration files can also damage the system - which the GUI tools rarely do (at least those that come bundled with the distribution) - making it unusable and thus setting me back and unable to work.

Don't get me wrong I am up and running and doing the work I want and need to do, it's just the little things that keep kicking me in the shins.

--Pontifex

---

### Post by Pontifex on 2008-09-21
It strikes me that the way I'm trying to go about this is non-standard; E.g. adjusting the taskbar size to include more windows on it.  Otherwise my problem would have been addressed long before now.

I'm sure I have more Windows open per desktop than pretty much anyone not developing a large-ish piece of software.  So I need some solution that would enable me to keep track of a large number of windows organized in my various work spaces.

I've read about some dock-like applications that may be the new solutions to this problem; Namely: [Avant Window Navigator]("http://en.wikipedia.org/wiki/Avant_Window_Navigator") and [Cairo-Dock]("https://help.ubuntu.com/community/CairoDock").

**_Question:_**

Would either [Avant Window Navigator]("http://en.wikipedia.org/wiki/Avant_Window_Navigator") and [Cairo-Dock]("https://help.ubuntu.com/community/CairoDock") be a better solution to my issue of managing open windows than adjusting my taskbar?

---

### Post by fabounet on 2008-09-22
Try with Cairo-Dock, you can group windows of a same appli in a sub-dock, to avoid having a huge amount of icons in your taskbar.
you can also show the current desktop's windows only, which might  be useful here.

---

### Post by northern lights on 2008-09-22
While resizing your initial panel will inevitably return larger icons, you can add an entirely new, separate panel.

Right-click on your current panel and select "New Panel". Left-click-hold it and drag it to the position of preference. With one pr more windows open,right-click on one of the buttons representing a windows and select "Remove from panel". Now right-click the new extra panel and select "Add to panel" in the resulting menu, select "Window List".

---

### Post by Pontifex on 2008-09-22
> Try with Cairo-Dock, you can group windows of a same appli in a sub-dock, to avoid having a huge amount of icons in your taskbar.
you can also show the current desktop's windows only, which might be useful here.

I generally like having an overview of all the windows I have open at once, see the screenshot I attached.  It's an example of one of my work space for a project under active development.

I tried to use the grouping mechanism that the gnome comes with, but I kept having to click around to look for things that I wanted to use.

From looking at the [Ubuntu page for cairo dock]("https://help.ubuntu.com/community/CairoDock"), it seems to be a good way to launch applications (sort of a fancy quick launch bar ala Windows); But you're saying it can be used to group open programs too?

I wish there an easier / more attractive way to provide a concise overview of all my open windows rather than using the taskbar. =/

---

### Post by Pontifex on 2008-09-22
> While resizing your initial panel will inevitably return larger icons, you can add an entirely new, separate panel...

This doesn't work quite the way you intend, I think.  See attached screenshot.

As you can see the new panel with the new Window List, lists the existing windows I have open; Rather than providing a new container for holding window icons, as I think you intended.

In short, I end up with two window lists; One like I want and another that is redundant, listing every open window again.

--Pontifex

---

### Post by Pontifex on 2008-09-23
I did however run into something interesting while experimenting with the panels, as above.  The window selector.  Looks interesting, but as you can see from the screen shot, it lists all of my desktops at once. =(

It would be a nice overview of my currently open windows and I could use it in conjunction with a dock for added functionality and decreased window clutter.

Is there a better solution out there for this type of functionality that doesn't list every desktop I have and provides some more customizable settings and aesthetic appeal?

--Pontifex

---

