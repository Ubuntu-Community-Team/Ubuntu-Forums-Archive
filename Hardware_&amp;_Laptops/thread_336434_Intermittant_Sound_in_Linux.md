---
title: "Intermittant Sound in Linux"
date: 2007-01-11
forum: Hardware &amp; Laptops
---

### Post by PremierSullivan on 2007-01-11
Ive only been using linux for about three months.  I tried to research this problem, but I didnt find anything.  Usually I get help on via IRC, but my schools internet is screwed up and I cant get on to IRC.

Im running Kubuntu Edgy on a Dell inspiron E1705 (which Im told also goes by the name 9600 ](*,) ).  It seems that my problem started around the time I installed starcraft using wine.  I know I had to mess with the sound options to get it to work.  I dont remember what I did (which is a problem I know) but I seem to remember killalling artsd.  

Since then, sometimes, my laptop wont play sound.  The computer is clearly "going through all the motions".    I can raise or lower the volume, and Amarok shows music playing in the audio analyzer.  But it wont play sound.  Now, sometimes, if I reboot, it magically fixes everthing.  Sound worked perfectly before.

---

### Post by moeFinley on 2007-01-11
Most of the time sound problems posted here are due to the volume being muted somewhere.  I'm not a KDE user but check your volume settings and make sure you go to Edit -> Preferences and switch on all the relevent controls.

The following will show you your installed sound cards.  Check that it's installed or you might have two and it's outputing to the wrong device.

```
aplay -l
```

This will play a sound file to the default device which is a great way of testing.

```
aplay -D default /path/to/audio/file.wav
```

You can also change 'default' to a sound device listed with the previous command.

If you using ALSA a lot of problems can be sorted by correctly editing your /etc/asound.conf file.  I really don't know why Ubuntu doesn't have a wizard during the install to configure this file!?  On [this page]("http://www.mythtv.org/wiki/index.php/Configuring_Digital_Sound") there is a good example which can be adapted quite quickly.

[Here is a good ALSA troubleshooting guide]("http://alsa.opensrc.org/TroubleShooting")

Hope this helps.

---

### Post by PremierSullivan on 2007-01-11
Thanks for you answer.  For a moment, my sound was working correctly, so I havent had a chance to inplement any of your recomendations, but I just recently had a new development.  I was listening to Amarok, and then paused the song and watched some youtube videos with sound.  I then paused the youtube videos and tried to play Amarok again, and I got an error message that said:
```

Audio output unavailable; the device is busy.
xine parameters: 
```

Amarok then cycled through all of the songs on my playlist but didnt play any of them, it just went right on to the next song.  (This is different than before.)
The youtube videos still seem to work.

edit: I cant find /etc/asound.conf

---

### Post by moeFinley on 2007-01-11
It sounds like you using OSS instead of the newer [ALSA]("http://alsa.opensrc.org/").  OSS can only playback one thing at a time.

You can use ```
aoss amarok
```or```
aoss firefox
```to force an application to use ALSA.  In Gnome you can also switch the device in audio preferences.  But as I said I'm not familiar with KDE.

Of course you might not have ALSA setup correctly in the first place and that is way everything is using OSS.  If you have problems with the above check the [ALSA trouble shooting guide]("http://alsa.opensrc.org/TroubleShooting").

---

### Post by PremierSullivan on 2007-01-14
Okay, yeah, it looks like that was the problem:  I couldn't have to sound playing programs at once.  I couldnt open anything like "aoss firefox"; bash said it couldnt find aoss.

However, the problem has gotton worse.  I went through the alsa trouble shooting guide and it said ```
Look at /proc/asound/version and that this says something like:

Advanced Linux Sound Architecture Driver Version 1.0.4.

```

Well, the file didnt say anything at all.  It was empty.  So I followed the instructions to reinstall alsa.  I could really follow the instructions... it said to apt-get something and *then* compile the source what the heck?

Well, screw that.  I skipped ahead to mod probing something:

   modprobe snd-ens1371
   modprobe snd-pcm-oss
   modprobe snd-mixer-oss
   modprobe snd-seq-oss

so now I dont have any sound what so ever.  

Basically, I cant follow the trouble shooting page at all.

---

### Post by moeFinley on 2007-01-14
I don't know why you would have to install ALSA, Ubuntu should install it as part of the setup? :-k 

The modprobe command adds the drivers to the kernel so they can be used.  But you didn't have the drivers as you hadn't compiled them in the previous step.

If you ever get to a point in instructions you don't understand, don't skip it and continue :p 

[This post]("http://ubuntuforums.org/showthread.php?t=311166&highlight=Installing+ALSA") shows you how to compile them from source or alternatively there are auto install .deb packages.

I think you can also install it all through Synaptic (System -> Administration -> Synaptic Package Monitor)(Gnome).  Someone correct me if I'm wrong but you just need to check

linux-sound-base
alsa-base
alsa-oss
alsa-utils
libesd-alsa0
---and maybe these two?---
libpt-plugins-alsa
libdl1.2debian-alsa

and then click apply

---

### Post by PremierSullivan on 2007-01-14
Okay, so I tried installing the .deb packages, and it seemed to work but it didnt solve anything, even after restarting x.  So I then tried the command line instructions, but by the time I got to the ./configure line, it gave me an error that said the libasound wasnt installed.  I also tried installing all those packages you listed, and adept said I had all those packages except the last one, and it said that it couldnt find that last one.

---

### Post by moeFinley on 2007-01-14
I don't know if restarting X will restart ALSA can you restart the whole machine.

If not, this will restart ALSA
```
sudo /etc/init.d/alsa-utils restart
```

---

### Post by PremierSullivan on 2007-01-15
That seems to have fixed it for now.  Thanks for all your help!

---

### Post by moeFinley on 2007-01-15
Cool, glad it work ;)

---

### Post by PremierSullivan on 2007-01-18
I thought this problem was solved but its doing it again

---

