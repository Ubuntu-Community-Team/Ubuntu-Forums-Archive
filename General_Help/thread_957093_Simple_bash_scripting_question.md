---
title: "Simple bash scripting question"
date: 2008-10-23
forum: General Help
---

### Post by beowulf62381 on 2008-10-23
I am trying to write a script to transcode some videos, But since I have no idea how to write a script I am having some difficulties.

OK the crux of my problem is this
If OUTDIR is /home/$USER/Desktop/vids/
and INPUT is uTube/flash.flv
how can I make OUTPUT=/home/$USER/Desktop/vids/flash.avi
and not OUTPUT=/home/$USER/Desktop/vids/uTube/flash.avi

```
OUTPUT="$OUTDIR/${INPUT%%\.???}.avi"
```

the script in full looks like this

```
#/bin/sh
###Start of Personal Settings###
#Set the output directory you want your finshed videos in
OUTDIR="/home/$USER/Desktop/vids"

#Set the Resolution you would like to encode at
RES=320:240
#Set bitrate in kb/s
BTR="-800"
###End of Personal Settings###

#Check to see if you have given us files to work with.
if [ -z "$1" ]; then
		echo "Usage: $0 file_2_convert"
		echo "    Or to convert all files in a directory"
		echo "Usage: $0 -d directory_name"
		exit 1
fi

#Check to see if we have an output directory and create one if we do not
 if [ -d /home/$USER/Desktop/Vids ]; then
		echo "~/Desktop/Vids directory exists - using for output"
	else
		echo "$OUTDIR not found - creating and using for output"
		mkdir -p "$OUTDIR"
 fi

### List of internal functions ###
function ENCODE {
	mencoder $INPUT -vf scale=$RES -ovc xvid -oac mp3lame -xvidencopts pass=1 -o /dev/null
	mencoder $INPUT -vf scale=$RES -ovc xvid -oac mp3lame -xvidencopts pass=2:bitrate=$BTR -o $OUTPUT
	rm divx2pass.log
}

function TEST {
	echo "Input is $INPUT"
	echo "Output is $OUTPUT"
}

### End List ###
#Check to see if any swiches where used
if [ "$1" = "-d" ]; then
		for INPUT in `find $2 -name *.???`
		do
		  OUTPUT="$OUTDIR/${INPUT%%\.???}.avi"
		  TEST
		done
	else
		INPUT="$1"
		OUTPUT="$OUTDIR/${INPUT%%\.???}.avi"
		ENCODE
fi
```

---

### Post by geirha on 2008-10-24
The basename command will strip away all leading directory components from the pathname.

```
OUTPUT="$OUTDIR/`basename "${INPUT/%.???/.avi}"`"
```

Your script will not work on paths with spaces in them btw. Replacing the `find ...` with "$2"/*.??? and always quoting variables containing path names should help on that, though replacing the find that way will not make it recursive.

EDIT: BTW, you should post shell scripting questions in the Development & Programming -> Programming Talk forum. You are likely to get a quicker response there.

---

### Post by beowulf62381 on 2008-10-24
Thank you for you help that did just what I wanted.

---

