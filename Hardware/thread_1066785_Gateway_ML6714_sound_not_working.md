---
title: "Gateway ML6714 sound not working"
date: 2009-02-11
forum: Hardware
---

### Post by marinegundoctor on 2009-02-11
I've got ubuntu 8.10 installed and everything working except my sound.  I have been working on this for three or four day and can't find any drivers. Can someone please help me out. It is a Gateway ML6714, ser# T3C7BS1000757. The audio is the High Definition Audio (HDA).
Thanks in advance.

edit: I, like [http://ubuntuforums.org/showthread.php?t=937902]("the guy in this post") figured it out, only I did it by reading his post.

My audio worked after initial install of ubuntu (intrepid) and would still work with the live CD.  After installing some things from the Add/Remove programs ( I selected a lot of stuff at once) my sound stopped working.

To get it started again just type 'gstreamer-properties' into a terminal (w/out the quotes) and change the ouput device to your sound card. Mine is STAC92xx Analog. The plugin I  made sure that ALSA is selected. 

That was half the fix. The rest follows: open your sound preferences (System / Preferences / Sound) from the menu. Under **Sound Events**...Sound Playback "Autodetect (Custom) was already chosen for me. I left it as is.
**Music and Movies**...Sound Playback I had to select HDA Intel STAC92xx Analog (OSS) as nothing else would work.
For some reason there are several identical entries, I chose one, tested, chose another, tested, and so on till the sound test worked. Some times the Sound Preferences would crash and I would have to force quit (or kill the process) and start over with the choose and test.

---

