---
title: "NEF tumbnails in Nautilus"
date: 2008-08-07
forum: General Help
---

### Post by sicofante on 2008-08-07
This has been asked before but not really answered (again, a pretty recent thread about it is already closed inside the archives). Some say installing gnome-raw-thumbnailer will do it, but others (like myself) cant' see the thumbnails after installing that package.

The [home page]("http://gnome-raw-thumb.sourceforge.net/") of the project is so sparse that I can copy it fully here:

"This is the home page of gnome-raw-thumbnailer.  It's largely based on Dave Coffin's parse.c and Bastien Nocera's totem-video-thumbnailer.  The thumbnailer doesn't support auto-rotation yet.  **It also doesn't install its metadata (gconf schema and shared-mime-info) into the proper directories.** 
 I accept patches. 
 george"

(Since the project has been stalled for more than three years now, we can safely assume George has abandoned it, and unless someone else takes it, we shouldn't expect improvements soon.)

I've highlighted the one sentence I don't understand and that maybe affects the behaviour of the software. What are those "gconf schema" and "shared mime info" things? Will set them properly make this work? How do I do that?

Thanks for any help.

---

### Post by silkstone on 2008-08-07
Well, I wouldn't worry too much about the warnings - I have gnome-raw-thumbnailer installed and it works fine for Canon .CR2 files with no tweaking at all. I think it reads the embedded JPEG so should work with new cameras - it certainly does with the 40D.

Maybe the problem is that you've set the filesize limit for thumbnail generation too low.

In Nautilus, Edit > Preferences > Preview Tab, and change the 'only for files smaller than' entry to a larger value.

---

### Post by sicofante on 2008-08-07
Thanks for the suggestion, but I already have my preview filesize limit set to 1 GiB. I've also deleted the .thumbnails folder to no avail.

My Nikon D40 is set to RAW only (not RAW+JPEG). Maybe that's the problem. I will check it tomorrow with a few pictures.

---

### Post by silkstone on 2008-08-08
Setting it to RAW only should be OK - RAW+JPEG is a waste unless you need an instant JPEG for printing or transmission. There is usually a JPEG embedded in the RAW file, and that's what the thumbnailer should read.

I'm sorry I can't explain why it doesn't work, unless there's something unusual about NEF files. It may be the type of compression they use, which will be different from Canon. I've tried it with a 10D, 30D and 40D and the thumbnailer works. It sounds like a compatibility issue rather than the way the software is set up, but if you know anyone with a Canon you may like to try it with CR2 files.

---

### Post by rvanderh on 2009-07-19
I noticed ...
 *.NEF gives thumbnails,  *.nef doesn't . 

Anyone?

---

### Post by richardq on 2009-08-08
> **rvanderh said:**
> I noticed ...
 *.NEF gives thumbnails,  *.nef doesn't . 

Anyone?

Yep. Me too. Only with me it's *.CR2 which gives thumbs and *.cr2 which doesn't. Thanks for pointing that out. I assume it's either a bug in gnome-raw-thumbnailer or I have to rename them all. :( 

Either way, thanks for the tip. At least now I can see them.

---

### Post by richardq on 2009-08-08
I've checked the /usr/share/mime/packages/gnome-raw-thumbnailer.xml file and it lists both upper and lower case versions of the file extensions and yet it only recognizes the upper case ones. I'm not sure where the problem lies.

---

### Post by mcduck on 2009-08-08
It works fine for me with both .nef and .NEF, I have ufraw installed and both desktop/gnome/thumbnailers/application@x-ufraw and desktop/gnome/thumbnailers/image@x-nikon-nef enabled in gconf-editor..

---

### Post by richardq on 2009-08-08
> **mcduck said:**
> It works fine for me with both .nef and .NEF, I have ufraw installed and both desktop/gnome/thumbnailers/application@x-ufraw and desktop/gnome/thumbnailers/image@x-nikon-nef enabled in gconf-editor..

Wow.. installing ufraw enabled a bunch of stuff. Now thumbnails show up perfectly in Nautilus!

Thanks for the hint. :)

---

### Post by hefko on 2011-11-04
Plaese mark the thread as [SOLVED]. Thx!

---

