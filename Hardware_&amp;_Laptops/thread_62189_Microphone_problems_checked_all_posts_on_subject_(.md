---
title: "Microphone problems: checked all posts on subject :("
date: 2005-09-03
forum: Hardware &amp; Laptops
---

### Post by meraya on 2005-09-03
Guys 

i checked all the post on the subjuct "microphone" (123 posts) and i could not figure out what the fcuk is wrong with it  :) 

Here is what i get from the Control Centre - Sound System: 

"Sound server informational message
Error while initialising the sound driver
device: default can't be open for capture (device or resource busy).
The sound server will continue, using the null output device."

I tried checking the mic on gnome meeting and this is what i get:

"impossible to open the selected audio device (ESS ES1938 (Solo-1) for recording. Please check your audio setup, the permissions and that the device is not busy).

I tried all possible checking and unchecking of microphones lines in and all the other stuff suggested in the posts.
My microphone was working perfectly with SUSE 9.1 and i'm reaching the top of the frustration and on monday i have to start working with Skype and Gnome meeting!

Please help
Cheers
Meraya

---

### Post by evilghost on 2005-09-03
Since that card doesn't support hardware mixing, have you tried killing ESD?

```

killall esd

```

Then, try Skype.

---

### Post by meraya on 2005-09-03
Thanx evilghost, 

this is what happens if i try to killall esd: 

esd: no process killed

i tried anyway skype and of course no luck 

any idea?
Meraya

---

