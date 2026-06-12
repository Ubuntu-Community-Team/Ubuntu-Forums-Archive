---
title: "shell script to use ID3tags for file name."
date: 2008-09-05
forum: General Help
---

### Post by rentacop on 2008-09-05
Hey guys, I am new to writing shell scripts so i have a few questions to get started. 

Heres what i would like to do. I would like to write a script that would browse though a directory of my unorganized mp3's and grab the id3 info from each song. Once i have gotten the info from each song, i would like to move the song to a directory created by the script. 

IE: current directory : song.mp3 ( ID3 : arist:TheBeets :album:Doug:song:killerTofu; )

moved to

IE: new dir : music/$ARTIST/$ALBUM/$song.mp3 

I downloaded id3v2 from the respos. Its used like so

```
id3v2 -l song.mp3
```

its output looks something like this

```
Title  : test                            Artist:test                          
Album  : test                            Year: test, Genre: Unknown (255)
Comment: test                            Track: 1

```

Is there anyway that i can run the command from the script and store the output in a variable so i can easily create directory's?

Any help / examples would be great!

Thanks
-rent

---

### Post by rentacop on 2008-09-05
Figured it out!

var=`id3v2 -l`

Thanks though!

---

