---
title: "Compiz disrupts playing video"
date: 2008-07-16
forum: General Help
---

### Post by enchance on 2008-07-16
I have compiz installed and everything runs fine but whenever I try to watch a movie (VLC/Totem/Movieplayer/Mplayer/etc.) all I get is the sound and no video. But once I switch off compiz (compiz-switch) only then does the video show itself.

Compiz switched on = no video! Is something wrong with that?

---

### Post by pauper on 2008-07-18
I suggest you to search forums more thoroughly next time. Though I could be
wrong in case the provided below solution doesn't not apply to Hardy. Anyway
it was posted on a few threads, blogs, refering to Gutsy I believe. I happened
to save the solution, but unfortunately can't give the credit to author,
because I didn't save the link.

To enable video playback:

* GStreamer (or any video player that is based on the gstreamer backend)
- Open a terminal and type "gstreamer-properties". Press Enter.
- Video--Default Output Plugin: "X Window System (No Xv)".
- Click Test to verify that video playback is working
- Click Close

* VLC
- Start VLC
- Settings--Preferences--Video--Output modules. Check the box "Advanced
options" at right bottom of the menu
- Video output module: X11 video output
- Click Save
- Restart vlc

* MPlayer (Mplayer is not installed by default)
- Start Mplayer
- Right-click on the screen and select Preferences
- Video--Available Drivers: "X11 (XImage/Shm)"
- Click Save
- Restart mplayer

* Xine (gxine, as well)
- Start xine
- Setup window--gui--Configuration experience level: "Master of the known
universe"
- Setup window--video--video driver to use: "xshm".
- Click Apply, OK
- Restart xine.

---

