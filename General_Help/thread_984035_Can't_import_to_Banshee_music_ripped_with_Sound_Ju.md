---
title: "Can't import to Banshee music ripped with Sound Juicer"
date: 2008-11-16
forum: General Help
---

### Post by wersdaluv on 2008-11-16
I ripped my music from my 2 new CDs with Sound Juicer. For some reason, I can't import them to Banshee. I get error messages saying the file locations of my songs on .oga format then "(taglib/oga)" like ```
[Error 22:40:20.290] /home/user/Music/Razorback/Hebigat Sounds Volume One/06 - Giyang.oga - /home/user/Music/Razorback/Hebigat Sounds Volume One/06 - Giyang.oga (taglib/oga)

```.

I can import them to Rhythmbox though. Another problem is that I can't see the songs on ExFalso. I guess, the problem really is with tags.

Any idea? :)

---

### Post by wersdaluv on 2008-11-17
Bomppydoodledoo

---

### Post by Jay_Bee on 2008-11-17
I had the same problem...
Bashee doesn't recognize the .oga extension, you will need to rename all .oga files to .ogg...

Edit:
To rename all oga files to ogg in one folder you can use this command
```
for file in *.oga; do mv "${file}" "${file/.oga/.ogg}"; done
```

---

### Post by starcannon on 2008-11-17
Heres some more advise in addition to Jay_Bee's advice:

[LIST]
[*]nature abhores a vacuum, and so does linux, don't use spaces in directory or file names (you can use spaces, but then you'll also have to learn how to use quotes in the filesystem, easier to just not use spaces)
[*]Ripperx is probably in my opinion the best ripper out there, bar none, regardless of OS. If you ever used CDex its like that only a little nicer (install it from synaptic grab lame as well)
[/LIST]
GL and have fun.

---

### Post by wersdaluv on 2008-11-17
Sweet. Thanks guys :D I used krename instead. Haha. GUI kid

---

### Post by Keith_Beef on 2008-11-17
> **Jay_Bee said:**
> I had the same problem...
Bashee doesn't recognize the .oga extension, you will need to rename all .oga files to .ogg...

Edit:
To rename all oga files to ogg in one folder you can use this command
```
for file in *.oga; do mv "${file}" "${file/.oga/.ogg}"; done
```

That's a great tip for renaming! For the last ten years, I've been using echo piped to cut to strip off the stem from the suffix; your way is much more elegant.

The question remains... why did the suffix of Ogg Vorbis audio files change from .ogg to .oga between Hardy and Intrepid? I've been using SoundJuicer for a little over a year, and all ways got .ogg files until now.

If I look at the profile named "CD Quality, Lossy", I see:
```
audio/x-raw-float,rate=44100,channels=2 ! vorbisenc name=enc quality=0.5 ! oggmux
```
which looks (from memory) just like the profile that previously generated .ogg suffixed files.

Is the only difference in the "file extension" (as SoundJuicer calls it)?

K.

---

### Post by ablewisuk on 2009-04-12
In case this is useful for someone: if you have .oga files in subdirectories, to rename recursively in all subdirectories of the current directory run

```

find . -type f | grep "\.oga" | while read ogafile; do mv "${ogafile}" "${ogafile/.oga/.ogg}"; done

```

Andrew

---

