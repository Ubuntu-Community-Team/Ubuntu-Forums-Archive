---
title: "fjbtndrv on Fujitsu T5010 Tablet PC on 10.10 Maverick"
date: 2010-10-07
forum: Hardware
---

### Post by fozzytbear on 2010-10-07
I recently ran the update manager and allowed it to install all recommended updates.  Now the screen rotation and side buttons no longer function.  This functionality was supported by the fjbtndrv package (which is available via a private repository).  It was all working fine (after a very simple installation) until I ran this update.

I've tried removing the package and reinstalling it, to no avail.

If I run fscd and press a button I get the following error:
"BadValue (integer parameter out of range for operation)"

If I run fscrotd screen rotation appears to work but the wacom input is not rotated.

Note that all of these functions worked perfectly on Maverick before running the update manager.  So something I updated broke all of this.  Also before removing and then reinstalling all of the packages for fjbtndrv neither fscd nor fscrotd worked at all.  So doing that fixed something.

So now I'm left hobbling along with no worthwhile screen rotation and no side buttons (like the one for rotating the screen manually).

I'd like to troubleshoot this further, but I'm a little lost with regards to where to look for debug information.  It's not a particularly popular package (only in private repository) and the documentation is a bit lacking, even in forums.

Any ideas?

---

### Post by kathleenhenri on 2010-10-08
The same thing has happened to me with my T730 in both Lucid and Maverick RC. I have been in contact with the maintainer of the fjbtndrv driver, Robert Gerlach, and he knows there is a problem. He said that the issue will be fixed and the driver re-released soon.

---

### Post by khnz on 2010-10-08
Hello,

I have uploaded new packages. What problems still exist?

---

### Post by kathleenhenri on 2010-10-08
All works fine now on my T730!
Thanks so much!

---

### Post by fozzytbear on 2010-10-09
That's better, but not quite.  The screen now automatically rotates and the buttons work.  fjbtndrv is clearly starting like it used to (green status indicator when gnome starts).

However, the vertical orientations are not the right resolution (bottom half of screen is cut off), and it appears the tablet/wacom coordinates were not rotated properly.

---

### Post by naviathan on 2010-10-10
I have the same problem on a T5022D.  Everything appears to rotate except the resolutions don't change and I end up with half the screen.  Also I started with Maverick and I had to use an xorg.conf I found by googling to get the screen to rotate.  Before the screen wouldn't rotate but the wacom did and the stylus would work on the rotated orientations.  Any help is appreciated.

---

### Post by kathleenhenri on 2010-10-11
I tried the updated driver with Maverick and it was still buggy. It doesn't seem to be quite ready for release yet. Some have suggested trying the driver with the visual effects turned off. System-> Preferences-> Appearance->Visual Effects. 

Because the driver works quite well with Lucid, I am staying with that till the issues are resolved.

