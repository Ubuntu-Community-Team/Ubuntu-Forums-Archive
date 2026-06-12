---
title: "[SOLVED] Firefox 3 - No &amp;quot;Window&amp;quot;"
date: 2008-10-25
forum: General Help
---

### Post by -kg- on 2008-10-25
I have searched the forums until I'm cross-eyed, and cannot find a reference to this, so I will post.  I'm relatively new to Linux (though I almost feel as if I'm not, considering the amount of research and work I've done) and I've been into PCs and Microsoft since dinosaurs roamed the earth (pre-Windoze) so bear with me if I still tend to think in M$ terms.

Lately (and I don't know when this started to happen) when I launch the Firefox browser, it opens full screen, similar to launching applications from DOS.  There is no "Window Bar" at the top of the browser...I have no access to the Minimize, Maximize, or Close buttons, no access to the Launch Bar at the top (I'm using Gnome) and no access to the "Task Bar" at the bottom.  The only way I can access my desktop is to select "Quit" from the File Menu.

I have discovered that I *can* get access to the Launch and Task bars by opening a sub menu of Firefox (such as Addons under the Tools Menu...it takes opening the menu and clicking on it twice to get it to come up).  I then get access to those bars.

If I right click on the icon for Firefox, I have access to the Minimize, Maximize, etc. commands.  I can minimize the window, and I can un-Maximize it.  However, when I un-Maximize it, I cannot resize it in any way.

This really confuses me.  I will often launch a browser when looking for information, then minimize the browser window to do another task.  I can't seem to do that anymore, not without jumping through hoops by launching a sub window so that I can get access to everything else without completely closing down the browser.

I'm going to try unloading and reloading the browser and see if that helps, but from what I've read in my research, that might not help, considering that the Firefox configuration files are not changed.  I'll do it in the hopes that something screwed up in some installation somewhere, and if it doesn't work, I'll be back looking for suggestions.

---

### Post by -kg- on 2008-10-25
Stranger and Stranger.

I completely uninstalled and reinstalled Firefox.  I left out all the plugins and helpers I had installed before, thinking I might have installed conflicting plugins, and just now pulling up the Addons menu, I now have significantly less, though not none.  Upon uninstall I even rebooted, just for S & G's.

Anyway, I launched Firefox and it launched like it used to, with the "window" bar at the top with the Minimize/Maximize, etc., bar at the top of the window, but when I closed it and relaunched it, back it was to full screen with no bar, no Launch bar/Task bar access...i.e., back to the way it was.

It did keep all settings, bookmarks, etc., through the un/reinstall process.  Could it be something in the configuration files?  I've gone through all the Preference settings and all and can find nothing that affected the window in the slightest.

Any ideas?

Thanks in advance for the help.

---

### Post by drs305 on 2008-10-25
I use compiz. I lose the top of the firefox window if my compiz settings get messed up. In Intrepid, it's System, Preferences, CompizConfig Settings Manager. I have enabled Windows Decorations. On the Windows Decoration page, if the 'Decoration Windows' is set to 'any' I get the top Firefox bar. If it is blank, I lose the top bar. If it is *already* set to 'any', you might try disabling 'Windows Decorations' to see if that corrects things.

Of course, you may have other compiz settings that are causing the problem. You could try to disable compiz entirely, using "metacity --replace" to see if your display is restored.

---

### Post by -kg- on 2008-10-26
Above, I stated that I was a relative Linux newbie, but one can also infer that I am not a newbie to computers.  I found a band aid type fix to my problem.  I shouldn't have to do it, but it seems to work.

I once again rebooted and launched Firefox and gained access to the window controls at the top of the Firefox Window.  This time I tried an experiment.

While I had access to those controls I unmaximized the window and resized it a bit.  This time when I closed and relaunched it, it relaunched unmaximized and with the controls visible.  I closed and relaunched several times with the same result.

I then resized the window to almost full screen size, then closed and relaunched to make sure.  I still have the controls and access to the Launch and Task bars.  So I supposed I'll just have to leave the browser window unmaximized but resized to full screen size.

