---
title: "[SOLVED] No Skydome?"
date: 2008-09-08
forum: General Help
---

### Post by Another Monkey on 2008-09-08
See the two posts after mine for the details.  basically, if the image is too big it won't display.  Makes sense.

---
I have been playing with Ubuntu today, fresh install on an old laptop.  Everything has gone pretty well and all I needed to do to get the compiz stuff running was the skip_check hack (I have an ATI Mobility Radeon 9000 graphics card).

Only that doesn't appear to work is Skydome.  I've downloaded a couple of images and tried them - no joy.  Anyone any clues?

The first post [here]("http://ubuntuforums.org/showthread.php?t=913803") contains details of my setup.

I should add that I'm pretty new at this....

Thanks!

---

### Post by Another Monkey on 2008-09-09
Well, I found that reducing the size (e.g. from 4000x2000 down to 2000x1000) allowed me to get a Skydome picture up.  Although the animation doesn't seem to do anything (yes, I downloaded an animated picture - correction, I donwloaded an image that claimed to be animated).

I guess I'll try reducing it again and seeing if that helps (I am guessing it's a plain old memory issue).

Or do I need to do something fancy to get the animation working?

Hmm...guess I also better check that I downloaded the correct picture.  I am going look a right div if that's what the problem is!  (Situation normal then....)

---

### Post by luxorvan on 2008-09-09
Under image loading in ccsm it only list's jpeg,png,svg and text. Although I've never tried to use any type of background like you propose! By selecting to animate the skydome will only rotate the image as you turn and rotate the cube I don't think it supports animations. Perhaps the image type you have or want is the problem and isn't supported by compiz at all?

---

### Post by sayakb on 2008-09-09
You need to use an image which is smaller than or equal to the largest image size supported by your graphics card. Plus, for an animated skydome, you do not need an animated image. Just **check** the Animated Skydome checkbox to get a rotating image as you rotate the cube.

---

### Post by Another Monkey on 2008-09-11
Ahhh....right...the penny drops.  I thought by "animated" it meant some kind of colouring shifting, basic movie or something.  That's cool, all makes sense now.

Thanks.

---

