---
title: "ImageMagick convert (PDF to JPG) not working"
date: 2008-09-26
forum: General Help
---

### Post by altonbr on 2008-09-26
For work, I've had to convert 54 PDF files into JPG files. I used ImageMagick like so:

```
for file in `ls *.pdf`; do
	convert $file -resize 800x800 `echo $file | sed 's/\.pdf$/\.jpg/'`
done
```

and everything appeared to work fine.

However, my boss and fellow employees, all who use IE7 and Windows can not see the images. I tested it in IE6 through Wine and it appears to be an IE problem.

I've tested the images in GIMP, Image Viewer, Konqueror, Epiphany, Safari, etc. and all seem to work fine.

Here's a link: [http://www.youronlineagents.com/kawarthahomeandcottageguide/guide.php?page=5](http://www.youronlineagents.com/kawarthahomeandcottageguide/guide.php?page=5). Only page=1 should show up properly.

Does anyone have any suggestions?

---

