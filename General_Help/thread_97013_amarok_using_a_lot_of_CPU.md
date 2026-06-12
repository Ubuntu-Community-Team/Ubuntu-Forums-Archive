---
title: "amarok using a lot of CPU"
date: 2005-11-30
forum: General Help
---

### Post by daedalusman on 2005-11-30
Amarok is using an unussual amount of processor power, around 30-40%. It does this whenever it is running, while playing, paused or stopped. Im using Gnome but I have used amarok in Gnome before without this problem, it use to use no more than a couple percent while playing, paused or stopped. Can anyone shed some light on this issue, I would like to resolve this so I can use amarok as it is the best audio player ever. Thanks

---

### Post by 23meg on 2005-11-30
Which version of amarok? Are any other KDE apps causing this? Do you get any error messages when you run amarok from terminal? Which audio engine are you using with it?

---

### Post by daedalusman on 2005-11-30
[QUOTE=23meg]Which version of amarok? Are any other KDE apps causing this? Do you get any error messages when you run amarok from terminal? Which audio engine are you using with it?[/QUOTE]


I'm using version 1.3.1. As far as I know I don't have any other KDE programs on my system, so no. I'm using the xine engine with alsa. And here is what I get when I run it from the terminal...

```
tyrion@HouseLannister:~$ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
QLayout: Adding KToolBar/mainToolBar (child of QVBox/unnamed) to layout for PlaylistWindow/PlaylistWindow
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
QColor::setRgb: RGB parameter(s) out of range
```

So I tried to the amarokapp comand and it tell me that there is no such comand. Hope this helps. Thanks

---

### Post by 23meg on 2005-11-30
See if you can reproduce the same behavior with the gstreamer engine. The 1.3.5 version seems to use a bit less CPU, maybe you should also give it a try.

---

### Post by daedalusman on 2005-11-30
When using the gstreamer egine files don't play. I think I know what the problem is though, I opened up rhythmbox and pointed it to my music folder, while loading it didn't recognize my mp3 files as audio stream files. I am going to search synaptic for an mp3 codec. I will post back here if that fixes the problem.

---

### Post by 23meg on 2005-11-30
Here's how you can enable mp3 playback with gstreamer: 

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs)

---

### Post by daedalusman on 2005-11-30
[QUOTE=23meg]Here's how you can enable mp3 playback with gstreamer: 

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs](http://help.ubuntu.com/starterguide/C/faqguide-all.html#codecs)[/QUOTE]


Well I've gotten the gstreamer plugins installed and now the same thing is happening with  that, and now xine uses up 99%, this is really starting to piss me off. Might I have too many codecs installed and amarok is getting confused or maybe its using a really crappy mp3 decoder?

Edit:
Alright so I didn't have some of the gstreamer plugins installed so I got them installed and no both gstreamer and xine are using up nearly 100%.

---

### Post by 23meg on 2005-11-30
Assuming you did everything else right, and that only amarok exhibits this behavior, it's probably an amarok issue with your configuration. Try amarok 1.3.5 and see if it improves things.

---

### Post by daedalusman on 2005-12-02
Alright, well I don't know what I did but amarok is no longer using a lot of CPU, its back down to only using about 2% while playing back a file which is nice and where it should be. Thanks for help, it probably helped but I'm just not sure what I did to fix it. It wasn't working right and then the next thing I know it was back to normal, weird, I can't firgure it out. Oh well I'll take it, :D

---

### Post by 23meg on 2005-12-02
Cool, now that it ain't broke, just don't fix it..

---

### Post by Adrian on 2005-12-06
[QUOTE=daedalusman]It wasn't working right and then the next thing I know it was back to normal, weird, I can't firgure it out.[/QUOTE]

Maybe you disabled last.fm support?

[http://www.ubuntuforums.org/showthread.php?t=78422](http://www.ubuntuforums.org/showthread.php?t=78422)
[http://www.ubuntuforums.org/showthread.php?t=78334](http://www.ubuntuforums.org/showthread.php?t=78334)

---

### Post by rskovacs on 2005-12-06
I just downloaded amaroK (from the repositories, btw) today, and I had the same problem at first, but then I went to Settings > Configure amaroK... > Collection, and then I unchecked "Watch folders for changes".  I know you seemed to have solved the problem, but for the rest of you with a similar problem...unless you really need this feature (and I don't) that might be an easy way to help free up some system resources as well.

---

