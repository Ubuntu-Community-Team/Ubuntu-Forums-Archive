---
title: "Install RealPlayer without it overriding default programs?"
date: 2008-09-01
forum: General Help
---

### Post by mb_webguy on 2008-09-01
I have a weird issue with RealPlayer and Deluge, though I have a feeling it would likely involve other programs as well.

I have VLC set as the default media player on my system.  It's set in Preferred Applications, and I've checked it on the Open With tab of the Properties of the various media files.  I've even edited /etc/gnome/defaults.list so that vlc.desktop is the default for all of the desired mime types, made sure that those mime types were in the vlc.desktop files, and updated the mime type database (using "sudo update-mime-database").

The problem is that after I install RealPlayer (using the bin file downloaded from the Real website), if I open Deluge and double-click on a file within one of the torrents I'm downloading, the file is opened in RealPlayer instead of VLC.  And no, Deluge doesn't have the option to set what media player you want it to use.  It uses (or is supposed to use) the system default.

After playing around with my system a while, I discovered that the command "gnome-open" would likewise ignore the Gnome mime type settings and open the file using RealPlayer.  The similar command "gvfs-open" (in the package gvfs-bin) correctly uses VLC.  Google led me to some posts mentioning this, and that gnome-open (and it's parent package libgnome) was being deprecated in favor of gvfs.  However, those posts were almost a year old, and while I see the letters "gvfs" in Hardy quite a bit, it apparently still uses gnome-open as a helper for some programs.

Having said that, I really don't care what has bugs or what's being deprecated. What I'd like to do is install RealPlayer without it screwing with my mime types.  It doesn't add any unusual entries in the usual locations (i.e. /etc/gnome/defaults or ~/.local/share/applications/mimeapps.list), but it has to be putting something *somewhere* for Deluge and gnome-open to be deciding that it should be the default application for these file types.  I used the command "sudo find / -name *realplay* -delete" (after running it once without the delete option to make sure it wasn't grabbing anything important) to remove RealPlayer from my system, and once I did, Deluge and gnome-open used VLC to open files again, as they should.

Does anyone know how to go about installing RealPlayer so that it won't mess around with my mime settings?

---

### Post by mb_webguy on 2008-09-02
*bump*

---

