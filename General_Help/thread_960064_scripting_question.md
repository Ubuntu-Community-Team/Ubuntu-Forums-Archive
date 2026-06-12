---
title: "scripting question"
date: 2008-10-27
forum: General Help
---

### Post by thestig_992 on 2008-10-27
i was about to write a script to convert one type of file to another using mplayer. I can use this normally in cli, but i want to be able to convert a file or every file in a folder to another file type.
The command that i normally use is this, the file extentions can be other things...
```
mplayer -dumpaudio nodame_theme.flv -dumpfile nodame_theme.mp3
```
I couldnt do this cause i realised i dont relly have the knowledge, and so i have a few questions.

1. how would i convert every file in a folder? I think i could use folder/* to 'select' the files, but then how would i name them when i write the new folder?

2. Can i tell the script to wait for an input, so that i can use that as the convert to file extension?

3. Is it possible/difficult to write a nautilus script so i can right click a file and say convert, followed by a popup box asking what to convert it to...?

---

### Post by ad_267 on 2008-10-27
It's better to take the extension as a parameter. Eg: "mediaconvert inext outext"

Here's an example script that does this and only selects files in a folder that have a certain extension:

```
#!/bin/bash

if [ $# -ne 2 ]; then
    echo "Usage: mediaconvert input_extension output_extension"
    exit 1
fi

IFSBAK=$IFS
IFS=$'\n'

for file in `ls *.$1`; do
    filebasename=`basename "$file" ".$1"`
    mplayer -dumpaudio "$file" -dumpfile "$filebasename.$2"
done

IFS=$IFSBAK

```

The "IFSBAK=$IFS, IFS=$'\n'" part is so that the for loop separates the ls output at new lines rather than spaces.

If you want to read in user input you could use read:
```
read -e EXTENSION
```

No it wouldn't be difficult to do this with a nautilus script. You could use this to get the extension:

```
EXTENSION=`zenity --entry --title="Convert Script" --text="What file type do you want to convert to?"`
```

Note the "`" are backticks, not single quotes.

---

### Post by ad_267 on 2008-10-27
Here's a nautilus script to do it:
```
#!/bin/bash

# Separate list with newline rather than spaces
IFSBAK=$IFS
IFS=$'\n'

EXTENSION=`zenity --entry --title="Convert Script" --text="What file type do you want to convert to?"`

for NAUTILUS_SCRIPT_SELECTED_FILE_PATHS; do
    # If a file
    if [ -f "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
        # Get file name minus extension
        FILEBASENAME=`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" | awk -F . '{print $1}'`
        # Convert file
        mplayer -dumpaudio "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" \
            -dumpfile "$FILEBASENAME.$EXTENSION"
    #
    # If a directory
    elif [ -d "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS" ]; then
        for FILE in `ls "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"`; do
            FILEBASENAME=`echo "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/$FILE"|awk -F . '{print $1}'`
            mplayer -dumpaudio "$NAUTILUS_SCRIPT_SELECTED_FILE_PATHS/$FILE" \
                -dumpfile "$FILEBASENAME.$EXTENSION"
        done
    fi
done

IFS=$IFSBAK

```

Hopefully that's pretty self explanatory and you can adapt it to do what you want.

There's some good tutorials on writing shell scripts at [http://linuxcommand.org/writing_shell_scripts.php](http://linuxcommand.org/writing_shell_scripts.php)
This explains nautilus scripts: [http://www.linux.com/feature/114134](http://www.linux.com/feature/114134)

---

### Post by thestig_992 on 2008-10-27
thanks, ill give it a try. I dont really have much clue whats going on, I dont really know much about scripts...

To make this a nautilus script do i have to save it in a special folder,? or just in bin/bash?

UPDATE: found it in /home/(username)/.gnome2/nautilus-scripts

---

### Post by thestig_992 on 2008-10-27
wow that fantastic, even more than what i wanted. Im gonna go research this now, but i was wondering if its possible to make a checkbox asking whether to delete the original (maybe doing so after running the conversion and making sur there are no errors?)

I take it that you used zenity to create the box? (Im not even close to learning any gui programming XD)

Added in this to the end of the script, its not perfect, but it will do for me...

```
DELETE=`zenity --question="Delete?" --text="Delete Original? This may cause data loss in case of an error."; echo $?`
if [ $DELETE -eq 0 ]; then
	rm $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS
fi
```

---

### Post by ad_267 on 2008-10-27
Yeah Zenity is quite good for small things like this but it can only really do one thing at once. If you want a more complicated gui then you could use something like glade to build the interface and python with gtk. There's a tutorial at [http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html](http://www.micahcarrick.com/12-24-2007/gtk-glade-tutorial-part-1.html) which is quite good.

---

### Post by thestig_992 on 2008-10-28
hmmm...looks interesting, ill bookmark for later XD

TY for all ur help

---

