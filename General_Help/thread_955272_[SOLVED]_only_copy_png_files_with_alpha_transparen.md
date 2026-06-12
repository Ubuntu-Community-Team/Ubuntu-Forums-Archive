---
title: "[SOLVED] only copy png files with alpha transparency in terminal"
date: 2008-10-22
forum: General Help
---

### Post by Korijn on 2008-10-22
Is it possible to only copy png files with alpha transparency in the terminal using some kind of command? I have a huge amount of png images and only a few have alpha transparency. They were recovered using foremost so the names are not logical and I could search through them but it would be easier if the above would be possible. Or perhaps delete all images that don't have alpha transparency.

---

### Post by geirha on 2008-10-22
The identify command from the [imagemagick](apt://imagemagick) package might be used for this. I can't guarantee this will work, but I created a png-file with transparency, and one without (using gimp). Then comparing ```
identify -verbose image.png
``` on those two images, the one with transparency had an entry for Opacity along with Red, Green and Blue under Channel statistics, while the other one didn't. Using that information we can loop through and separate them.

```

#!/bin/bash

for file in "/path/to/images/"*.png; do
   if identify -verbose "$file" | grep -q "Opacity:"; then
       echo "$file"
       # mv -v "$file" "/path/to/alphaimages/"
   fi
done

```

Check some random samples of the list it produces, if it looks ok, use the same loop to move them with the mv command (as suggested on the commented line)

---

### Post by Korijn on 2008-10-23
That didn't work too well for me.

I figured something out that worked though.

```
root@KorijnServer:~# for f in *.png; do if [ `file $f | cut -f9 -d\ ` = "RGBA," ] && [ `file $f | cut -f5 -d\ ` -gt 780 ] && [ `file $f | cut -f7 -d\ | sed -e s/,$//` -gt 166 ]; then cp $f /media/external/wolf/pngSel; fi; done

```

---

