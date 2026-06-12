---
title: "[SOLVED] Script for editing id3 tag"
date: 2008-07-17
forum: General Help
---

### Post by nisde on 2008-07-17
I'm new to ubuntu and I would like to know if there is a way to edit the id3 tags of all my mp3 files. They are organized like this:

./Artist Name/Album Name/Track Number - Track Name.mp3

Is it possible to make a script that will edit for each file the information for track name, track number, album name and artist name?

Thanks
best regards
Denis

---

### Post by apswartz on 2008-07-17
Do you know much about writing scripts? The command line utility that will do the job is mid3v2, see...

```
man mid3v2
```

for instructions on using the command. You will need to write a script lists all of the filenames in the directory and then acts on the files one by one. Extracting information from the directories is possible (see pwd), but not easy.

The script would work/look something like this...

```
#!/bin/sh

TEMPLIST=/tmp/tempfile.`date +%s`_$RANDOM
ls -- *.mp3  >$TEMPLIST 2>/dev/null

while read FileFromList
   do
      command to extract information from path, e.g., pwd
      command to extract track number and title from file
      mid3v2 with the necessary options to write the tags
   done < $TEMPLIST

rm -f $TEMPLIST
```

That's just a start.

---

### Post by apswartz on 2008-07-18
You will want to look at sed and awk...

```
man sed
man awk
```

---

### Post by ramjet_1953 on 2008-07-18
If you would like a GUI editor for your music files [COLOR="Blue"]EasyTag[/COLOR] is very good.

To install it, just type this into a terminal screen.

[COLOR="Red"]sudo apt-get install easytag[/COLOR]

Here's the SourceForge website, if you would like to check out screenshots, documentation, etc.:

[http://easytag.sourceforge.net/](http://easytag.sourceforge.net/)

Regards,
Roger :cool:

---

### Post by nisde on 2008-07-19
This shellscript worked for me. I used the id3v2 command to edit the tags

```

#!/bin/bash

for i in *
do
    if test -d "$i"
    then
        pushd "$i"
        for j in *
        do
            if test -d "$j"
            then
		pushd "$j"
		if test -d CD1
		then
		    for kk in CD*
		    do
		    pushd "$kk"
		    for k in *.mp3
		    do
		        echo "$k" | \
		        awk -v Artist="$i" -v Album="${j}-${kk}" -v MusicFile="$k" -F"(.mp3| - )" '{ print "id3v2 -T \""$1"\" -t \""$2"\" -a \""Artist"\" -A \""Album"\" \""MusicFile"\"" }' | bash
		    done
		    popd
		    done
		else
		for k in *.mp3
		do
		    echo "$k" | \
		    awk -v Artist="$i" -v Album="$j" -v MusicFile="$k" -F"(.mp3| - )" '{ print "id3v2 -T \""$1"\" -t \""$2"\" -a \""Artist"\" -A \""Album"\" \""MusicFile"\"" }' | bash
		done
		fi
		popd
            fi
        done
        popd
    fi
done

```

I had to add a case because some of my albuns are double and in this case they are organized like this:

./Artist Name/Album Name/CD*/Track Number - Track Name.mp3

Thanks for everyone that helped.

---

### Post by apswartz on 2008-07-19
Wow! Great job!

---