A link to another T730 and Ubuntu.
[http://thelackthereof.org/Fujitsu_Lifebook_T730](http://thelackthereof.org/Fujitsu_Lifebook_T730)

---

### Post by naviathan on 2010-10-11
I don't think the problem is the driver.  I've tried manually doing an xrandr rotate and it does the same thing (except for rotating the wacom of course).  So the screen rotation problem is something to do with a change made in Maverick.  I noticed the module used for the video is i910 module.  Shouldn't there be a driver better suited for the i855gm?

How did you get Lucid to work?  My T5022D won't boot Lucid at all.  It freezes 2 seconds after the splash screen and I can't get to a terminal at all.

---

### Post by naviathan on 2010-10-11
I turned off the window decorations and everything works perfectly now.  I just wish it would rotate right first instead of left.

---

### Post by fozzytbear on 2010-10-11
For the record this was working in Maverick RC2 (I think that's what I started with).  It was an update issued in the last week or two that broke it.  I don't think the update was from khnz (Robert Gerlach).  I'm guessing it was a package that changed functionality, and this broke things for the fjbtndrv package.

I will check out how things work without screen decorations.  However, things were working before.

---

### Post by naviathan on 2010-10-11
I dont think fjbtndrv is broken.  I think it's either xrandr or possibly something in gnome stopping the screen from rotating and shifting the resolution properly.

---

### Post by fozzytbear on 2010-10-12
Agreed.  I'll add that I ran the following command after rotating the screen and letting fscrotd handle rotating the tablet:

```
xrandr -o r
```

You can replace 'r' with 'l', 'inverted', or 'normal' depending on how you rotate your screen.  This worked perfectly.  However, I had to issue a similar command to rotate the screen back

In the past I wrote a shell script and placed 3 icons (for each rotation) on a toolbar.  However, the whole beauty of fjbtndrv is that it does the rotation automatically.  I think you could write this script and set it up to be run by fscrotd.  I believe you just place the script in '/home/USR/.fjbtndrv'.  However, I don't know what you should call it, or how it should be formatted.  Supposedly there are ENV variables describing the orientation, but I can't find them when I run printenv.  Maybe they are in source code only?  Here is a link describing briefly the existence of the scripts:  [http://sourceforge.net/apps/mediawiki/fjbtndrv/index.php?title=Usage_hints#Event_Scripts](http://sourceforge.net/apps/mediawiki/fjbtndrv/index.php?title=Usage_hints#Event_Scripts)

But I wonder if the syntax for xrandr changed or, maybe how's it being invoked by fjbtndrv?

Looking at the source code for rotation.c, and considering the problem I'm having (wrong visual resolution, right rotation and tablet resolution) I think there is probably a problem with the way the 'sz' variable is being determined originally, or how it's being handled by the xrandr.h extensions.  I'm not prepared to dive into that too much due to lack of free time and confidence...

---

### Post by naviathan on 2010-10-12
I've been thinking about it and I think the problem is more an issues with the gnome window decorations.  Once they're disabled everything works just fine.  There's some scripts in /usr/lib/fjbtndrv, but I can't quite figure out if they can help disable the other rotations.

---

### Post by fozzytbear on 2010-10-12
I just killed gtk-window-decorator, and the screen still wasn't rotated properly.  How did you go about disabling it?

---

### Post by naviathan on 2010-10-12
System > Preferences > Appearance > Visual Effects

---

### Post by fozzytbear on 2010-10-12
Yeah.  That didn't work...

---

### Post by naviathan on 2010-10-13
I have no idea then.  It worked immediately for me.

---

### Post by fozzytbear on 2010-10-13
Looks like khnz pushed out a new update in the last day or two which seems to be working fine for me now.  So I'd consider this solved for me.  Thanks everyone.

What about you naviathan?  After installing the latest update does it work with window decorations?

---

### Post by naviathan on 2010-10-13
I'll have to give it a go when I get home.

---

### Post by naviathan on 2010-10-14
Negative on the window decorations.  It's probably something to do with my video card.  This is an older Stylistic tablet so it's not the most graphics intensive machine.

---

### Post by naviathan on 2010-10-15
I sent a message to khnz about the rotation issue and he sent me a diff for the code changes to limit the rotation to right or normal which is perfect!  Anyway, thought someone might like the code:

```
diff --git a/src/rotation.c b/src/rotation.c
index a9e9eb5..a78758a 100644
--- a/src/rotation.c
+++ b/src/rotation.c
@@ -217,9 +217,7 @@ void rotate_display(Display *display,
Rotation rr,
int mode)

   sz = XRRConfigCurrentConfiguration(sc, &cr);
   if(!rr) {
-        rr = (cr & 0x7) << 1;
-        if(!rr)
-            rr = RR_Rotate_0;
+        rr = ((cr & 0xf) == RR_Rotate_0 ? RR_Rotate_270 :
RR_Rotate_0);
   }

   if(rr != (cr & 0xf)) {

```
It didn't work for me as a patch, but I can read what lines to remove and what to add from that so it wasn't hard.  Also he said version 3 will have a GUI for easy configuration of these options.

---

### Post by naviathan on 2010-11-08
I have one issue now that has been irritating me.  When I initially boot my slate it comes up with the screen rotated to the right position, but the desktop is in the normal resolution, meaning the desktop covers half the screen.  The digitizer I think is inverted or left.  Interestingly enough if I pass "xrandr -o right" from a terminal after login it snaps the desktop to size and everything works.  I tried setting this as a startup program and when set that way the digitizer stays in an inverted or left orientation while the dekstop properly takes the right orientation.  Any way I cut this, if I press the rotate button everything aligns properly and I can go about my business, but I have to press the rotate button to get it.  I realize this was a lot of jumble so I think my best way to put this is:
 
On initial login, why does the screen come up rotated instead of at the normal orientation?
Why doesn't the orientation of the digitizer and the desktop match on initial login?

---

### Post by hempytree on 2010-11-13
hi ; same problem here (on a t3010 ; vga is 855gm)
fjbtndrv is working fine ; rotates wacom with xrandr

problem with screen mis-aligned in portrait orientation ; I can click on where the button should be, not where it appears
[IMG]http://www.imageno.com/t0ajjth10rp1pic.html[/IMG]

is there a way to ajust screen position (tried xrandr -pos but no succes)
thanks

---

### Post by naviathan on 2010-11-13
> **hempytree said:**
> hi ; same problem here (on a t3010 ; vga is 855gm)
fjbtndrv is working fine ; rotates wacom with xrandr

problem with screen mis-aligned in portrait orientation ; I can click on where the button should be, not where it appears
[IMG]http://www.imageno.com/t0ajjth10rp1pic.html[/IMG]

is there a way to ajust screen position (tried xrandr -pos but no succes)
thanks

Turn off window decorations

---

### Post by kuppi on 2010-11-14
> **hempytree said:**
> hi ; same problem here (on a t3010 ; vga is 855gm)
fjbtndrv is working fine ; rotates wacom with xrandr

problem with screen mis-aligned in portrait orientation ; I can click on where the button should be, not where it appears
[IMG]http://www.imageno.com/t0ajjth10rp1pic.html[/IMG]

is there a way to ajust screen position (tried xrandr -pos but no succes)
thanks
Have the same problem here (also with a t3010). However, if you use the rotation button besides the screen, it works perfectly. Give it a try.

Turning window decorations off or on, doesn't change anything in my case.

---

### Post by hempytree on 2010-11-19
turning visual effects worked for me ; thanks

---

