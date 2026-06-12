---
title: "sixaxis, ps3 wireless, oneiric"
date: 2012-01-06
forum: Hardware
---

### Post by checkup on 2012-01-06
Hello.

I was using a third-party ps3 wireless controller with ubuntu happily for quite some time now. It's one of the Gasia type controllers.

What i had to do was use jstest to calibrate the joystick and load the correction at boot. No problem there.

Now with oneiric, the controller reports 28 axes instead of six. Which totally confuses me and the apps i'm using.

How do i restrict that to the "old" 6 analog axes and n buttons?

 best regards

---

### Post by survient on 2012-01-11
check out 'jscal'. I'm not sure if ubuntu the latest jscal is patched to support remapping axis and buttons but I was able to use this to remap all my buttons and axis to lower values. A great help to figure out the mapping is joydevmap. While I had issues with joydevmap performing the remapping, it showed me the values to use with jscal instead. The option you are looking for is 'jscal -u'. Try 'jscal -h' to see if it has this flag available, if not then get a patched version of jscal that supports button remapping and compile it to a random folder. Use jstest to see what buttons are mapped to what values and take it from say button 18 down to button 4.

The issue is that the button and axis values are so high that most programs freak out and don't recognize them. Using jscal I was able to remap them to lower numerical values all within the comfort range of the program.

Now if I can only get the motion control to work via USB...

Also pressure sensitivity in linux owns.

---

