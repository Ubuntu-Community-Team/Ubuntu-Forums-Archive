---
title: "volume control on toshiba laptop broken"
date: 2008-12-13
forum: Hardware
---

### Post by jtofu on 2008-12-13
hello,

i've recently made the switch to linux after about ten years of thinking about it.  i really like it a lot.  recently, i upgraded from hardy to intrepid.  with the upgrade, i've lost control of my volume dial on the side of my toshiba u300 laptop.

when i try to turn up, or down, the volume with the dial, it seems to repeat the volume adjustment.  this makes the speaker icon pop-up on the screen and flash on and off.  this also makes me loose control of my mouse buttons.

i think i found a fix here: [http://lists.freedesktop.org/archives/xorg/2008-June/036373.html](http://lists.freedesktop.org/archives/xorg/2008-June/036373.html) but i don't how to implement it.

could someone help me with a walk-through?  or tell me if the above will even work?

thanks,

tofu

---

### Post by turelincon on 2008-12-13
Mine too!  
  Thanks for whatever you've done to get Wubi/Ubuntu 8.10 to load on my Toshiba G25-Av513. Have attempted it on the past two distros, and at last either I've not been shutting down Windows properly all along, or the and the machine is running the bugs into the corners. Some sound problems, can't get the onboard mike to work with Skype phone conversations. The external volume control throws up an icon when you twist it, bargraph slides back and forth; but there is no change to the actual sound volume. Pull up the volume control window and the sliders in it work just fine quite similar to that big-hard to work on operating system. But none of the sliders in the sound volume display are adjusted when the external volume control knob spins. Seems to run kinda hot. 
Other than the quirks in my hardware the system runs great. Beginning to figure out those packages, got Thunderbird up and running. The rubber windows were a little much for me, that came with the Nvidia driver. The wireless and Cat5 network connections work fine, even simultaneously. The display is clear and crisp. It took a while to get the DVD player to work. Some old style CDs that worked in the "big-hard" operating system wouldn't pickup in Linux. Boot it up and it runs for days smooth and clean. The latest service pack for XP totally trashed my system, couldn't import user settings from SP2 to SP3 going in and continued crashing after uninstall, until reformatted and reloaded. I just can't spend the rest of my life rebooting. Thanks for allowing me to feel the power of this laptop with out that famous crippleware system. If I never see a security alert again it will be too soon. Somebody call Toshiba make'em deliver the video drivers for the tuner, and video I/O. I'll keep trying.

---

### Post by sarbruis on 2008-12-30
I have this problem as well.  The dial worked when using Gutsy, but I've just switched to Intrepid and it's doing what the OP described.  Is there any way to disable the dial?

EDIT: I found how to disable the dial.  System -> Preferences -> Keyboard Shortcuts; then I disabled "Volume up" and "Volume down", which were apparently controlled by the dial.

---

### Post by thingy87654321 on 2008-12-31
on my toshiba satellite m45-s351 laptop, the volume control knob is broken off, is there anyway to disable it software wise so the laptops speakers work?
 
i have figured out how to override the volume switch physicsly,
but removing the motherboard and sodering  the 2 and 3 pin together on the volume control base thingamagiger
but i dont want to do that just yet
:shock:](*,)

---

### Post by goodrench on 2009-02-14
I have a u300  toshiba with the same condition.
I have disabled the volume up and down in keyboard shorcuts and that works fine.
I just tried the 64 bit version of jaunty 9.04 and the condition is still present.
I also found this page that sounds like the same bug.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271706)
I sure hope that this will be fixed soon.

---

### Post by meditatingfrog on 2009-02-22
I have the same issue.  I have a toshiba u305-s7448.  I disabled the volume up and down in system -> preferences -> keyboard shortcuts.  I'm going to try reassigning the up on the knob to up volume, and down on the knob for down volume to see if reassigning will fix the issue.  

Incidentally, I already used gconf-editor to change the increments to 1% (previously, the incremental bumps were too great).

EDIT:  Disabling then reassigning the key values didn't do the trick.  I wonder why it worked in hardy for me, but now in Intrepid it doesn't work.  It's a Mystery.

EDIT:  I reassigned the volume up to 'cntrl uparrow' and down volume to 'cntrl downarrow'.  Oddly, I don't have to restart after attempting to turn up the volume with these keys, BUT, it doesn't actually turn the volume up.  It just displays the volume control graphic, but the actual volume slider bar doesn't move.

---

### Post by jurusu on 2009-10-30
> **meditatingfrog said:**
> 

EDIT:  I reassigned the volume up to 'cntrl uparrow' and down volume to 'cntrl downarrow'.  Oddly, I don't have to restart after attempting to turn up the volume with these keys, BUT, it doesn't actually turn the volume up.  It just displays the volume control graphic, but the actual volume slider bar doesn't move.

I reassigned the same way you did ctrl+up and ctrl+down and it worked like a charm. I am using Karmic. But still i would love to use the dial instead of the keys. I hope they can find the solution fast.

---

### Post by goodrench on 2009-10-31
> **jurusu said:**
> I reassigned the same way you did ctrl+up and ctrl+down and it worked like a charm. I am using Karmic. But still i would love to use the dial instead of the keys. I hope they can find the solution fast.

Fast????
Doesn't look like it. This has been around for a while now.
Bugs have been reported. This will likely  NEVER get fixed.
Sometimes developers think that this kind of workaround is "good enough".

---

### Post by gnanavale on 2011-03-23
I too have the same type of problem. my mike is working, but my opponent cannot able to hear me properly. they complaining like my volume s low. how to increase my mike volume further. i tried in the sound preferences, but i cant succed.. kindly suggest...

---

### Post by meditatingfrog on 2011-03-23
> **gnanavale said:**
> I too have the same type of problem. my mike is working, but my opponent cannot able to hear me properly. they complaining like my volume s low. how to increase my mike volume further. i tried in the sound preferences, but i cant succed.. kindly suggest...

you can try "alsamixer" in a terminal.  i need to have frontmic to 50% in order for someone to hear me.  unfortunately, pushing it above this causes distortion.

i'm in #ubuntu-beginners on irc, nickname jhanafrog.

---

