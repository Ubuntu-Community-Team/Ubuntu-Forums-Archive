---
title: "Transparent konsole in KDE 4.1"
date: 2008-07-30
forum: General Help
---

### Post by chandra on 2008-07-30
I use Kubuntu 8.04.

I have not been able to get a transparent konsole in KDE 4.1. The transparency slider under Settings -> Appearance simply did not show up.

So, I tried to create a New setting and got a warning message:

"The background transparency setting will not be used because your desktop does not appear to support transparent windows."

FYI, I **am** using a transparent konsole 1.6.6 in KDE 3.5.9.

I do not use compiz but have used the compiz-check script ```
wget http://blogage.de/files/4359/download -O compiz-check
``` to confirm that the checks are all OK.

Can someone please throw light on this and suggest a workaround.

Thank you.

---

### Post by robertknight on 2008-07-30
Hi chandra,

Transparency in Konsole under Kubuntu 8.04 (KDE 4.0) requires that:

1. You have desktop effects support (using Compiz, or KWin with desktop effects enabled)
2. You start konsole with the --enable-transparency argument

In KDE 4.1, transparency is enabled by default if desktop effects are available, so passing --enable-transparency is not necessary.  

The 'fake transparency' in KDE 3 which showed the desktop background under the window but not windows underneath Konsole is no longer supported.

---

### Post by chandra on 2008-07-30
Thanks, robertknight.

I have installed compiz but did not know how to activate it. I finally tried typing
```
compiz
``` at the konsole and it got activated but not without some setbacks.

I am running KDE 3.5.9 and have multiple desktops (> 2). Unfortunately, they have all been squashed by compiz activation, and I only have two desktops now.

Finally, I needed to set select Settings->Appearance->New to and select transparency (no warnings this time, thanks to you) to get a transparent konsole-kde4.

I now have three questions:

1. Have I messed up my system by typing compiz at the konsole? If so can you tell me how to undo it and do it the correct way, please?

2. How do I get my multiple desktops back in the Panel in KDE 3.5.9 (which I am running as standard while I test out KDE 4.1)?

3. Why does transparency already not get activated for the standard background/foreground settings for konsole-kde4? I needed to roll my own and call it something for that to happen. Why did the slider not show up simply under settings?

Many thanks.

---

### Post by chandra on 2008-07-30
I have just read this writeup:

[http://www.300penguins.org/?p=9](http://www.300penguins.org/?p=9)

and think that I might be better off using KWin. So, the more pertinent question is "How do I activate desktop effects with KWin?"

Thanks.

---

### Post by chandra on 2008-07-31
I realize that window effects are natively supported in KDE 4.1 and that Compiz is not needed.

So, I logged into a KDE 4.1 session. Under 

System Settings -> Desktop -> Desktop Effects, I checked the Enable Desktop Effects box.

I then tried to invoke a konsole with transparent background but again was told it was not possible. So, now my question is simply:

How do I invoke KWin effects in a KDE 4.1 session to allow a transparent konsole?

I do not need transparency in KDE 3.5.9 as I am quite content with the "fake" version. But how do I get this behaviour for konsole in KDE 4.1 without Compiz?

Thank you.

---

### Post by chandra on 2008-08-01
My video card is an nVidia Corporation NV17 [GeForce4 MX 440] (rev a3) running on nvidia-glx. I wonder if that is the cause of the problems as suggested at:

[http://liquidat.wordpress.com/2008/07/22/nvidia-on-kde-41-a-greedy-problem/](http://liquidat.wordpress.com/2008/07/22/nvidia-on-kde-41-a-greedy-problem/)

Is anyone else having the same issues?

---

### Post by tarahmarie on 2008-09-11
I also use an nVidia GeForce 8600 with KDE 4.1.1, compiz-fusion, and Kubuntu 8.04.  I am also having trouble figuring out a way to get a transparent konsole.  My ideal is to have total transparency for konsole so it looks like it's running all by itself on the desktop.  Here's a screenshot I saw on KDE-Look:

[http://www.kde-look.org/content/preview.php?preview=2&id=48303&file1=48303-1.jpg&file2=48303-2.jpg&file3=48303-3.jpg&name=True+transparency+for+Konsole](http://www.kde-look.org/content/preview.php?preview=2&id=48303&file1=48303-1.jpg&file2=48303-2.jpg&file3=48303-3.jpg&name=True+transparency+for+Konsole)

That look to the right is exactly what I want (although I'd like colored text, too!).  Has anyone figured out a way to do this?

---

### Post by tarahmarie on 2008-09-11
Hey! I've got a transparent Konsole now! (also yakuake!)  Here's what I did:

(1) Open a Konsole.
(2) Go to settings--edit current profile.
(3) Hit the appearance tab.
(4) Pick any color scheme you want (I picked the black on white one at the bottom)
(5) There are three buttons by the color scheme picker; new, edit, remove.
(6) Click on 'edit'
(7) There will be a slider there at the bottom of the edit window; slide transparency up to 100% (or however much--I wanted mine totally transparent).
(8) Exit out of the settings windows.  Mine was transparent immediately; I don't know if you'll have to restart Konsole to make it work.  Notably, this also changes the settings for Yakuake.

---

### Post by sakis001 on 2009-09-27
> **tarahmarie said:**
> Hey! I've got a transparent Konsole now! (also yakuake!)  Here's what I did:

(1) Open a Konsole.
(2) Go to settings--edit current profile.
(3) Hit the appearance tab.
(4) Pick any color scheme you want (I picked the black on white one at the bottom)
(5) There are three buttons by the color scheme picker; new, edit, remove.
(6) Click on 'edit'
(7) There will be a slider there at the bottom of the edit window; slide transparency up to 100% (or however much--I wanted mine totally transparent).
(8) Exit out of the settings windows.  Mine was transparent immediately; I don't know if you'll have to restart Konsole to make it work.  Notably, this also changes the settings for Yakuake.

this does it right,
great :D

---

