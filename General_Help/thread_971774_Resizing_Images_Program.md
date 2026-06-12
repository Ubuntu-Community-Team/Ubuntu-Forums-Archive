---
title: "Resizing Images Program"
date: 2008-11-05
forum: General Help
---

### Post by George7a on 2008-11-05
Hi all,

I have about 1200 JPG files stored in one directory (lets call it main directory) in side the main directory there are sub directories each one have some JPG files & other sub directories the contains more JPGs.

All the JPGs are 8.1 MP I would like to resize them to let say 1 MP. Is there a program that can go over all the images and resize?

- George

---

### Post by renzokuken on 2008-11-05
does this help?
[http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux](http://www.smokinglinux.com/tutorials/howto-batch-image-resize-on-linux)

---

### Post by geirha on 2008-11-05
With [apt://imagemagick](apt://imagemagick), making a script to loop through the jpegs and resize shouldn't be too hard.

The following will recursively find all jpg files in the current directory and create a .small.jpg-file which is 15% of the original size
```

find . -iname "*.jpg" -not -iname "*.small.jpg" | while read filename; do
    prefix="${filename%.*}"     # Pathname without extension
    extension="${filename##*.}" # Extension
    echo "Resizing $filename to ${prefix}.small.${extension}"
    convert "$filename" -resize 15% "${prefix}.small.${extension}"
done

```

---

### Post by George7a on 2008-11-05
Thank you! Great tool and great script!

---

### Post by SoCalChris on 2008-11-05
How would I have this script only create the small image if it doesn't already exist?

---

### Post by George7a on 2008-11-06
Hi,

This link has the documentation of the "if" command.:
[http://www.ss64.com/bash/if.html](http://www.ss64.com/bash/if.html)

I have used it to check if a file exist, then delete it. Here is the example:
[http://ubuntuforums.org/showpost.php?p=6078195&postcount=11](http://ubuntuforums.org/showpost.php?p=6078195&postcount=11)

I hope it helps,

- George

---

