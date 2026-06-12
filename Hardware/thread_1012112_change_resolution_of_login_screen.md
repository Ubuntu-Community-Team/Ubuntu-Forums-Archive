---
title: "change resolution of login screen?"
date: 2008-12-15
forum: Hardware
---

### Post by bsmith1051 on 2008-12-15
I'm running Ubuntu 8.10 and the ATI proprietary driver provided by Hardware Drivers (I have not manually installed a newer driver).  My CRT monitor reports a max resolution of 1400 or something but I only run it at 1024x768.  I have my desktop resolution set to that but the graphical login screen always resets to the max-possible 1400.

All I've tried so far was to edit my splash.conf file (and rebuild the boot image) but it didn't fix it.

Where can I tweak this setting?  And shouldn't the login resolution 'follow suit' with the desktop resolution?  Thank you for any help!

---

### Post by Cadeyrn on 2008-12-16
DUDE!!! I have the same problem!

Except, well, mine keeps switching the res to 320xsomething. XD

...And Screen Resolution says it can't detect my monitor. I know it could before.

And this problem is extremely annoying. A recent Ubuntu update has caused all ATI users to NEED the Restricted driver for things like All-in-oneSidebar and workspaces to work decently. But then the driver messes up the system in some odd way and we have to uninstall it through xfix. It's an endless cycle!

---

### Post by Cadeyrn on 2008-12-16
BUMP.

I'm impatient.

---

### Post by bsmith1051 on 2008-12-18
Have you tried editing your xorg.conf file?  It's not really used anymore but it may still have some influence.
```
> gksu gedit /etc/X11/xorg.conf
```
Edit the "Screen" section and add,
```
Option          "PreferredMode" "1280x1024"
```

---

### Post by Cadeyrn on 2008-12-18
Well, in a different topic I already discovered everything is going wrong because ATI graphics cards cannot handle updating anything in Ubuntu through the prorgam or console.

I have tried editing my xorg file, which didn't work, and unless xfix is blatantly lying to me, the file is totally still used completely, and this problem comes because the ATI driver edits it in a way that makes my monitor undetectable.

---

### Post by Cadeyrn on 2008-12-18
Well, in a different topic I already discovered everything is going wrong because ATI graphics cards cannot handle updating anything in Ubuntu through the prorgam or console.

I have tried editing my xorg file, which didn't work, and unless xfix is blatantly lying to me, the file is totally still used completely, and this problem comes because the ATI driver edits it in a way that makes my monitor undetectable.

EDIT: Whoops double post! Also, it was already decided I'm gonna reinstall Ubuntu. So my problem is solved...

---

### Post by bsmith1051 on 2008-12-19
editing 'xorg.conf' did not work for me

---

### Post by bsmith1051 on 2008-12-20
Still no solution but I did manage to accomplish one weird thing...

Simply adding the "PreferredMode" setting to xorg.conf did nothing.  Instead I found this discussion,
[http://www.linuxquestions.org/questions/debian-26/does-gdm-and-gnome-have-different-resolution-settings-639460/](http://www.linuxquestions.org/questions/debian-26/does-gdm-and-gnome-have-different-resolution-settings-639460/)
and edited my xorg.conf to look like this:
```
Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	24
	SubSection "Display"
		Depth	24
	        Modes	"1024x768" "1280x1024" "800x600" "640x480"
	EndSubSection
EndSection
```
Basically, I added the 4 lines re SubSection and also intentionally put the 1024x768 entry in front of the other higher resolution.  This had the effect of booting-up the GDM login screen in 1024x768 resolution... but it was only a 'window' on the same original background resolution?!  In other words the login box ended-up in the lower-right corner of the screen and the Options button (which normally goes in the bottom-left corner) was down out of sight and inaccessible.

I think what we need is to set the default Gnome resolution rather than the default video-card resolution.  I found this discussion about such a setting,
[http://kbase.redhat.com/faq/docs/DOC-2239](http://kbase.redhat.com/faq/docs/DOC-2239)
and I'm able to load 'gconf-editor' to edit these Gnome settings.  But there's no such entry, /desktop/gnome/screen/default/0/resolution, as mentioned in the discussion?

---

### Post by bsmith1051 on 2009-01-02
Fixed it!  The problem is that X (not Gnome?) creates a Virtual Desktop resolution and this is what Gnome's login screen always uses.  By default it is set to the highest available resolution which, in my case, was an unusable one.

The solution is to manually specify -- in 'xorg.conf' -- the available resolutions and/or the Virtual Desktop resolution.  
[LIST]
[*]specify your desired resolution as the max available
[*]use the 'Virtual' setting to specify a different (lower than max) resolution to use for the Virtual Desktop
[/LIST]
My previous attempt at specifying the resolutions had failed because I included both my standard res (1024) and a higher max-res (1280) -- so the Virtual Desktop (which I didn't know about) was higher than my desired.

---

### Post by ktiniatros on 2009-01-27
> **bsmith1051 said:**
> .

The solution is to manually specify -- in 'xorg.conf' -- the available resolutions and/or the Virtual Desktop resolution.  
[LIST]
[*]specify your desired resolution as the max available
[*]use the 'Virtual' setting to specify a different (lower than max) resolution to use for the Virtual Desktop
[/LIST]


can u post plz the xorg.conf to see how can i do these 2 steps??
im a noobuntu yet !

---

### Post by Post Monkeh on 2009-01-27
try downloading startupmanager through synaptics.

worked for me.

---

### Post by bsmith1051 on 2009-01-29
All the steps have already been posted, individually, but I'll try to summarize them here:

1. open your configuration file in the text editor (and as 'root' otherwise you don't have permissions),
```
> gksudo gedit /etc/X11/xorg.conf
```
2. The default/base configuration looks something like this,
 (note how most sections are empty since the goal is to auto-detect everything; the only detail specified is the use of the ATI 'fglrx' driver)
```
Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	DefaultDepth     24
EndSection
```
3. Edit the file so that the "Screen" section explicitly specifies which resolutions to allow (instead of using auto-detect).  The simplest solution to setting a particular login resolution is to specify that res as the highest available (since the login defaults to the highest available)
```
Section "Files"
EndSection

Section "Module"
	Load  "glx"
EndSection

Section "Device"
	Identifier  "Default Device"
	Driver      "fglrx"
EndSection

Section "Screen"
	Identifier "Default Screen"
	SubSection "Display"
		Depth	24
	        Modes	"1024x768" "1280x1024" "800x600" "640x480"
	EndSubSection

	DefaultDepth     24
EndSection
```

---

