---
title: "[SOLVED] Eliminating spaces in file names"
date: 2008-10-20
forum: General Help
---

### Post by jonathonblake on 2008-10-20
I'm trying to run the script

```

#!/bin/bash
for f in *.mp3; do ffmpeg -i "$f" -acodec wmav2 -ab 128k "${f%.mp3}.wma"; done

```

However, it fails, because all of the file names are of the form "book chapter.mp3".  Since I have 1130 of these to change, I'd prefer not to do them individually.  (Actually, I have 1130 times 3 to convert to wma, from mp3.) 

I tried 
```

cp "book chapter.mp3"  book_chapter.mp3
```
but that failed with an error message* of book_chapter.mp3 is not a directory*.  :(

Trying
```
cp book\ chapter.mp3  book_chapter.mp3 
```
my error message was *cp: cannot stat `Galations 06.mp3': No such file or directory*

[http://ubuntuforums.org/showthread.php?t=368708&highlight=remove+spaces+filename](http://ubuntuforums.org/showthread.php?t=368708&highlight=remove+spaces+filename)   had the suggestion ```
for i in *.mp3; do mv -i "$i" "${i// }"; done

```
That deleted the content of the files.  :( :(

```

# Test it out by using the -n option
rename -n 's/ //g' "filename with spaces"
# Same thing but with globbing:
rename -n 's/ //g' *.ext

```
had the same result.  :(

###
For those who are wondering, the purported mp3 player I have only plays WMA.  All of the public domain audio Bibles I could find are in mp3 format. Eventually I'll put in the 1,500 hours that are required to create a new good quality audio Bible.  

xan

jonathon

---

### Post by sisco311 on 2008-10-20
replace *.ext with the extention of the file(in your case *.mp3)

or try a gui application, for example krename, gprename or thunar file manager.

or try this script:
```
#!/bin/bash
IFS=$'\t\n'
for f in *.mp3; do ffmpeg -i "$f" -acodec wmav2 -ab 128k "${f%.mp3}.wma"; done
```
[http://ubuntuforums.org/showthread.php?t=824489]("http://ubuntuforums.org/showthread.php?t=824489")

---

### Post by jonathonblake on 2008-10-20
> **sisco311 said:**
> 
or try a gui application, for example krename, gprename or thunar file manager.

gprename converted the names correctly.  :)

And the shell script I was using to convert from mp3 to wma works properly, now.  :)

xan

jonathon

---

### Post by sisco311 on 2008-10-21
Cool!

Please mark the thread solved by selecting 
**Mark this thread as solved** from the [COLOR="Red"]**Thread Tools**[/COLOR].

---

