---
title: "HELP! Screen resolution change and monitor detection won't work!"
date: 2008-06-08
forum: Hardware
---

### Post by oleksus on 2008-06-08
I've just installed Hardy (after two years using Feisty) on my Toshiba laptop.

First off, I can't set screen resolution to native 1024x768, because it's just not there! The 800x600 is the top res, why? I remember Feisty detected my laptop monitor without any problems.

That strange 'detect displays' button won't do anything.

What's up with that? Is it the new 'improvement'?
How can I set it properly?

---

### Post by avtolle on 2008-06-08
[http://ubuntuforums.org/showthread.php?t=817611](http://ubuntuforums.org/showthread.php?t=817611) may have something to help you.

---

### Post by ubuntu-freak on 2008-06-08
Try setting it with:
 
**sudo xrandr -s 1024x768**

---

### Post by oleksus on 2008-06-09
Tried that. But it says 'Size not found in available modes.'

How do I unlock it to 'available modes'?
I remember someone said about some X config file to edit...

---

### Post by ubuntu-freak on 2008-06-09
> **oleksus said:**
> Tried that. But it says 'Size not found in available modes.'

How do I unlock it to 'available modes'?
I remember someone said about some X config file to edit...

Doesn't work? It's only one setting above 800x600. Anywho, try:

**sudo xrandr -q**

It will tell you what's available. Failing that, try:

**gksudo displayconfig-gtk**

You may have to select a different screen in the list, but that's not normally necessary.

---

### Post by oleksus on 2008-06-10
The xrandr -q displays
```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x x600
default connected 800x600+0+0 0mm x 0mm

```

Obviously there's something with the monitor settings, it simply hasn't detected the monitor type.
Where can I set it in the xorg.config file?

I tried displayconfig-gtk but the only available modes still are none higher than 800x600.
The monitor model there is 'Plug'n'Play'.

How to set the maximum display mode to 1024x768?

---

### Post by mindshift0 on 2008-06-10
Hi,

first----mind shift gives you.......

Recover a lost or stolen laptop with a theft recovery service that not only ttempts to recover the lost or stolen machine, but also remotely wipes data from it when it connects to the Internet.


your business depends on IT, these unrelenting IT problems are beyond annoying.

Sania,
([http://www.mindshift.com/Products-and-Services_PCRetrieve.aspx](http://www.mindshift.com/Products-and-Services_PCRetrieve.aspx))

---

### Post by editrix on 2008-06-10
This happened to me when I booted up this morning. I spent 2 hours trying all the things suggested, as well as other things, and documenting it all, to no avail. I'm in Kubuntu Hardy but I also have Gnome, and tried everything in both.

Then, when switching from Gnome to KDE for about the 4th time, I noticed that one of the menu options at login is restart X server.

It worked.

Update: But now I have no sound :-(

---

### Post by ubuntu-freak on 2008-06-11
> **oleksus said:**
> The xrandr -q displays
```

Screen 0: minimum 320 x 240, current 800 x 600, maximum 800 x x600
default connected 800x600+0+0 0mm x 0mm

```

Obviously there's something with the monitor settings, it simply hasn't detected the monitor type.
Where can I set it in the xorg.config file?

I tried displayconfig-gtk but the only available modes still are none higher than 800x600.
The monitor model there is 'Plug'n'Play'.

How to set the maximum display mode to 1024x768?

Try changing your monitor to "generic" instead, that has worked for some.

---

### Post by oleksus on 2008-06-11
It somehow worked!
After a dozen attempts at tweaking all possible tweaks, I happened to be able to select 'Generic', although I remember NOT having this option before... Weird.
But cool.

Thanks folks! Your help encouraged me.
That's the strength of Ubuntu.

(how do you switch a post to SOLVED state?)

---

