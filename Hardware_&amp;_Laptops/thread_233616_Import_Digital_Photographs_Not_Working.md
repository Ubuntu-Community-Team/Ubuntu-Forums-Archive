---
title: "Import Digital Photographs Not Working"
date: 2006-08-10
forum: Hardware &amp; Laptops
---

### Post by _Dan on 2006-08-10
Hi!

I need to setup ubuntu so my mother can easily download photos from a camera.

But I have several problems!!

Firstly, when a digital camera is detected, the camera model defaults to the first in the list (Argus DC). Then import photos says "no images found"! And the button to select a camera model does not work. The auto-run program is gthumb.

Second problem:

f-spot and gtkcam both work, gtkcam if I specify the correct camera model (auto detect doesn't work), f-spot just works (even though it says the incorrect, default, camera model)

BUT they use a "ppm" format I have never heard of before. I need the images to be converted to jpg to streamline uploading to the internet for ebay.

Is there a way to configure f-spot or gtkam (f-spot preferably) to do this automatically?

(and/or can anyone suggest a different camera program to try)

THANKYOU!:KS

---

### Post by _Dan on 2006-08-12
I just wrote my first shell script!!:cool: 

```
#!/bin/bash

photodir="Pencam Photos"

cd "$HOME"

if [ ! -d "$photodir" ]
then
	mkdir "$photodir"
fi

cd "$photodir"

echo ""
echo "Please enter a name for the photos, then press ENTER:";

read name;
echo "";

# if no name entered give default name
if [ "$name" = "" ]
then
	name="images"
fi

# new directory is name+date+time
newdir="$name-$(date +"%A_%B_%-d_%Y_%X")"
mkdir "$newdir"
cd "$newdir"

gphoto2 --get-all-files

if [ -f "image001.pnm" ] # if at least one photo copied
then
	convert *.pnm "$name.jpg"
	rm *.pnm
	gphoto2 --delete-all-files
	echo "Photos successfully copied to folder: $photodir/$newdir.";
	nautilus "."
else
	cd ..
	rmdir "$newdir"
	clear
	echo "ERROR: Either there are no photos on the camera or it is not connected."
	echo ""
	read
fi


```

So in a way my problem is solved, it is annoying it didn't just *work* though.:shock:

---

