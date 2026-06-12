---
title: "Is there a way to do this?"
date: 2008-11-13
forum: General Help
---

### Post by plantboy1 on 2008-11-13
I tend to copy files out of my browser cache in batches since there's not much point in downloading things that I already have stored on my PC.  I don't know any scripting or anything, but I was wondering if there was a way to have my pc look through all the files, add the proper file extensions to them (jpg, png, html, mpg, or w/e), then send them to another script I have which sorts files into folders according to file extension.

Can this be done (for me :p...i don't know how to write a script) or is it just too complicated?

---

### Post by kidders on 2008-11-15
Hi there,

Since changing a file's extension involves moving/copying it anyway, you might as well identify and sort your files in one go, rather than in two separate steps. I would suggest something like this ...```
#!/bin/bash

# Make at least some effort to check that the script is being called properly
if [ -z "$2" ]; then
	echo "Usage: $0 file target"
	exit 2
fi

# Get some basic file type information
typeinfo=`file -b "$1" | cut -d, -f1`

# Map the file types you're interested in to suitable extensions
case "$typeinfo" in
"Macromedia Flash Video") extension="swf"  ;;
"gzip compressed data")   extension="gz"   ;;
"PNG image data")         extension="png"  ;;
"HTML document text")     extension="html" ;;
"GIF image data")         extension="gif"  ;;
"ASCII text")             extension="txt"  ;;
*)                        extension=""     ;;
esac

# Copy the original to a new location
if [ -n "$extension" ]; then
	targetdir="$2/$extension"
	mkdir -p "$targetdir"
	cp "$1" "$targetdir/`basename $1`.$extension"
else
	echo "$1: File type not recognised"
	exit 1
fi
```

The script is intended to be run like this ...```
/path/to/script /path/to/unidentified_file /path/to/sort_destination
```
For example ...```
find /path/to/browser/cache -type f -exec /path/to/script {} /path/to/sort_destination \;
```


A few notes:[LIST]
[*]I figured not mangling your browser cache by renaming/deleting bits of it was safer, so my suggestion copies files, rather than moving (ie renaming) them.
[*]The **file** utility can identify files by MIME type, if you prefer.
[*]My script could do with some error handling. For instance, it doesn't check whether you have read access to source files ... or that they're even *files*.
[/LIST]

I hope that helps.

---

### Post by plantboy1 on 2008-11-15
Thanks!  That was just what I was looking for.  Just out of curiosity though, how do I change where it puts them?  That's no biggie though.

Thanks a lot, that was exactly what I was looking for!

---

### Post by Mardoct909 on 2008-11-15
Change "/path/to/sort_destination" to wherever it is you want it. Like "/home/USERNAME" would dump it in your home folder.

---

### Post by plantboy1 on 2008-11-16
I know that much, wasn't what I meant.  I figured out what I was trying to do though.  I may not know how to write scripts (yet, im learning) but I can tell basically what they do and how to modify them.

---

