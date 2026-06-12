---
title: "this should be a simple script. mp3 - ogg"
date: 2008-09-14
forum: General Help
---

### Post by jakupl on 2008-09-14
I like to convert my mp3 to ogg, when I get new music. For this i use a CLI program called SOX. But it is a pain to convert entire cd's.
for instance, i had to write this in terminal to convert a Rage Against the Machine cd - it takes a while.

```
sox 01\ Microphone\ Fiend.mp3 01\ Microphone\ Fiend.ogg && 
sox 02\ Pistol\ Grip\ Pump.mp3 02\ Pistol\ Grip\ Pump.ogg && 
sox 03\ Kick\ out\ the\ Jams.mp3 03\ Kick\ out\ the\ Jams.ogg && 
sox 04\ Renegades\ of\ Funk.mp3 04\ Renegades\ of\ Funk.ogg && 
sox 05\ Beautiful\ World.mp3 05\ Beautiful\ World.ogg && 
sox 06\ I\'m\ Housin\'.mp3 06\ I\'m\ Housin\'.ogg && 
sox 07\ In\ My\ Eyes.mp3 07\ In\ My\ Eyes.ogg && 
sox 08\ How\ I\ Could\ Just\ Kill\ a\ Man.mp3 08\ How\ I\ Could\ Just\ Kill\ a\ Man.ogg && 
sox 09\ The\ Ghost\ of\ Tom\ Joad.mp3 09\ The\ Ghost\ of\ Tom\ Joad.ogg && 
sox 10\ Down\ on\ the\ Street.mp3 10\ Down\ on\ the\ Street.ogg && 
sox 11\ Street\ Fighting\ Man.mp3 11\ Street\ Fighting\ Man.ogg && 
sox 12\ Maggie\'s\ Farm.mp3 12\ Maggie\'s\ Farm.ogg && 
sox 13\ Kick\ Out\ the\ Jams.mp3 13\ Kick\ Out\ the\ Jams.ogg && 
sox 14\ How\ I\ Could\ Just\ Kill\ a\ Man.mp3 14\ How\ I\ Could\ Just\ Kill\ a\ Man.ogg && 
rm *.mp3
```

If I write for instance

```
sox *.mp3 *.ogg
```

then all the mp3's in the current folder get converted (yey) to ogg, but they also become one long song, simply called "*.ogg".

Is there a way to make a simple script to make this easier, where all songs get to keep their names?
and recursive if possible?

---

### Post by gaussian on 2008-09-14
This might have mistakes, test it on a copy of your directory. It is also not very elegant:
```

for x in *.mp3; do sox $x $x.ogg;done

```

This should create filenames song.mp3.ogg. To rename them do (I hope this is right):

```

rename 's/\.mp3\.ogg/\.ogg/' *.mp3.ogg

```

---

### Post by Raffles10 on 2008-09-14
Is there any particular reason why you want to do it this way ?

There are many simple GUI apps that can transcode quickly and easily.

[Sound Converter]("http://soundconverter.berlios.de/") will do it, but you probably know that already, why use cli if takes longer and is more difficult ?

---

### Post by jakupl on 2008-09-14
I think it gets confused by the names of the songs.
I just tried it in a directory containing 

01  Damien Rice - 9 Crimes.mp3  
02  Damien Rice - The Animals Were Gone.mp3  
03  Damien Rice - Elephant.mp3

and I get this:

```
sox soxio: Can't open input file `9': No such file or directory
sox soxio: Can't open input file `Were': No such file or directory
sox soxio: Failed reading `-': unknown file type

```

---

### Post by gaussian on 2008-09-14
Ok, it is the spaces in names causing the problems. Try the following:
```

for x in *.mp3; do sox "$x" "$x".ogg;done

```

---

### Post by jakupl on 2008-09-14
> **Raffles10 said:**
> Is there any particular reason why you want to do it this way ?

There are many simple GUI apps that can transcode quickly and easily.

[Sound Converter]("http://soundconverter.berlios.de/") will do it, but you probably know that already, why use cli if takes longer and is more difficult ?

Yeah.. I could.
I dont know. I guess i really like the cli, so i prefer it to gui now and then, but when there is something hard to do, I sometimes forget the nice gui programs. No I did not know that program.


But then, I would really like to become more familliar with loops... so this is a great way of finding out how it can be done.

---

### Post by NoReflex on 2008-09-14
You can try looping through all the files in a directory. Copy all your mp3 files in a folder (like /home/username/convert) and then create a small script like this : 
```
#!/bin/sh
for f in `ls ~/convert/`
do
echo &#8220;Processing $f file &#8230;&#8221;
sox "$f" `echo "$f" | sed 's/\(.*\.\)mp3/\1ogg/'`
done
```

Make sure you don't have any other files or directories ~/convert folder, otherwise sox will probably issue some errors (like "Is a directory" or "Unknown file format" etc.).

Best wishes,
NoReflex

---

### Post by mali2297 on 2008-09-14
In one line..
```

for i in *.ogg; do sox -V3 "$i" "`echo $i | sed 's/.ogg/.mp3/g'`"; done

```

---