I'm still interested in figuring out what is going on, though.  I shouldn't have to do it that way, and I'm an old hacker from way back...if my system doesn't behave as I think it should, it makes me crazy until I find out what the problem is.  It's just that I'm unused to Linux conventions as yet.

Still looking for ideas.

---

### Post by -kg- on 2008-10-26
> **drs305 said:**
> I use compiz. I lose the top of the firefox window if my compiz settings get messed up. In Intrepid, it's System, Preferences, CompizConfig Settings Manager. I have enabled Windows Decorations. On the Windows Decoration page, if the 'Decoration Windows' is set to 'any' I get the top Firefox bar. If it is blank, I lose the top bar. If it is *already* set to 'any', you might try disabling 'Windows Decorations' to see if that corrects things.

Of course, you may have other compiz settings that are causing the problem. You could try to disable compiz entirely, using "metacity --replace" to see if your display is restored.

Thanks for the quick reply.

I was just about to post that I didn't have compiz installed (I looked in Add/Remove and didn't find anything compiz related that was checked, but before I did that I decided to check Synaptics, and there it all was.

I am confused, though.  I seem to have all the relevant packages installed, including this one:

[I]This meta-package provides the components necessary for running compiz. It
provides the compiz core, a set of standard plugins, a window decorator using
the Gtk toolkit and the files necessary to integrate compiz with the GNOME
desktop environment.[/I] 

But I'll be darned if I can find the configuration utility or the windows decorator anywhere in the menus (System/Preferences or /Administration.  I even tried under Applications).  I'm using 8.04, if that's any help to anyone.

Like I said, I've got it working (kinda), but it still drives me crazy for my systems to work "kinda." :evil:

Now I'm going to have to research and find out how to access the settings for compiz, since they're not where they are on your system, not because it might be what's causing this problem, but because it's installed but the controls aren't where I can find them. #-o

Thanks for the heads up, though.  I'll get this system down yet.  I'm surely disgusted with Windows and Micro$oft these days and I'm determined to make the switch as totally as I possibly can.

(Still gotta keep it for now, though...I like Flight Simulator X too much!) :)

---

### Post by drs305 on 2008-10-26
You might get into compiz with the following:
```
ccsm
```

---

### Post by JEJ514 on 2008-10-28
I have the same problem with FF 3 in the Release Candidate of 8.10.  I found some bug reports, though, so I'm assuming there will be a fix coming by Thursday - D-day for 8.10.

If not, I'll certainly be interested to see what solves this problem.

---

### Post by lepork on 2008-11-03
I have the same problem...Maybe I click or I did something wrong??? If somebody know how to fix this will be great..thank you so much....

---

### Post by niccholaspage on 2008-11-03
This is simple. When you start Firefox, Press F11 twice. Now resize the window and maximize it again. Close and Open. It should be fixed.

---

### Post by lepork on 2008-11-03
> **niccholaspage said:**
> This is simple. When you start Firefox, Press F11 twice. Now resize the window and maximize it again. Close and Open. It should be fixed.

niccholaspage, thank you so much...It worked

---

### Post by -kg- on 2008-11-06
Yes indeed, it most certainly did!

Thank you very much nicholaspage!  I can now mark this as "Solved."

Just a side question:  How was this brought about?  Was it something that I (we) did, or just a little glitch?

---

### Post by niccholaspage on 2008-11-08
It is a little glitch. I guess Compiz has some weird code.

---

### Post by Riqz on 2008-11-24
> **niccholaspage said:**
> This is simple. When you start Firefox, Press F11 twice. Now resize the window and maximize it again. Close and Open. It should be fixed.

Oh wow.... simple and yet so perfect... Thanks mate... You-ve earned a thanks click.

---

### Post by incubii on 2008-11-29
I found while doing the F11 trick does work, on some machines i have seen this happen way too much as is such not an acceptable solution.

Don't fret though! I did find a solution. You need to fire up Compiz Settings Manager (need to install it), and under Utility -> Workarounds, disable Legacy Fullscreen Support.

This has fixed it up for every machine i have see the issue with.

---

### Post by -kg- on 2008-12-13
Thanks incubii!

I was having trouble with occasional recurrence of the problem, necessitating repeat of the F-11 trick, but once I used your procedure the problem cleared up and hasn't happened since.

---

