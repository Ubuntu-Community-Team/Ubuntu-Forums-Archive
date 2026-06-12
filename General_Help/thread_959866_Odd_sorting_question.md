---
title: "Odd sorting question"
date: 2008-10-26
forum: General Help
---

### Post by DuplexEmotions on 2008-10-26
Okay, here's the dilly-o.

I have a bunch of files here (music files in several formats) with names like  "02 - song title.mp3" and "song title.flac" and "02 - Different Song.mp3". I'd like to put these on my MP3 player (a sansa e260, works like a flash drive) as a custom sorted folder so I can play the songs in a particular order.

What it comes down to is this: I'd like to take this big folder of files and slide them around to the order I want, then batch rename them to 01.mp3 , 02.m4a , 03.flac , etc. That way when I sort them by name they're in the order that I want to play them in.

Is there any program anybody can think of that will do that for me? If not, I'll do it all by hand. It's just a pain since these are custom playlists for work and each one has 20+ songs on it.

Thanks!

DEmo

---

### Post by geirha on 2008-10-26
Make a simple playlist. For example by doing ```
ls >playlist
``` editing the playlist-file to put them in the order you want, then something like this script should copy them to the pmp:

```
#!/bin/bash

musicfolder="$HOME/Music"      # Path to the folder with the music
playlist="/path/to/playlist"   # Path to the file with list of filenames
pmp="/media/sansa"             # Path to the portable media player

i=0
while read filename; do
  extension="${filename##*.}"
  destination=$(printf "$pmp/%02d.$extension" $i)
  cp -v "$musicfolder/$filename" "$destination"
  ((i++)) 
done < "$playlist"

```

---

### Post by DuplexEmotions on 2008-10-26
Thanks! That worked like a charm would work if charms did work. What I mean to say is, once I finagled with the basic settings on it, it works perfectly. Thanks a bunch!

DEmo

---

