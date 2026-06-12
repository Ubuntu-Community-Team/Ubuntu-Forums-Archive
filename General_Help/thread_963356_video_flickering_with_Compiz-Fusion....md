---
title: "video flickering with Compiz-Fusion..."
date: 2008-10-30
forum: General Help
---

### Post by muddi900 on 2008-10-30
All video in VLC flickers after I installed Comiz.

What should I do?

---

### Post by DerHesse on 2008-10-30
You could turn off some of the modules in the compiz settings manager: trial and error.

I had problems when I enabled the caps on the 3d Desktop-Cube. No Video was shon at all by then. Turned it of and it was fine again.

---

### Post by loomsen on 2008-10-30
> **muddi900 said:**
> All video in VLC flickers after I installed Comiz.

What should I do?

Either post some info about your hardware, installed drivers and your config.

Or you can use the "workaround" and simply buy a blue-with-red-dots computer next time. Ignore people talking about "inner values" or such, most likely you won't have a look at your bare-naked graphics card more than 5 times in its lifetime. Ridiculous.

OK, my turn... I'm looking at sth you don't see, and it is blue-with-red-dots...


sudo /etc/init.me/sarcasm stop..............................  [COLOR="Red"][failed!][/COLOR] ([COLOR="Red"]using default values...[/COLOR]) 


You maybe just have to add a (maybe hardware) specific Option to your xorg.conf, or your lacking some codecs, or you might just give another player a try, or try SMS-Guru, he claims to answer any question.

---

### Post by leodp on 2008-10-30
> **muddi900 said:**
> All video in VLC flickers after I installed Comiz.

What should I do?

What kind of graphic card do you have?
If it is an ATI there are limitations on how video/openGL applications are rendered in compiz.

Solution should come with DRI2, most probably in a few months time (new xorg/xserver and ati driver releases).

Workaround for video: render video using x11 and not xv. When in full screen it should not flicker.
I do not know VLC, but from the command line you can try:
mplayer -fs yourvideo.avi
(flickers)
mplayer -fs -vo x11 yourvideo.avi
(should not flicker)


Leodp

---

### Post by muddi900 on 2008-10-30
I have an Ati 4850 and I am using the Ati Propreity drivers.

---

### Post by toystory on 2008-10-31
I know this is no final solution, but this worked for me at least...

Learned it in the forums elsewhere..

sudo apt-get install fusion-icon

This will install a program that switches Compiz on and off :) I turn it off for video, and then on for everything else :) 
If not, switch all playback methods to X11 (no XV). 

Best regards, 
Toystory

---

### Post by fooey on 2008-11-01
> If not, switch all playback methods to X11 (no XV). 

ya. that worked for me a while back.

---

### Post by zika on 2008-11-01
can I use x11 in totem or is it just for mplayer? 

if I can, how to try that (unless it is fullscreen and I do not want to use that)?

it seems that mplayer that is offered in intrepid repositories is an old version, am I right?

just to add, when I have compiz enabled (either normal or full) I have flicker (just in that part of screen where video is played) even in a fulscreen mode.

VLC did not help much since most of the videos vere not played correctly, and many were without sound.

in compiz->None mode everything (totem) is OK. VLC is problematic in all three modes.

---

### Post by iblazev on 2008-11-07
As said before, when using x11 in mplayer, the video doesn't flicker but the picture is only the windows size and doesn't resize to full screen. When using gl picture can be resized to full screen but flickers....
So how to watch x11 in full screen and not in a small window?

---

### Post by alwayshere on 2008-11-07
try compiz switch [http://forlong.blogage.de/entries/pages/Compiz-Switch](http://forlong.blogage.de/entries/pages/Compiz-Switch)

---

### Post by Evzen on 2008-11-07
> **iblazev said:**
> As said before, when using x11 in 
So how to watch x11 in full screen and not in a small window?
Put the line
```
zoom=yes
```
into the file ~/.mplayer/config and x11 video should be displayed properly in fullscreen.

---

### Post by iblazev on 2008-11-07
> **Evzen said:**
> Put the line
```
zoom=yes
```
into the file ~/.mplayer/config and x11 video should be displayed properly in fullscreen.

It worked great! quite simple solution really:) Thanx!

---

