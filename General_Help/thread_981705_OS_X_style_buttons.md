---
title: "OS X style buttons"
date: 2008-11-14
forum: General Help
---

### Post by Totenglocke on 2008-11-14
Does anyone know how I can get OS X style buttons on my windows?  I'm not interested in an OS X makeover, not interested in switching the buttons to the other side of the window, just changing the minimize, maximize, and close buttons to the color and shape they are in OS X.

---

### Post by loomsen on 2008-11-14
Your currently active emerald theme should be located in
```

~/.emerald/theme/

```

If you move there with your favorite file-browser you'll see a couple of Pictures and 2 textfiles. Thats you current theme. I'd copy the whole dir to a temp dir while modifying it tho, for instance do this, open up a terminal and copy n paste, assuming your workdir in the terminal is ~/:
```

mkdir temp && mkdir temp/custom-emerald/ && cp ./.emerald/theme/* ./temp/custom-emerald/

```

Modify the pics as you want them to be, when you're done copy the whole dir back to ~/.emerald/themes/
Not, its not the same dir as before, this is the one where currently inactive emerald themes go to. See:
```

me@tiffany:~$ ls .emerald/
settings.ini  theme  themes
me@tiffany:~$ 

```

---

