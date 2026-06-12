---
title: "Mplayer problem sound..."
date: 2005-12-01
forum: General Help
---

### Post by sweetthdevil on 2005-12-01
Good afternoon,

I just install Kubuntu 5.10, and install Mplayer 586 plus the plugin for firefox, when i try to play any video from the web, the sound isn't fluide.
I'm using Arts.



Plus when i open mplayer i got this error message:

New_Face failed. Maybe the font path is wrong.
Please supple the text font file (~/.mplayer/subfont.ttf)

How to fix it? 

Thanks

---

### Post by chandra on 2005-12-01
[QUOTE=sweetthdevil]Good afternoon,

I just install Kubuntu 5.10, and install Mplayer 586 plus the plugin for firefox, when i try to play any video from the web, the sound isn't fluide.
I'm using Arts.



Plus when i open mplayer i got this error message:

New_Face failed. Maybe the font path is wrong.
Please supple the text font file (~/.mplayer/subfont.ttf)

How to fix it? 

Thanks[/QUOTE]

Try

sudo apt-get install mplayer-fonts

and see if the problem disappears.

---

### Post by sweetthdevil on 2005-12-01
Ok thanks that fix the problem for the error message :D 


But i still have a problem when i try to read any video from internet. The sound is really crap,  you know, start, stop, start, stop... But i doesn't come from my connection:???:

---

### Post by sweetthdevil on 2005-12-02
Any one?

:confused:

---

### Post by BoredOutOfMyMind on 2005-12-08
[QUOTE=sweetthdevil]Any one?

:confused:[/QUOTE]

Did you install the fonts as described above?

[http://linux.sys-con.com/read/32880.htm](http://linux.sys-con.com/read/32880.htm)

# Examine the .mplayer subdirectory that the installation creates in your home directory. If there is no codecs.conf file present, copy it from the MPlayer installation/etc subdirectory. Also, copy from that same subdirectory the example.conf file and rename it to config. Then edit config so that only the gui and the skin lines are left uncommented. You can experiment with the other config options at your leisure.

# If the font subdirectory does not exist in the .mplayer directory, create it. Then unzip the downloaded fonts into a temporary directory, select the size font you want and copy the contents of the subdirectory for that size to the .mplayer/font directory.

---

