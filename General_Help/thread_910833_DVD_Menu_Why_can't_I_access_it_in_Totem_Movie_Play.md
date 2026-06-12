---
title: "DVD Menu: Why can't I access it in Totem Movie Player?"
date: 2008-09-04
forum: General Help
---

### Post by OzzyFrank on 2008-09-04
I'm wondering how to get the menus for DVD titles opened in Totem Movie Player 2.22.1 to appear... and as far as I can remember, I've never been able to access them in Totem, which is why I ended up going for Kaffeine.

I mean, I know "DVD Menu" (and "Title Menu" and "Chapter Menu") are in the "Go" menu, but clicking any of these does absolutely nothing. Am I missing something here? Is there any way to get to the title or chapter menu in Totem? Do I need a plugin (and if so, why is the option already in the "Go" menu)? Cheers.

---

### Post by Bakon Jarser on 2008-09-04
[https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd](https://help.ubuntu.com/8.04/musicvideophotos/C/video.html#video-dvd)

Personally i use VLC.

---

### Post by genesis2seven on 2008-09-04
DVD menu's don't work in Totem.

You need to go to System > Synaptic Package Manager and then search for libdvdnav4, libdvdread3 and mark both for installation. Then install and exit.

Might work after those are installed but I'm pretty sure Totem won't support menus.

If you want my advice after you've done that go to System > Software Sources and on the Ubuntu Software tab make sure everything is checked. Then on the Third-Party Software tab check "http://archive.canonical.com/ubuntu partner"

Finally go to Applications > Add/Remove... and search for VLC and install. It is my preference for watching DVD's and works great with Menu's.

The only one I've had a problem with using VLC is Office Space which I couldn't get to work on Linux period thanks to all the MS based extras they added.... Hope that helps. Xine is another good package to install over Gstreamer.

---

### Post by Chunky Dunk on 2008-09-05
Menu's work in Totem for me, but I use the Totem-xine package, not the gstreamer one that comes default.

---

### Post by Irihapeti on 2008-09-05
DVD menus work in Totem-xine and vlc. You need to install libdvdcss2 from the Medibuntu repositories to be able to play encrypted DVDs.

More information here: 
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

