---
title: "Finally upgraded to Hardy - No sound!"
date: 2008-10-05
forum: Hardware
---

### Post by wingsofseraphim on 2008-10-05
I finally upgraded from gutsy to hardy because i was sick of not being able to use firefox 3 from the repository.

Now I have no sound!  My kernel is 2.6.24-19.  I tried installing the 2.6.24-18 kernel (yes I installed generic and the appropriate restricted modules)  but it kept getting hung up at starting the HSF Softmodem Driver.  Then I trie going back to using the 2.6.24-15 kernel that was already in my Grub boot list.  But it couldn't detect my graphics card and I got stuck with 800x600 resolution.  Was able to get it up to 1024x768, but the natural resolution is 1440x900!  Then when I went back to the newest kernel, it still can't get the resolution right, BUT my NVidia driver is detected and enabled.

I'm at my wit's end here.  I bought the Inspiron 1420N with Gutsy preinstalled and it worked flawless, I tried upgrading to Hardy back when it was in beta, but same no sound problem.  So I scrubbed the disc and restored it to factory defaults.  I do not want to do that again.  It was a pain importing all the settings and programs.

I searched and searched for a solution to the "hardy upgrade no sound" problem, but the few solutions I did find on the forums and on google just did not work.  And now I have to sort out my screen resolution problem

---

### Post by TheLions on 2008-10-05
can you tell us which sound card?

---

### Post by wingsofseraphim on 2008-10-05
$ lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)

---

### Post by TheLions on 2008-10-05
this may be of interest:

[http://ph.ubuntuforums.com/showthread.php?t=747054](http://ph.ubuntuforums.com/showthread.php?t=747054)

---

### Post by wingsofseraphim on 2008-10-05
I have no idea why I upgraded anymore... Everything is pretty much broken.  

Nothing on that page helped.  His problem was not the same as mine, and none of the things worked.

---

### Post by TheLions on 2008-10-05
did you recompile alsa?

does sound work from LiveCD?

---

### Post by wingsofseraphim on 2008-10-05
I'm compiling alsa right now

```

$ ls -l /dev/snd
total 0
crw-rw----+ 1 root audio 116,  1 2008-10-05 14:31 seq
crw-rw----+ 1 root audio 116, 33 2008-10-05 14:31 timer

$ ls -l /dev/dsp
ls: cannot access /dev/dsp: No such file or directory

$ aplay
ALSA lib confmisc.c:768: (parse_card) cannot find card '0'
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_card_driver retur\
ned error: No such file or directory
ALSA lib confmisc.c:392: (snd_func_concat) error evaluating strings
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_concat returned e\
rror: No such file or directory
ALSA lib confmisc.c:1251: (snd_func_refer) error evaluating name
ALSA lib conf.c:3513: (_snd_config_evaluate) function snd_func_refer returned er\
ror: No such file or directory
ALSA lib conf.c:3985: (snd_config_expand) Evaluate error: No such file or direct\
ory
ALSA lib pcm.c:2145: (snd_pcm_open_noupdate) Unknown PCM default
aplay: main:546: audio open error: No such file or directory

$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory


```

Maybe this will help?  I think I'm just gonna reinstall.  Maybe try to install heron from a livecd?  I don't know...

---

### Post by TheLions on 2008-10-07
And? Do you have sound in Hardy LiveCD?

---

