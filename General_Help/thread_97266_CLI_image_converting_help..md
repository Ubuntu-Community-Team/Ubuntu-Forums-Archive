---
title: "CLI image converting help."
date: 2005-11-30
forum: General Help
---

### Post by denisesballs on 2005-11-30
Hey guys. This has been bugging me for a while. I use convert a lot to scale a directory of images down all at once. But is there a way to convert a bunch of images down to a specific size and cut off the excess? Like say I want to take a bunch of images of random size and make them all 48x48 pixels. Without scaling them by either height or width, but just cut off whatever part of each image is over that size? This would be very helpful.

---

### Post by rsay on 2005-11-30
If you install imagemagick you can use mogrify

```
mogrify -format gif -geometry 100x100 *.jpg

```

This command will crop all jpgs in the directory with preserved aspect ratio to maximum dimension of 100 pixels and save the resultant image as gif. (If you choose jpg it will overwrite the original)

If you have some images in the directory that are already below 100 pixels you can use -geometry '100x100>' to prevent them from being enlarged.

To get more options:
```
man mogrify
```

p.s. Make a backup of your directory before you start playing with this command.

---

