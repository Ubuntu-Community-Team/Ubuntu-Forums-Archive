---
title: "Global mouse hotkeys?"
date: 2008-11-03
forum: General Help
---

### Post by Mcgeesteh on 2008-11-03
Hi,

I would like to use the side buttons on my mouse to switch workspace no matter what program I have open. I have the 'viewport switcher' option enabled in Compiz, but when I am using something like firefox for example it overrides my side mouse buttons for 'back' and 'forward' so it no longer changes workspaces.

Another quick thing that slightly bugs me- when I drag windows to the edge of the screen to move them to an adjacent workspace- as the screen flips to the next workspace the mouse will stay on said edge such that the workspaces keep flipping back and forth because the mouse is right on the right edge- it changes workspace so the mouse is on the left edge- so it changes back etc.. Can I make it so the mouse snaps to the middle when a window is dragged across workspaces?

Any help is appreciated, Thanks.

---

### Post by loomsen on 2008-11-03
Open up ccsm, and go to 

Desktop --> Rotate Cube

[[img]http://img112.imageshack.us/img112/5663/screenshot49ra3.th.png[/img]](http://img112.imageshack.us/img112/5663/screenshot49ra3.png)

Hint: Sometime, well, often more likely you won't be able to make up what exactly an option does. But, as compiz usually applies such Options instantly, I'd suggest going to the max/min if you're unsure and look what has changed.

*edit*

Yeah, your mouse key...
I'm sure you may set a global button, but, as it's not always nice to override any other programs behavior imho, you might want to do it like me.

[[img]http://img120.imageshack.us/img120/9082/screenshot50cw3.th.png[/img]](http://img120.imageshack.us/img120/9082/screenshot50cw3.png)

I set combined it with screen edges. So if I move my mouse to the edge of my screen an then hit the right button, I switch to the next slide.
Moving to the top and holding right button initiates manual rotation. 
Compiz will draw a non visible border of 1 pixel then, so you can access it from everywhere and regardless of maximized/open windows.

---

### Post by Mcgeesteh on 2008-11-03
Thanks for the reply.

I set the "flip time" to zero which seems to make dragging windows across workspaces alot easier.
I'm not sold on the screen edge workspace switching though :p I tried it and it seems a bit unnatural for me- and I never use the side mouse buttons for anything else so I'll keep trying.

Just to be annoying another question :)

When the cube is in free rotate mode and I release it it seems to take a very long time to 'fall back into place' where I can start using my desktop again. None of the sliders seem to change how fast it snaps back from the cube effect to being normal, and pointers here?

---

### Post by loomsen on 2008-11-03
Try under Desktop Cube --> Behavior

There you've got sliders for accel, timestep and speed of folding/unfolding the cube.

Tho, they should be ok as they ship... Dunno exactly, I'm running compiz from git... Runs flawlessly here.

---

### Post by Mcgeesteh on 2008-11-04
I tried the accel etc however they don't change the thing which was annoying me in the first place. The windows snap back into the screen off the cube easily. However if I have '3D windows' for the cube enabled, the windows still come back normally but the desktop takesl about 3 seconds to zoom back in.

---

