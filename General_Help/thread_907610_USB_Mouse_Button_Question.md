---
title: "USB Mouse Button Question"
date: 2008-09-01
forum: General Help
---

### Post by FokkerCharlie on 2008-09-01
Hi All

I have a small problem with my USB Logitech Trackman under Hardy- it is a 10-button device, and actually works rather well.

Apart from this- above and below the scroll wheel, which I would like to use as scroll (up/down) buttons.  Unfortunately, they cause Firefox to navigate back/forward.

xev reports that these buttons are mapped as 9 and 10 - so how do I get them behaving properly?  I have had a go with xbindkeys, but can't see how that provides a solution to me.

All advice appreciated!

Charlie

---

### Post by Xgen on 2008-09-01
Try  [http://ubuntuforums.org/showthread.php?t=455656]("http://ubuntuforums.org/showthread.php?t=455656")

---

### Post by FokkerCharlie on 2008-09-01
Thanks Xgen

I have tried btnx, but for some reason the app doesn't seem to recognise my mouse!  No idea why that should be...  other ideas?  Is there a way within FF, perhaps?

Charlie

---

### Post by FokkerCharlie on 2008-09-03
OK, I now have btnx detecting my mouse...

However, there is a further issue.  What is happening, according to xev, is when I am holding the 'scroll up' button, a button 8 pressed event occurs, then button 4 press/release events for as long as the button is held, and then finally one button 8 released event.

That seems to be preventing btnx detecting button 8, as its detection is being prevented by button 4!

Hmmmmmm.

Go on, give us a clue!
Charlie

---

### Post by Shazaam on 2008-09-03
If I remember right there is a checkbox under Button config that says something about multiple button presses (limit). I have btnx set up in Gutsy but I am on Hardy right now.

---

### Post by FokkerCharlie on 2008-09-04
Hi Shazaam

The only thing I could find is a check-box for 'Force immediate button release'.  Using that does not have the desired effect!

I see that in the config files, the buttons reference 'rawcodes'; is it possible to find my rawcode from button 8 and manually edit the file?  I can't see an equivalent piece of data from xev.

Cheers
Charlie

---

