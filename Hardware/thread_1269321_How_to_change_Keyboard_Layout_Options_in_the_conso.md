---
title: "How to change Keyboard Layout Options in the console?"
date: 2009-09-18
forum: Hardware
---

### Post by benpaka on 2009-09-18
Hello,

I need to change some parameters in  System > Preference > Keyboard > Layout > Layout Options at each reboot and shutdown.
(See [http://ubuntuforums.org/showthread.php?t=1197838](http://ubuntuforums.org/showthread.php?t=1197838))

I have made a script but I don't find how to change these parameters from the console?

I've look in gconf-editor and there is nothing... Someone could help me???

---

### Post by keplerspeed on 2009-09-18
[http://ubuntu-tutorials.com/2008/01/31/changing-the-system-keyboard-mapping-on-ubuntu-dvorak-vs-qwerty/](http://ubuntu-tutorials.com/2008/01/31/changing-the-system-keyboard-mapping-on-ubuntu-dvorak-vs-qwerty/)

Use:
```

sudo dpkg-reconfigure console-setup

```

To make system wide changes.

---

### Post by benpaka on 2009-09-18
Thanks,

It seems to work with ```
setxkbmap -option lv3:ralt_switch
``` at gnome startup... (Just put a script in Startup program)

---

### Post by benpaka on 2009-09-18
Arff ... I have a problem with this function

If i do consecutively:

```

$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+es+inet(evdev)"	};
	xkb_geometry  { include "pc(pc104)"	};
};

```

then

```

$ setxkbmap -option lv3:ralt_switch
$ setxkbmap -option lv3:ralt_alt
$ setxkbmap -print
xkb_keymap {
	xkb_keycodes  { include "evdev+aliases(qwerty)"	};
	xkb_types     { include "complete"	};
	xkb_compat    { include "complete"	};
	xkb_symbols   { include "pc+es+inet(evdev)+level3(ralt_switch)+level3(ralt_alt)"	};
	xkb_geometry  { include "pc(pc104)"	};
};


```


I have the two options activated but I don't know how to remove one of them, or delete them :(

---

### Post by benpaka on 2009-09-21
nobody know another way to do this... because it still doesn't work :(

---

