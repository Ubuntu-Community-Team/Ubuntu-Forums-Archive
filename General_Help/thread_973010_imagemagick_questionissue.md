---
title: "imagemagick question/issue"
date: 2008-11-06
forum: General Help
---

### Post by kuja on 2008-11-06
Okay, so I've got a few images that I'm putting together into one ... I've set the density and the units, but when I open the output with other programs it still seems to think the res is the default 72 instead of 300. Any idea why? Here's the command that I'm using:

```
montage -units PixelsPerInch -depth 300x300 -tile x1 -geometry +0+0 2b.png 1w.png 2b.png joined.png
```

What's going on here?

---

### Post by kaibob on 2008-11-06
> **kuja said:**
> ```
montage -units PixelsPerInch -depth 300x300 -tile x1 -geometry +0+0 2b.png 1w.png 2b.png joined.png
```

I'm not an expert on Imagemagick, but your command line appears to use the depth rather than the density option:

[http://www.imagemagick.org/script/command-line-options.php#density](http://www.imagemagick.org/script/command-line-options.php#density)

---

### Post by kuja on 2008-11-06
:oops: Now when did that get there ... I know at some point or other that line said density...


Oh well. All is well now. Thank you.

---

