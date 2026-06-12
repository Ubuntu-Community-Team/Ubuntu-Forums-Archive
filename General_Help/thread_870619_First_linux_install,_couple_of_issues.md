---
title: "First linux install, couple of issues"
date: 2008-07-26
forum: General Help
---

### Post by dontTaseMe on 2008-07-26
Hi, so I decided to give linux a whirl on my parents computer, played with it for a couple hours, and have a couple problems.

1.  One of my dad's only uses for the computer is to watch streaming-video from israel, so if he can't get this to work smoothly, its kind of a show stopper and its back to windows.  Right now it works, but its pretty messy, for instance this site:
[http://www.iba.org.il/mabat/index.asp?classto=1]("http://www.iba.org.il/mabat/index.asp?classto=1")
If you click play on the second(peach/white gradient) box on the left(javascript needed).  It pops up a window that is too big for the screen(and ends up covering everything), is there a way to make this window fit the screen or force it to open in a tab(I'd even be willing to write a small greasemonkey script or whatever if someone pointed me in the right direction).  Then the embedded video player is called CUPlayer, and it doesn't seem to support linux, however, it offers link to the stream which mplayer plays(its just a little difficult to get to since mplayer opens up in a new tab in the original window).  I just need a way to stop the javascript from creating an oversized window(which obscures the ubuntu toolbars).

2.  Somehow I seem to have lost the shutdown and restart options in the logout dialog, I would like to get them back.

That's it for now, I am new to installing/configuring linux, but have used it in school for Comp Sci labs.  Thanks for the help :)

---

### Post by AaronLS on 2008-07-26
On number 1, there is a way in Firefox to force new windows to instead open in a tab.  Tools->Options->Tabs->New pages should be opened in->a new tab.  At least that's where I find the option in Firefox 3.

It is not perfect though, as some sites still manage to create new windows.

---

### Post by dontTaseMe on 2008-07-26
> **AaronLS said:**
> On number 1, there is a way in Firefox to force new windows to instead open in a tab.  Tools->Options->Tabs->New pages should be opened in->a new tab.  At least that's where I find the option in Firefox 3.

It is not perfect though, as some sites still manage to create new windows.

Yea its set to do that, I believe(from a cursory look at the page source) the site uses JavaScript to force a pop-up.  I appreciate the help though!

---

### Post by Roasted on 2008-07-26
When I open that site and click on a video, it says I need the windows media player plugin to watch.

WTF, I thought I had that. Which one in particular is it referring to?

---

### Post by dontTaseMe on 2008-07-26
> **Roasted said:**
> When I open that site and click on a video, it says I need the windows media player plugin to watch.

WTF, I thought I had that. Which one in particular is it referring to?

I believe the site uses some sort of wrapper for windows media player(that appears to be pretty common for online news streams from israel) with its own firefox plugin(called CastUP), that is windows only(or atleast i couldn't get it to install on linux).  It does offer(or offered me atleast) a direct link to the windows media stream which I could play.

---

### Post by Roasted on 2008-07-26
ah yeah, I can play that. Good tip!

---

### Post by dontTaseMe on 2008-07-26
I was able to fix 1. by going to about:config and changing browser.link.open_newwindow.restriction from 2 to 0  .  It now forces the window into a new tab(yay).

Anybody have any ideas on 2?  I may have mucked about a bit in the terminal and authorizations, but I don't think i changed anything to cause it to remove the options from the logout dialog.

Right now the icons for hibernate, logout, lock screen, and switch user are there.  I don't even know how to power down with the terminal!  (shutdown, seemed to make ubuntu angry, i'll look that up i guess, but i really want those gui options back :( )

---

### Post by user_linux08 on 2008-07-29
> **dontTaseMe said:**
> I was able to fix 1. by going to about:config and changing browser.link.open_newwindow.restriction from 2 to 0  .  It now forces the window into a new tab(yay).

Anybody have any ideas on 2?  I may have mucked about a bit in the terminal and authorizations, but I don't think i changed anything to cause it to remove the options from the logout dialog.

Right now the icons for hibernate, logout, lock screen, and switch user are there.  I don't even know how to power down with the terminal!  (shutdown, seemed to make ubuntu angry, i'll look that up i guess, but i really want those gui options back :( )
Try watching iba with kaffeine. I have been using it for sometimes to watch Mabat. One drawback. It does not have the FF, and if you pause, and start it will take you back to the star point.

I am also trying to figure out how to use the mplayer to watch streaming media with castup. (They do have the plug in for firefox), but for some reason, FF does not allow it to be added as addon, and treats it as suspected unknown and unauthorized pluin.

---

