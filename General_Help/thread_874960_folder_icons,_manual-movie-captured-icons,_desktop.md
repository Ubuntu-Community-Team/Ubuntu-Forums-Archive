---
title: "folder icons, manual-movie-captured-icons, desktop icons, disabled right-click"
date: 2008-07-30
forum: General Help
---

### Post by tsr on 2008-07-30
Hi,

I'm preparing a desktop for my daughter (4years, not very experienced with comps). I want to customize the interface a bit.

For starters I would like to know how to (if possible at all):
- Create big custom icons from images in nautilus (I know I can stretch them on the desktop.
- Customize which frame in a movie will be shown in nautilus (or how I can capture a certain frame and use it as an image in the previous point)
- how I can disable the mouses right-click for her but not for other users.

/tsr

---

### Post by tsr on 2008-07-30
Progress:

> **tsr said:**
> 
- Create big custom icons from images in nautilus (I know I can stretch them on the desktop.


The easiest way is to customize one icon in the folder where I want to have customized icons, that will create the file **/home/username/.nautilus/metafiles/file:%2F%2F%2Fhome%2Fusername.xml** (or something similar).

Then it's just a matter of editing that file and append something like 'icon_scale="2.2"' to every line where you want bigger icons.

Example:
```

<?xml version="1.0"?>
<directory>
	<file name="Video" timestamp="1217457267" custom_icon="file:///home/username/.thumbnails/custom/test.png" icon_scale="2"/>
</directory>

```

> **tsr said:**
> 
- Customize which frame in a movie will be shown in nautilus (or how I can capture a certain frame and use it as an image in the previous point)


I found the program 'gnome-video-thumbnailer' by looking around in gconf. This made my day. Using it I could make custom thumbnails that I then put in the folder /home/username/.thumbnails/custom/ then it was just a matter of pairing the thumbnails with the files and upping the size by the method described above.

> **tsr said:**
> 
- how I can disable the mouses right-click for her but not for other users.


Still unsolved, I'll hunt around for a while...

/tsr
/tsr[/QUOTE]

---

### Post by Psyphre on 2008-12-02
Hi,

I'm suprised no-one has responded to this thread.
Thank you so much for sharing your progress, the thumbnailer modifying will be extremely useful for me.

Thanks again.

---

