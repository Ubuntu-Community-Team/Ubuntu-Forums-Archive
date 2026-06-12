---
title: "Compiz Update Killed My Window Decoration?"
date: 2008-08-18
forum: General Help
---

### Post by safetycopy on 2008-08-18
Hi,

Last night I updated compiz from

```
http://ppa.launchpad.net/compiz/ubuntu hardy main
```

Today when I rebooted I have no window decoration.

Running

```
compiz-decorator
```

from the CLI results in this error:

```
Starting gtk-window-decorator
/usr/bin/gtk-window-decorator: symbol lookup error: /usr/bin/gtk-window-decorator: undefined symbol: decor_blend_border_picture
```

The compiz-related packages I have installed are:

compiz 1:0.7.6-0ubuntu2~ppa1
compizconfig-backend-gconf 0.7.4-0ubuntu1
compizconfig-settings-manager 0.7.6-0ubuntu1~ppa1
compiz-core 1:0.7.6-0ubuntu2~ppa1
compiz-fusion-plugins-extra 0.7.6-0ubuntu1~ppa1
compiz-fusion-plugins-main 0.7.6-0ubuntu1~ppa1
compiz-gnome 1:0.7.6-0ubuntu2~ppa1
compiz-plugins 1:0.7.6-0ubuntu2~ppa1
fusion-icon 0.0.0+git20071028-2ubuntu2
libcompizconfig0 0.7.6-0ubuntu1~ppa1
simple-ccsm 0.7.4-0ubuntu1

At the moment, the only way I can get any window decoration is Compiz Fusion Icon > Select Window Decorator > Emerald.

Have I done something wrong (or missed something) when upgrading compiz, and if so, how do I fix it?

---

### Post by overdrank on 2008-08-18
moved to Desktop Effects & Customization  :)

---

