---
title: "How do I change the default program?"
date: 2008-08-21
forum: General Help
---

### Post by theilliniguy on 2008-08-21
When a click on a file and the default ap opens, how do I change the default ap that opens to another?

---

### Post by Nepherte on 2008-08-21
Right click on a file that has the extension you want to change the default program of, choose properties and go the 'open with' tab. Pick the program you want.

---

### Post by theilliniguy on 2008-08-21
> **Nepherte said:**
> Right click on a file that has the extension you want to change the default program of, choose properties and go the 'open with' tab. Pick the program you want.

I know that will open the file in a substitute ap but will it assign that ap as default for that file type forever?

---

### Post by Nepherte on 2008-08-21
It should have that effect yes.

---

### Post by theilliniguy on 2008-08-21
> **Nepherte said:**
> It should have that effect yes.

Hmmm.... No dice.  Opened a WMV file in VLC (by selecting "use other ap") and it opened in VLC.  Then double clicked it and it opened Totem video player still.

---

### Post by mb_webguy on 2008-08-21
I don't think you were paying attention, young man... er, woman... er, person!

He didn't say right-click on the file and select "Open with other application".  He said to right-click on a file, and select "*Properties*", and go to the "Open With" *tab*, and select the program you want to open the file.

---

### Post by theilliniguy on 2008-08-21
> **mb_webguy said:**
> I don't think you were paying attention, young man... er, woman... er, person!

He didn't say right-click on the file and select "Open with other application".  He said to right-click on a file, and select "*Properties*", and go to the "Open With" *tab*, and select the program you want to open the file.

"Young" - thanks!

Yer rite I was "speed" reading and missed the key words!  I'm good to go now - and thanks for the help.

---

### Post by silkstone on 2008-08-21
If you want DVDs to open automatically in VLC, you have to edit a file and do one or two other things...

gksudo gedit /etc/gnome/defaults.list

Search for "x-content/video", then change the "totem.desktop" entries to "vlc.desktop". Close and save.

Next, right-click on Applications in the top panel and select Edit Menus. Navigate down to "Sound & Video" in the left pane and click on it to show the applications in the right-hand pane. Scroll down to VLC media player, right-click on it, then click on Properties

In Launcher Properties, change vlc %U to vlc %m

Close the VLC properties dialog and exit the menu editor. Finally, in the Nautilus file browser, click on Edit > Preferences > Media > DVD Video and select VLC.

---

