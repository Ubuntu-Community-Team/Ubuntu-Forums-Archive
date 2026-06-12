---
title: "Logitech Dual Action Gamepad?"
date: 2007-06-04
forum: Hardware &amp; Laptops
---

### Post by cmillican on 2007-06-04
I recently bought the above gamepad, thinking it should work since it said PnP. I thought it would work like some joysticks I've used, where you hold down the joystick button then click the keyboard key you would like to program it to, but that's not so. It has M$ software to program it, and I haven't found any software where I can do that.

It turns out all the buttons work, it's just everything without a number on it (the D-pad and the two thumbsticks) that doesn't register when I'm trying to program it in TORCS (a racing game if you don't know). I went to look for people with similar problems and I used jscalibrator and tried to follow all of the instructions, but none of them were very clear, and I couldn't get which lines I was supposed to actually type in for this gamepad.

Any help is greatly appreciated.

Chris

---

### Post by dfreer on 2007-06-04
I have this gamepad, I <3 logitech! 
That being said, I haven't had any problems with linux recognizing it's keypresses whatsoever, used it with ZSNES, pSX, FCEUltra. no need for jscalibrator so far.
There is a button just below the number 9 button that says "Mode", this will swap the dpad with the left joystick, and the 1-4 buttons with the right joystick. however you should be able to use these independently of each other.
Lemme try finding and downloading this TORCS game, see if I have the same problem. you might just have a bad gamepad.

---

### Post by dfreer on 2007-06-04
I didn't really have any problems with setting the controls for this game, the only thing I had to do was set the axis for steering left and right. I noticed that it seemed to recognize only one axis, so I went into the games Calibration and it told me to hold down left and press a button, and then hold down right and press a button. This correctly detected the left joystick axis for me.

crap I'm not very clear, lemme see if I can get some screenshots up for you if that didn't make any sense. let me know!

---

### Post by cmillican on 2007-06-04
Well I don't know what happened with mine, because I tried to set it up in Zsnes and when I try to set the D-pad or analog sticks to anything it doesn't do anything, as if they're not being registered.

Thanks for your help.

Chris

---

### Post by junglist313 on 2008-01-07
I am having this same problem. I have a logitech dual action and when i run jsconfigurator it recognizes all the axis on both sticks. but when i run kxmame the buttons register but not the joysticks or the d-pad. I have tried just about every possible combination of settings, with the mode button lit, without, using only d-pad, using only sticks. Have tried all the different settings under control options in kxmame to no avail. 

The location of the dual action is /dev/input/js0 

Any ideas?

---

### Post by Databit on 2008-03-23
Hey junglist313 did you find a fix for this. I'm having the same issue.

---

### Post by Databit on 2008-03-23
I know I specified that last question too junglist313 but if anyone else has an answer it would be appreciated. Basically my axis sticks and dpad don't register inside of game play. They work in jcalibrate but not in any emulators. 
Any ideas?

---

### Post by dfreer on 2008-03-23
Supposedly jcalibrate messes up these controls, see these threads for some more information:
[http://ubuntuforums.org/showthread.php?t=729049&highlight=logitech+dual+action](http://ubuntuforums.org/showthread.php?t=729049&highlight=logitech+dual+action)
[http://ubuntuforums.org/showthread.php?t=586160&highlight=logitech+dual+action](http://ubuntuforums.org/showthread.php?t=586160&highlight=logitech+dual+action)

---

