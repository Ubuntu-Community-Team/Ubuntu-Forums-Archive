---
title: "Intrepid Multimedia Apps crashing"
date: 2008-11-01
forum: General Help
---

### Post by das7002 on 2008-11-01
I upgraded my Acer Extensa from Hardy to Intrepid and now everytime I try to run Totem to play something it crashes I did decide to run it from the Terminal and I got this for output
```
david@david-laptop:~$ totem
** (totem:7285): DEBUG: Init of Python module
** (totem:7285): DEBUG: Registering Python plugin instance: YouTube+TotemPythonPlugin
** (totem:7285): DEBUG: Creating object of type YouTube+TotemPythonPlugin
** (totem:7285): DEBUG: Creating Python plugin instance
** (totem:7285): DEBUG: Init of Python module
** (totem:7285): DEBUG: Registering Python plugin instance: BBCViewer+TotemPythonPlugin
** (totem:7285): DEBUG: Creating object of type BBCViewer+TotemPythonPlugin
** (totem:7285): DEBUG: Creating Python plugin instance
**[COLOR="Red"]And here is where I open the file[/COLOR]**
The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'. **[COLOR="Red"]Odd I have plenty[/COLOR]**
  (Details: serial 46 error_code 11 request_code 140 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```
I tried reinstalling all of gstreamer and Totem I even tried VLC both Totem and VLC experience this issue yet Rythmbox has yet to crash please what is wrong?

(Addl Inf. I did a fresh install of Intrepid, installed the "ugly" codecs and from then on I have had this yet as I said it appears as Rythmbox is immune to this somehow)

---

### Post by crazybilly on 2008-11-01
I'm having the exact same problem on my Acer Extensa (new Intrepid install) as well.

Any solutions?

---

### Post by das7002 on 2008-11-01
At least I am not the only one

Anyone know what is wrong?

---

### Post by crazybilly on 2008-11-02
My problem went away.  I just needed to get the (restricted) ATI driver installed. 

For whatever reason, that seemed to fix it. Although now, I get some really annoying flickering when I play multimedia (which I have a sneaky suspicion has something to do with Compiz...but I haven't looked into it yet).

I just needed to open the System->Hardware Drivers and enable the ATI driver, then reboot (maybe I could have just logged out and logged back in? dunno).  

Hope that helps!

---

### Post by das7002 on 2008-11-02
Hmmm I only got the flickering on 8.04 I will try with the Restricted Driver although I don't think I would need it I get higer FPS w/o it then 8.04 could get with it

---

### Post by das7002 on 2008-11-03
It worked yet now I get a rather annoying flicker anyone know how to fix that? Or is there a way to get the Multimedia apps to not crash while using the default driver not the restriced one? Please I want to know

---

### Post by crazybilly on 2008-11-04
Have you tried multimedia aps in a different desktop environment (like openbox or something)? I haven't given it a go yet--I need to. But I have a sneaky suspicioun that we're getting some sort of wierd compositing-type errors.  

If I remember to test it out, I'll report back.

Also, I had problems w/ my sound being really quiet on my Extensa 4420 in Intrepid.  I ran ```
alsamixer -Dhw
``` and pumped up everything (part. the PCM and front spkr). Problem solved.

---

### Post by das7002 on 2008-11-04
> **crazybilly said:**
> Have you tried multimedia aps in a different desktop environment (like openbox or something)? I haven't given it a go yet--I need to. But I have a sneaky suspicioun that we're getting some sort of wierd compositing-type errors.  

If I remember to test it out, I'll report back.

Also, I had problems w/ my sound being really quiet on my Extensa 4420 in Intrepid.  I ran ```
alsamixer -Dhw
``` and pumped up everything (part. the PCM and front spkr). Problem solved.


Oh Hardy did the same thing with the sound also to make the Mic work go over to recording a raise it all the way up (Not the second one if it is there that makes it echo the mic back to you)

Also I will see about trying it with Metacity as I have read around the forum that it is GNOME and I would have thought that by now this would have been fixed yet anyway I don't care it is still better then Windows (GO BSOD!!! :lolflag::lolflag::lolflag::lolflag:)

---

### Post by johntinsley on 2008-12-12
I have the same problem, but when I install the restricted driver my x-server stops working. I have to reboot in recovery mode and then I'm back to square one.

Can anyone help with this?!

---

### Post by crazybilly on 2008-12-12
I've since done some research--the flicker is an ATI+compiz problem.  You can resolve it by changing the video output to something like X11 (from xvev, iirc). 

Not too hard to do in mplayer and vlc...I'm not too sure about totem, though.

As far as the crashing goes...if installing the restricted ATI driver doesn't help, I'm not going to be much help--I'm clueless :D

---

