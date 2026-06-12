---
title: "Cannot Burn Audio CD From MP3.  Used Multiple Apps"
date: 2005-11-25
forum: General Help
---

### Post by poopdog on 2005-11-25
I've installed codecs. 
I've tried multiple applications.
I've tried all day today, but I cannot get an audio CD to burn.

The closest I could get was using Serpentine.

At first, it wouldn't accept the format of mp3s I was dropping in. 

I eventually got this fixed.

Now, I get all my mp3s added, and click "Write to Disc"

Now, It's stuck at "Fixating Disc" (less then 1/4 of a inch from the end of the progress bar).

I just want to burn an audio CD.

What do I need to do?!

---

### Post by oskude on 2005-11-25
you have to convert the mp3 files to wav (44khz 16bit) files (if the burnprogram doesnt support that)
and no need to make a new thread, try search on this forums
[http://www.ubuntuforums.org/showthread.php?t=76589&highlight=mp3+audio+cd](http://www.ubuntuforums.org/showthread.php?t=76589&highlight=mp3+audio+cd)

---

### Post by poopdog on 2005-11-25
Thanks for the quick reply.

I had done a ton of searching on this forum, as well as others. I saw that thread that you linked to, but it had a lot of different solutions, none of which worked.

I haven't tried the "converting mp3 to wav" solution yet, because it seemed kind of ridiculous to me.

I'll give it a swing though.



edit: I converted the .mp3s to .ogg and it burnt just fine.

Thanks for the help.

---

### Post by oskude on 2005-11-25
[QUOTE=poopdog]I haven't tried the "converting mp3 to wav" solution yet, because it seemed kind of ridiculous to me[/QUOTE]well, thats what a burn programm would do automaticly for you :)

mp3/ogg is NOT compatible with audio cd !
[http://en.wikipedia.org/wiki/Red_Book_%28audio_CD_standard](http://en.wikipedia.org/wiki/Red_Book_%28audio_CD_standard)

edit:
[QUOTE=poopdog]edit: I converted the .mp3s to .ogg and it burnt just fine.[/QUOTE]what a waste of quality...

---

### Post by poopdog on 2005-11-25
> 
well, thats what a burn programm would do automaticly for you :)
mp3/ogg is NOT compatible with audio cd !


I know about all that. 

The problem is that I have a large mp3 library that I dont feel like converting over to .ogg.

Now, anytime I go to burn a mix CD or something for my car, I'm going to have to copy and convert the files to .ogg, then burn the CD, then delete the .ogg files.

I realize  that there are licensing issues with the .mp3 format, but it seems like someone would have been able to hack it by now.


> what a waste of quality...
All my mp3s are at 196. That's good enough for me.

---

### Post by rubengs on 2005-11-25
Just use K3b with the mp3 plugin (search them in synaptic use this [sources]("http://www.ubuntuforums.org/showthread.php?t=92672")) and be sure that you have all the codecs installed. 

K3b burns mp3, ogg and flac directly.

k3b - A sophisticated KDE cd burning application
k3b-mp3 - The KDE cd burning application library - MP3 decoder

---

### Post by skeezer65134 on 2005-12-02
[QUOTE=poopdog]All my mp3s are at 196. That's good enough for me.[/QUOTE]
I used to be the same way; still am mostly. I recently discovered the beauty of VBR and the --aps and --ape settings. Better quality and typically very little extra file size. I'd get more into .ogg, but I have the same issue, a huge collection. My MP3 player does play .ogg files though (iRiver rules!), so I have no reason not to add them to the collection. Converting all the .mp3 files to .ogg seems like a waste personally.

Anyway, what burning program are you using? I immagine it's just a matter of a missing plugin or library. Worse-case you could dedicate a directory to burning mix CDs and make a bash script to run through and convert the files to .wav before burning. Just a thought, as cubersome as you might find it.

I have been using k3b for a very long time now (being a formet Gentoo/KDE user and recently becoming a Kubuntu user) and it has always been drag and drop for me. Once in a great while I will come across an mp3 that it can't convert, but I think if I did it by hand it would work out just fine. I would think that whatever Gnome uses (it's been a while, xcdroast or something like that I would think) should be able to do it. It's not an uncommon thing to want (or for software to do).

---

