---
title: "Acer Aspire One Keyboard Map"
date: 2009-10-30
forum: Hardware
---

### Post by datajack on 2009-10-30
Hi All,

I have just installed Karmic as a fresh install after breaking the upgrade process (hibernating then battery death is not a good thing to happen in the middle of an upgrade ;) )

The biggest problem that I have noticed so far is that the 'House' key (replacement of the Windows key) does not function as it did in Jaunty. It used to toggle between the 'desktop' and the last running application (now mapped to CTRL-ALT-D in Karmic). I ahve tried in Keyboard Shortcuts to re-map this but it seems that this key is no longer fully supported in Karmic.

Is thre any way I can get this to work?

TIA

---

### Post by laurybueno on 2009-12-19
I have had the same issue.

Run the command gconftool-2 --set /apps/metacity/global_keybindings/show_desktop --type string "Super_L"

---

