---
title: "Audacity and libmp3lame ??? Where?"
date: 2005-12-02
forum: General Help
---

### Post by shane2peru on 2005-12-02
I have installed Audacity and cannot find the libmp3lame.  I have searched in my file system and asked it to look for hidden files too, but nothing.  Where and how should I get this thing?  I tried ```
 sudo apt-get install libmp3lame
``` and no luck.  Any ideas greatly appreciated.  Thanks.

Shane

---

### Post by aysiu on 2005-12-03
Try ```
sudo apt-get install gstreamer0.8-lame lame liblame0
```

---

### Post by shane2peru on 2005-12-03
```
Reading package lists... Done
Building dependency tree... Done
gstreamer0.8-lame is already the newest version.
lame is already the newest version.
liblame0 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
shane@ubuntu:~$


```

Thanks for the reply, now what?  

Shane

---

### Post by Bachstelze on 2005-12-03
The problm is that Audacity can't find your libmp3lame.so file, right ? The correct file is libmp3lame.so.0 so you can make a symbolic lnk to it or tel Audacity to use this file.

---

### Post by shane2peru on 2005-12-03
[QUOTE=HymnToLife]The problm is that Audacity can't find your libmp3lame.so file, right ? The correct file is libmp3lame.so.0 so you can make a symbolic lnk to it or tel Audacity to use this file.[/QUOTE]
Actually the problem is that **I **can't find any libmp3lame files at all.  I don't know where they are hiding.  I have done a search for files and typed in libmp3lame and told it to look in the filesystem and include hidden files, and it still doesn't find them.  Where can I find that file?  I would point it to any libmp3lame file to try and get it to work.  I also can't play any mp3 files with any program.  I know I have sound, but none of the programs play mp3 files.  That is kind of 'lame'.  :D  MP3 is only the most popular music file around and I can't play them?  I think this is yet another problem, and probably should be another post, but I'll take any help I can get.  Thanks!

Shane

---

### Post by Bachstelze on 2005-12-03
If you have VLC installed, try reading your mp3s with. If it works with this and not with others, try installing the libmad0 package.

---

### Post by shane2peru on 2005-12-03
What is VLC??? and how do I run it, or install it?  Thanks for your help.

Shane

---

### Post by Bachstelze on 2005-12-03
VLC is (in my opinion, of course), the best media player available. It reads almost every audio/video format available "out of the box" (i.e. without installing any extra plugins). You can get it through Synaptic.

---

### Post by shane2peru on 2005-12-03
Ok, that is installed, and at least I can finally play MP3.  Does that have the libmp3lame file with it?  Thanks for the info.  Just for the record, I did find that VLC doesn't play .rm or .ra files.  I know I know, that is exclusive for Real player, but I thought that maybe it might play them.  O well.  That is for another day.  Now, is this libmp3lame included with this program?  Thanks for your help in real time!

Shane

---

### Post by shane2peru on 2005-12-03
Never mind, I found it.  :p :D   Yippie!  Thanks for the info.  I knew there had to be a program out there that would have it.  It popped right up in my /usr/lib folder when I did the search (for any noobs like me who might read this in the future.)  Thanks HymntoLife you were a great help!

Shane

---

### Post by Gray. on 2005-12-03
System > Administration > Synaptic
Search > liblame > OK
Make sure that liblame0 is installed.
Applications > Sound & Video > Audacity
Open whatever file yo wish to export
File > Export as MP3
When it asks to locate libmp3lame.so make sure that all files are shown
Then select libmp3lame.so.0
When the warning pops-up just ignore it and accept anyways.
There you have it!

*EDIT* Looks like I was too late lol

---

### Post by shane2peru on 2005-12-03
Sorry for the triple post.. True to linux, fix something break something.  Now, when I start Audacity I get this error:
```

There was an error initializing the audio i/o layer. 
You will not be able to play or record audio.  

Error:  Host error.


```

Any ideas?  Audacity is useless unless I can play or record audio.  Thanks.

Shane

---

### Post by Gray. on 2005-12-03
Audacity can't use the audio i/o layer when it's in use by another application. Maybe another application is using the layer?

*EDIT* I just found the Audacity wiki [here]("http://audacityteam.org/wiki/index.pl?LinuxIssues"). This page has specific troubleshooting help.

---

### Post by deadgobby on 2006-01-17
I would like to thank you guys for posting this and the replies. I am a happy gut today. I got a new sound card and now i am able to take my old 4 track stuff and convert over to mp3's. I feel like a 5 year old at xmas time :p

---

### Post by thequickbrownfox on 2006-02-10
Shane,
The culprit is usually esd (enlightenment sound daemon, I think). A quick 
> sudo killall esd should solve your problemo.
Peter

---

### Post by cvmostert on 2006-04-15
[QUOTE=HymnToLife]The problm is that Audacity can't find your libmp3lame.so file, right ? The correct file is libmp3lame.so.0 so you can make a symbolic lnk to it or tel Audacity to use this file.[/QUOTE]

I just changed libpm3lame.so to libmp3lame.so.0 as the file to be used by Audacity and it worked like a charm, or so it seemd.

Thank you!

Ciao

---

### Post by mjunior on 2006-09-29
I had the same problem, so thanks for this tip..

I have the required library to export ogg to mp3 now..and that's what I was eager for..
But does anyone know a sound format converter ogg-->mp3 and mp3-->ogg available for Gnome? I know I said the Audacity do the job, but the point is I need to open and export a single file at the time...I'm looking now for a program that do it on the fly..extracting a whole folder of ogg's files and exporting on mp3 format in other and vice versa..
I remember I had used a program that suits this needs in the past but can't remember the name or the distro I was using at that age..

---

### Post by mjunior on 2006-09-29
I found a way to do it on wound juicer!!

[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

---

### Post by satbunny on 2006-09-30
My advice is that if the file 'libmp3lame.so.0' isn't in /usr/lib then install the package libmad0. The tell Audacity to link to the file which will be in usr/lib
It will ask if this right since it will be surprised by the .0 ending, but it'll work fine. No need for a symlink.

I just did all that and it worked fine.

---

