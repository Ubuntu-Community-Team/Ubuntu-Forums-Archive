---
title: "Help on script with zenity"
date: 2008-11-09
forum: General Help
---

### Post by globalenigma on 2008-11-09
I want to create a script for nautilus that will move all files I have selected into a folder that is created from the beginning of the file name untill it hits a number.

For example I have files:
picture01.jpg
picture50.jpg
picture100.jpg
picture150.jpg

I want to select all those files right click "SendtoFolder" and it will create a folder in current dir named picture and move all the files to it.

Thank you in advance if you can help.

The only thing I can come up with is a modded form of a copy script, thanks to moment, but I created it to manually type in the name every time. (this is getting old)



```
#! /bin/bash
# Create a folder and move files to that folder
location=`zenity --entry --text "Enter folder name" --entry-text "New Folder"`
mkdir $location
for arg
do
if [ -e "$location/$arg" ]; then
zenity --question --title="Conflict While Copying" --text="File $location/$arg already exists. Would you like to replace it?"
if [ "$?" = 1 ]; then
exit 1
fi
fi
mv -f "$arg" "$location" &
ORIG_SIZE=`du -bs "$arg"|awk '{print $1}'`
MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`

(
while [ $MV_SIZE -ne $ORIG_SIZE ]; do
expr `expr $MV_SIZE \* 100` / $ORIG_SIZE
MV_SIZE=`du -bs "$location/$arg"|awk '{print $1}'`
done
echo 100
)| zenity --progress --auto-close --text "Copying \"$arg\"..."

done

```

---

### Post by globalenigma on 2008-11-11
Came up with something that better fit my needs that does not need my interaction with gui.

```
#!/bin/sh
#Script to copy multiple image files into a directory
#based off of the filename preceding a 0 in the name.
#ex. mv image001.jpg image010.jpg image020.jpg to dir image

for FNAME in $( ls *.jpg ); do
    DNAME=`echo "$FNAME" | cut -d 0 -f1`

    if [ -d $DNAME ]; then
        echo "Directory exists, Copying File $FNAME"
        mv $FNAME $DNAME
    else
        mkdir -p $DNAME
        echo "$DNAME created successfully, Copying File $FNAME"
        mv $FNAME $DNAME
    fi
done
```

If anyone has a better idea please let me know.  I am new at scripting.

---

### Post by -Zeus- on 2008-11-11
```
#!/bin/sh
#Script to copy multiple image files into a directory
#based off of the filename preceding a 0 in the name.
#ex. mv image001.jpg image010.jpg image020.jpg to dir image
ls *.jpg | while read FNAME; do
    DNAME=$(echo "$FNAME" | cut -d 0 -f1)

    if [ -d "$DNAME" ]; then
        echo "Directory exists, Copying File $FNAME"
    else
        mkdir -p "$DNAME" || (echo "Failed to make directory $DNAME, exiting"; exit 1)
        echo "$DNAME created successfully, Copying File $FNAME"
    fi
    mv "$FNAME" "$DNAME" || (echo "Failed to move $FNAME to $DNAME, exiting"; exit 1)
done
```

I changed the for to a while (reads better), added "" around all variables, changed use of ` to $(, added exit 1 if directory could not be created/moved, and condensed if statement by putting mv outside (was executed in both states).

Overall, a very nice script!

---

### Post by globalenigma on 2008-11-11
Thanks for all of your help and quick reply, I changed one thing to make it cut all after any number.  I dont know why I just did not do this before.  Thanks again:

revised
```
#!/bin/sh
#Script to copy multiple image files into a directory based
#off of the filename preceding any number in the name.
#ex. mv image001.jpg image010.jpg image100.jpg to dir image
ls *.jpg | while read FNAME; do
    DNAME=`echo "$FNAME" | sed -e 's/[0-9].*//'`

    if [ -d "$DNAME" ]; then
        echo "Directory exists, Copying File $FNAME"
    else
        mkdir -p "$DNAME" || (echo "Failed to make directory $DNAME, exiting"; exit 1)
        echo "$DNAME created successfully, Copying File $FNAME"
    fi
    mv "$FNAME" "$DNAME" || (echo "Failed to move $FNAME to $DNAME, exiting"; exit 1)
done
```

---

### Post by -Zeus- on 2008-11-11
> **globalenigma said:**
> Thanks for all of your help and quick reply, I changed one thing to make it cut all after any number.  I dont know why I just did not do this before.  Thanks again:

revised
```
#!/bin/sh
#Script to copy multiple image files into a directory based
#off of the filename preceding any number in the name.
#ex. mv image001.jpg image010.jpg image100.jpg to dir image
ls *.jpg | while read FNAME; do
    DNAME=`echo "$FNAME" | sed -e 's/[0-9].*//'`

    if [ -d "$DNAME" ]; then
        echo "Directory exists, Copying File $FNAME"
    else
        mkdir -p "$DNAME" || (echo "Failed to make directory $DNAME, exiting"; exit 1)
        echo "$DNAME created successfully, Copying File $FNAME"
    fi
    mv "$FNAME" "$DNAME" || (echo "Failed to move $FNAME to $DNAME, exiting"; exit 1)
done
```

great, except you changed the $() back to ``:)

---

### Post by globalenigma on 2008-11-11
Wow I am a tard, I also noticed one other thing.  I have copying but I am moving.

---

### Post by -Zeus- on 2008-11-11
I'm curious, why are you using ```
       -e script, --expression=script
              add the script to the commands to be executed
```

---

### Post by geirha on 2008-11-13
Iterating on the output of ls is bad practice; the shell handles this much better itself, so no need to use an external command for that. The shell can also do the job sed is doing here.

```

for file in *.jpg; do
  dir="${file%%[0-9]*}"
  [ -d "$dir" ] || mkdir -v "$dir" || exit 1
  mv -v "$file" "$dir" || exit 1
done

```

---

