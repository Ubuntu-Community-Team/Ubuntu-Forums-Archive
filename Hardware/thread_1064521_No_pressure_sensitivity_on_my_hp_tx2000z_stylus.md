---
title: "No pressure sensitivity on my hp tx2000z stylus"
date: 2009-02-08
forum: Hardware
---

### Post by sha.goyjo on 2009-02-08
Hey there,

I'm new-ish to linux, but I've got a mild amount of computer experience. I just put ubuntu on my system after a harrying support adventure, and I finally got the tablet screen to work after following gali98's tutorial. There is only one problem. When I open to gimp (or for that matter any program where sensitivity matters) my stylus gives only two signals, full pressure or none. any ideas on a fix?

---

### Post by Favux on 2009-02-08
Hi sha.goyjo,

If you've already used wacomcpl to calibrate and have generated a .xinitrc that runs each time you login check that you have a line similar to:
```
xsetwacom set stylus PressCurve "0 10 90 100"
```
in the stylus section.

---

### Post by sha.goyjo on 2009-02-09
Further questions:

Is it possible to do this globally by editing the Xorg.conf instead of creating a session specific executable?

How would I set pressure sensitivities for touch and the eraser? Would I just change the command from "stylus" to "touch" or "eraser"?

Thanks for your time.

EDIT/ADDENDUM:

in .xinitrc
1. xsetwacom set touch PressCurve "0 10 90 100" causes device to stop functioning.
2. xsetwacom set stylus PressCurve "0 10 90 100" produces no noticeable effect.
3. xsetwacom set eraser Presscurve "0 10 90 100" produces no noticeable effect. 

I hope that helps. Thank you for your time.

---

### Post by Favux on 2009-02-09
Hi sha.goyjo,

As far as I know pressure sensitivity applies only to stylus and only in programs that support it like Gimp.

In xorg.conf I believe it would be:
```
Option	"PressCurve"	"0,10,90,100"
```
Two inner numbers add up to 100, as do the two outer numbers.  For example:

0,0,100,100
0,10,90,100
5,15,85,95

But why do it that way, since to calibrate you use wacomcpl which generates the .xinitrc?

For more explanation see appendix 2 at:

