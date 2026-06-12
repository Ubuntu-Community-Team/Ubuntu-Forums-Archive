---
title: "firefox 3 sucks"
date: 2008-09-01
forum: General Help
---

### Post by syms on 2008-09-01
recently ive found that when i load some page my cpu usage gets to 97%, the same thing is with epiphany, but when i tried that with firefox 2 i didnt see that problem. i really want to come back to firefox 2 of many reasons, but the problem is that theres no gstreamer plugin for firefox 2, it says that i require plugin, but it cant find it and that plugin is installed and works with firefox 3. how can i fix this?

---

### Post by arch0njw on 2008-09-02
I ended up completely uninstalling firefox 3 and going back to firefox 2.x.  All of the plugins I like aren't available in 3 yet.

Here is what I did:
1. remove firefox (e.g., sudo apt-get remove firefox)
2. remove all plugins that you have installed
3. install firefox 2 (e.g., sudo apt-get install firefox-2)
4. reinstall the plugins

I know gstreamer works because I have it installed.
```
$ dpkg -l *gstream* | grep ii
ii  gstreamer0.10-alsa                         0.10.18-3                                                  GStreamer plugin for ALSA
ii  gstreamer0.10-gnomevfs                     0.10.18-3                                                  GStreamer plugin for GnomeVFS
ii  gstreamer0.10-plugins-bad                  0.10.6-5                                                   GStreamer plugins from the "bad" set
ii  gstreamer0.10-plugins-base                 0.10.18-3                                                  GStreamer plugins from the "base" set
ii  gstreamer0.10-plugins-good                 0.10.7-3ubuntu0.1                                          GStreamer plugins from the "good" set
ii  gstreamer0.10-plugins-ugly                 0.10.7-3ubuntu1                                            GStreamer plugins from the "ugly" set
ii  gstreamer0.10-x                            0.10.18-3                                                  GStreamer plugins for X11 and Pango
ii  libgstreamer-plugins-base0.10-0            0.10.18-3                                                  GStreamer libraries from the "base" set
ii  libgstreamer0.10-0                         0.10.18-4ubuntu1                                           Core GStreamer libraries and elements
ii  phonon-backend-gstreamer                   4:4.2.0-0ubuntu1~hardy1~ppa1                               Phonon GStreamer 0.10.x backend

```

---

### Post by chadeldridge on 2008-09-02
Just as a question ... did you try swiftfox?  I had the same issue with ff3 .. i removed it and went to swiftfox and no longer have that problem.

---

