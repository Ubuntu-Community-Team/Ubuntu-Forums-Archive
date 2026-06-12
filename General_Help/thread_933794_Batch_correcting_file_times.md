---
title: "Batch correcting file times?"
date: 2008-09-29
forum: General Help
---

### Post by alexgieg on 2008-09-29
I've recently copied a LOT of files from many old backup CD-Rs to my home folder using "cp -fRv /cdrom/* ." (where "." is a distinct folder for each CD-R inside my backups folder) . Hours later, task completed, I noticed all the copied files had the current date and time instead of the original ones. Yes, my mistake: I forgot to add "-p" to the cp command.

My question then is: what's the correct way for me to automatically correct the three date/times (creation, modification and last access) for all of these files without having to copy everything again? I've looked man pages around but bash scripting is still kind of esoteric for me, and I have no idea how to proceed.

Ideally, I'd like to type something like "./correctdates.sh ./foldername", and have the script do this for each file and folder inside ./foldername/*: if there's a "/home/alexgieg/Backup/foldername/a/b/file.txt" file, check whether there's also a "/cdrom/a/b/file.txt" too (notice "a/b/file.txt" is equal in both), and if there is (that's not guaranteed), read the three dates from the /cdrom one and apply them to the /home/alexgieg/Backup one. This way I could put the first CD in the drive, type the command, done; put the second CD, type the command, done; put the third... and so on and so forth, until all of them are processed.

So far I have the impression I'd have to use "find", "xargs" and "touch" inside a complex series of "if"s and loops, but I really don't know how to place everything together.

Any help is most welcome!

---

### Post by alexgieg on 2008-10-04
Well, no one replied, but after reading lots of tutorials and man pages, I finally figured it out. Nothing like a need to prompt some learning. :)

Here's my script. Pretty rough, without any advanced feature and almost zero intelligence, but it does the job:

```
#!/bin/bash

DIR=`pwd`
if [ "$DIR" = "/home/(username)/Backups" ]; then exit 1; fi

ifs="$IFS"
IFS='\
'

for FILE in `find . -depth -printf "\"%p\"\n"`
do
  if [ "$FILE" != "\".\"" ]
  then
    NAMELEN=$(( ${#FILE} - 4 ))
    FILE="${FILE:3:$NAMELEN}"
    CDFILE="/media/cdrom/$FILE"
    if [ -e "$CDFILE" ]
    then
      echo "touch -c -r \"$CDFILE\" ..."
      # read -p "Press Enter to continue..."
      touch -c -r "$CDFILE" "./$FILE"
    else
      echo "Error: \"$CDFILE\" doesn't exist!" >> /dev/stderr
    fi
  else
    echo "touch -c -r \"/media/cdrom\" ..."
    # read -p "Press Enter to continue..."
    touch -c -r "/media/cdrom" "."
  fi
done

IFS="$ifs"

echo "Done!"
exit 0
```

Usage: Place it at /home/(username)/Backups (edit the "username" and folder according to your system) as "correctdates.sh"; "cd" into a subdirectory containing files from a CD that you copied with the incorrect parameters; insert the CD; type "../correctdates.sh"; wait for the dates to be corrected; done.

PS.: Don't try running it from anywhere other than a subdirectory from your backups folder. It can cause nasty thing to your system if you do.

---

