---
title: "titlebars pop under (behind) gnome panel"
date: 2008-11-05
forum: General Help
---

### Post by Shardsofmetal on 2008-11-05
I'm using Ubuntu Intrepid with Compiz and Emerald. I use custom Compiz effects, and recently disabled the ability to snap off/move fullscreen apps. I made some other modifications, but none that I know of that would be relevent to this issue. Anyway, sometimes when I start an application the titlebar of the window is stuck under the panel. While I can hold alt and drag the window down, this is very annoying, and it didn't used to happen. It doesn't happen if an application starts in fullscreen mode. Does anybody know how to make new windows appear below the panel, as they should, without re-enabling that setting? Thanks

---

### Post by pytheas22 on 2008-11-05
Take a look at this [bug report]("https://bugs.launchpad.net/compiz/+bug/82654"), especially the last post.  I'm not sure if this is the same issue that you're experiencing, but there are a few suggestions that you could try.

I also seem to remember that there's a value that you can set somewhere in gconf-editor to tell it to prevent windows from ever invading the space of the gnome-panel.  This might help (or might not since it's unclear whether the issue here is compiz's or Gnome's fault), but I'm not positive of the exact path of the value that you would need to change.

---

