---
title: "[SOLVED] VLC + PulseAudio = Sound Choppy"
date: 2008-08-24
forum: General Help
---

### Post by ashmew2 on 2008-08-24
Hello people. I upgraded to Hardy quite a long time ago and have been having this problem of sound choppiness and clicking/skipping of songs. I googled and found a sort of fix for the problem , which is to execute in the terminal :

```
killall pulseaudio -- vlc
```

How do i go about adding this to Vlc Startup ? I mean i dont want to execute this command everytime i want to open an audio file with VLC. So how can i add this command to VLC startup so that this is executed and then VLC plays the song normally. I hope im clear ;)

Thanks.

---

### Post by bthoward on 2008-08-24
Have you contemplated uninstalling pulseaudio?  It was just added in Hardy.  Uninstalling it would make things just work and you'd no longer have to run that command.  

Personally I use some of the network audio stuff that pulse provides but I still don't see it working as well as ESD did.  Given time I'm sure it will mature.  Especially now that it is the mainstream used stuff but for now its still just a smidgin green.

---

### Post by ashmew2 on 2008-08-24
Thanks for the quick reply.
You sure uninstalling it will solve the problem ? I mean if not solve it not worsen it at least :P
So how do i go about it , 
just an apt-get remove pulseaudio ?

---

### Post by bthoward on 2008-08-24
sudo apt-get remove pulseaudio

Worst case if you're not happy...

sudo apt-get install puseaudio

and you're back...

Edit:  Lemme know how it goes!

---

### Post by ashmew2 on 2008-08-24
Ill be happy :)

Im rebooting , will get back here in a minute or so.

---

### Post by ashmew2 on 2008-08-24
I uninstalled Pulse Audio , And the choppiness etc is gone (At least for now :P). Thanks !!

But the startup sound of ubuntu ( i hadnt changed the default one) , didnt play this time when i rebooted. 

Plus , you have any ideas of adding that command to the startup of VLC ? I would still like to know (just to add to my knowledge about the distro).

---

### Post by bthoward on 2008-08-24
Appreciate the reply.  Always good to know when things worked out for someone!  I really like the little thanks idea that Ubuntu has added to the forum.  

One thing that you may do is use &&.

You may have seen the use of these in console commands...

Such as "sudo apt-get update && sudo apt-get install <some app>" or "./configure && make && make install"

What the && means is if the previous command completed successfully then continue on.

So you could perhaps go into the menu editor and change the command to have killall pulseaudio -- vlc in there.  That however doesn't make it run if vlc is automatically called because of a filetype association...

---

### Post by bthoward on 2008-08-24
Perhaps you could make a bash script that ran the kill command and then kicked off vlc and then tried associating everything that is associated with vlc to the script.  Or you could rename your vlc executable and then put a script in its place that ran what you wanted and then kicked off the renamed executable.

---

### Post by ashmew2 on 2008-08-24
Yeah  , it doesnt make VLC run properly because of filetype associations.Ill do some research and will get back to you if i find something useful. Thanks for all the help bthoward.

Bte , if i use && in a script  , i think the process will only continue if the previous one completed successfully. If something in between returns an error , i think the script will exit abruptly.

---

### Post by mb_webguy on 2008-08-24
I'm not necessarily a fan of PulseAudio, but since Hardy is was put together with PulseAudio in mind, I was hesitant to uninstall it.  Psyke83 has put together an easy-to-install collection of fixes for PulseAudio in Hardy that works extremely well for me.  Check the link in my signature if you're interested.

---

### Post by blazemore on 2009-06-03
make a script
```
nano vlc
```
Type
```
killall pulseaudio && /usr/bin/runvlc
```
Press Ctrl + W, then Ctrl + x
```
sudo cp /usr/bin/vlc /usr/bin/runvlc
```
```
sudo chmod +x /usr/bin/*vlc
```

Done!

---

### Post by ashmew2 on 2009-06-04
The solution was always elegant , But at that time i wasnt as comfortable with Linux/Ubuntu as i am now :)

Thanks for the reply though blazemore. I think someone should find it useful :D

---

### Post by blazemore on 2009-06-05
Yeah that's why I put it here, if people are searching, they should find it. Another way would be to use Symbolic links.

---

### Post by Patriot1776 on 2009-07-13
Is 'killall pulseaudio -- vlc' run while VLC is running or not?  I'm having choppy audio problems too with VLC.

---

### Post by cheecheeo on 2009-08-09
```
sudo apt-get install vlc-plugin-pulse
``` and selecting 'Pulseaudio audio output' from the audio section of preferences (Tools -> Preferences) seemed to help me.

---

