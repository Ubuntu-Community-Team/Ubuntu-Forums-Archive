---
title: "Resizing terminals with wmctrl"
date: 2008-11-12
forum: General Help
---

### Post by Crick on 2008-11-12
I have made two resize scripts executed using xbindkeys-config via CTRL+ALT+4 and CTRL+ALT+6 (ala winsplit revolution). They are move_e:
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
wmctrl -r :ACTIVE: -e 1,960,0,960,1080
```

and move_w
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
wmctrl -r :ACTIVE: -e 1,0,0,940,1080
```

The problem is that terminal windows refuse to comply (they just seem to get the height and width right), although everything else does. Anyone have any idea why? I have tried experimenting with the "gravity", but that doesn't appear to do anything. Screen size is 1920x1080 btw.

Thanks also to spiregrain for showing me how to do this, on this thread:
[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=601186](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=601186)

---

### Post by zhocchao on 2008-11-15
Hi
I seem to have the same Problem. I wrote a tiling script for Metacity and all the windows but the terminal do what they should do. This problem occurs in Hardy. Intrepid is working properly. If you are using Hardy then this could be a bug .I thought i may have changed some settings. But it looks like this is normal.

greeting z


It's been a long time since I wrote in English, so if you find any heavy mistakes you could tell me.

---

