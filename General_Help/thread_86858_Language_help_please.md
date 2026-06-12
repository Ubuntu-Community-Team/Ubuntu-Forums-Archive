---
title: "Language help please"
date: 2005-11-06
forum: General Help
---

### Post by mikwig on 2005-11-06
I am an Australian who has a collection of Koreaan music CDs.
I installed my ubuntu desktop in korean and have full korean 
supports it seemed until I tried to play a disk. All cd and track
names are screwed up.

any hints?

---

### Post by pickarooney on 2005-11-06
What program are you playing them in? It most likely has no non-European character support.

---

### Post by mikwig on 2005-11-06
[QUOTE=pickarooney]What program are you playing them in? It most likely has no non-European character support.[/QUOTE]

I have tried rhythmbox, amarok, grip, sound juicer, xine and madcow.
I checked out the freedb website, they say there is only utf-8 there.
All of my programs are already set to utf-8. I think I will just have to use a 
tag editer - and redo it all

---

### Post by pickarooney on 2005-11-06
If you've loads to be done manually, I'd say there's a script that can be put together to auto-tag them.

As a matter of interest, try installing **id3ed** via apt-get and then running this from the command line:

/usr/bin/id3ed -i <filename>

and see if the tag displays in Korean in a terminal.

---

### Post by mikwig on 2005-11-09
[QUOTE=pickarooney]If you've loads to be done manually, I'd say there's a script that can be put together to auto-tag them.

As a matter of interest, try installing **id3ed** via apt-get and then running this from the command line:

/usr/bin/id3ed -i <filename>

and see if the tag displays in Korean in a terminal.[/QUOTE]

No it doesn't display korean in the terminal, the files names show as korean but
not the tags. I checked in windows though, and they are working.

I hate when windows out-does ubuntu - but it happen sometimes

---

### Post by pickarooney on 2005-11-09
I'm not really sure what kind of settings are needed to display the characters properly. The system seems to be able to display them, but not recognise the encoding properly...

Maybe try running this script on an MP3 file. It uses the id3 tag to rename the file. Let me know if the filename becomes garbled after running it.

```

#!/bin/bash

if [ $# -lt 1 ]; then
  echo ""
  echo "Usage: id3name <mp3file>"
  exit
fi

artist=`/usr/bin/id3ed -i "$1"|grep "artist:"|sed s'/\//+/'g|cut -c9-100`
songname=`/usr/bin/id3ed -i "$1"|grep "songname:"|sed s'/\//+/'g|cut -c11-100`

if [ "$artist" == "" ]
then 
  echo "unknown artist"
  echo "$1" >>unknown.lst
  exit
fi

if [ "$songname" == "" ]
then
  echo "unknown songname"
  echo "$1" >>unknown.lst
  exit
fi

newname=`echo "$artist - $songname.mp3"`

echo "$1 will be renamed to $newname"
if [ ! -f "$newname" ]
then
  mv "$1" "$newname" 
fi	

```

Then make a copy of an mp3 file, rename it as **artistname_songname** and run the following on it:

```

artist=`echo **yourfilename.mp3** |cut -f1 -d_`
song=`echo **yourfilename.mp3** |cut -f2 -d_`
id3ed -s $song -n $artist -q **yourfilename.mp3**

```

If the second script works, and there's very little guarantee that it will, you can put the code in a loop to rename all your music files with readable Korean tags.

If not, maybe you can attach a file and let me play around with it?

---

### Post by mikwig on 2005-11-09
Neither script worked - but I have figured it out:

freedb.freedb.org - has recieved some corrupt korean
file names - and my programs keep updating the tags- 
even if I manually set them - they change.

I am still however stumped - thankyou for all of your
help so far though - I am fairly new to messing with
mulimedia.

---

