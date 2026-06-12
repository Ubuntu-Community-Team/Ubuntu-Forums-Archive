---
title: "Replacing the URL Launcher"
date: 2008-11-10
forum: General Help
---

### Post by Bill_MI on 2008-11-10
I'm looking for expert help in completely replacing the launcher of *.desktop files.  These are the files created by dragging the site icon in Firefox (the icon in the URL bar) to the desktop or Nautilus directory.

The launching script (I assume) would have to go inside this plain text file, parse the URL, then launch Firefox on this URL.

Reasons:
1) [https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233913](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/233913)
A bug truncating URLs at any question mark (?parameters) starting before Hardy release not fixed in Intrepid.  Intrepid also breaks a reasonably quick Hardy workaround.

2) Nautilus performs stifling checks (mainly DNS lookup) on the URL that is not at all appreciated.

TIA

---

