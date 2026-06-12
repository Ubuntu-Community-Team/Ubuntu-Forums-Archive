---
title: "how can i manually compile ffmpeg?"
date: 2008-09-09
forum: General Help
---

### Post by hempa on 2008-09-09
hi i need to manually compile ffmpeg with the plugins aac and h264. i would not mind to throw in some other handy plugins there as well if anybody knows how to do this and were to get those two plugins mentioned above and maybe some other good ones please help me.when compiled it has to be installed in /usr/local/bin

the reason for all this is that a program i need for putting videos on my ipod (floola) needs this to convert different video files so it can put it on my ipod nano. please help im new so i need a step by step guide cause i never manually compiled anything before.

im using gutsy.

---

### Post by whitethorn on 2008-09-09
B4 you try compiling it yourself.  You could try adding the medibuntu repository

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

then 
```
sudo apt-get update
```
```
sudo apt-get install ffmpeg
```

From what I've read found

[http://ftp.leg.uct.ac.za/pub/linux/medibuntu/gutsy/ffmpeg.html](http://ftp.leg.uct.ac.za/pub/linux/medibuntu/gutsy/ffmpeg.html)

It seems like h264 and aac are installed with the version ffmpeg from medibuntu.  You might also what to have a look at this GUI for ffmpeg called WinFF.  I'm not sure if it's in the repositories,

```
sudo apt-get install winff
```

hope this helps

after you've finished getting your ffmpeg, don't forget to go to System -> Administration -> Software Sources (that's in Hardy) wherever you have your repositories and turn off the medibuntu repository. It is very active and has a lot of updates which you probably don't need and might be unstable.

---

### Post by Irihapeti on 2008-09-09
If you end up needing to compile it yourself, there are some instructions here:

[http://stream0.org/2008/05/ffmpeg-update-installing-on-ub.html](http://stream0.org/2008/05/ffmpeg-update-installing-on-ub.html)

That article is for Hardy, but there are links to an earlier one written for Gutsy.

I couldn't get the libx264 option to work on Hardy, but I think it did on Gutsy (but it's a while since I did it).

---

### Post by FakeOutdoorsman on 2008-09-09
I second the Medibuntu recommendation.  If that doesn't work then take a look at my tutorial:
[HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095")

It's for Hardy, but you can probably get it working with a little work and package searching/renaming.

---

### Post by mb_webguy on 2008-09-09
I third the Medibuntu repository.  I use FFMpeg with aac and h.264 all of the time, and I didn't have to compile it myself.

---

### Post by hempa on 2008-09-11
ok i did like you guys told me and added medibuntu repsitories,downloaded and installed ffmpeg from there and now floola works just fine and can convert almost anything i thtrow at it. Thank you guys for this awesome tip. i did not know there was a difference on the ffmpeg i had in synaptic and the one i got from medibuntu, the one in synaptic did not work at all. Thats why i thought i had to manually compile,but this saved me alot of time since im new and dont know so much about compiling yet. thanks again

---

