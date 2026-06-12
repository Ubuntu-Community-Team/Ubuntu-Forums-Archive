---
title: "&quot;Places&quot; Menu Items Broken - &quot;Could not open location&quot;"
date: 2008-08-14
forum: General Help
---

### Post by bunnyfly on 2008-08-14
Hello - almost none of my "Places" folders are working anymore! If I click on them I get an error: "Could not open location 'file:///home/bunnyfly' There was an error launching the default action command associated with this location."

How it happened was this: I wanted to get rid of Nautilus and use Dolphin, so I followed the scripts here:

[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

I downloaded the .desktop files the scripts use and switched "thunar" or whichever I grabbed with dolphin on the exec line. Then I moved them into /usr/share/applications. This didn't work, and only broke my Places menu, except for the "Computer" item that opened nicely in Dolphin. I tried to replace "dolphin" with nautilus in the files but that didn't fix anything, only turned the Computer link back to nautilus.

Any help is really appreciated!
[bunnyfly]

---

### Post by iaculallad on 2008-08-14
Try resetting your panels:

```
sudo gconftool-2 --shutdown
sudo rm -rf ~/.gconf/apps/panel
sudo pkill gnome-panel
```

---

### Post by bunnyfly on 2008-08-14
Thanks for the try - that didn't help though.
[bunnyfly]

---

### Post by sayakb on 2008-08-14
Have you completely removed Nautilus? And why did you change to "thunar"?

---

### Post by bunnyfly on 2008-08-14
No - as I understand it, you can't remove Nautilus because Gnome uses it to draw the desktop along with other things.

And I don't want Thunar - as I said in my post, I want Dolphin, so I took one of the other scripts (I don't know if it was Thunar or Konqueror or what) and replaced it's command with Dolphin's since the psychocats site doesn't have a script for Dolphin.

And the why? Because now that it's gotten to the point it has speed and stability-wise, Dolphin's awesome and Nautilus...isn't? : )
[bunnyfly]

---

### Post by sayakb on 2008-08-14
Afaik, the places menu is what only nautilus handles. Open a nautilus window, goto Bookmarks->Edit Bookmarks and remove and re-add the bookmarks you want to. They will appear under places.

---

### Post by bunnyfly on 2008-08-15
That didn't affect it. Within Nautilus the bookmarks work, it's only within the Places menu. But it's also the Home, Desktop, and other hard drives listed in the menu that don't work.

I really appreciate the suggestions though!
[bunnyfly]

---

### Post by bunnyfly on 2008-08-17
Anybody?

---

### Post by pgn674 on 2008-10-04
Use Synaptic Package Manager to reinstall Nautilus, to get that menu working with Nautilus again.

---

### Post by pluckypigeon on 2008-10-29
is it fixed?

---

### Post by maurice_chavez on 2008-10-30
I have had the same problem.
It seems that url handler for protocol "file://" is not set.

Try this:
```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

I hope this solve the problem.

---

### Post by HDave on 2008-11-11
I have this exact same issue...reinstalling nautilus didn't help.  Any other ideas?

---

### Post by HDave on 2008-11-12
Solved this by running nautilus from a command line.  Right clicking on a folder and selecting "open with...." and picking nautilus from the list of applications.  Viola fixed.

I have no idea what I did to break it, but it is a well reported bug.

---

### Post by pluckypigeon on 2008-11-12
[http://ubuntuforums.org/showthread.php?t=962209](http://ubuntuforums.org/showthread.php?t=962209)

this fixed it for me

---

### Post by frogotronic on 2010-05-02
> **maurice_chavez said:**
> I have had the same problem.
It seems that url handler for protocol "file://" is not set.

Try this:
```
gconftool-2 -s /desktop/gnome/url-handlers/file/command -t string "nautilus \"%s\""
gconftool-2 -s /desktop/gnome/url-handlers/file/enabled -t bool true
```

I hope this solve the problem.

Wow, THANKS!  This totally solved my problem - PLACES menu was opening up ClamTK

- CH    :guitar:

---

