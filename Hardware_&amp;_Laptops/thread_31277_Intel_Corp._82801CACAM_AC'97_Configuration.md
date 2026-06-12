---
title: "Intel Corp. 82801CA/CAM AC'97 Configuration"
date: 2005-05-02
forum: Hardware &amp; Laptops
---

### Post by derdewey on 2005-05-02
Hi everybody,
When I first installed hoary I had sound.  I'm not sure if it was multichannel or whatnot, but it made sound when I would logon.

I'm using an IBM T30 laptop with Ubuntu Hoary.

```

$ lspci -v | grep -i audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)

```

I then followed another guide on the forum and compiled my own alsa to use the snd_intel8x0 driver.

```
lsof /dev/dsp
```

This doesn't show anything (so I guess that means nothing is using the sound at the moment).  Also, whenever a KDE app tries to make sound (error report, etc) it pops up saying that it doesn't know where the sound is.  So, this leads me to believe that the alsa driver isn't configured properly.  Or maybe my kernel breaks compatibility? From 'uname -r' I get 2.6.10-5-686.

---

### Post by Gandalf on 2005-05-02
[QUOTE=derdewey]Hi everybody,
When I first installed hoary I had sound.  I'm not sure if it was multichannel or whatnot, but it made sound when I would logon.

I'm using an IBM T30 laptop with Ubuntu Hoary.

```

$ lspci -v | grep -i audio
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 02)

```

I then followed another guide on the forum and compiled my own alsa to use the snd_intel8x0 driver.

```
lsof /dev/dsp
```

This doesn't show anything (so I guess that means nothing is using the sound at the moment).  Also, whenever a KDE app tries to make sound (error report, etc) it pops up saying that it doesn't know where the sound is.  So, this leads me to believe that the alsa driver isn't configured properly.  Or maybe my kernel breaks compatibility? From 'uname -r' I get 2.6.10-5-686.[/QUOTE]
 use Esound not alsa, ubuntu use ESD by default, if you still want to use Alsa then follow [HOWTO: Hear multiple sounds at once](http://ubuntuforums.org/showthread.php?t=8882&highlight=multiple+sound) NOTE: please read that whole topic before begining in it!!!

---

### Post by derdewey on 2005-05-02
Hmm, I had already followed that guide, hehe.  I've tried lots of things and I fear that I may have done something which created another conflict.  Problem is, I didn't keep track of everything I've done (I've been futzing around for about a month now).

When I do gstreamer-properties I get a screen which has buttons labelled 'test'.  When I hit those I get an error message saying that a test pipe could not be contstructed for alsa (that's the thing selected on the drop down menu).

---

### Post by Gandalf on 2005-05-02
[QUOTE=derdewey]Hmm, I had already followed that guide, hehe.  I've tried lots of things and I fear that I may have done something which created another conflict.  Problem is, I didn't keep track of everything I've done (I've been futzing around for about a month now).

When I do gstreamer-properties I get a screen which has buttons labelled 'test'.  When I hit those I get an error message saying that a test pipe could not be contstructed for alsa (that's the thing selected on the drop down menu).[/QUOTE]
 use Esound not alsa!!!

---

### Post by ivoks on 2005-05-03
[QUOTE=Gandalf]use Esound not alsa!!![/QUOTE]

No. Don't use esound. Esound sucks. Get ur self polypaudio (apt-get install polypaudio) and compile gstreamer plugin for it (gst-polyp IRC). It creates backward compatibility with Esound, but it's much better.

It seems that polypaudio will be sound server for Gnome3 and KDE4.

---

### Post by derdewey on 2005-05-04
Thanks for the feedback, but I still can't get the audio to work.  Are there any commands I should try to see if this thing is configured properly?

I installed polyp-audio (thereby removing esound) and then I restarted my laptop.  I think logged on and there was no chime.  How should I go about cleaning up all the configurations so that I can start off fresh?

Hmm, about this business with the gst-polyp, what if I would rather use something like amarok?

---

### Post by Gandalf on 2005-05-04
[QUOTE=derdewey]Thanks for the feedback, but I still can't get the audio to work.  Are there any commands I should try to see if this thing is configured properly?

I installed polyp-audio (thereby removing esound) and then I restarted my laptop.  I think logged on and there was no chime.  How should I go about cleaning up all the configurations so that I can start off fresh?

Hmm, about this business with the gst-polyp, what if I would rather use something like amarok?[/QUOTE]
 before doing this, did you at least tried ESD???

---

### Post by derdewey on 2005-05-04
Yep, I tried ESD (that was the first FAQ I followed) and that didn't work.  I'm wondering if something i's taking up the soundcard or not.  I don't know how to check for this.  Your feedback is greatly appreciated.

I know the sound has worked because it worked the first time I installed Hoary so I know I can get it to work again.

EDIT: Oh, question.  Isn't ESD just a mixer?  Isn't that why I have alsa or oss for the hardware level?

---

### Post by derdewey on 2005-05-11
Would anyone care to help me start over from square one?  I'd like to strip out all of the sound related stuff but I do not know where to start.

---

