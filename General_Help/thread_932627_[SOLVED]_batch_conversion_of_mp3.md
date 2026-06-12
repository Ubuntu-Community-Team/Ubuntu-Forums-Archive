---
title: "[SOLVED] batch conversion of mp3"
date: 2008-09-28
forum: General Help
---

### Post by EvilRobotDrew on 2008-09-28
i have about 2 gigs of MP3's that i need to convert to WMA. i have installed ffmpeg and the command:

ffmpeg -i file1.mp3 file1.wma

seems to work. Is there an easy way to batch convert these files? soundconverter doesn't allow output of WMAs.

thx

---

### Post by mc4man on 2008-09-28
here's a basic way to do it, will convert in place so either adapt script to save else where or after done you could move or remove the.mp3's with a script or command.
I'd install nautilus-open-terminal first, makes it easy cd to folders (especially 'odd' named ones (or get paths for other uses

create a new text docu. in home directory, name it it whatever you want (I used convert
Paste this inside

```
#!/bin/bash
for f in *.mp3; do ffmpeg -i "$f" -acodec wmav2 -ab [COLOR="Red"]128[/COLOR]k "${f%.mp3}.wma"; done
```

then in terminal
```
 chmod +x convert
```

Then browse to your music folder, right click -> open in terminal
At the prompt use this
```
~/./convert
```

You can adjust the red to some extent (bitrate

thanks to Creative2 : logos34 for suggestions

[http://ubuntuforums.org/showthread.php?p=5440950](http://ubuntuforums.org/showthread.php?p=5440950)

Ex. to move or remove 
To remove (using the open in terminal to get prompt

> doug@doug-desktop:~/mp3/Otis Redding (1992) The Very Best Of Otis Redding$ rm *mp3

To move (created a folder first coping album name from open in terminal, also using open in terminal to open at prompt
> doug@doug-desktop:~/mp3/Otis Redding (1992) The Very Best Of Otis Redding$ mv *.mp3 ~/"Otis Redding (1992) The Very Best Of Otis Redding"

---

### Post by EvilRobotDrew on 2008-09-29
THANKS!

this works, thank you very much.

---