[http://ubuntuforums.org/showthread.php?p=6546012#post6546012]("http://ubuntuforums.org/showthread.php?p=6546012#post6546012")

Also see section 3.

---

### Post by sha.goyjo on 2009-02-09
wacomcpl produces errors on my system during calibration. All steps proceed fine until I reach wacomcpl. I receive the attached errors there.

Also, even with the PressureCurve lines inserted into my .xinitrc, my stylus shows no pressure functionality. I'll check using it in my xorg.conf to see if it helps. In the mean time, any more advice?

---

### Post by Favux on 2009-02-09
Hi sha.goyjo,

OK, those are new to me.  What version of the linuxwacom drivers and wacom-tools are you using?  Are they the 0.8.1-4 versions in the Intrepid repository (Synaptic)?  Or since you used gali98's tutorial are they 0.8.1-6?

To help I need some more information from you.  What is the make and model of your Table PC.  Which version of Ubuntu are you on?  Which kernel?  What Wacom input devices do you have:  stylus, side-switch, eraser, touch, etc.?  I also think I need to see your xorg.conf.  Please attach it to your next post.

---

### Post by sha.goyjo on 2009-02-09
Actually, in order to make sure we are on the same page, I ran through your tutorial. I have everything up to date, including kernel and linux-wacom driver 0.8.2-2

Also, I'm on an hp tx2000z. Stylus, side switch, and eraser. Everything is set up as per your tutorial. With the "sudo nano" fix for getting wacom into the modules. Wacom activates at boot every time. wacom works in all functionalities except pressure sensitivity. the stylus and touch are both fairly well calibrated from the values in xorg.conf.

Tell me if you have any ideas.

EDIT:
also, doesn't it say PURGE wacom-tools in your tutorial? are they supposed to stay off or go back on? I left them purged.

---

### Post by Favux on 2009-02-09
Hi sha.goyjo,

Given that you ran through my updated version of gali98's tutorial I am rapidly running out of ideas.

My first thought is still that there is something wrong with your xorg.conf.  Maybe in the ServerLayout section.

Also I hadn't heard before of any TX2000 needing martinjochimsen's module fix.  Only TX2500 owners have been reporting that.  That makes me think something went wrong with your compiling.  Or somehow you are loading an old version of the kernel driver.  The wacom tools should still be loaded.  The purge line should remove extraneous stuff, like old wacom tools stuff.  You could retry the compiling part up to and including the cp the kernel driver part.  Then be a little patient, trying a few reboots and a X restart or two before resorting to the fix.

Oh, and on pressure sensitivity.  Have you set up your stylus, and eraser and stuff in Gimp?

---

### Post by sha.goyjo on 2009-02-09
Went back through and did as you said. Still had to use the module fix. Attached is my xorg.conf

EDIT

The pressure sensitivity is reading just fine. The problem was in gimp, as you suggested looking for. That means that we have solved the pressure sensitivity problem. If you want to pursue the other issue further, that's your choice.

---

### Post by Favux on 2009-02-09
Hi sha.goyjo,

Nothing stands out except maybe in eraser.  Try commenting out the mouse section below keyboard.  HAL should be able to run it.  Also comment out PressCurve in stylus and especially eraser.  I don't think it belongs in eraser.  Restart.  Then try wacomcpl again.

I have my fingers crossed.

---

### Post by sha.goyjo on 2009-02-10
No dice my friend. It's all commented out but still no calibration. Also, pressure sensitivity worked in gimp with those lines commented out.

Don't know if that helps you any.

---

### Post by Favux on 2009-02-10
Yeah Gimp kind of does input its own way.

So no wacomcpl calibration gui?  About the only thing left I can think of is to examine your Xorg.O.log in your System Log and see if anything unusual is happening during the linuxwacom initiation.  You usually start seeing in about 2/3 of the way down, starting near the first instance of your stylus's pci path.  If something does seem to be happening, try rebooting and seeing if it's reproducible.

---

### Post by sha.goyjo on 2009-02-10
Where is that log located?

---

### Post by Favux on 2009-02-10
Sorry, it's in System>Administration>System Log.  I'll attach the relevant part of mine.

---

### Post by sha.goyjo on 2009-02-10
*

---

### Post by Favux on 2009-02-10
????? !

---

### Post by sha.goyjo on 2009-02-11
sorry about that last post. Anyways, I'm not gonna bother posting my log, because it matches yours to a tee (excepting the stock calibration values on mine). I know this is frustrating. As far as I'm concerened, the tablet is pretty well calibrated as is. Not being able to calibrate with wacomcpl isn't going to kill me in any way, shape, or form. that being said, if you can think of a fix, I'd be greatful

---

### Post by Favux on 2009-02-11
Hi sha.goyjo,

While we talked about your .xinitrc, I didn't ever see it.  In order to have one I'd think wacomcpl worked at some point.  So is it your latest run through the tutorial that "broke" wacomcpl?  I'll attach mine for comparison.

While we're at it let's look at your xinitrc.  Go to "/etc/X11/xinit/xinitrc.  Everything in it should be commented out. If you see something like:
```
# invoke global X session script
. /etc/X11/Xsession
```
try commenting it out like so:
```
# invoke global X session script
#. /etc/X11/Xsession
```

---

### Post by sha.goyjo on 2009-02-11
I commented that line out and rebooted. No effect on our problem.

---

### Post by Favux on 2009-02-11
Hi sha.goyjo,

Further proof something is going on.  Your stylus, etc. should not have been working right with that line invoking the Xsessions script.

A clue must lie in those error messages.  I just can't spot it.

At this point I'm throwing in the towel and chalking it up to something idiosyncratic in your set-up.  Hopefully, with the next kernel or linuxwacom update, running through the tutorial again will fix it.

If you have any more thoughts?

---

