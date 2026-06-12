---
title: "No sound in Jaunty, had it in Intrepid"
date: 2009-05-04
forum: Hardware
---

### Post by linduxed on 2009-05-04
I installed Jaunty a couple of days ago and while I enjoy improvements on many fronts, I can't get my sound to work.

I have the problematic ALC889 card. In Intrepid I needed to do use the [following script]("http://ubuntuforums.org/showthread.php?t=1046137") to manually update to alsa-1.0.19 for my sound to work properly (I could use .18 and utilise tools like hda-verb for subpar sound from two channels but that's all).
In Jaunty this has no effect, which I find mighty strange because when I install .19 with the script, sound utilities like the pulse-audio mixer clearly show bars jumping up and down, so there has to be some activity (no sound though).

I've checked all possible places, nothing is muted.

---

### Post by linduxed on 2009-05-06
I just tried another method I read about, [Luke Yelavich's ALSA PPA](https://launchpad.net/~themuso/+archive/ppa).

I installed the PPA and then ran an update followed by an upgrade.
After reboot I'm still out of sound. I think I'm back where I was when I installed .19 with the script.

---

### Post by linduxed on 2009-05-06
I just tried restarting alsasound (now ive used the PPA method for installing) and I got the following output:
```
linduxed@lawliet:~$ sudo /etc/init.d/alsasound restart
[sudo] password for linduxed: 
Shutting down sound driver: ERROR: Module snd_hda_codec_nvhdmi is in use
ERROR: Module snd_hda_codec_realtek is in use
ERROR: Module snd_hda_codec is in use by snd_hda_codec_nvhdmi,snd_hda_codec_realtek
ERROR: Module snd_hwdep is in use by snd_hda_codec
ERROR: Module snd_pcm is in use by snd_hda_codec
ERROR: Module snd_timer is in use by snd_pcm
ERROR: Module snd is in use by snd_hda_codec_realtek,snd_hda_codec,snd_hwdep,snd_pcm,snd_timer
done
ALSA driver is already running.

```
Is it just me or should there be less modules printed out?

After doing it again I got the following:
```
linduxed@lawliet:~$ sudo /etc/init.d/alsasound restart
Shutting down sound driver: /usr/sbin/alsactl: save_state:1502: No soundcards found...
done

```

Oh and the first restarting didn't help at all.

---

### Post by linduxed on 2009-05-06
While the script obviously just overwrites the everything that has to do with ALSA, I just noticed that the PPA method does not.
Kinda obvious in a way since the packages installed were called stuff like "lib32asound2" instead of "alsa-base" and such. It hit me that there might be something important about the fact that all the packages coming from official sources (alsa-base, alsa-utils, etc...) are still at 1.0.18.dfsg-1ubuntu8.

I also tried adding the following to /etc/modprobe.d/alsa-base.conf :
```
options snd-hda-intel model=acer-aspire
```
But that didn't help at all.

---

### Post by linduxed on 2009-05-06
An important piece of info that I forgot to mention is that I don't get any sound in GDM either. I assume that in Jaunty there's still some sound when the login screen pops up, and sound's missing too.

---

### Post by Glowball on 2009-05-10
Since I received a notification about this topic on my bug report for ACER Aspire 8930G, I assume you have the same or a similar model.

I had the same problem (except for the fact that it *didn't* work in Intrepid). It took me 3 days to get it to work, but I think it were these that did the trick (I also tried to install Pulseaudio and stuff, but as far as I know, I'm not using it), and I don't remember the other things anyway... But it might help you :)

In /etc/modprobe.d/alsa-base.conf, I added:
```
options snd-hda-intel model=acer
options snd-hda-intel index=0
```I downloaded and compiled hda-verb 0.3 and copied it to /usr/local/bin/

Then I added this line in /etc/rc.local:

```
/usr/local/bin/hda-verb /dev/snd/hwC0D0 0x15 SET_EAPD_BTLENABLE 2
```(Don't forget to delete -e on the first line; if you are using another model, you might have to change hwC0D0 accordingly)

Then you'll have to reboot. Maybe it was because of my other edits, but everything was muted at that point. Don't forget to check it out ;)

---

### Post by linduxed on 2009-05-10
I finally found the solution to my problem.
Apparently the .18 driver provided in Jaunty is capable of give close to full functionality, it's a matter of adding two lines of text into a config file.

First open up /etc/modprobe.d/alsa-base.conf with preferred editor. In my case it's vim so it would look like the following:
```
sudo vim /etc/modprobe.d/alsa-base.conf
```
Add this to the end of the file:
```

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

```
After this a reboot was all I needed to get the sound working. I had to unmute and move some sliders in alsamixer but that was it.

I found the fix in the [following bug report](http://bugs.launchpad.net/ubuntu/+bug/218165) in Launchpad. The relevant posts are found on the very bottom, written by "pedja_portugalac".
The first solution he offers is the one I outlined here and used, the other one involves downloading the driver from Realtek's page instead of using any of the mentioned methods in this thread (official repos, .19-script, PPA).
The difference between the two is that the one I outlined above is first and foremost a lot simpler, but it also gives only 3 channels (right, left and centre). This was tested with a [surround sound testing audio file](http://www.lynnepublishing.com/surround/www_lynnemusic_com_surround_test.ac3).
According to "pedja_portugalac" the Realtek-driver-method provides him with the full 5.1 (as stated in the bug report thread), something I have not tried and cannot confirm. Some day maybe, now I'm well satisfied with the sound I've got.

---

### Post by Squarc on 2009-05-31
Hi there,
I got 2.0 output working according to the 5.1 test file used with vlc (5.1 output enabled)... though when listing music using 2.0 output (amarok, vlc (2.0 output enabled)) the music is  matrixed to all speakers.

Did anyone got real 5.1  working yet? isn't it actually better to create a new alsa model that serves the acer-aspire 8930G and models like it? or is that a huge job ? (I'm into Kubuntu and linux for about 2 months now).  I really hope 5.1 will be available soon. On the preinstalled vista the sound was quite nice.
Greetings

---

### Post by Foofoouk on 2009-06-01
Hey linduxed, thanks so much for your post. I am completely new to Linux and have spent many hours trying to get the sound working on my Acer 8930G with no success. I had turned to a blog post here: [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/) for help but no joy. 

Following your directions about appending the below to /etc/modprobe.d/alsa-base**.conf** is what got things behaving.  Although one small difference was that the file I had to alter had **.conf** at the end.

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
Thanks again! I'm not going to give up now! :p

---

### Post by Foofoouk on 2009-06-01
Hey linduxed, thanks so much for your post. I am completely new to Linux and have spent many hours trying to get the sound working on my Acer 8930G with no success. I had turned to a blog post here: [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/) for help but no joy. 

Following your directions about appending the below to /etc/modprobe.d/alsa-base**.conf** is what got things behaving.  Although one small difference was that the file I had to alter had **.conf** at the end.

alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto
Thanks again! I'm not going to give up now! :p

---

### Post by linduxed on 2009-08-07
Fixed the .conf bit. I've compiled a guide on my blog that's a bit more readable than my post, it can be found [here]("http://www.linduxed.com/notes/2009/5/24/sound-in-ubuntu-904-on-acer-aspire-8930g.html").

---

### Post by Foofoouk on 2009-08-09
Thanks for that, I will take a look at your blog post.

I only seem to have got the front two speakers working so no 'sub' or rear speakers. At least some sound is better than no sound!

---

