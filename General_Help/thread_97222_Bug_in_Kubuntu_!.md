---
title: "Bug in Kubuntu !"
date: 2005-11-30
forum: General Help
---

### Post by infoseeker on 2005-11-30
Just found a bug in Kubuntu/KDE : 
Step 1 : right click desktop 
Step 2 : select 'create new' --> 'text file' 
Step 3 : enter filename eg. 'crashtest' and select 'ok' (saves as text file)
Step 4 : Open the newly created text file (opens with Kate on mine) 
Step 5 : enter 'top' on line 1 and 'free' on line 2
>  top
free  
Step 6 : save the file

THE FILE IS THEN SAVED BUT KDE SEES IT AS A QUICKTIME VIDEO :confused:  . DO NOT ATTEMPT TO OPEN THE FILE...NOATUN, FOR ONE, GOES BANANAS!

---

### Post by aysiu on 2005-11-30
Save the file?
As what?
What extension did you give it?

---

### Post by infoseeker on 2005-11-30
I did not enter an extension....just saved it.

---

### Post by aysiu on 2005-11-30
[QUOTE=infoseeker]I did not enter an extension....just saved it.[/QUOTE] Every file has an extension, whether you write it in there or not. If it doesn't, maybe you have your settings to open all non-extensioned files with Noatun.

---

### Post by noigeaR on 2005-11-30
tried this and can reproduce it.
create new text file on the desktop, open with kate, then add
```
top free and random text blabla
```
save the file and it shows as a quicktime file on the desktop and if you click it the player associated with quicktime files (kaffeine for me) wants to open it and crashes.
some things i've noticed:
-after the word free you can write random text, the file is still recognized as quicktime file. you can write "top freeblablabla" and it's still recognized as a quicktime file.
-you can write "top free" with space or return between top and free or "top.free" or "top-free" or "top,free" **but** if you write "topafree" or "top--free" (a letter or more than one character or space between top and free) the file is handled as simple textfile, not as quicktime, and it will be opened with kate when clicked.
-if you name the file test.txt it's always handled as text file, if you name it test.jpg it's handled as jpeg file, if you name it test.bla or test.foo or some different non-existing extension, then it's handled as quicktime.

i think that's more a kde problem than a kubuntu problem. i think that when the extension is missing from a filename, kde tries to find out from the header (the first few bytes of a file) what kind of filetype the file actually is and quicktime files probably start with "top free" or something so kde thinks the file is a quicktime movie.

---

### Post by vh1 on 2005-11-30
[QUOTE=noigeaR]i think that when the extension is missing from a filename, kde tries to find out from the header (the first few bytes of a file) what kind of filetype the file actually is and quicktime files probably start with "top free" or something so kde thinks the file is a quicktime movie.[/QUOTE]
bingo

but to extend on what you said, it's not when there is no extension, but when KDE sees an extension it doesn't reckognize. which can either be a file with no extension, or a filetype you haven't come across before

---

### Post by Alpha_toxic on 2005-11-30
This reminds me of sth. It's out of topic, but...
As I recall in Win it's not possible to name a directory [COLOR="Red"]con[/COLOR]. On some versions it gives a warning, on others just doesn't do anything, and I think on older ones (98,95) it actually crashed. Another was typing [COLOR="#ff0000"]con/con[/COLOR] in the Start->Run menu. I suppose it was recognised as trying to open a console inside a console and it also crashed. LOL!!! The second one is fixed in later vers, but the first is still here. LOL,LOL,LOL!!!
-------------------
I used to spend some quality time abusing Wins back then :twisted:

---

