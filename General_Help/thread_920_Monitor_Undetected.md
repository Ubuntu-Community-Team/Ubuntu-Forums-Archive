---
title: "Monitor Undetected"
date: 2004-10-16
forum: General Help
---

### Post by bartleby on 2004-10-16
Hi

I've just been installing Ubuntu for the second time--on my wife's work pc this time. Everything seems fine apart from the monitor. In the screen resolution tool I can only see 800x600 and 640x480 so I can't select the 1024x768 that my monitor can handle (and indeed has been handling in Xandros for the last six months). I suspect this is because Ubuntu has identified the monitor as a "generic monitor" rather than an LCD flat screen. How do I change the monitor type?

I'm happy to use the command line but I don't know the commands very well--in KDE, which is what I've always used up to now, there seems to be a graphical tool for everything.

Ubuntu is fantastic overall though; after a couple of years of experimenting with different distros I think this one has cracked it. It's fast (even on this ancient 400mhz machine that I rescued from a skip), very stylish, and apt-get makes it really easy to customize. Very well done indeed.

Cheers

---

### Post by triad169 on 2004-10-16
Open a terminal and type this:

```

sudo cp /etc/X11/XF86Config-4 /etc/X11/XF86Config-4.original
sudo gedit /etc/X11/XF86Config-4

```

This backs up your config file and will open Config file for editing.  Scroll down to *Section "Screen"*

You want to change all the lines that look like this:

> Modes		"800x600" "640x480"

to

> Modes		"1024x768" "800x600" "640x480"

also you might want to change the Section "Monitor" to match the specifications of your monitor.  specifially the HorizSync and vertRefresh.  Make sure you use the specifications for your monitor or bad things can happen.  Also dont change Identifier or else you have to adjust your config file to point to this new identifier.  I have attached an example from my config file as reference.:

> 
Section "Monitor"
	Identifier	"KDS XF-7p"
	HorizSync	30-72
	VertRefresh	50-160
	Option		"DPMS"
EndSection


Once you have edited the XF86Config-4 file just save your changes.  log out of Gnome.  Hit *ctrl+alt+backspace* this will restart the XServer with your new setting and it should default to 1024x768 mode.  If for some reason something strange happens it wont start up.  It will plop you out to the Command Prompt and Server might ask you to run a diagnostic.  just say no then Just log with your username and password and type:
```

sudo cp /etc/X11/XF86Config-4.original /etc/X11/XF86Config-4

```
This will restore you Backup Xfree config file. Then restart computer by hitting *ctrl+alt+del*  

Triad

---

### Post by bartleby on 2004-10-16
Thanks Triad

I don't have time to try it right now but that file does look promising, though it includes 1024x768 along with the other numbers. I had the idea of looking at the same file on my other install and that has only 1024x768 and nothing else. I'll give that a go.

Cheers--learning gradually.

---

### Post by bartleby on 2004-10-17
Ok, it's fixed. I worked out that in the XF86Config-4 file the default "mode" was 24 and it should have been 16--presumably because of the ancient video card. I still needed to set the resolution in the gui tool in Gnome though. I also discovered that

a: having a Mepis live disk handy allows you to fix stuff when you break it, and

b: if you type sudo dexconf into a root terminal you get a brand spanking new XF86Config-4 file (I did make a backup but this was neater).

So thanks again for the help--you pointed me in the right direction.

Cheers

---

