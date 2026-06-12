---
title: "Jaunty and Flash are System Freeze"
date: 2009-04-23
forum: Installation &amp; Upgrades
---

### Post by Amazona aestiva on 2009-04-23
Well, I need some sort of help I geuss and you may want to know about this:

I've tried a fresh install of i386 and amd64 version too.

Both seems to have a serious bug with Adobe flash player. If I go on youtube my whole system will freeze after 6-7 minutes and I have to reset. I have md5sum checked the images on computer and ran defect check on boot. I have also tried to use the flash player I can download from adobe's webpage but it fails too.
Workaround: it can freeze at once when the video starts :(

This is a pretty big problem to me andI do not think I will be the one.

I've been using Ubuntu since Edgy and have quite a lot of experience so I do not think I have done something wrong.

The sound laggs after freezing. I think it could be a pulseaudio malfunction or wrong configuration. In this case do you know any how-to I could try?
By the way, this has a rather big chance. I mean until gutsy, OSS didn't work at all with my sound card and I barely got ALSA work.
Workaround: Nope I killed pulseaudio and reloaded alsa but freezed again.

Is there any way I could give you more information?
What sould I do now? Report a bug? Where?   Solutions? :)

Thanks

---

### Post by Amazona aestiva on 2009-04-23
Do I only get this error, bug or whatever it is? :( :(

---

### Post by jsnelli2 on 2009-04-23
I would let you know how it is working for me, but I haven't been able to install flash.  Regardless of whether I run the auto install through firefox or try to manually install it I get an error.  The error is telling me I am running another synaptic type process...in which I'm not.  I'm assuming you had no such problem?

---

### Post by Amazona aestiva on 2009-04-23
> **jsnelli2 said:**
> I would let you know how it is working for me, but I haven't been able to install flash.  Regardless of whether I run the auto install through firefox or try to manually install it I get an error.  The error is telling me I am running another synaptic type process...in which I'm not.  I'm assuming you had no such problem?

No I didn't have such problem. Well, what happens when you try to run Synaptic? Can you start it? If yes you can install it from there. It's name is ```
flashplugin-installer
```

or can try from terminal:
```
sudo apt-get install flashplugin-installer
```

If you can't even start Synaptic and sure there is no update, remove or install process, you should start a new thread about this issue.

All the best, :)

---

### Post by jsnelli2 on 2009-04-23
Hmm, yeah Synaptic runs fine.  Not to take over your thread (sorry about that) but it seems like anything coming from us.archive.ubuntu.com just sits there not responding when trying to connect.  I see that that is the location it is coming from when trying to install through terminal.  Could that be the problem?

---

### Post by jsnelli2 on 2009-04-23
Eh, it finally went through.  Thanks for your help.  I'm going to watch a bunch of youtube videos to see if I have the same problem you have.  If I run into any problems like you are having I will let you know.  Good luck in the meantime!

---

### Post by Amazona aestiva on 2009-04-23
Ohh well, I don't know what the problem might be after this:
Installed Opera to find out if it has the same issue, but it freezed before I would start the installation process of flash.

So I guess this is it, I didn't have any problems in Hardy and Intrepid. I guess it would be easier for me to downgrade and try Jaunty a month later.

I need a stable system for my work.:rolleyes:

I'll keep my eyes open if there is any news here.

All the best,

---

### Post by viduliya on 2009-04-24
This post by psyke83 helped me with some pulseaudio and flash issues before:  

[http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+woes]("http://ubuntuforums.org/showthread.php?t=789578&highlight=pulseaudio+woes")

---

### Post by katula on 2009-04-25
I ran into this same issue when after upgrading to Jaunty through synaptic.  Firstly, in order to get flash to work at all I had to remove it, and reinstall it.  Then came the freezing issues.  Same as the issue reported, after about 6-8 minutes of viewing flash content my whole system would freeze.  If I tried to view flash video in fullscreen it would freeze in about 1 -2 minutes on average.  In order to resolve this I had to remove compiz entirely.

```
sudo apt-get remove --purge compiz*
```

Now I can view flash videos (youtube.com, etc) without any freezes in full screen or standard viewing.

Good luck.

---

### Post by Amazona aestiva on 2009-04-26
> **katula said:**
> I ran into this same issue when after upgrading to Jaunty through synaptic.  Firstly, in order to get flash to work at all I had to remove it, and reinstall it.  Then came the freezing issues.  Same as the issue reported, after about 6-8 minutes of viewing flash content my whole system would freeze.  If I tried to view flash video in fullscreen it would freeze in about 1 -2 minutes on average.  In order to resolve this I had to remove compiz entirely.

```
sudo apt-get remove --purge compiz*
```

Now I can view flash videos (youtube.com, etc) without any freezes in full screen or standard viewing.

Good luck.

Thank you very much for your help, but even if you are right, I will not try upgrading again. You know I use AWN, which needs compiz to run, for half which a year now and I love it :D, therefore I'll wait for an update that fixes this issue. Maybe then.

Regards

---

### Post by Amazona aestiva on 2009-06-07
Hi All!

However removing compiz worked well, I finally found out what was the real problem: nVidia driver rev. 180

I do not know why but it is simply bad for my card (GeForce 7300 GS)

So it works with the old one (rev. 173)

Regards,

---

